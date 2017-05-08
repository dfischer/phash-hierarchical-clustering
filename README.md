# phash-hierarchical-clustering

An app clusters a given set of images and displays results via a simple JavaFX GUI.
First, [Perceptual Hashing](http://www.phash.org/) is used to map the images to binary feature vectors. Then 
[Agglomerative Hierarchical Clustering](https://en.wikipedia.org/wiki/Hierarchical_clustering) with 
[Hamming distance](https://en.wikipedia.org/wiki/Hamming_distance) as a distance measure is used to group similar
binary vectors.

Note: we use a low hard-coded `cutHight` value of `2.0` in order to cut the dendrogram tree into *small* clusters with 
low number of outliers. You might experiment with different values of `cutHeight` in the 
[HCluster](https://github.com/wolny/phash-hierarchical-clustering/blob/master/src/main/scala/com/brandwatch/HCluster.scala)
depending on your dataset size and required 'quality' of the clustering.

## Running

Build the project with `sbt assembly`. This will generate a `phash-hierarchical-clustering-${version}.jar` uberjar 
file in the `target/scala-<scalaVersion>` subdirectory (where `${version}` is the current version defined in `build.sbt`).

Run the application from the `.jar` with the `java -jar` command, e.g.:
- `java -jar target/scala-2.12/phash-hierarchical-clustering-assembly-1.0.jar <imageDirectory>`

where `<imageDirectory>` is the folder where the images are stored (use as many images as possible for better results).
