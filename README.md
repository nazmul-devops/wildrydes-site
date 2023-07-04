# wildrydes-site
wildrydes-site

## Build a Serverless Web Application

- with AWS Lambda, Amazon API Gateway, AWS Amplify, Amazon DynamoDB, and Amazon Cognito by Nazmul

[AWS HandsOn Guide Link](https://aws.amazon.com/getting-started/hands-on/build-serverless-web-app-lambda-apigateway-s3-dynamodb-cognito/)

#### Overview
In this tutorial, you will create a simple serverless web application that enables users to request unicorn rides from the Wild Rydes fleet. The application will present users with an HTML-based 
user interface for indicating the location where they would like to be picked up and will interact with a RESTful web service on the backend to submit the request and dispatch a nearby unicorn. The 
application will also provide facilities for users to register with the service and log in before requesting rides.

#### Prerequisites
To complete this tutorial, you will need an AWS account, an account with ArcGIS to add mapping to your app, a text editor, and a web browser. If you don't already have an AWS account, you can follow 
the Setting Up Your AWS Environment getting started guide for a quick overview.

#### Application architecture
The application architecture uses AWS Lambda, Amazon API Gateway, Amazon DynamoDB, Amazon Cognito, and AWS Amplify Console. Amplify Console provides continuous deployment and hosting of the static 
web resources including HTML, CSS, JavaScript, and image files which are loaded in the user's browser. JavaScript executed in the browser sends and receives data from a public backend API built 
using Lambda and API Gateway. Amazon Cognito provides user management and authentication functions to secure the backend API. Finally, DynamoDB provides a persistence layer where data can be stored 
by the API's Lambda function.

![AWS Basic serverless application architecture](https://d1.awsstatic.com/diagrams/Serverless_Architecture.d930970c77b382db6e0395198aacccd8a27fefb7.png)

##### Static Web Hosting

- AWS Amplify hosts static web resources including HTML, CSS, JavaScript, and image files which are loaded in the user's browser.

##### User Management

- Amazon Cognito provides user management and authentication functions to secure the backend API.


##### Serverless Backend

- Amazon DynamoDB provides a persistence layer where data can be stored by the API's Lambda function.

##### RESTful API

- JavaScript executed in the browser sends and receives data from a public backend API built using Lambda and API Gateway.

#### Commands

[YouTube video link](https://youtu.be/kA2ZYD4zgEo)
All the commands that are executed in the above youtube video are mentioned in this gist.

[Github Repo Link](https://gist.github.com/teja156/67faf07de60d6650c26f8d3a05120094)
```
1. Install AWS shell
pip install aws-shell

2. Configure AWS shell
aws configure

3. Create a repo on AWS CodeCommit
aws codecommit create-repository --repository-name wild-rydees

4. Clone the source code from Github
git clone https://github.com/aws-samples/aws-serverless-webapp-workshop

Once you've used either AWS CodeCommit or GitHub.com to create your git repository and clone it locally, you'll need to copy the website content from an existing publicly accessible S3 bucket associated with this workshop and add the content to your repository.

a. Change directory into your repository and copy the static files from S3:

cd wildrydes-site

aws s3 cp s3://wildrydes-us-east-1/WebApplication/1_StaticWebHosting/website ./ --recursive

b. Commit the files to your Git service
$ git add .
$ git commit -m 'new'
$ git push

Counting objects: 95, done.
Compressing objects: 100% (94/94), done.
Writing objects: 100% (95/95), 9.44 MiB | 14.87 MiB/s, done.
Total 95 (delta 2), reused 0 (delta 0)
To https://git-codecommit.us-east-1.amazonaws.com/v1/repos/wildrydes-site
* [new branch] master -> master

5. Split the WildRydes app into a branch
cd aws-serverless-webapp-workshop
git subtree split -P ./resources/code/WildRydesVue/ -b WildRydesVue

6. Create a git repo and populate it with source code of WildRydesVue
mkdir ../wild-rydes
cd ../wild-rydes
git init
git pull ../aws-serverless-webapp-workshop WildRydesVue

7. Create a repo and AWS CodeCommit and push this source code
git remote add origin codecommit://wild-rydes
git push -u origin master

8. Install amplify cli
npm install -g @aws-amplify/cli
amplify init

9. Add user pool to amplify app
amplify add auth

10. Push changes to the codecommit
git add .
git commit -m "made changes"
git push
```


`By Nazmul - Cloud DevOps Engineer`
