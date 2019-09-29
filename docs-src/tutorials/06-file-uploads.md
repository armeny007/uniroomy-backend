## Add house_photo using Altair GraphQL client example 

<a href="./example-upload-altair.png" target="_blank"><img src="./example-upload-altair.png"></a>

## add house_photo using curl

```
curl --request POST \
  --insecure \
  --url https://uniroomy.co.uk:3003/api/ \
  --header 'accept: application/json' \
  --header 'accept-encoding: gzip, deflate, br' \
  --header 'connection: keep-alive' \
  --header 'dnt: 1' \
  --header 'origin: http://uniroomy.co.uk:3003' \
  --form 'operations={"query": "mutation ($file: Upload!){ addHousePhoto(input: {house_id: 2, url: $file}){ _id url house_id } }",   "variables": { "file": null } }' \
  --form 'map={ "nFile": ["variables.file"] }' \
  --form nFile=@/xxx/yyy/zzz.png
```

Replace /xxx/yyy/zzz.png with a file path
