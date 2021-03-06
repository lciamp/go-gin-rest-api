# go-gin-rest-api-f1
go-gin-rest-api

Tutorial from: https://golang.org/doc/tutorial/web-service-gin
I just used F1 Drivers.

```go get .```  to get gin

```go run .``` to start server

All logic is in ```main.go```

## List Drivers:

```curl localhost:8080/drivers``` 

Result:
```
[
    {
        "id": "1",
        "firstName": "Charles",
        "lastName": "LeClerc",
        "team": "Scuderia Ferrari",
        "number": 16
    },
    {
        "id": "2",
        "firstName": "Carlos",
        "lastName": "Sainz",
        "team": "Scuderia Ferrari",
        "number": 55
    }
]
```

Gin logging:
```[GIN-debug] GET    /drivers                  --> main.getDrivers (3 handlers)
[GIN-debug] Listening and serving HTTP on localhost:8080
[GIN] 2021/10/16 - 22:40:57 | 200 |     141.856µs |       127.0.0.1 | GET      "/drivers"
```

## Add Driver:
```bigquery
curl http://localhost:8080/drivers \
    --include \
    --header "Content-Type: application/json" \
    --request "POST" \
    --data '{"id": "3", "FirstName": "Lewis", "LastName": "Hamilton", "Team": "Mercedes AMG Petronas", "Number": 44}'
```

Result:
```
HTTP/1.1 201 Created
Content-Type: application/json; charset=utf-8
Date: Sun, 17 Oct 2021 03:26:35 GMT
Content-Length: 118

{
    "id": "3",
    "firstName": "Lewis",
    "lastName": "Hamilton",
    "team": "Mercedes AMG Petronas",
    "number": 44
}%
------------------------------------------------------------```
~ » curl http://localhost:8080/drivers                                                                                                          lou@Lous-iMac
[
    {
        "id": "1",
        "firstName": "Charles",
        "lastName": "LeClerc",
        "team": "Scuderia Ferrari",
        "number": 16
    },
    {
        "id": "2",
        "firstName": "Carlos",
        "lastName": "Sainz",
        "team": "Scuderia Ferrari",
        "number": 55
    },
    {
        "id": "3",
        "firstName": "Lewis",
        "lastName": "Hamilton",
        "team": "Mercedes AMG Petronas",
        "number": 44
    }
]
```

gin logging:
```
[GIN-debug] Listening and serving HTTP on localhost:8080
[GIN] 2021/10/16 - 23:26:35 | 201 |     129.192µs |       127.0.0.1 | POST     "/drivers"
[GIN] 2021/10/16 - 23:26:59 | 200 |      67.174µs |       127.0.0.1 | GET      "/drivers"
```

## Driver by ID:
```curl localhost:8080/drivers/1``` 

Result:

```
{
    "id": "1",
    "firstName": "Charles",
    "lastName": "LeClerc",
    "team": "Scuderia Ferrari",
    "number": 16
}
```

gin logging: 
```
[GIN] 2021/10/17 - 01:11:18 | 200 |     103.605µs |       127.0.0.1 | GET      "/drivers/1"
```