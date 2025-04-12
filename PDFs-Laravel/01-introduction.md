# 1 - Welcome To The Course

Hey guys welcome to my Laravel From Scratch course. This course was a long time in the making. I;ve had people asking for it for about two years now. So I spent the last 4 months or so creating it and as with most of my courses, it's project based. In fact the project may look famililar to you if you took my PHP from scratch course. It's a new and improved Workopia job listing website. Ill go over a demo in the next video but we added things like bookmarking and applying to jobs throught website.

Now even though this is  project based, it's not just rush through and copy what I type. I stop and take the time to explain every line of code and go off script a little bit to explain certain things. You're going to learn all about routes, controllers, models, views with UI components, migrations, the Artisin CLI and much more. You'll learn the tools to help you start building your own Laravel projects. At the end, we'll be deploying with Laravel Forge and Digital Ocean and we'll hook up a domain and an SSL. So it's a very thorough project.

Now for the past 6 or 7 courses, I've included what I call the premium docs as long as the course was purchased at traversymedia.com. However for this course, I decided to included the premium docs no matter where it's purchased. These docs are essentially a written version of the entire course. There's a markdown file for every video lesson with code samples as well as written explanations. So you can use that as a supplement to the videos.

As far as who should take this course, I would say anyone that knows the fundamentals of PHP. I won't be explaining what loops and functions are or how to structure arrays. You should know that stuff and if you don't I would just suggest taking my PHP from Scratch course first and building that version of the Workopia website.

So like I said, we'll take a quick look at the main project and then we'll talk a little bit about what Laravel is and what it includes, we'll setup our enviroment and then we'll start learning and building. See you in the next video.


# 2 - What Is Laravel?

Laravel is a popular open-source PHP web framework designed for building modern, scalable, and secure web applications. It is an opinionated and a high-level framework. I'll talk more about what that means in a minute. It also follows the Model-View-Controller (MVC) architectural pattern, which we'll get into later, and it  aims to make the development process more efficient and enjoyable. 

I'm sure most of you are aware of what a web framework is, but just in case you aren't, it's a collection of libraries and tools that help developers build applications faster by providing common functionality, such as routing, database management, and authentication. If you took my PHP from scratch course and create the Workopia project, then you know that just using PHP can be a bit cumbersome and repetitive and even messy. Laravel and frameworks in general make things much easier and more organized.

Laravel was created by Taylor Otwell in 2011 and has since become what I would say the most popular PHP framework. It's known for its expressive syntax, robust features, and active community. Laravel is used by developers around the world to build a wide range of applications, from simple blogs to complex enterprise systems.

Usually when people learn PHP, they go in one of two directions. They either learn WordPress or they learn Laravel. Wordpress is more for smaller content-based websites and blogs, while Laravel is for more complex applications. And there is nothing that says that you can't learn both.

## Opinionated Framework

Laravel is an opinionated framework, which means it comes with a set of conventions and best practices that guide developers in building applications. This can be a good thing because you usually get a ton of features right out of the box, it helps maintain consistency across projects and makes it easier for developers to collaborate. However, it can also be restrictive if you prefer more flexibility and control over your code.

If you have ever used Ruby On Rails, Django or Angular, then you know what an opinionated framework is. There are a lot of features and conventions. If you have used Express.js or React, those are very unopinionated frameworks where you don't need to do things a certain way. You have a lot of freedom, but you also have to make a lot of decisions and don't get many out of the box features. There are pros and cons to both approaches.


## Why Use Laravel?

There are a ton of reasons to use Laravel for your projects. This is a list of some of the common ones. It's not a complete list, but it's a start.

