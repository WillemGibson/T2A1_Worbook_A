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

## Q3: Discuss the implementation of Agile project management methodology

The agile project management system is an industry-standard system in the software engineering space. This management system has grown its users due to the iterative and incremental approach. It emphasizes flexibility, collaboration, and customer satisfaction above all else. Here is a quick dive into the implementation of the system:

1. Define user-stories:
    - Take a look at the requirements of the software and represent them as if you were a user.
    - Create a list of functionalities and features.
    - Created a backlog of all user stories.

2. Sprints:
    - Plan work in short bursts, or sprints, nothing exceeding 2-4 weeks.
    - In these sprints, dev teams will be assigned different user stories to complete.

3. Daily stand-up meetings:
    - These go for 15 mins as you go around asking 3 simple questions to everyone then moving on with the work ahead for the day.
    - Each person will answer what the
    -This is used to make sure the work is progressing towards the sprint goals.

## Q4: Provide an overview and description of a standard source control workflow

A standard source control workflow is a process that dev teams use to manage any changes done in the source code to a project, collaborate, and manage versions. The most popular of these workflows is Git. Git works very much like a tree diagram with the ```main``` branch being the root, which sprouts out into designated supporting branches:

!['Git Workflow Diagram'](/git.png)

1. Main Branches:
    - Usually name the ```Master``` or ```Main``` branch, this is where you activate and most up-to-date version of your project sits. The consumer version.
    - The ```develop``` branch serves as an integration branch for any ongoing development. Features, Hot Fixes, Updates, anything that would change the source code. These components will be merged into this branch for testing before being integrated into the ```Main``` branch for consumers.

2. Suporting Branches:
    - Feature branches are used to contain the development of new features to be later merged with the ```develop``` branch. Each new feature has its own branch.

    - Hotfix branches are used to implement a small quiz on a critical error in the ```Main``` branch.

    - Release branches are used to merge into both the ```Main``` branch and the ```Develop``` branch and are assigned a version tag to mark the release.

## Q5: Provide an overview and description of a standard software testing process (e.g. manual testing)

Manual testing is a process in which a developer manually executes test cases without using any automated tools to complete the testing of a software solution. The process involves the careful systematic examination of the developer's code, software's functionality, and features to identify any issues or errors that may affect the solutions mark against the specified requirements. This is a quick overview of the process:

1. Planning:
    - Going over the software solution's requirements.
    - Developing and planning an outline of the testing process.
    - Identifying the features and functionalities of the solution.

2. Setting up the testing environment:
    - Creating the test environment by installing and configuring any necessary third-party software and/or test data.
    - Running through the environment closely to make sure it resembles a realistic testing case.

3. Execution of testing:
    - Inputting necessary test data into test cases
    - One last final check of the reliability of the test cases.
    - Manually executing the testing environments for the software solution.

4. Reporting findings:
    - Report any identified results or errors.
    - Provide detailed accounts of all test outcomes.
    - Communicate with the dev team your findings.


## Q6: Discuss and analyse requirements related to information system security and how they relate to the project

1. Data encryption:
    - In the ACME use case, using HTTPS to encrypt data between the web app's client and server and ensure that the connection is uninterrupted and secure.
    - Also using web certificates to once again ensure the reliability and safety of the user's experience on ACME's web interface. 

2. Authentication and Authorization: 
    - Using user authentication and authorization on the web app will greatly increase the security of the site and allow the secure management of the app content.
    - This can be a token-based session authentication to ensure that a user can be authenticated and authorized.

3. Session Management:
    - As mentioned above, this session-based token system will allow the distinction of main users and admins for content management and security.
    - This will also create an environment in which the user will need to log in after a specific amount of time, removing the factor of hackers gaining access to a physical device getting in if the session has expired.

## Q7: Discuss common methods of protecting information and data and how you would apply them to the project

1. Backups:
    - ACME will need regular automated back ups of all data this  prevents the loss of data in the event of an attack, power outages and/or corruption.
    - Having anothor backup in another phyical locaiton is also recommended

2. Patches and Updates:
    - ACME will also benefit from regualr updates and hot fixes to teh web app to ensure the latest technology being used and all issuing on the platform and addressed asap.
    - Also monitoring for issueing in the platform at all times.

3. Phyiscal security measures:
    - ACME's data should be upheld to the data protection regulations. 


## Q8: Research what your legal obligations are in relation to handling user data and how they can be met for the project

1. Privacy Law Compliance:
    - ACME will need to adhere to the Australian Privacy Act 1988, to ensure the safety and security of their users.
    - This will make sure that users are completely aware of what is happening with their data and how secure it is which will be all noted in a privacy agreement that is open to all users to view and read through.

2. User Rights:
    - Another legislation from the privacy act is users' rights. ACME will need to adhere to these just as equally as the privacy laws.
    - This will ensure all users will have access to their personal data/information and be informed of how ACME will use it.

3. Data collection:
    - ACME will need to clearly state how and why they intend to get/use personal data.
    - They will need to implement some sort of consent form to get legal confirmation of personal data collection.

## Q9: Describe the structural aspects of the relational database model. Your description should include information about the structure in which data is stored and how relations are represented in that structure.

The realational database model is one of the most common models in databsea technology. It is used to seperate specific information and connect them respectively. Data is sorted into tables, also known as relations. These are sorted in collumn and rows to better layout for readability, which can relate to eachtother using foregin keys. Here is a dive into the basic structure of a relational databsae:

1. Tables
    - Tables are used to separate the information into specific areas. Such as users, customers, products, orders, etc.
    - Each table consists of columns to specify certain aspects of each entry, for example, name, quantity, cost, etc.
    - The rows are used to display each data entry as a readable structure. 

2. Keys
    - keys are used to sort and call different data entries, for example, foreign keys which are used to call data between tables.
    - Another example of keys is primary keys. These are auto-incrementing integer entries to give each entry a specific number to call on. for example, entry 001, 002, 003, etc.

3. Normalisation
    - Normalisation is the act of cleaning up and preventing unnecessary data.
    - It also reduces the likelihood of data issues.

### Q10: Describe the integrity aspects of the relational database model. Your description should include information about the types of data integrity and how they can be enforced in a relational database.



## Q11: Describe the manipulative aspects of the relational database model. Your description should include information about the ways in which data is manipulated (added, removed, changed, and retrieved) in a relational database.



## Q12: Conduct research into a web application (app) and answer the following parts:

### a. List and describe the software used by the app.



### b. Describe the hardware used to host the app.



### c. Describe the interaction of technologies within the app



### d. Describe the way data is structured within the app



### e. Identify entities which must be tracked by the app



### f. Identify the relationships and associations between the entities you have identified in part (e)



### g. Design a schema using an Entity Relationship Diagram (ERD) appropriate for the database of this website (assuming a relational database model)



## References:

- https://flask.palletsprojects.com/en/3.0.x/lifecycle/
- https://realpython.com/flask-blueprint/
- https://flask.palletsprojects.com/en/3.0.x/quickstart/
- https://www.guru99.com/introduction-postgresql.html
- https://cloud.google.com/learn/postgresql-vs-sql
- https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow
- https://www.guru99.com/manual-testing.html
- https://www.atlassian.com/continuous-delivery/software-testing/types-of-software-testing
-https://www.geeksforgeeks.org/software-testing-manual-testing/
- https://www.atlassian.com/agile#:~:text=What%20is%20the%20Agile%20methodology,planning%2C%20executing%2C%20and%20evaluating.
- https://en.wikipedia.org/wiki/Agile_software_development
- https://www.bmc.com/blogs/data-normalization/



- Get pic url