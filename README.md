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
    - ACME will need regular automated backups of all data this prevents the loss of data in the event of an attack, power outages, and/or corruption.
    - Having another backup in another physical location is also recommended

2. Patches and Updates:
    - ACME will also benefit from regular updates and hot fixes to the web app to ensure the latest technology is being used and all issues on the platform and addressed ASAP.
    - Also monitoring for issues in the platform at all times.

3. Physical security measures:
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

## Q9: Describe the structural aspects of the relational database model. Your description should include information about the structure in which data is stored and how relations are represented in that structure

The relational database model is one of the most common models in database technology. It is used to separate specific information and connect them respectively. Data is sorted into tables, also known as relations. These are sorted in columns and rows to better layout for readability, which can relate to each other using foreign keys. Here is a dive into the basic structure of a relational database:

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

## Q10: Describe the integrity aspects of the relational database model. Your description should include information about the types of data integrity and how they can be enforced in a relational database

1. Referential Integrity:
    - This ensures that the relationships between tables are consistent throughout the database.
    - This can be achieved by referencing child tables in parent tables and matching foreign keys with existing primary keys.

2. Domain Integrity:
    - This refers to the integrity of the range and domain of data in a database. In turn, preventing invalid data.
    - This can be achieved by implementing the correct data types to columns and checking the contents of data entry.

3. Entity Integrity:
    - This refers to the integrity of each entry/row's primary key.
    - this can be achieved by using auto-incrementing id attributes to each entry/row and making sure these attributes are not nullible.

## Q11: Describe the manipulative aspects of the relational database model. Your description should include information about the ways in which data is manipulated (added, removed, changed, and retrieved) in a relational database

1. INSERT:
    - This refers to the act of adding an entry/row into a table of a database.
    - Example:

    ```sql
    INSERT INTO table_name (column1, column2, column3, ...)
    VALUES (value1, value2, value3, ...);
    ```

2. UPDATE:
     - This refers to the act of modifying an entry/row into a table of a database.
     - Example

     ```sql
    UPDATE table_name
    SET column1 = value1, column2 = value2, ...
    WHERE condition;
     ```

3. DELETE:
     - This refers to the act of removing an entry/row from a table of a database.
     - Example

     ```sql
    DELETE FROM table_name
    WHERE condition;
     ```

4. SELECT:
     - This refers to the act of retrieving an entry/row into a table of a database.
     - Example

     ```sql
    SELECT column1, column2, ...
    FROM table_name
    WHERE condition;
     ```

## Q12: Conduct research into a web application (app) and answer the following parts

The following case study will be conducted on the communication platform known as Discord.

### a. List and describe the software used by the app

Discords tech stack/software is built up of several programming languages and frameworks. These include:

**- Frontend Development:** Discord primarily uses JavaScript as their main programming language stacked up with the React.js framework to create their user interfaces. Also utilising CSS for styling the various elements.

**- Backend Development:** Discord mainly uses Elixir, which is built on the Erlang Virtual Machine (BEAM) in combination with the Phoenix web framework for real-time applications. Their main choice in database management and creation is PostgreSQL.

**- Real-Time Communication:** Discord uses WebSockets to transmit all forms of communication over a TCP connection. For Voice and Video communication, Discord uses Opus audio codec & WebRTC (Web Real-Time Communication) protocol.

### b. Describe the hardware used to host the app

**- Hardware Infrastructure** Discord uses a combination of cloud-based platforms and physically distributed systems around the globe to host and run their applications. They primarily use both Amazon Web Services (AWS) and Google Cloud services for their cloud-based infostructure for most and the physical servers for distributed caching systems and load balancing.

### c. Describe the interaction of technologies within the app

**- Service Architecture:** Discord follows a very strict microservices architecture for their interaction of technologies. Microservice architecture is the process in which all functionalities and components are divided into smaller, independent services that all communicate with each other over these servers. This helps Discord to be optimized and stay organized when in development.

### d. Describe the way data is structured within the app

**- Data Structure:** Discord was in need of a DAG (Directed Acyclic Graph) System to store all their user's data, therefore they opted for derived tables in a BigQuery Data warehouse. A divided table can be defined as a SQL SELECT statement that references raw data or other derived tables. This diagram is used to reference the approach taken by the company in data structure:
![Discord Data Structure Diagram](/diagram.png)

### e. Identify entities that must be tracked by the app

Discord is very open about what information they track of users' interactions in their privacy policy. Discord states that the only information they track is:

- Identifiers (such as your username, the email address you used to sign up, and your phone number if you’ve chosen to provide it)

- Commercial information (a record of what you’ve bought from Discord if anything)

- Financial data (payment information and your history of purchases from Discord)

- Internet or other network information (how you interact with the application)

- Internet or other network information (how you interact with the application)

- Inference data about you (for example, what content you may be interested in)

### f. Identify the relationships and associations between the entities you have identified in part (e)

The relationships between these said entities can all come under one belt. Users. The identifiers can be used to assign personal information to users and distinguish them from other users. Commercial information is directly tied to user engagement with the platform. Financial is dependable on user behavior and entry of personal data. Network information is also tied to user behaviour same as the inference data. 

### g. Design a schema using an Entity Relationship Diagram (ERD) appropriate for the database of this website (assuming a relational database model)

![Discord ERD Diagram](/discord.jpg)

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
- https://www.astera.com/type/blog/data-integrity-in-a-database/
- https://www.linkedin.com/pulse/tech-stack-discord-faysal-ahmed/
- https://discord.com/blog/how-discord-stores-trillions-of-messages
- https://discord.com/privacy
- https://discord.com/blog/how-discord-creates-insights-from-trillions-of-data-points
- https://creately.com/diagram/example/jqf0pnzj2/discord-diagrama-clases-classic

- [Get pic url](https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.gliffy.com%2Fblog%2Fgitflow-diagrams&psig=AOvVaw3hFv6YtNqGq6ePNWKy3kir&ust=1709543229497000&source=images&cd=vfe&opi=89978449&ved=0CBMQjRxqFwoTCPCikvne14QDFQAAAAAdAAAAABAE)