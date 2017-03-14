# README

Pygrant contains a class that utilizes the request library to interact with grunt dockers

```
from pygrant import *

g = grunt("http://ril-gpu10:9916")
# Syntax 1
j=g.classeval
j.datset="/Users/m112447/Documents/TestData/diab.csv"
j.output="classeval.zip"
job =j()
job.wait()
# Write some output
job.save_output("output", "/Users/m112447/Downloads/")
```
