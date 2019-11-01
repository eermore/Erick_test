# Technical Support Engineer Assesment
## Steps to Submit
1. Create an ssh key on your machine if you do not have one
1. Send us your ssh public key
1. Create a GitHub Account
1. Git Clone this repository to your local machine
1. Remove the current origin remote (git remote remove origin)
1. Create a new repository under your GitHub account (do NOT fork this repository)
1. Follow the instructions to push an existing repository from the command line...
1. Add answers to this Document (either to this document or create different for each question), commit your answers to the branch
1. Push your answers to your personal remote origin in your git account
1. Send a notification to us with a link to your repository
If any of the steps above is unclear, please try GitHub user guides.
The method of submission is part of the test (usage of Git)

## Questions
1. A customer has reached out to us that he cannot access our platform running on 45.33.22.50. Customer's complain is as follows:
- "Hello, It seems i cannot access http://45.33.22.50/test1"

2. A customer has reached out to us that he cannot access our platform running on 45.33.22.50. Customer's complain is as follows:
- "Hello, It seems i cannot access http://45.33.22.50:444/test2. When i access it seems that nothing happens"

## To Do
- For both above questions what are the actions you will take to evaluate customers request.

* Check if I can enter or if I don't have access either.
* Validate what is the error message, normally it could be 404 or 500.
* What is the script supposed to do?
* What is it actually doing?
* Ask questions to customer to get more detail of the fault.

- Include questions we may need to ask to get additional information to ensure the best customer support.

* At what time did the fault occur?
* Do you know if anyone else has the same fault?
* When was the last time it worked correctly?
* Was there any recent change on your system or some application recently installed?
* What browser are you using, have you tried any other? 






- Add an explanation why you ask each question (what do you expect to receive back.

The first step before starting a problem analysis is to identify if it is an isolated fault or if it is a massive problem, so it is important to collect information regarding the end user, date and time of the problem, error message, recent changes in the equipment, etc ... 

- Additionaly you need to ssh to the machine and troubleshoot the above scenarios.

Check log files, for example:

/var/log/nginx/error.log

Check coredumps:

/tmp/core

Check status of service of nginx

sudo service nginx status

if nothing happened when webpage is open is important to check with development team, maybe one line is wrong or missing.




- Make sure you list in detail what are the steps you followed to identify and resolve the problem.

1.- Get more details about the issue.
2.- Try to replicate the fault.
3.- Analyze error messages on the screen (webpage).
4.- Analyze logs on the server.
5.- If the service is down, start it and report the event to 
    The development team.
6.- If the service is up report to the development team.
7.- Validate if problem has been solved.
8.- Document the fault to get the root cause of the problem.


Hint: The platform runs on nginx and python
