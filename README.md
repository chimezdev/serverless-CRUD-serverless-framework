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
- On the home directory, create a src/lambda/http directory. This http folder will contain all our lambda functions that are triggered by http events
- Create `getGroups.ts` file in the http folder. Copy the lambda function created from previous project that gets all items from our dynamodb Groups table. Available here: https://github.com/chimezdev/serverless-post-endpoint.git. Edit it to look like the one in this current repo.

# Time to configure our severless configuration file
- In the serverless.ts

#SERVERLESS LESSON 3
- In lesson2 error, delete package-lock.json and node_module.
- Install typescript version 4.x.x
- Run `npm install`
- In the tsconfig file add: "useUnknownInCatchVariables": false, save and rerun `npm i`

# Incase you get the following errors when you run `sls deploy`
# ERROR
- Webpack compilation failed: Module build failed (from ./node_modules/ts-loader/index.js):
- Debug Failure. False expression: Non-string value passed to `ts.resolveTypeReferenceDirective`, likely by a wrapping package working with an outdated `resolveTypeReferenceDirectives` signature. This is probably not a problem in TS itself.

#SOLUTION
- npm install typescript@latest ts-node@latest
- install this webpack version: webpack": "^5.74.0" or any other version but
- search for 'ts-loader' for the version of webpack that you installed in my case it was: "ts-loader": "^9.4.1"
- Then rerun 'npm install'
- then run 'sls deploy'