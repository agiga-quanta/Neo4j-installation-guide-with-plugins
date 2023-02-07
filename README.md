# Neo4J
This repository provides a step-by-step instruction to the installation of Neo4J and some plugins.

## 1/ Download and install Neo4J Desktop: 
Neo4J Desktop can be downloaded and installed without admin permission. When accessing the link below and begin the download process, however, you will have to enter some informatin to generate a personalized product key. This key will last for 1 year.  
[Neo4J Desktop Download link here](https://neo4j.com/download/)  
*Noted: Version installed in this guide is 1.5.7*  
Also the installation will prompt you to either install for your own user account on the computer, or for everyone who uses the computer. The guide will proceed with install for local user only. 
Once complete, you can tick “Run Neo4j Desktop” to launch, else untick and proceed to “Finish”

## 2/ Deploy Neo4J Enterprise Server on Neo4j Desktop: 
> Neo4j Desktop is the mission control center for Developers. It's free with registration, and it includes a free development license for Enterprise Edition allowing you to use Neo4j Enterprise on your local desktop for developing applications.   
  
Neo4J Desktop already comes with Neo4J Enterprise Server. Thanks to that, other users can access the server through local IP and port when the connection status once server is launched. 
![image](https://user-images.githubusercontent.com/60938608/217304342-234ec71b-f796-46dd-bf3d-3353503e84a2.png)
The main difference between Neo4J Desktop's Enterprise server and Full Neo4J Enterprise Server are server authentications and sharing. Further details can be accessed [here](https://neo4j.com/licensing/)

## 3/ Installing plugins: APOC and Graph Data Science 
### [APOC:](https://neo4j.com/labs/apoc/)
> APOC (Awesome Procedures on Cypher) is an add-on library for Neo4j that provides hundreds of procedures and functions adding a lot of useful functionality.Those are custom implementations of certain functionality, that can’t be (easily) expressed in Cypher itself. They are implemented in Java and can be easily deployed into your Neo4j instance, and then be called from Cypher directly.  

### [Graph Data Science:](https://neo4j.com/docs/graph-data-science/2.3/introduction/)
> The Neo4j Graph Data Science (GDS) library provides efficiently implemented, parallel versions of common graph algorithms, exposed as Cypher procedures. Additionally, GDS includes machine learning pipelines to train predictive supervised models to solve graph problems, such as predicting missing relationships.  

In order to install the 2 plugins APOC and Graph Data Science, select the project from the left column, once selected, and right side column would pop out with 3 options to choose: “Details”, “Plugins”, and “Upgrade”. Select the “Plugins” and click on both APOC and Graph Data Science Library. Once selected, a blue button will show up with the words “Install and Restart”. Select both and wait for restart.  
![image](https://user-images.githubusercontent.com/60938608/217303624-b1d8af72-8632-45bf-ae58-cb100129029a.png)
## 4/ Deploying databases on Neo4J. 
Neo4j might start with a Movie DBMS by default, but if needed, you can create a new project to run further tests. All project require an 8 character password.
![image](https://user-images.githubusercontent.com/60938608/217303851-a2ce6fc0-7ee0-446d-856c-3a523657a875.png)

Once created, the top bar would show Active DBMS. Click Open will run the Neo4j Browser on an internet browser, and you can use neo4j from here.
To deploy any of the preset database, you would enter in the above line “:play movies”. 
![image](https://user-images.githubusercontent.com/60938608/217305330-a39f8e2e-5469-4dea-8e70-cdb46000e180.png)

Then navigate the the project files and run the “load-movies.cypher”. This is a tailored version of the Movie DB for Neo4J. The new tab showed below would have basic guides to navigate and create queries that can present the database or manipulate it.
![image](https://user-images.githubusercontent.com/60938608/217303979-595094c2-6ac5-497e-9f5b-e83dda7ffda9.png)

From Neo4J browser, you can access certain queries and run small graph results such as:
> MATCH (actor:Person {name: "Keanu Reeves"})-[:ACTED_IN]->(movies) RETURN movies  
![image](https://user-images.githubusercontent.com/60938608/217309666-eb26aef4-417d-413c-a0c1-b3892913e9fa.png)
> You can definitely run more detailed queries such as getting who also acted with Keanu Reeves via below query and the result:
> MATCH (actor:Person {name: "Keanu Reeves"})-[:ACTED_IN]->(movies)<-[ACTED_IN]-(otheractor:Person) RETURN actor, movies, otheractor
![image](https://user-images.githubusercontent.com/60938608/217310716-b2496b48-ca39-43e4-b462-70c9cd962625.png)
This will give you results within the browser, with precise details.

## 5/ Deploy Bloom
### [Bloom:](https://neo4j.com/docs/bloom-user-guide/current/)
> Neo4j Bloom client comes pre-packaged within Neo4j Desktop. Starting with Bloom 1.3, the Bloom client is enabled and ready to use in Desktop. In Neo4j Desktop 1.2.5 and prior versions, the Bloom client app can be added to any project. Starting with Desktop 1.2.6, you can find and directly run the Bloom app from the “Applications” sidebar drawer. In case you are not seeing the Bloom app there, make sure offline mode is disabled and restart your Desktop. Your Desktop will automatically search for the latest version of Bloom and install it if it is either missing or an older version.  

Neo4J Bloom will only run if there is a Neo4J Server. The reason why Bloom can now run on Neo4J Desktop is because after version 1.2.5 of Neo4J Desktop, Neo4J then included a limited license of Neo4J Enterprise Server. Since the version downloaded in this guide is 1.5.7, Bloom is available for us, and already activated. To see it, we go back to Neo4J Desktop and hover on the arrow next to the Open tab (Both Open button have this option)
![image](https://user-images.githubusercontent.com/60938608/217306917-43466976-5861-495e-bb98-7ebf80b81a24.png)
![image](https://user-images.githubusercontent.com/60938608/217306952-e68dcd7a-c863-4e8e-936c-9f804a8ff8b4.png)

A new window will open that looks like this. This Bloom is tied to the project we open, hence anything we have in it, such as the Movie DB, will be available to Bloom here. 
![image](https://user-images.githubusercontent.com/60938608/217307061-7789f9c7-5e84-4488-9b56-e4bb5ae3a7b6.png)

Should the right hand side be empty and not showing any data:
![image](https://user-images.githubusercontent.com/60938608/217312425-2c0c3585-0786-4a9c-9bcc-aaa2ebac19e2.png)
then database has not been loaded into the project. In that case, go back to step 4 and load the database. 
  
Bloom, hoever, focuses on presenting the bigger pictures. To use Bloom with the database, we'll need to "generate a perspective". The perspective is done via the following steps:
![image](https://user-images.githubusercontent.com/60938608/217314927-c6fea2d2-18fa-44b5-8dd7-812c93c7de79.png)
![image](https://user-images.githubusercontent.com/60938608/217314861-a71eb91d-448c-48c5-94ca-2e4b38b83025.png)
![image](https://user-images.githubusercontent.com/60938608/217313349-079ae38e-5755-47a1-b983-73f46488c761.png)
Once made, we can generate the queries above in Bloom via:
![image](https://user-images.githubusercontent.com/60938608/217313453-f790f7b2-b25b-40d3-a6d3-865219ff53da.png)
You can then add a filter to find specifics, such as an actor:
![image](https://user-images.githubusercontent.com/60938608/217313619-9cadecb6-587b-4df8-a120-5e3b40218d52.png)
There is a lot of commands you can enter in the box above (shown in picture below):
![image](https://user-images.githubusercontent.com/60938608/217308243-1c138dd4-88aa-4df1-8d23-b7b20534eb3d.png)

On Bloom, however, results can be shown such as below, and when hovering on top of them, the details will also show. This is because Bloom prioritize showing the graph, and Neo4J Browser prioritizes small scale work and detail oriented queries.
![image](https://user-images.githubusercontent.com/60938608/217315006-11e0efa3-f6b6-47a2-8a0f-ce6551741854.png)

Further details about bloom can be accessed via the link below
[Neo4j Bloom 2.6 - Neo4j Bloom](https://neo4j.com/docs/bloom-user-guide/current/)
