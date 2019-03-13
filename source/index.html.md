---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - curl

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the CENNZ scan API! You can use our API to access CENNZ scan API endpoints, which can get information on various transactions, blocks, and address from CENNZ net (RIMU version)

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Blocks endoint

## Get All Blocks

```curl
curl -X GET "https://dh8cl297ul.execute-api.ap-southeast-1.amazonaws.com/api/blocks?limit=30&page=1" -H "accept: application/json"
```

### HTTP Request

`GET https://dh8cl297ul.execute-api.ap-southeast-1.amazonaws.com/api/blocks`


> The HTTP request returns the following JSON structure:
> Code 200 - Success

````json
{
  "params": {
    "limit": 30,
    "offset": 0,
    "start_time": 1540608690,
    "end_time": 1548384690
  },
  "result": {
    "number": 158174,
    "hash": "0x9965008d9b0e6f3d07f0b274c0dfaff4bdc86f99a0f229c11f3b5dbb8ab00a68",
    "parentHash": "0xf710b4cd572c6f078f4b59405ee35dc3f40d58e76aeceb5beeae7b9d3f720c7a",
    "stateRoot": "0x71d488ad7d7d95a68d6b1445727890c3c54d1fdb9e8393d8cf94f30755eaf99c",
    "extrinscicsRoot": "0xc8d89314f6372c38e66292de1278970f93ea1b541aa401fa52aa4ce941fbcf7c",
    "timestamp": 1548384684,
    "transactionCount": 0,
    "baseFee": 10,
    "byteFee": 1,
    "transferFee": 1,
    "author": "5DcS1HEPFaPJVwoU52HLZNkuikoP5Qey2eU5B26v6D7qjkiB",
    "extrinsicsCount": 1,
    "validators": [
      "5DcS1HEPFaPJVwoU52HLZNkuikoP5Qey2eU5B26v6D7qjkiB",
      "5G6tDRK9KSWLx3zL4gMnzh2K6QUNAb6EGCiyPMTAzCmt45A4",
      "5EKGZwAuwvVpVaGWZJ3hYDqTSxQCDDUgeMv36M4qLq7wtWLH"
    ],
    "status": "complete"
  }
}
````
> Code 400 - Error

> Possible response 1:

````json
{
  "params": {
    "Code": 400,
    "Message": "start/end time must be less than the current timestamp ({current_time})!"
  }
}
````
> Possible response 2:

````json
{
  "params": {
    "Code": 400,
    "Message": "start/end time must be greater than zero!"
  }
}
````
> Possible response 3:

````json
{
  "params": {
    "Code": 400,
    "Message": "start time must be smaller than end time!"
  }
}
```

This endpoint retrieves all the blocks from cennznet restricting to 30 blcoks by default.



### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
limit | 30 | (Optional) Specifies the number of records per page. If set to true, the result will get 30 blocks by defult.
page | 1 | (Optional) Displays the page number. If set to true, the result will be displayed in 1 page.
start_time | - | (Optional) Represents the lower bound for time range and takes last 90 days from end_time(UTC) as default value in UNIX epoch timestamp format.
end_time | - | (Optional) Represents the upper bound for time range and takes current time(UTC) as default value in UNIX epoch timestamp format.

## Get latest Blocks

```curl
curl -X GET "https://dh8cl297ul.execute-api.ap-southeast-1.amazonaws.com/api/blocks/latest" -H "accept: application/json"
```

### HTTP Request

`GET https://dh8cl297ul.execute-api.ap-southeast-1.amazonaws.com/api/blocks/latest`


> The HTTP request returns the following JSON structured:

> Code 200 - Success
````json
{
  "params": {
    "limit": 30,
    "offset": 0,
    "start_time": 1540608690,
    "end_time": 1548384690
  },
  "result": {
    "number": 158174,
    "hash": "0x9965008d9b0e6f3d07f0b274c0dfaff4bdc86f99a0f229c11f3b5dbb8ab00a68",
    "parentHash": "0xf710b4cd572c6f078f4b59405ee35dc3f40d58e76aeceb5beeae7b9d3f720c7a",
    "stateRoot": "0x71d488ad7d7d95a68d6b1445727890c3c54d1fdb9e8393d8cf94f30755eaf99c",
    "extrinscicsRoot": "0xc8d89314f6372c38e66292de1278970f93ea1b541aa401fa52aa4ce941fbcf7c",
    "timestamp": 1548384684,
    "transactionCount": 0,
    "baseFee": 10,
    "byteFee": 1,
    "transferFee": 1,
    "author": "5DcS1HEPFaPJVwoU52HLZNkuikoP5Qey2eU5B26v6D7qjkiB",
    "extrinsicsCount": 1,
    "validators": [
      "5DcS1HEPFaPJVwoU52HLZNkuikoP5Qey2eU5B26v6D7qjkiB",
      "5G6tDRK9KSWLx3zL4gMnzh2K6QUNAb6EGCiyPMTAzCmt45A4",
      "5EKGZwAuwvVpVaGWZJ3hYDqTSxQCDDUgeMv36M4qLq7wtWLH"
    ],
    "status": "complete"
  }
}
```

This endpoint retrieves the latest block from cennznet.

