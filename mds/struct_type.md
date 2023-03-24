Transform JSON file into spark dataframe
```
import requests
import json
from pyspark.sql.types import *
import pyspark.sql.functions as F

url = "...."

payload={}
headers = {}

response = requests.request("GET", url, headers=headers, data=payload)

# if response is not a list structure
lst = []
lst.append(json.loads(response.text))

schema = StructType([
  StructField("normal", StringType(), True),
  StructField("structure1", StructType([
        StructField('structure2',StructType([
            StructField('structure3',MapType(StringType(),StringType()), True),
            StructField('structure3',MapType(StringType(),StringType()), True),
            StructField('structure3',MapType(StringType(),StringType()), True),
        ]), True),
  
    ]
), True),

])


spark.createDataFrame(lst, schema).display()

```