# Lesson 0: Data Engineering
[Today's Jupyter notebook](https://github.com/aeason18/SAC-Coding-Meetings-26-27/blob/main/Notebooks/notebook_01.ipynb) <br>

To start, make sure you have Docker and TablePlus installed. Next, open Docker. Navigate to the images tab and use the search bar to find and run Postgres (when prompted to make a new container, press cancel): <br>

![pg install](https://github.com/aeason18/SAC-Coding-Meetings-26-27/blob/main/Images/pg%20install.png)

Now, open your terminal, customize your database name and password, and run this line: <br>
```
docker run --name sac_example -e POSTGRES_PASSWORD=your_password_here -d -p 5432:5432 postgres:14.23-alpine3.24
```
You should now have something like this in your containers tab: <br>

![pg db running](https://github.com/aeason18/SAC-Coding-Meetings-26-27/blob/main/Images/pg%20db%20running.png)

Next, open TablePlus, hit Create Connection, and select PostgreSQL. When you get here, **Name** can be anything, and everything else should match. Use the password you created earlier. <br>

![pg db connection](https://github.com/aeason18/SAC-Coding-Meetings-26-27/blob/main/Images/pg%20db%20connection.png)

Press connect. <br>

Now, go to VS Code and make a new text file. Let's use this [data set](https://www.pro-football-reference.com/years/2025/passing.htm) from Pro Football Reference as an example. On their website, go to the **Share & Export** option and select **Get table as CSV.** Then, copy and paste the information into the text file you made in VS Code and save it as a CSV. <br>

**Reminder:** Always cite where you get your data for your projects. <br>

Go back to TablePlus and right-click on Tables: Import > From CSV. Next, choose the file you just made. In the Import CSV Wizard, make sure that Create new table is selected and then press Import. Refresh the workspace, and you should have a working DB with some data in it! <br>

It should look something like this: <br>

![working db](https://github.com/aeason18/SAC-Coding-Meetings-26-27/blob/main/Images/working%20db.png)

Now open the provided notebook and fill in your password and table name. You should see the data you imported to TablePlus. <br>

If you encounter a psycopg2 error, try running this line:
```
%pip install psycopg2-binary
```
