Udacity Cloud Developer Nano-Degree Program Capstone Project For David Fish

Overview of Project:

A few years ago, Kathy Fish started an online workshop program for creative writing. The popularity of these workshops has grown so much that when she would open up the online registration system, the website would crash from the volume of people wanting to register for the courses.

Additionally, there are many people from other parts of the world who want to participate in the workshops but the registration window was not convenient for their time zone (the workshops would sell out in less than 30 minutes).

It has been decided that the fairest way to handle registrations is to let people enroll in a lottery for the workshops. This will reduce the spike on the servers, and lets people register within a one-week window at their convenience.

An online registration tool is needed to allow people to enter their registration information (name, email address, phone number, and the workshops they wish to enroll in), and then receive a confirmation email that they have been registered for the lottery.

It has been decided to build this registration tool using Serverless technology for the backend data storage and business logic, and the React/Typescript for the front-end web application.

Requirements:

1. Allow a user to visit a registration page and enter their email address, first name, last name (all required) phone number (optional)
2. Allow user to select from the list of workshops being offered. They will click on the checkbox for the workshop(s) for which they wish to register in the lottery.
3. Allow the user to click the Enroll button and get taken to a confirmation page where they will be told they have successfully enrolled in the lottery and that they will receive an email confirming their enrollment.
4. Send the email to the email address entered on the form.
5. Validation rules:
   a. User must enter an email address, first name, and last name and select at least one workshop from the list.
6. When the Enroll button is clicked the registrant data should be sent to AWS Dynamo DB tables:
   a. FFReg-dev – Registrants table - Contains the following columns:
   i. emailAddress: string – Partition Key
   ii. first Name: string
   iii. Last Name: string
   iv. Phone Number: string
   b. FFWSReg-dev – Workshps Registrants Table - Contains the following columns:
   i. workshopId: string – Partition Key
   ii. emailAddress: string – Partition Key
   iii. paid: string – Payment made (defaults to No)
   iv. selected: string – Selected in lottery (defaults to No)
   v. waitlisted: string – Put on waitlist for workshop if not selected in lottery (defaults to No)
7. There is also a DynamoDB table that holds the Workshop Information and is used to populate the registration form:
   a. FFWorkshops-Dev – Workshops Table - Contains the following columns
   i. workshopId: string – Partition Key
   ii. workshopName: string – Name of Workshop
   iii. workshopType: string – Type of workshop
   iv. price: number – Cost of workshop
   v. workshopStart: string – Start Date of Workshop
   vi. workshopEnd: string – End Date of Workshop

Technologies Used:
AWS:
Lambda
API Gateway
Dynamo DB
CloudWatch
S3
IAM
Simple Email Service
Amplify

APIs
The Serverless app consists of a number of APIs deployed to AWS:

/nodemailer
POST – Sends an email to the enrollee confirming their lottery enrollment

/registrants
GET – Get a list of Registrants (requires Auth)
POST – Create a registrant
GET/{emailAddress} – Get a registrant (requires Auth)

/workshops
GET – Get a list of workshops
POST – Create a workshop (requires Auth)
DELETE/{workshopId} – Delete a workshop (requires Auth)

/wsRegistrants
POST – Create a workshop Registrant

Code Repository:
The source Code for this project can be found at:
https://github.com/defish1962/udacity_capstone

The Website can be accessed at:
https://master.d3gc9u1uje5zge.amplifyapp.com

Postman Collection Fast Flash Workshops Lottery Project.postman_collection can be found in the Backend folder

Notes:

Not all functions have been fully implemented and I intend to continue working on this code to create a full featured website that will allow users to register for the lottery and register and pay for a workshop if they are selected.

I will also create a function to run the lottery to select winners based on a random number generator. I will also incorporate payments using PayPal and/or Stripe.
