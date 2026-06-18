# Lesson 0: Data Engineering
To start, make sure you have Docker and TablePlus installed. Next, open Docker. Navigate to the images tab and use the search bar to find and run Postgres (when prompted to make a new container, press cancel): <br>

![pg install](https://github.com/aeason18/SAC-Coding-Meetings-26-27/blob/main/images/pg%20install.png)

Now, open your terminal and run this line: <br>
'''python
docker run --name sac_example -e POSTGRES_PASSWORD=your_password_here -d -p 5432:5432 postgres:14.23-alpine3.24
'''
