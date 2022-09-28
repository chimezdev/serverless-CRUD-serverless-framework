# CREATING A SERVERLESS APPLICATION USING 'SERVERLESS' FRAMEWORK

- Clown the repository and run the command `npm install -g serverless` to install the framework globally
- Go to the IAM dashboard of the aws console, create a new user and assign administator access(or restrict access to only what you want serverless to have access to)
- Run the command with the credentials of the IAM user you created `sls config credentials --provider aws --key YOUR_ACCESS_KEY --secret YOUR_SECRET_KEY --profile IAM_user_name`
- To create a serverless project you need a template. To get a list of available templates you can use, run `serverless create --help`
For this project, we will make use of the aws-nodejs-typescript template. Run the command `sls create --template aws-nodejs-typescript --path serverless-demo1` to create the template in the path you specify

# Deploy the default application

- cd into the path and run `npm i` to install the dependencies required.
run the command: `npx sls deploy` to deploy the stack to aws cloudFormation
Goto your aws dashboard(lambda, api gateways, s3, cloudformation dashboards) and notice that CloudFormation stack had been deployed.
copy the api endpoint displayed on the terninal to postman and test 
- run the command `sls remove` to delete the entire project

# Setting up the project structure

- delete the 'handler.ts' file, we don't need it
- 