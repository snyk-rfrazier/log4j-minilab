# LOG4J Mini Lab

The Log4J incident from December 2021 was one of the biggest and most impactful security issues in recent Java history. 

In this minilab, we will look into the vulnerability and try to create our own server. 

### Check out this repository

```
git clone https://github.com/bmvermeer/log4j-minilab.git
```

The repository contains an __application__ and a template for a malicious __log4shell server__.

### Running the application
```
cd log4japp
./mvnw compile spring-boot:run 
```

### Running the server
```
cd log4shell-server 
./mvnw compile exec:java
```

The application contains a vulnerable Log4j version. It evaluates JNDI commands and you can connect to an LDAP server that you own to create arbitrary code execution.
The log4shell-server already contains an incomplete LDAP server based on the [marschalsec](https://github.com/mbechler/marshalsec/blob/master/src/main/java/marshalsec/jndi/LDAPRefServer.java) project by [Moritz Bechler](https://github.com/mbechler). This server gives a reference to Evil.class which is served to you using an HTTP server. Both the LDAP server and the HTTP are fully functional.

## Assignment 1 
### check if we are vulnerable

- Startup the log4japp 
- go to http://localhost:8080/
- try to login with an incorrect username and password.
- See in the console what is logged
- Check if we use a log4j version that is vulnerable (<2.15) 
	- ​​[Hint1](/hints/a1/hint1.md)
- Startup the log4shell-server and try to connect to to the server
	- [Hint2](/hints/a1/hint2.md)
- If the console gives you a `javax.naming.NamingException` with `Root exception is java.lang.ClassCastException`, than you are on the correct spot.

## Assignment 2
### Implement class Evil


Implement class Evil so it will print “HACKED AT DEVOXXUK” when we load it using the LDAP string from before.

- [Hint 1](/hints/a2/hint1.md)
- [Hint 2](/hints/a2/hint2.md)
- [Hint 3](/hints/a2/hint3.md)
- [Hint 4](/hints/a2/hint4.md)
- [Hint 5](/hints/a2/hint5.md)

## Assignment 3
### Try to execute a command. 

For instance open the calculator on your machine.


- [Hint 1](/hints/a3/hint1.md)
- [Hint 2](/hints/a3/hint2.md)
- [Hint 3](/hints/a3/hint3.md)

## Assignment 4
### Create a reversed shell attack

- Install netcat on your machine 
- Open netcat and listen to port 9001 (in a new shell window)
	- [Hint 1](/hints/a4/hint1.md)
- Edit your Evil class so it opens a connection to your (local) host on port 9001
	- [Hint 2](/hints/a4/hint2.md)
	- [Hint 3](/hints/a4/hint3.md)
	- [Hint 4](/hints/a4/hint4.md)
- If everything works out, netcat is now connected to your machine and you have shell access. Imagine doing this on a remote machine :)





