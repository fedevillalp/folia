+++
author = ""
date = ""
draft = true
hero = ""
title = "Calculate Row Averages "
type = "blog"

+++
\`\`\`python:

from pyspark.sql.functions import udf, array

from pyspark.sql.types import DoubleType

\# 1. Register the UDF

avg_cols = udf(lambda array: sum(array)/len(array), DoubleType())

\# 2. Specify the arguments of the UDF -> an array of columns

df.withColumn("average", avg_cols(array("marks1", "marks2"))).show()

\`\`\`