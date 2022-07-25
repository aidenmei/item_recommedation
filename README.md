# TL;DR
This is a event search and recommmendation engine written in Java, implementing keyword extraction and content-based recommendation. It implements RESTful APIs using Java servlets, retrieves event descriptions using TicketMaster API and stores data in MySQL. Users can: 
- Search nearby available event
- Save favorite event to account
- Get recommendated event based on extracted keywords from favorites
 
 ### Demo
 
 - Link: http://ec2-54-91-165-108.compute-1.amazonaws.com:8080/Jupiter/#
 

## Behind the Scenes 
Java servlets are Java classes to handle RPC on the server side.Java servlets are created in this app: ```searchItem```,```recommendItem```,```ItemHistory```,```favoriteItem```.

```searchItem```communicates with the TicketMaster API to get available events.
```recommendItem```does both to relay keywords from database to the search. 

A recommendation system seeks to predict the "rating" a user would give to an item. **Content-based recommendation** makes such prediction based on similarity shared between items themselves. This is usually used when we don't have enough user activity to begin with. In contrast, **user-based recommendation** makes the prediction based on similarity between users, while **item-based recommendation** will consider both similarity between items as well as the user's history of liking similar items. 

Session is used to store a series of interations of the user currently visiting the webapp. When a user logs in, a session ID is assigned to the user. Users need to provide session ID to access resources that require authentication. ```HttpSession``` is an interface provided by the servlet API. HttpSession allows us to set attributes in key-value pairs that can be retrieved in future requests. The session ends when the user logs out or inactive after a predetermined period of time.

### Dependencies
- TicketMaster API: https://app.ticketmaster.com/discovery/v2/
- Apache Tomcat: http://tomcat.apache.org/
- MySQL Java connector: https://mvnrepository.com/artifact/mysql/mysql-connector-java