- **Rapid Development**: Laravel streamlines common tasks like routing, authentication, and database management, allowing developers to focus on building features rather than reinventing the wheel.
- **Security**: With built-in features for protecting against SQL injection, cross-site request forgery (CSRF), and cross-site scripting (XSS), Laravel helps ensure that your application is secure from common vulnerabilities.
- **Scalability**: The framework is designed to handle growth, making it suitable for both small projects and large enterprise applications.
- **Built-in Authentication**: It provides built-in authentication and authorization features, making it easier to manage user access and security.
- **Elegant Syntax**: Laravel offers a clean and elegant syntax that allows developers to write code that is both readable and maintainable.
- **Robust Ecosystem**: Laravel has a rich ecosystem with tools and features such as Eloquent ORM, Blade templating engine.
- **Migration System**: Laravel offers database tools. It has a complete migration system to manage database schema changes, making it easier to collaborate with teams and maintain consistency. Eloquent ORM to interact with the database as well as factories and seeding to quickly add data.
- **Community Support**: Laravel has a large and active community, which means you can find plenty of tutorials, documentation, and third-party packages to enhance your project.
- **Task Scheduling**: The framework includes a task scheduling system, which lets you automate repetitive tasks using a clean, fluent API.
- **Testing**: Laravel comes with tools for automated testing, which helps ensure your code is reliable and free of bugs.


There are so many more features, but these are some of the key ones that make Laravel so popular. In the next video I will give you a large list of the features and libraries that are come built in to the framework.


# 3 - Laravel Libraries

Laravel is one of the most feature-packed web frameworks that exist. It has a ton of libraries and features built in. I talked a little bit about some of these in the last video, but this is an exhaustive list of what is included in the framework. We will be using just about all of these in the course.

### Built-in Laravel Components

1. **Blade Templating Engine**  
   Blade is Laravel's default templating engine for rendering views. We can pass data from the database or snywhere else into our views. There's also a component system now and we construct our UI like we would with a frontend framework like React. And of course Laravel is also great for APIs. So you can return JSON and use React or Vue or anything else for your frontend.

2. **Eloquent ORM**  
   Eloquent is Laravel's built-in ORM for interacting with databases. So we don't need to wrote raw SQL queries. It has a very elegany syntax for fetching, creating, updating, etc.

3. **Artisan CLI**  
   Command-line tool for managing Laravel applications. You can do everything from run database migrations to create controllers and models, run the dev server and so on.

4. **Tinker**  
    REPL (Read-Eval-Print Loop) for interacting with your application. You can do just about anything you can do from your code in a command line.

5. **Laravel's Routing**  
   The routing system is very dynamic and easy to use. Handing url patterns and ataching middleware grouping routes. You can generate resource routes.

6. **Validation**  
   Laravel has built in validation for form inputs.

7. **Session Management**  
   Built-in session handling.

8. **Cache**  
   Built-in caching system with support for various cache drivers.

9. **Authentication**  
   FOr authentication, you have all kinds of options. You can build it from scratch, which is what we'll be doing but you can also use scaffolding with something called Laravel Breeze. You basically run a command and it sets up the authentication along with the pages or views and forms to go with it. 

10. **Mailing**  
    Basic mail sending functionality using Laravel's `Mail` facade.

11. **Database Migrations**  
    Tools for managing and applying database schema changes.

12. **Logging**  
    Built-in logging functionality with support for various log channels.

13. **Testing**  
    PHPUnit testing framework integration for running unit and feature tests.

14. **Configuration Management**  
    Built-in configuration management using `.env` files.

15. **CSRF Protection**  
    Cross-Site Request Forgery protection built into forms and routes.

16. **Password Hashing**  
    Built-in password hashing functionality using Bcrypt.

17. **Laravel Collections**  
    Collection class for working with arrays and data more efficiently.

18. **Factories & Seeders**  
    Factories and seeders allow you to generate data for your models.

19. **Faker Library**  
    Faker is a library that allows you to generate very specific types of data like phone numbers, emails, job titles, etc.

20. **Carbon**  
    Library for working with dates and times.

As you can see, this is a massive list of features and tools that Laravel provides out of the box. You also have other tools that are avaialable like Sanctum for API authentication, Horizon for monitoring queues, Dusk for browser automation and many more that you can install or configure.

In the next section, we are going to get setup with PHP and Laravel.