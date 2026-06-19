# Lesson 0: Data Engineering
To start, make sure you have Docker and TablePlus installed. Next, open Docker. Navigate to the images tab and use the search bar to find and run Postgres (when prompted to make a new container, press cancel): <br>

![pg install](https://github.com/aeason18/SAC-Coding-Meetings-26-27/blob/main/images/pg%20install.png)

Now, open your terminal, customize your database name and password, and run this line: <br>
```
docker run --name sac_example -e POSTGRES_PASSWORD=your_password_here -d -p 5432:5432 postgres:14.23-alpine3.24
```
You should now have something like this in your containers tab: <br>

![pg db running](https://github.com/aeason18/SAC-Coding-Meetings-26-27/blob/main/images/pg%20db%20running.png)

Next, open TablePlus, hit Create Connection, and select PostgreSQL. 
