# Mongo / Voyage FAQ

---

# MongoDB FAQ

## Q How to set the db location?
Run
```
mongod --config .../mongodb.config
```
Where the config file contains
```
dbpath=/path-to-db-dir
```

## Q How do I specify a db name other than "test"?
```
use *db*
```

## Q How do I find out what collections are defined?
```
show collections
```
or:
```
db.getCollectionNames()
```

## Q How do I drop all collections?
```
db.getCollectionNames().forEach(function(n){db[n].remove({})})
db.dropDatabase()
```

## Q How to import/export JSON files?
Use mongoimport / mongoexport tools
```
mongoimport --db users --collection contacts --file contacts.json
```

---
# Voyage FAQ

## Q How do I retrieve objects from an existing DB?


