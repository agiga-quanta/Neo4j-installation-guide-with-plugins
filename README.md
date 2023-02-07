# Neo4J
This repository provides a step-by-step instruction to the installation of Neo4J and some plugins.

## 1/ Download and install Neo4J Desktop: 
Neo4J Desktop can be downloaded and installed without admin permission. When accessing the link below and begin the download process, however, you will have to enter some informatin to generate a personalized product key. This key will last for 1 year.
*Noted: Version installed in this guide is 1.5.7*
Also the installation will prompt you to either install for your own user account on the computer, or for everyone who uses the computer. The guide will proceed with install for local user only. 
Once complete, you can tick “Run Neo4j Desktop” to launch, else untick and proceed to “Finish”

## 2/ Deploy Server on Neo4j Desktop without admin: 
Neo4J Desktop is a tool to use Neo4J Enterprise Server. This means other users can access it through local IP and port when the connection status once server is launched. The main difference between Neo4J Desktop and Neo4J Enterprise are server authentication, sharing and others.... insert more details here.

## 3/ Installing plugins: APOC and Graph Data Science 
APOC:
> 
Graph Data Science:
> 
In order to install the 2 plugins APOC and Graph Data Science, select the project from the left column, once selected, and right side column would pop out with 3 options to choose: “Details”, “Plugins”, and “Upgrade”. Select the “Plugins” and click on both APOC and Graph Data Science Library. Once selected, a blue button will show up with the words “Install and Restart”. Select both and wait for restart.

## 4/ Deploying databases on Neo4J. 
Neo4j might start with a Movie DBMS by default, but if needed, you can create a new project to run further tests. All server require an 8 character password.

Once run, the top bar would show Active DBMS. Click Open will run the Neo4j Browser on an internet browser, and you can use neo4j from here.

To deploy any of the preset database, you would enter in the above line “:play movies”. Then navigate the the project files and run the “load-movies.cypher”. This is a tailored version of the Movie DB for Neo4J. The new tab showed below would have basic guides to navigate and create queries that can present the database or manipulate it.

## 5/ Deploy Bloom
Quoted from Neo4j’s own statement: Neo4j Bloom client comes pre-packaged within Neo4j Desktop. Starting with Bloom 1.3, the Bloom client is enabled and ready to use in Desktop. In Neo4j Desktop 1.2.5 and prior versions, the Bloom client app can be added to any project. Starting with Desktop 1.2.6, you can find and directly run the Bloom app from the “Applications” sidebar drawer. In case you are not seeing the Bloom app there, make sure offline mode is disabled and restart your Desktop. Your Desktop will automatically search for the latest version of Bloom and install it if it is either missing or an older version.
Since the version downloaded in this guide is 1.5.7, Bloom has already been installed for us, and already activated. To see it, we go back to Neo4J Desktop and hover on the arrow next to the Open tab (Both Open button have this option)
A new window will open that looks like this. This Bloom is tied to the project we open, hence anything we have in it, such as the Movie DB, will be available to Bloom here.

From Neo4J browser, you can access certain queries and run small graph results such as MATCH (actor:Person {name: "Keanu Reeves"})-[:ACTED_IN]->(movies)
RETURN movies

Bloom can show nodes such as below, and when hovering on top of them, the details will also show. This is because Bloom prioritize showing the graph, and Neo4J prioritizes small scale work and detail oriented queries.

Further details about bloom can be accessed via the link below
Neo4j Bloom 2.6 - Neo4j Bloom
