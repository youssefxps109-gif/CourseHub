# CourseHub -- Project Documentation

## 1. Project Overview

CourseHub is an online learning platform prototype designed to provide
users with a simple way to browse courses and manage their selected
courses.

The project uses a frontend built with HTML, CSS, and JavaScript and a
lightweight JSON Server backend.

## 2. System Components

### Frontend

The frontend contains the following pages:

-   `index.html`
-   `products.html`
-   `register.html`
-   `login-in.html`
-   `myprofile.html`
-   `contact.html`

The shared JavaScript functionality is implemented in `script.js`, while
the main styling is provided by `style.css`.

### Backend / Data Layer

`db.json` is used with JSON Server to provide REST-style endpoints for:

-   Users
-   Courses
-   Selected courses

`products.json` contains the course catalog data separately.

## 3. User Features

### Registration

A user enters:

-   Name
-   Email
-   Password

JavaScript validates the fields before sending a POST request to:

``` text
POST /users
```

### Login

The login form checks the entered credentials against the users returned
from:

``` text
GET /users
```

When the credentials match, basic user information is stored in browser
LocalStorage.

### Course Browsing

The courses page requests course data from:

``` text
GET /products
```

Each course card displays its name, price, description, duration,
instructor, and rating.

### Course Selection

When the user selects a course, the application checks whether the same
user has already selected that course.

If it has not been selected, the application sends:

``` text
POST /selectedCourses
```

### Profile

The profile page displays the current user's stored name and email.

It also supports:

-   Saving a phone number
-   Uploading a profile image
-   Viewing selected courses

Profile information and the uploaded image are stored using browser
LocalStorage.

### Contact Form

The contact form validates:

-   Name
-   Email
-   Message

The name field accepts alphabetic characters and spaces.

## 4. Data Model

### Users

``` json
{
  "name": "User Name",
  "email": "user@example.com",
  "password": "demo-password"
}
```

### Products

``` json
{
  "id": "1",
  "name": "HTML Course",
  "price": 30,
  "description": "Course description",
  "duration_hours": 20,
  "instructor": {
    "name": "Instructor Name"
  },
  "rating": 4.5
}
```

### Selected Courses

``` json
{
  "courseId": "1",
  "userEmail": "user@example.com",
  "name": "HTML Course",
  "price": 30,
  "instructor": "Instructor Name"
}
```

## 5. API Configuration

The frontend currently uses:

``` javascript
var API_URLS = ["http://localhost:3002"];
```

Start JSON Server with:

``` bash
json-server --watch db.json --port 3002
```

## 6. Future Improvements

Possible improvements for a production-ready version include:

1.  Secure backend authentication
2.  Password hashing
3.  Database such as MySQL or PostgreSQL
4.  User authorization
5.  Course enrollment and payment functionality
6.  Search and filtering
7.  Course progress tracking
8.  Instructor dashboard
9.  Admin dashboard
10. Deployment to a cloud platform
11. Better error handling
12. Automated testing

## 7. Project Learning Outcomes

The project demonstrates practical knowledge of:

-   HTML5
-   CSS3
-   JavaScript
-   DOM manipulation
-   Form validation
-   REST API concepts
-   JSON Server
-   Fetch API
-   LocalStorage
-   Frontend/backend integration
-   Basic CRUD-style data operations
