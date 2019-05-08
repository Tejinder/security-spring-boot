# security-spring-boot
This repository demonstrates integration of Security in Spring Boot

In this repository I have adding Spring Security to perform authentication and authorization for the requested URLs (REST API endpoints)

A normal GET and POST will return a 401, all endpoints are protected, need authentication.

 Send a GET request along with user login.

> curl localhost:8080/books -u user:password

> curl localhost:8080/books/1 -u admin:password


Try to send a POST request with ‘user’ login, it will return 403, Forbidden error. This is because the user has no right to send a POST request.

> curl -X POST localhost:8080/books -H "Content-type:application/json" 
	-d {\"name\":\"dummyName\",\"author\":\"tejinder\",\"price\":\"9.88\"} -u user:password

{
	"timestamp":"2019-02-25T04:16:58.702+0000",
	"status":403,
	"error":"Forbidden",
	"message":"Forbidden",
	"path":"/books"
}


 Try to send a POST request with admin login

> curl -X POST localhost:8080/books -H "Content-type:application/json" 
	-d {\"name\":\"dummyName\",\"author\":\"tejinder\",\"price\":\"9.88\"} -u admin:password
	
{
	"id":2,
	"name":"dummyName",
	"author":"tejinder",
	"price":9.88
}
