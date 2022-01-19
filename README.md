# Image Repository/Marketplace Challenge

Thanks for taking the time to view my project!

## Technologies Used
1. Node.js
2. PostgreSQL
3. Stripe (for payment flow)
4. Cloudinary

## Prerequisites
* [node.js](https://nodejs.org/en/) (server-side)
* [PostgreSQL](https://www.postgresql.org/download/)
* Stripe dev account
* Cloudinary dev account

The following steps assume that all dependencies are present.

## Run the Project

1. Clone this repo
2. cd into the repo ```cd image-repo```
3. Set environment variables. To do this, create a ```.env``` file in the root directory, and add the following details taken from the prereqs. 
```
DB_USERNAME=
DB_PASSWORD=
DB_NAME=
DB_HOST=
CLOUD_NAME=
CLOUDINARY_API=
CLOUDINARY_SECRET=
JWT_SECRET=
JWT_EXPIRY_TIME_MS=
STRIPE_SECRET=
```
4. Use npm to install dependencies ```npm install```
5. Run ```sequelize-cli db:migrate```
6. Start the server using ```npm run``` or ```npm run server``` 


## Project Scope

Users are able to:
1. Upload and store one or bulk images in a secure and reliable platform
2. Delete one or bulk images
3. Update image details
4. Buy and sell existing images on the platform
5. User permissions

The application only has the backend setup for now since the challenge did not require a frontend component. 


## User Flow - API's

| Type | Purpose | Endpoint
| ------------- | ------------- | ------------ |
| GET  | Get all existing public images | /images |
| GET  | Get all of your images | /images/private |
| DELETE  | Delete an image | /images |
| POST | Registers New User  | /users/register |
| POST | Login to the session | /user/login |
| POST | Add image  | /images |
| PUT  | Edit image by id | /images/{imageId} |
| POST  | Buy an existing public image | /payment |


## DB Models

This project is modelled using 2 main models:

#### Image
```
userId: UUID
name: STRING
description: STRING
url: STRING
isPrivate: BOOLEAN
quantity: INTEGER
price: DOUBLE
discountPercentage: FLOAT
cloudinaryId: STRING
```

#### User
```
firstName: String
lastName: String
email: String
hashedPWD: String
```
This is a simple user model for time-being. The password is salted and hashed using bcrypt before being stored to improve security. 

### Testing and Improvements:

Tests are run using the ```mocha``` framwork. Due to the smaller nature of this project, very simple tests were added. In the future, other unit tests providing complete code coverage will be included. 

Improve:
1. Deployment
The current process is made to run locally. Dockerizing this system and adding a CI/CD pipeline for further development is key to this. 
2. Authentication
The authentication system can be improved by using a 3rd party such as firebase or cognito, providing services such as 2FA, reset, and verification.


