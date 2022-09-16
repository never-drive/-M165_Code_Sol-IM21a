### Übung 3.01: MongoDB-Datenbank wiederherstellen
Stellen Sie die MongoDB-Datenbank sample_mflix in Ihrem lokalen Server 
wieder her. Siehe dazu auch die entsprechenden Links im 01_Intro/01_Demo.md

### Download-Links
* MongoDB Tools Download: 
https://www.mongodb.com/try/download/database-tools
* Repo Sample-MongoDB:
https://github.com/huynhsamha/quick-mongo-atlas-datasets


### How to restore
```bash
cd <to your local repo-clone>
mv quick-mongo-atlas-datasets sample-db
cd sample-db
# restore sample-db airbnb
mongorestore --host localhost --port 27017 --db mflix --dir ./dump/sample_mflix
```
