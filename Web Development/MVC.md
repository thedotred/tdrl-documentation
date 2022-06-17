# What is MVC?
*MVC (Model-View-Controller)* is a design pattern for application development. This design pattern separates application business logic from user interface. MVC stands for Model-View-Controller:
* Model: The model defines the data structure of the application. The number of tables and fields within a database are deifned in models.
* View: The view handles layout & user interactivity and how the data should be displayed.
* Controller: The controller sits in-between Model and View. It contains all the application logic and routes. 
    * What is a *Route*: When a user enters a link in the browser, that link is the route. Behind the scene, the routes determine which page should be viewed to the user. All routes within an application are mentioned in controllers.
    * What is Application Logic: Application logic contains functions for CRUD operations and statements for reporting. 

# How MVC works?
Let me give an example of User login process in MVC framework: 
1. User sees the Login Interface, enters username and password and hits the submit button. This part is taken care of by the `VIEW`.
2. The `VIEW` gives the username and password to a controller. In the controller a logic is written to check if the username and password is actually exists in the database. So, the controller asks the database to give the details.
3. Now the database looks for the username and password and if it finds anything, then it gives the details to the controller. If it can't find the username and password, then it returns something called `null` to the controller.
4. Then controller might process the result from the database and then sends a response to the `VIEW`. Finally, the user is either logged in or the user gets a message saying it can not find anything.

The whole process is illustrated below:

![MVC Steps](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/MVC-2.png)

# Why use MVC?
At `Dot Red`, we use MVC architecture because this pattern helps us to manage complex applications easily by breaking up the front-end, back-end and database into components. As a result, several developers can work simultaneously in different components. For example, when we start any project, we divide an application into 3 parts:
1.	Database (Model)
2.	User interfaces (View)
3.	Routes, API’s and data processing logics (Controller)

# How to use MVC?
At `Dot Red`, the structure of a Project with MVC structure will look like the followings: 

![mvc folder structure](https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/MVC-1.png)

Lets consider a sample project. In this project we will have 2 modules:
1. Book module
2. User module

### Folder: models
Inside `models` folder, a new folder will be created for each module. For the above example, inside `models` folder, there will be 2 separate folders for Book and User. The folder name will be in `PascalCase` format and the folder structure will look like the followings:

<img src="https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/MVC-3.png" alt="models folder structure" width="300"/>

Inside each of these folders, we will create a `.js` file with the name of the module followed by `Model` in camelCase format. A screenshot is attached below:

<img src="https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/MVC-4.png" alt="inside module's model folder structure" width="300"/>

### Folder: views
Inside `views` folder, a new folder will be created for each module. For the above example, inside `views` folder, there will be 2 separate folders for Book and User. The folder name will be in `PascalCase` format and the folder structure will look like the followings:

<img src="https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/MVC-5.png" alt="views folder structure" width="300"/>

Inside each of these folders, we will create a `Index.handlebars` file. A screenshot is attached below:

<img src="https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/MVC-6.png" alt="inside module's model folder structure" width="300"/>

### Folder: controllers
Inside `controllers` folder, a new folder will be created for each module. For the above example, inside `controllers` folder, there will be 2 separate folders for Book and User. The folder name will be in `PascalCase` format and should be followed by `Controllers`. The folder structure will look like the followings:

<img src="https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/MVC-7.png" alt="controllers folder structure" width="300"/>

Inside each of these folders, we will create two controllers files. One file for View/Route handling and another view for API's (All business logics). A screenshot is attached below:

<img src="https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/MVC-8.png" alt="inside module's controllers folder structure" width="300"/>


The final structure will look like the following image:

<img src="https://elasticbeanstalk-ap-southeast-1-677312808939.s3.ap-southeast-1.amazonaws.com/uploads/notes/MVC-9.png" alt="final project structure" width="300"/>
