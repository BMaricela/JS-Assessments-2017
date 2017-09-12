### Javascript Course Assessment

## Week 5 Assessment

Try your best to answer each question on your own before looking up the answer online. Once you're done writing your first answer, you can google the question and write the best answer you find.

#### 1. Comment this code from an express server to explain what each part is doing.

My answer: Respond with Hello World when a GET request is made to the homepage. 

Researched answer:
// the first line calls the main function (GET) in Express. It creates a new application and assigns it to a local variable called app 
app.get('/', function (request, response) { // we pass in 2 parameters (request and response): the first is the path we want this route to respond to, and the second is a callback function that will run when that route is accessed
  response.send('Hello World!'); // respond with Hello World when a GET request is made to the homepage

});

app.listen(3000, function () { // this declaration gets our server to start listening for incoming requests on port 3000
  console.log('Example app listening on port 3000!'); // the callback function prints out information to the console that things are working correctly
});


#### 2. We have now used both EJS and React to render views with dynamic javascript content (If you want a refresher, take a look at the "Full Stack Express" day). Compare and contrast the two approaches, include a pro and con of each. Which one did you prefer?

My answer: Both EJS and React afford us a quicker workflow, enabling us to stand up a website more quickly. Express is more server-side, while React is more front-end oriented. React makes the most sense when designing a project that requires lots of interactivity and has frequent state changes. 

Express on the other hand is pretty minimalist in terms of interactivity offerings right out of the box. It’s a very lightweight framework, so much of its potential comes from third party modules/features, which can be either a pro or a con, depending on how much flexibility you want.

I tend to learn more toward frameworks that don’t require as many outside modules, so I think I’d lean more toward React, if I’m working on something where interactivity is important.

Googled answer: I’m struggling to find any sources that directly compare/contrast Express with React. 


#### 3. Sequelize and Express are the Model and Controller portions of our MVC structure. How the two relate and pass information between each other is important to understand but can be hard to follow. Below are some generic events that happen when a browser requests a web page, but they are not in order. Put them in order and also specify whether the task is done by Sequelize or Express. The first step has been given to you as an example:

1. Server is set to "listen" for requests coming in on a port, or range of ports (Express)

----- organize from here down:

3. SQL responses are translated into a javascript object (Sequelize)

4. If incoming requests require information from the database, the request is parsed into a SQL query (Sequelize)

2. The content required for a view is sent back to the browser, along with any additional information required (Express)

5. Incoming requests are handled by the router (Express)

** Understanding this process will be important to building full stack apps, if you have any questions about this process, write them here and I will answer them with you in the future:

#### 4. We implement back end tests with Jest and Supertest, look back at the "Testing Express" day and do a few minutes of outside research to understand what this code is doing, and what it is testing. Add comments explaining your findings.

** Also comment any piece you don't understand with questions, and I will get back to you.


const request = require('supertest')
const app = require('./App.js')

describe('Test the root path', ()=>{ //this tests the root path, which is the homepage
  it('Should respond to GET', () => { //this is saying that when you request the root path, it should respond to the GET request with 
    return request(app).get('/').then((response)=>{ // the homepage, and then
      expect(response.statusCode).toBe(418) //the expected response status code to be 418
    })
  })

  it('Should respond with a message of "Relax, and have a cup of tea", ()=>{ //a message should show that reads, “Relax, and have a cup of tea”
    return request(app).get('/').then((response)=>{ //a GET request for the homepage
      expect(response.body.greeting).toBe('Relax, and have a cup of tea') //the greeting in the body of the homepage should say, “Relax, and have a cup of tea”
    })
  })
})


#### 5. What are cookies and sessions? Try to explain what they are, and any differences between them that you remember.

//My answer: Cookies are data about a user that can get stored on said user’s browser. They can remember details about this user, for instance her name. A session keeps track of multiple details about a user, and is server side. One example of session data is when a user selects her language; the session remembers which language she chose when rendering other page requests. 

//Googled Answer: 
What is a "Cookie"?
A cookie is a small piece of text stored on a user's computer by their browser. Common uses for cookies are authentication, storing of site preferences, shopping cart items, and server session identification.
Each time the users' web browser interacts with a web server it will pass the cookie information to the web server. Only the cookies stored by the browser that relate to the domain in the requested URL will be sent to the server. This means that cookies that relate to www.example.com will not be sent to www.exampledomain.com.
In essence, a cookie is a great way of linking one page to the next for a user's interaction with a web site or web application.


What is a "Session"?
A session can be defined as a server-side storage of information that is desired to persist throughout the user's interaction with the website or web application. 
Instead of storing large and constantly changing information via cookies in the user's browser, only a unique identifier is stored on the client side (called a "session id"). This session id is passed to the web server every time the browser makes an HTTP request (ie a page link or AJAX request). The web application pairs this session id with it's internal database and retrieves the stored variables for use by the requested page.

#### 6. Try to explain the process of how information from a user can be persisted to a database using a form, the "post" method, sequelize, and express.  Look back at the "Full Stack Express" day for a refresher.

The markup would look like this: <form action="/club_name_url/" method="post">. The POST method allows us to send data to the server, after it’s been validated. Express can use the body-parser middleware to process the POST parameters from the form, and the express-validator module can validate the form data. 

I’m still a little unclear about how exactly we go about saving the data we collect to a database. I looked through the Saving Form Data tab in Full Stack Express, but could only find information about how to save the data to a file, not a database...



 #### 7. What is sequelize "seed" data for? Why can it be helpful as you develop a project?

 //My answer: Seed data is used to setup a development environment with some records so developers can get up and running quickly without having to hand-enter lots of data into the database. 

 //Googled Answer: Seed data is anything that must be loaded for an application to work properly. An application needs its seed data loaded in order to run in development, test, and production. Examples can include: initial accounts for the application administrator and client users.


 #### 8. Red, Green, Refactor is the process for TDD - what does this mean to you right now, and what do you think it might look like to do this in a work environment?

What it means to me right now is exactly what Test Driven Development is about--I should create a test and make it fail (Red). I should then work to make the test pass (Green), and after that I can Refactor to remove duplicate code, while ensuring it still passes all the tests. Approaching a project this way will make the code so much more maintainable, and my future workplace will encourage writing tests first. If it’s a smaller company, I imagine the developers might have to write some of the tests for their code themselves.


 #### 9. This is an example express application on github: https://github.com/shapeshed/express_example. Take a few minutes to go to the address and look around in the files. List a few things here about the project - what do you notice that is different about their setup? What looks familiar from class? What sticks out to you or gives you questions? 

First off, I noticed there was a Routes folder and a bin folder. What’s inside the Routes folder makes (some) sense to me, and there are a few things that look familiar in the www file, and a lot of things that look unfamiliar. I also noticed that shapeshed uses jade, which is a templating engine I have no experience with. The overall project structure looks similar to what we did in class.


#### 10.  Try to explain what an express router does in your own words. 

 //My answer: An express router returns content based on the path specified. In Express, a route, which can also be called an endpoint, is a command to run a specific function that sends a response back to the client. For example “/” would be a GET request that returns the homepage.

//Googled answer: Routing refers to determining how an application responds to a client request to a particular endpoint, which is a URI (or path) and a specific HTTP request method (GET, POST, and so on).
Each route can have one or more handler functions, which are executed when the route is matched.
Route definition takes the following structure:
app.METHOD(PATH, HANDLER)




