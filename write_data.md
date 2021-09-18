# Zuri Chat Core API (Data write Endpoint)
​
Getting started with the write endpoint is easy, all you need to do is to get parameters and arrange them in proper order as shown below. You then make a POST request to the endpoint and you should receive a status code of 200 showing your write request was successful.
​
Contact Support: Email: developer@zuri.chat
​
​
## Write 
## POST /data/write
​
```sh
https://api.zuri.chat/v1/data/write
```
Let's the plugin make a write request to the data endpoint.
​
## Request Headers
Content-Type: application/json
​
## Body
Format type : raw(json)
```sh
{
    "plugin_id": "string",
    "organization_id": "string",
    "collection_name": "string",
    "payload": {},
    "bulk_write": true,
    "object_id": "string",
    "filter": {}
}
```
## Examples
​
### For a successful write request
​
##### Request:
```sh
curl --location --request POST 'https://api.zuri.chat/v1/data/write' \
--header 'Content-Type: application/json' \
--data-raw '{
    "plugin_id": "string",
    "organization_id": "string",
    "collection_name": "string",
    "payload": {},
    "bulk_write": true,
    "object_id": "string",
    "filter": {}
}'
```
​
##### Response:
```sh
{
 "status": "204",
 "message": "resource successfully written",
 "data": {
  "written_count": 0
 }
}
```
​
### For an unexpected error
​
##### Request:
```sh
curl --location --request POST 'https://api.zuri.chat/v1/data/write' \
--header 'Content-Type: application/json' \
--data-raw '{
    "plugin_id": "string",
    "organization_id": "string",
    "collection_name": "string",
    "payload": {},
    "bulk_write": true,
    "object_id": "string",
    "filter": {}
}'
```
​
##### Response:
```sh
{
 "status": "400",
 "message": "there was an unexpected error",
}
```
##### Request Body Schema 
​
| Plugin | README |
| ------ | ------ |
| Plugin_ID* | String: The Plugin ID |
| Organization_ID* | String: The ID of the organization the plugin belongs to |
| Collection_name* | String: The name of the collection plugin wants to add data to |
| Bulk_write | Boolean: The value indicates whether many documents are to be written or not |
| Object_id | String: The ID of previously inserted data at the server side |
| Filter | Query to be matched |
| Payload* | Actual data the plugin wants to add to the database |
​
##### Things to note:
- There are no parameters in the url, everything required is going to be part of the payload.
- The required values are starred in the schema.
- Only valid id's, collection name and payloads will be accepted. If not provided 400 status errors will be raised
