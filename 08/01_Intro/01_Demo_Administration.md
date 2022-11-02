### Backup und Restore 
1. Backup/Dump (Datensicherung)
```mongodump --host localhost --port 27017  --db mflix --out . ```
2. Restore (Wiederherstellen)
```mongorestore --host localhost --port 27017 --db mflix --dir ./mflix```



### Export
### Examples


```
# Export thea
mongoexport --host localhost --port 27017 --db=mflix --collection=theaters
mongoexport --host localhost --port 27017 --db=mflix --collection=theaters --out=mflix_theaters.json
mongoexport --host localhost --port 27017 --db=mflix --collection=theaters --type=CSV \
--fields=location.address,location.address.city,location.address.state
mongoexport --host localhost --port 27017 --db=mflix --collection=theaters --type=CSV \
--fields=location.address.street1,location.address.zipcode,location.address.city,location.address.state  \
--out=mflix_theaters.csv

mongoexport --host localhost --port 27017 --db=mflix --collection=theaters --limit=10 --sort="{theaterId:1}" 
```
Remark
The last export can be checked with a similar query
```
use mflix
db.theaters.find({},{theaterId:1})
.limit(10)
.sort({theaterId:1})
```


```
--type: This will affect how the documents are printed in the console and defaults to JSON. For example, you can export the data in Comma-Separated Value (CSV) format by specifying CSV.
--fields: This specifies a comma-separated list of keys in your documents to be exported, similar to an export level projection.
--skip: This works similar to a query level skip, skipping documents in the export.
--sort: This works similar to a query level sort, sorting documents by some keys.
--limit: This works similar to a query level limit, limiting the number of documents outputted.
```
More options can be printed with the --help argument
```
mongoexport --help
```