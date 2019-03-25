# Spark 

This creates a local Spark cluster with:
- A Spark master instance
- 3 Spark workers
- A Jupyter notebook instance that can be used to submit jobs to the cluster

The intention is to play around with Spark and explore its capabilities.

# Initializing Spark in a Jupyter notebook

```python
# Prefer using SparkSession over SparkContext as SparkSession is a newer API
from pyspark.sql import SparkSession # Only run after findspark.init()
spark = SparkSession.builder.appName('Demo').master('spark://spark-master:7077').getOrCreate()
```
The script above assumes that the master instance is visible on the network as "spark-master" and on port 7077 (Default for Spark master instances).
