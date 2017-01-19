
# hastebin docker container
This is just a has autobuild repo for a haste-server

Check out the original source [haste-server](https://github.com/seejohnrun/haste-server)

## Start a hastebin instance
```
docker run -p 7777:7777 -d jonberenguer/hastebin-server
```

## POST to hastebin
Simple client-side function to post to hastebin
### For Linux
```
haste() { a=$(cat); curl -X POST -s -d "$a" http://localhost:7777/documents | awk -F '"' '{print "http://localhost:7777/"$4}'; }
```
### For Windows
```
function haste { param([Parameter(Mandatory=$True,ValueFromPipeline=$True,ValueFromPipelinebyPropertyName=$True)] [string[]] $data) ; $key = (Invoke-RestMethod -Uri http://localhost:7777/documents -Method POST -Body $data).key.trim() ; Write-Host "http://localhost:7777/$key"}
```

Test command after you created the function:
```
echo "Successful POST" | hastebin
```
