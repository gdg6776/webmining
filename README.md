Step 1 : Unzip 
You can unzip using following command
unzip project_phase4.zip
Step 2: Setting up the environment
directory lib has all the requires jars for spring framework
Hnece you need to update your CLASSPATH variable such that program 
can find all the used classes in the program
Here is how you can do that;
a ) Open the terminal
b ) Open bash profile file
  vi ~/.bash_profile
c ) Append this line into that file;
   export CLASSPATH=$CLASSPATH:/<path-to-project-directory>/lib/*

d ) save the file and restart your terminal.
	Restarting the terminal will load all the environment variables with
	new values.
	Open the terminal and type
	echo $CLASSPATH
	to see if the path variable has been updated successfully.



Step 3 : Creating and configuring database
We assume you have the Mysql 5.7.13  or higher to run this program
run following command to created database on the go 
mysql < webmining.sql

This command will create the database called web_mining 
with all required tables with sample data in them.


part b} Configuring database handler program:
Open file DatabaseHandler.java
-> DB_URL: 
on line 21 we have static final String DB_URL = "jdbc:mysql://localhost:3306/web_mining";
make sure you have mySQL running on port 3306 and have the database web_mining in it
if you have different configuration, then please change it accordingly

-> Credetials:
on lines 24 and 25 we have database credentials as follows;
    static final String USER = "root";
    static final String PASS = "Root@01";

    Change those credentials to your database user name and password.
    Make sure that user has root previlleges.



Step 4 : Compile the java source files
you can compile the source files as follows;
a) javac model/*.java
b) javac BlogMining.java


Step 5 : Run the program
You can run the program as follows
java BlogMining

Step 6: Interacting with the program
You can interact with the program as follows;
1. crawl <url> : where url is valid wordpress blog url
2. crawl <site-id> <post-id> :  where 
	site-id is valid Wordpress Blogger site ID
	And post-id is valid wordpress post-id
3.help: To print this help instruction
4. updateDB: This command crawls top 10 uncrawled sites
5. top: This command prints top trending posts as per comments and likes count
6. related <post-id> <site-id> :  where
     site-id is valid Wordpress Blogger site ID
     And post-id is valid wordpress post-id
7. quit: To quit this program



e.g.
A}you can type 
crawl https://truthandsatire.wordpress.com/2015/07/03/greece-the-one-biggest-lie-you-are-being-told-by-the-media/

This command will help you crawl through all the related blogs 
(i.e. blogs posted by people who have commented on this blog)




######### DATA SET DESCRIPTION #######
Our datase has been adaptively generated using WordPress APIs.
We are calling WordPRess APIs to get the post details and blogger details.
Using those details we are storing them into database named 'web_mining'.
Web mining database has 3 tables;
1. posts :  It stores post details
2. bloggers :  It stores blogger details
3. comments : It stores comments done on a particular post

We have desgned our application such that while consuming 
WordPress APIs, we are creating a kind of relationship between posts 
and hence classifying them as related and non-related posts.


######### WORK DESCRIPTION OF EACH TEAM MEMBER #######
The project was has divided into three modules with each person responsible for every module - 
Person Responsible:- Alimuddin Khan
Task:- Performed reasearch on several blogs and implemented REST APIs for wordpress and it’s crawling
       This work can be found in Blogmining.java file

Person Responsible:- Gaurav Gawade
Task:- Performed research on several blogs and took the responsibility of all the DML and DDL Queries therby also implementing the Backend database.

Person Responsible:- Chirag Kular
Task:- Took the job establishing the communication between Java and MySql and wrote queries to database for extracting the data.
	


