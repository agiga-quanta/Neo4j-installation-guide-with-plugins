# Handy guide to installing Neo4j Desktop and some useful plugins
This repository provides a step-by-step instruction to the installation of Neo4j Desktop and some example of using it. Later on, we'll also be introduced to some useful plugins such as `APOC` - known for its extensive functions and queries to furether utilize Neo4j - and `Graph Data Science` - which contains libraries of graph algorithms and tools for machine learning. Lastly, the guide also expanded to include an instruction to access and use `Neo4j Bloom` - a visualization tool developed for Neo4j. 

This guide is also included in a YouTube playlist showing how to download and install `neo4j` Desktop [here](https://youtube.com/playlist?list=PL3KBtMOTv6gM73L33Ie1kHHKp6SXbEpyH)

## 1/ Download and install `Neo4j Desktop`: 
### [Neo4j Desktop](https://neo4j.com/docs/desktop-manual/current/) *([download here](https://neo4j.com/download/))*
> Neo4j Desktop is the mission control center for Developers. It's free with registration, and it includes a free development license for Neo4j Enterprise Edition allowing you to use Neo4j Enterprise on your local desktop for developing applications.  
> 
Neo4j Desktop can be downloaded and installed on Windows without admin permission. When accessing the link above and begin the download process, however, you will have to enter some information to generate a personalized `product key`. This key will be valid for 1 year.  
![image](https://user-images.githubusercontent.com/60938608/217350562-14594681-b912-4cb6-b7ad-2082e3617a4a.png)
  
Also the installation will prompt you to either install for your own user account on the computer (such as below), or for everyone who uses the computer. The guide will proceed with install for local user only.  

![image](https://user-images.githubusercontent.com/60938608/217351282-5f736acd-8e19-4cf0-9ed1-257bca97e8ab.png)  

When selected the path to install, Neo4j will proceed to install and once complete, you can tick `Run Neo4j Desktop` to launch, else untick and proceed to `Finish`.  

![image](https://user-images.githubusercontent.com/60938608/217351306-4e2b0bd4-9d4f-4bf8-a1cc-55b99fd8fbcd.png)

## 2/ Deploy `Neo4j Enterprise Server` on `Neo4j Desktop`: 
### [Neo4j Enterprise:](https://neo4j.com/product/neo4j-graph-database/)  

> Neo4j Enterprise edition allows you to develop a graph database with enterprise level security and efficiency. The included Enterprise version with Desktop does not have full functionality of a server, and is limited to run only locally. The full version would also include more security and efficiency for large scale usage.
  
Once you launched Neo4j Desktop for the first time, you will be prompted to paste `product key`. Copy the key from before and input into the Software key on the right side. In case you forgot to save the old key, you can re-register on the left side to get a new key.  
![image](https://user-images.githubusercontent.com/60938608/217350863-29211de0-c8df-47c0-81f1-b18804d0f98d.png)

When Neo4j completed its setup, the Movie DBMS will be availble immediately and already up and running. 
![image](https://user-images.githubusercontent.com/60938608/217351243-c87b0347-26b8-4baf-a157-03fca854ed4c.png)

Click on `Open` to launch Neo4j Browser, a tool for interacting with Neo4j Desktop and Neo4j Enterprise Server. 
![image](https://user-images.githubusercontent.com/60938608/217351890-aa98d133-1bdb-4005-b6fa-dd0b7f50fdb9.png)  
Once inside, you will be greeted with this interface:  
![image](https://user-images.githubusercontent.com/60938608/217351213-bb7316f5-4172-480d-b430-59c4aea82c07.png)

Do note that your current username is `neo4j` as seen below.
![image](https://user-images.githubusercontent.com/60938608/217351021-47e61936-0d52-4e70-b655-ca4acf5165dd.png)

Within this interface, your main focus would be the top bar, the result under it, and the left column:
pic of layout

The left column consists of 4 things: 
 - Graph informations

 - Favorite scripts

 - Project scripts

 - Neo4j Cypher guides

## 3/ Installing plugins `APOC` and `Graph Data Science`: 
### [APOC:](https://neo4j.com/labs/apoc/)
> APOC (Awesome Procedures on Cypher) is an add-on library for Neo4j that provides hundreds of procedures and functions adding a lot of useful functionality.Those are custom implementations of certain functionality, that can’t be (easily) expressed in Cypher itself. They are implemented in Java and can be easily deployed into your Neo4j instance, and then be called from Cypher directly.  

### [Graph Data Science:](https://neo4j.com/docs/graph-data-science/2.3/introduction/)
> The Neo4j Graph Data Science (GDS) library provides efficiently implemented, parallel versions of common graph algorithms, exposed as Cypher procedures. Additionally, GDS includes machine learning pipelines to train predictive supervised models to solve graph problems, such as predicting missing relationships.  

In order to install the 2 plugins `APOC` and `Graph Data Science`, select the project:  
![image](https://user-images.githubusercontent.com/60938608/217351972-21bd195c-7356-4757-9e09-17a54ef14d20.png)  

Once selected, and right side column would pop out with 3 options to choose: `Details`, `Plugins`, and `Upgrade`. Select the `Plugins` and click on both `APOC` and `Graph Data Science Library`.   
![image](https://user-images.githubusercontent.com/60938608/217352202-01018d59-558a-419d-b0f9-05cf5a44404a.png)  
Once selected, a blue button will show up with the words `Install`. Select it and wait for installation.

## 4/ Deploying databases on Neo4j. 
When opening the `Movie DBMS` project, neo4j starts with a movie database loaded, and to present the database, you can run a query below to see all the nodes and their relationships in the graph:
```cypher
  MATCH (any)
  RETURN any
```
- This query would find any thing in the graph and return it to user. Since the graphs are made with `Nodes` that have informations as well as their `Relationships` to one another, we get a graph of everything return to us.
![image](https://user-images.githubusercontent.com/60938608/217366592-7314475a-207b-4174-8d59-b4abb0fb54e9.png)

Note that the graph above is too small and would not be overly useful in this situation. However, we know that there is an actor in here name "Keanu Reeves", we can use that to our advantage to make some more tailored queries such as: 
```cypher
MATCH (actor:Person {name: "Keanu Reeves"})-[:ACTED_IN]->(movies) 
RETURN movies  
```
- This would return us all movies that Keanu Reeves have acted in. 
![image](https://user-images.githubusercontent.com/60938608/217309666-eb26aef4-417d-413c-a0c1-b3892913e9fa.png)

Because of this flexibility and easy to understand language, we can write more detailed queries such as getting who also acted with Keanu Reeves via below query: 
```cypher 
MATCH (actor:Person {name: "Keanu Reeves"})-[:ACTED_IN]->(movies)<-[ACTED_IN]-(otheractor:Person) 
RETURN actor, movies, otheractor
```
- This query finds not only the movies that Keanu Reeves has acted in, but also who else are in those movies (that has their name noted in the database) *(Keanu is in the center, Orange, where purple are the other films, and other actors are in orange pointing into the purple node)*
![image](https://user-images.githubusercontent.com/60938608/217366712-b8dae2bd-d411-4eab-a0f1-2416a4b38c3a.png)

These works because in the database, both `movies` and `actors` are noted as `Nodes` and their involvement are noted as `Relationships`.

## 5/ Deploy `Bloom`
### [Bloom:](https://neo4j.com/docs/bloom-user-guide/current/)
> Neo4j Bloom is a visualization tool. While Neo4j Browser allows users to access and run detailed queries, Bloom focuses on the overall graph. Bloom now comes pre-packaged within all Neo4j Desktop 1.2.6 and later, Neo4j Desktop will also automatically search for the latest version of Bloom and install it if it is either missing or an older version.  

Neo4j Bloom will only run if there is a Neo4j Server. The reason why Bloom can now run on Neo4j Desktop is because by version 1.2.6 and later, Neo4j Desktop included a limited license of Neo4j Enterprise Server. Since the version downloaded in this guide is 1.5.7, Bloom is available for us, and already activated. To see it, we go back to Neo4j Desktop and hover on the arrow next to the `Open` drop down menu.
![image](https://user-images.githubusercontent.com/60938608/217371193-5e9cf716-d1ca-4f67-8866-60d2c03675ce.png)

A new window will open that looks like this. This Bloom is tied to the project we open - Movie DBMS - hence anything we have in it, such as the Movie DB, will be available to Bloom here. 
![image](https://user-images.githubusercontent.com/60938608/217307061-7789f9c7-5e84-4488-9b56-e4bb5ae3a7b6.png)

This display has 2 things that are important to us:
- This bar is where you can input your queries, use filters, as well as the perspective button:
![image](https://user-images.githubusercontent.com/60938608/217372261-d303fece-7421-4111-931c-848bd17f2cf1.png)

- Available data such as the `Nodes` and the `Relationships` are on the right side:
![image](https://user-images.githubusercontent.com/60938608/217371879-678b1144-eaf7-439a-b1dd-b8454d945b04.png)

Here, we can generate the queries such as above in Bloom via entering nodes or relationships into the search bar:
Similar to the *Show me everything* query above, we can recreate it by going to the search bar, select `Person` and `Movie` and click Enter.
![image](https://user-images.githubusercontent.com/60938608/217373097-7ad73b3c-e6e7-477e-82c2-d293dd7a868c.png)  

The result will look like this:  
![image](https://user-images.githubusercontent.com/60938608/217372805-f8e9bc54-ded2-4735-b945-f3deda2abed4.png)  
You can then add a filter to find specifics, such as "Keanu Reeves" above:  
![image](https://user-images.githubusercontent.com/60938608/217313619-9cadecb6-587b-4df8-a120-5e3b40218d52.png)

This is the final result, with zooming in to see which movies Keanu is in:
![image](https://user-images.githubusercontent.com/60938608/217373728-d84f5dc0-0a81-4b7a-b0ea-6a43e9b87b8d.png)

Overall, Bloom is a very interactive visualization tool, and further details about Bloom can be accessed via the link below
[Neo4j Bloom 2.6 - Neo4j Bloom](https://neo4j.com/docs/bloom-user-guide/current/)
