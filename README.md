# Neo4j-install-guide-and-plugins
This repository provides a step-by-step instruction to the installation of Neo4j version 1.5.7 and some useful plugins such as `APOC` and `Graph Data Science`. The guide also expanded to include an instruction to access and use `Neo4j Bloom`.  
[Download here](https://neo4j.com/download/)

## 1/ Download and install `Neo4j Desktop`: 
### [Neo4j Desktop](https://neo4j.com/docs/desktop-manual/current/)
> Neo4j Desktop is the mission control center for Developers. It's free with registration, and it includes a free development license for Neo4j Enterprise Edition allowing you to use Neo4j Enterprise on your local desktop for developing applications.  

Neo4j Desktop can be downloaded and installed without admin permission. When accessing the link above and begin the download process, however, you will have to enter some informatin to generate a personalized product key. This key will last for 1 year.  
![image](https://user-images.githubusercontent.com/60938608/217350562-14594681-b912-4cb6-b7ad-2082e3617a4a.png)
  
Also the installation will prompt you to either install for your own user account on the computer (such as below), or for everyone who uses the computer. The guide will proceed with install for local user only.  

![image](https://user-images.githubusercontent.com/60938608/217351282-5f736acd-8e19-4cf0-9ed1-257bca97e8ab.png)  

When selected the path to install, Neo4j will proceed to install and once complete, you can tick “Run Neo4j Desktop” to launch, else untick and proceed to “Finish”  

![image](https://user-images.githubusercontent.com/60938608/217351306-4e2b0bd4-9d4f-4bf8-a1cc-55b99fd8fbcd.png)

## 2/ Deploy `Neo4j Enterprise Server` on `Neo4j Desktop`: 
### [Neo4j Enterprise:](https://neo4j.com/product/neo4j-graph-database/)  

> Neo4j Enterprise edition allows you to develop a graph database with enterprise level security and efficiency. The included Enterprise version with Desktop does not have full functionality of a server, and is limited to run only locally. The full version would also include more security and efficiency for large scale usage.
  
Once you launched Neo4j Desktop for the first time, you will be prompted to paste product key. Copy the key from before and input into the Software key on the right side. In case you forgot to save the old key, you can re-register on the left side to get a new key.  
![image](https://user-images.githubusercontent.com/60938608/217351890-aa98d133-1bdb-4005-b6fa-dd0b7f50fdb9.png)
![image](https://user-images.githubusercontent.com/60938608/217350863-29211de0-c8df-47c0-81f1-b18804d0f98d.png)

When Neo4j completed its setup, the Movie DBMS will be availble immediately and already up and running. 
![image](https://user-images.githubusercontent.com/60938608/217351243-c87b0347-26b8-4baf-a157-03fca854ed4c.png)

Click on `Open` to launch Neo4j Browser, a tool for interacting with Neo4j Desktop and Neo4j Enterprise Server. 
Once inside, you will be greeted with this interface
![image](https://user-images.githubusercontent.com/60938608/217351213-bb7316f5-4172-480d-b430-59c4aea82c07.png)

Do note that your current username is `neo4j` as seen below.
![image](https://user-images.githubusercontent.com/60938608/217351021-47e61936-0d52-4e70-b655-ca4acf5165dd.png)

## 3/ Installing plugins `APOC` and `Graph Data Science`: 
### [APOC:](https://neo4j.com/labs/apoc/)
> APOC (Awesome Procedures on Cypher) is an add-on library for Neo4j that provides hundreds of procedures and functions adding a lot of useful functionality.Those are custom implementations of certain functionality, that can’t be (easily) expressed in Cypher itself. They are implemented in Java and can be easily deployed into your Neo4j instance, and then be called from Cypher directly.  

### [Graph Data Science:](https://neo4j.com/docs/graph-data-science/2.3/introduction/)
> The Neo4j Graph Data Science (GDS) library provides efficiently implemented, parallel versions of common graph algorithms, exposed as Cypher procedures. Additionally, GDS includes machine learning pipelines to train predictive supervised models to solve graph problems, such as predicting missing relationships.  

In order to install the 2 plugins `APOC` and `Graph Data Science`, select the project:  
![image](https://user-images.githubusercontent.com/60938608/217351972-21bd195c-7356-4757-9e09-17a54ef14d20.png)  

once selected, and right side column would pop out with 3 options to choose: `Details`, `Plugins`, and `Upgrade`. Select the `Plugins` and click on both `APOC` and `Graph Data Science Library`.   
![image](https://user-images.githubusercontent.com/60938608/217352202-01018d59-558a-419d-b0f9-05cf5a44404a.png)  
![image](https://user-images.githubusercontent.com/60938608/217303624-b1d8af72-8632-45bf-ae58-cb100129029a.png)  
Once selected, a blue button will show up with the words `Install` or `Install and Restart`. Select both and wait for restart (if button has it).  
The reason for this is because these plugins is project wide plugins. It affects all databases in that project.


## 4/ Deploying databases on Neo4j. 
Neo4j starts with a Movie DBMS by default, and to present the database, you can access certain queries and run small graph results such as:
```cypher
MATCH (actor:Person {name: "Keanu Reeves"})-[:ACTED_IN]->(movies) 
RETURN movies  
```
![image](https://user-images.githubusercontent.com/60938608/217309666-eb26aef4-417d-413c-a0c1-b3892913e9fa.png)
You can definitely run more detailed queries such as getting who also acted with Keanu Reeves via below query and the result:
```cypher 
MATCH (actor:Person {name: "Keanu Reeves"})-[:ACTED_IN]->(movies)<-[ACTED_IN]-(otheractor:Person) 
RETURN actor, movies, otheractor
```
![image](https://user-images.githubusercontent.com/60938608/217310716-b2496b48-ca39-43e4-b462-70c9cd962625.png)
This will give you results within the browser, with precise details.

## 5/ Deploy `Bloom`
### [Bloom:](https://neo4j.com/docs/bloom-user-guide/current/)
> Neo4j Bloom is a visualization tool. While Neo4j Browser allows users to access and run detailed queries, Bloom focuses on the overall graph. Bloom now comes pre-packaged within all Neo4j Desktop 1.2.6 and later, Neo4j Desktop will also automatically search for the latest version of Bloom and install it if it is either missing or an older version.  

Neo4j Bloom will only run if there is a Neo4j Server. The reason why Bloom can now run on Neo4j Desktop is because by version 1.2.6 and later, Neo4j Desktop included a limited license of Neo4j Enterprise Server. Since the version downloaded in this guide is 1.5.7, Bloom is available for us, and already activated. To see it, we go back to Neo4j Desktop and hover on the arrow next to the `Open` drop down menu (Both `Open` buttons have this option)
![image](https://user-images.githubusercontent.com/60938608/217306917-43466976-5861-495e-bb98-7ebf80b81a24.png)
![image](https://user-images.githubusercontent.com/60938608/217306952-e68dcd7a-c863-4e8e-936c-9f804a8ff8b4.png)

A new window will open that looks like this. This Bloom is tied to the project we open, hence anything we have in it, such as the Movie DB, will be available to Bloom here. 
![image](https://user-images.githubusercontent.com/60938608/217307061-7789f9c7-5e84-4488-9b56-e4bb5ae3a7b6.png)

Bloom, however, focuses on presenting the bigger pictures. To use Bloom with the database, we'll need to `generate a perspective`. The perspective is done via the following steps:
- Select the button of 3 slide bar in the top left corner shown below  
![image](https://user-images.githubusercontent.com/60938608/217314927-c6fea2d2-18fa-44b5-8dd7-812c93c7de79.png)  
- Click on the blue area `neo4j>xxxxxx` to access the perspective generator
![image](https://user-images.githubusercontent.com/60938608/217314861-a71eb91d-448c-48c5-94ca-2e4b38b83025.png)  
- Once inside, click on `Create` => `Generate Perspective` such as below to get the visual set up and ready to use  
![image](https://user-images.githubusercontent.com/60938608/217313349-079ae38e-5755-47a1-b983-73f46488c761.png)  

Once made, we can generate the queries such as above in Bloom via entering nodes or relationships into the search bar:
![image](https://user-images.githubusercontent.com/60938608/217313453-f790f7b2-b25b-40d3-a6d3-865219ff53da.png)
You can then add a filter to find specifics, such as an actor:  
![image](https://user-images.githubusercontent.com/60938608/217313619-9cadecb6-587b-4df8-a120-5e3b40218d52.png)
There is a lot of commands you can enter in the box above (shown in picture below):  
![image](https://user-images.githubusercontent.com/60938608/217308243-1c138dd4-88aa-4df1-8d23-b7b20534eb3d.png)

On Bloom, however, results can be shown such as below, and when hovering on top of them, the details will also show. This is because Bloom prioritize showing the graph, and Neo4j Browser prioritizes small scale work and detail oriented queries.
![image](https://user-images.githubusercontent.com/60938608/217315006-11e0efa3-f6b6-47a2-8a0f-ce6551741854.png)

Further details about bloom can be accessed via the link below
[Neo4j Bloom 2.6 - Neo4j Bloom](https://neo4j.com/docs/bloom-user-guide/current/)
