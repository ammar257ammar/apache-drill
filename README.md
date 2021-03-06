# apache-drill

## get apache-drill 
e.g. for version 1.17.0 ([Mirrors](https://drill.apache.org/download/))
```bash
wget -N http://apache.40b.nl/drill/drill-1.17.0/apache-drill-1.17.0.tar.gz
```

## Build
e.g. for version 1.17.0
```
docker build -t apache-drill:1.17.0 . --build-arg VERSION="1.17.0"
```

## Run
```
docker run -dit --rm --name drill -v /data:/data:ro -p 8047:8047 -p 31010:31010 apache-drill:1.17.0
```

## Apache Drill memory
#### Memory can be configured by passing environment variables as following:
##### NOTE that without passing the env variables, memory settings configured to work with DSRI at UM will be applied.
```
docker run -dit --rm -p 8047:8047 -p 31010:31010 --name drill \
	-e DRILLBIT_MAX_PROC_MEM='8G' \
	-e DRILL_HEAP='4G' \
	-e DRILL_MAX_DIRECT_MEMORY='3G' \
	-e DRILLBIT_CODE_CACHE_SIZE='1G' \
	-v /data:/data:ro apache-drill
```


## Test
1. Navigate to http://localhost:8047
2. Try following query ```show files in dfs.root.`/data/` ```
