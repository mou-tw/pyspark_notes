
```
df.write\
.format()\ #delta, parquet etc
.option("mergeSchema",'true')\
.option("replaceWhere", [replace string]) \
.mode()
.save() # saveAsTable or save

ex:
replace string
columns_name == "sample"


```