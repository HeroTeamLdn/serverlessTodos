# Extending a Serverless REST API example

This project riffs off of the [Serverless Framework Todo example](https://github.com/serverless/examples/tree/master/aws-node-rest-api-with-dynamodb), which demonstrates how to to create, list, get, update and delete Todos. DynamoDB is used to store the data.

## What's Different?
This repo extends the Serverless Framework example by adding:

* [Mocha](https://mochajs.org/) tests (current iteration)
* CI/CD using [AWS CodePipeline](https://aws.amazon.com/codepipeline/) (future)
* Anonymous [Bootstrap](http://getbootstrap.com/)-based web/mobile UI (future)
* Authenticated (with [AWS Cognito](https://aws.amazon.com/cognito/)) [Bootstrap](http://getbootstrap.com/)-based web/mobile UI (future)

## Setup
First, [follow the setup instructions for the Serverless Framework](https://serverless.com/framework/docs/providers/aws/guide/installation/), then:
```bash
npm install
```
will load additional dependencies this project requires.

## Deploy

Like in the example it is based on, in order to deploy your endpoint simply run

```bash
serverless deploy
```

The expected result should be similar to:

```bash
Serverless: Packaging service…
Serverless: Uploading CloudFormation file to S3…
Serverless: Uploading service .zip file to S3…
Serverless: Updating Stack…
Serverless: Checking Stack update progress…
Serverless: Stack update finished…

Service Information
service: serverless-rest-api-with-dynamodb
stage: dev
region: us-east-1
api keys:
  None
endpoints:
  POST - https://45wf34z5yf.execute-api.us-east-1.amazonaws.com/dev/todos
  GET - https://45wf34z5yf.execute-api.us-east-1.amazonaws.com/dev/todos
  GET - https://45wf34z5yf.execute-api.us-east-1.amazonaws.com/dev/todos/{id}
  PUT - https://45wf34z5yf.execute-api.us-east-1.amazonaws.com/dev/todos/{id}
  DELETE - https://45wf34z5yf.execute-api.us-east-1.amazonaws.com/dev/todos/{id}
functions:
  serverless-rest-api-with-dynamodb-dev-update: arn:aws:lambda:us-east-1:488110005556:function:serverless-rest-api-with-dynamodb-dev-update
  serverless-rest-api-with-dynamodb-dev-get: arn:aws:lambda:us-east-1:488110005556:function:serverless-rest-api-with-dynamodb-dev-get
  serverless-rest-api-with-dynamodb-dev-list: arn:aws:lambda:us-east-1:488110005556:function:serverless-rest-api-with-dynamodb-dev-list
  serverless-rest-api-with-dynamodb-dev-create: arn:aws:lambda:us-east-1:488110005556:function:serverless-rest-api-with-dynamodb-dev-create
  serverless-rest-api-with-dynamodb-dev-delete: arn:aws:lambda:us-east-1:488110005556:function:serverless-rest-api-with-dynamodb-dev-delete
```

## Usage

You can create, retrieve, update, or delete todos with the same `curl` commands as the [Serverless Framework ToDo example](https://github.com/serverless/examples/tree/master/aws-node-rest-api-with-dynamodb).

## Run Tests
Before you can run tests, you need to set the `TODOS_ENDPOINT` environment variable to the value of the domain name returned when you deployed your service.  Using values from the example above:

```bash
export TODOS_ENDPOINT=45wf34z5yf.execute-api.us-east-1.amazonaws.com
```

Now to run the tests:

```bash
npm test
```

The results should be similar to:

```bash
> aws-rest-with-dynamodb@1.0.0 test /Users/petercjo/serverlessTodos
> mocha



  Create, Read, Delete
    ✓ should create a new ToDo, read it, & delete it (1756ms)


  1 passing (2s)

```


