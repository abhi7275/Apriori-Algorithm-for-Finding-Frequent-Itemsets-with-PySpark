# Apriori-Algorithm-for-Finding-Frequent-Itemsets-with-PySpark
Overview:

This project implements the Apriori algorithm in a distributed computing scenario using PySpark. The goal is to identify sets of items frequently bought together based on point-of-sale data from a grocery store. The algorithm's efficiency is crucial for scalability, making it suitable for large retail datasets.
Environment Setup:

    Ensure you have the necessary libraries installed, including PySpark.
    Set up a SparkConf and SparkContext for distributed computing.
    Initialize a SparkSession.

python

import itertools
import findspark
findspark.init()
import pyspark
from pyspark.sql import *

conf = pyspark.SparkConf().setAppName('Apriori').setMaster('local')
sc = pyspark.SparkContext(conf=conf)
spark = SparkSession(sc)

Algorithm Implementation:
1. Generate Combinations - Parent Intersection Property

    A pre-check function identifies potential combinations based on the parent intersection property.

2. Generate Combinations - Subset Frequency Property

    A post-check function filters combinations based on the subset frequency property.

3. Count Check

    Check the count of filtered combinations against a support threshold.

4. Generate k-Size Combinations

    A generator function orchestrates the entire process for a given k.

5. Generate Singles

    Identify single items that meet the support threshold.

6. The Worker Partition Mapper

    The apriori function serves as the worker node, executing the Apriori algorithm on a partition.

7. Load Data and Preprocess

    Load data from the provided CSV file and preprocess it for analysis.

8. The Distributed Transform

    Apply the apriori function to each partition of the dataset in a distributed manner.

9. Auxiliary Function to Check Presence

    An auxiliary function checks the presence of combinations in each row.

10. Count Check at Master

    Check the count of filtered combinations at the master node.

Running the Project:

    Ensure PySpark and other required libraries are installed.
    Load the provided dataset (Dataset.csv).
    Execute the provided Python code in a PySpark environment.

Results:

The project outputs possible frequent itemsets based on the Apriori algorithm, providing insights for strategic product placements in the grocery store
