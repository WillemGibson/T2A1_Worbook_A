# CodeAcd T2A1 - Worbook A

## Q1: Describe the architecture of a typical Flask application

A flask application follows the Model-View-Controller (MVC) architecture. It is a lightweight web framework for Python that provides the necessary tools to build web applications. Here is an overview of some common components of a flask app:

1. Application Objects aka. ```app```:
    - ```App``` is the main component of a Flask app and is an instance of the Flask class that represents the web app.
    - They are created by using ```Flask(__name__)```, where ```__name__``` is the name of the current Python module.

    ```py 
    from flask import Flask

    app = Flask(__name__)
    ```

2. Routes:
    - Routes are used to define the URL navigation that the app will respond to.
    - They are created by using a ```@app.route``` decorator, which connects a function with a specified URL.

    ```py
    @app.route('/test')
    def testing():
        return 'Testing, testing, 1... 2... 3...'
    ```

3. Controllers:
    - Controllers (or views) are functions created with the intention of handling requests and return responses.
    - They work in conjunction with models such as fetch or update to render the appropriate data.

    ```py
    @app.route('/test/user/<username>')
    def testing():
        # Logic to fetch user data
        return render_template('user.html', username=username)
    ```

4. Models:
    - A model is used to interact with a database. Storing and retrieving data, SQLAlchemy is a common choice for database interactions.

    ```py
    from flask_sqlalchemy import SQLAlchemy

    app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///example.db'
    db = SQLAlchemy(app)

    class User(db.Model):
        id = db.Column(db.Integer, primary_key=True)
        username = db.Column(db.String(100), unique=True, nullable=False)
    ```

5. Templates:
    - A template is used in a Flask app to generate HTML dynamically. Using the Jinja2 engine by default, allows developers to embed Python code in HTML and generate dynamic content.

    ```html
    <!-- user.html -->
    <!DOCTYPE html>
    <html>
    <head>
        <title>User Profile</title>
    </head>
    <body>
        <h1>Hello, {{ username }}!</h1>
    </body>
    </html>
    ```

## Q2: Identify a database management system (DBMS) commonly used in web applications (including Flask) and discuss the pros and cons of this database

PostgreSQL is one of the most common relational database management systems (RDBMS) in the world. It has gained this popularity due to its immense power and the fact it is completely open source. Here are some Pros and Cons of this software:

### Pros

1. Open-source and Free:
    - Being 100% open-source means that PostgreSQL is free to use and distribute. This can be a very important factor when considering what DBMS you use when it comes time to monetize your web app.

2. Community and Support:
    - PostgreSQL is famous for its overwhelmingly supportive community and ongoing maintenance. This ensures that this DBMS gets ongoing development, updates, bug fixes, etc. The vibrant and active community also supplies it with plenty of add-ons and plugins. PostgreSQL also has plenty of forums and documentation to help developers navigate it.

3. Plenty O' Features:
    - This DBMS is known for its unbelievably extensive set of features. From complex queries and indexing to even handling advanced data sets. PostgreSQL also natively supports JSON, XML, arrays, and even hstore, which is used to store key-value data.

### Cons

1. Memory Usage:
    - Unfortunately in specific circumstances, PostgreSQL tends to use a lot of RAM. With proper optimisation, this can be avoided but this takes skills that aren't very beginner-friendly. Which leads me to my next cons...

2. Steep Learning Curve:
    - The second massive con is the steep learning curve. PostgreSQL isn't easy to learn. This is due to just how many features PostgreSQL has. Although most find that it is worth the time invested in learning this tool.

3. Uncommon in Web Hosting:
    - While PostgreSQL is widely used in projects, it is uncommon to see support for it in hosting services. Thankfully we are starting to see more support for PostgreSQL as we progress.

### Q3: Discuss the implementation of Agile project management methodology
### Q4: Provide an overview and description of a standard source control workflow
### Q5: Provide an overview and description of a standard software testing process (e.g. manual testing)
### Q6: Discuss and analyse requirements related to information system security and how they relate to the project
### Q7: Discuss common methods of protecting information and data and how you would apply them to the project
### Q8: Research what your legal obligations are in relation to handling user data and how they can be met for the project
### Q9: Describe the structural aspects of the relational database model. Your description should include information about the structure in which data is stored and how relations are represented in that structure.
### Q10: Describe the integrity aspects of the relational database model. Your description should include information about the types of data integrity and how they can be enforced in a relational database.
### Q11: Describe the manipulative aspects of the relational database model. Your description should include information about the ways in which data is manipulated (added, removed, changed, and retrieved) in a relational database.
### Q12: Conduct research into a web application (app) and answer the following parts:
#### a. List and describe the software used by the app.
#### b. Describe the hardware used to host the app.
#### c. Describe the interaction of technologies within the app
#### d. Describe the way data is structured within the app
#### e. Identify entities which must be tracked by the app
#### f. Identify the relationships and associations between the entities you have identified in part (e)
#### g. Design a schema using an Entity Relationship Diagram (ERD) appropriate for the database of this website (assuming a relational database model)


### References:
- https://flask.palletsprojects.com/en/3.0.x/lifecycle/