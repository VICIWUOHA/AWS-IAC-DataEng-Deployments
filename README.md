# IAC /SERVERLESS DEPLOYMENTS ON AWS FOR DATA ENGINEERING WORKLOADS

This repository houses some quick and easy to use templates for deploying resources on AWS.

### Prerequisites

- Basic knowledge of the services below via the AWS console.
- AWS CLI Installlation.


### Services Deployed

- RDS
- Step Functions (Using CF Templates and [regular ASL using VSCode Extension])
- Lambda Functions

### Creating a Stack

            aws cloudformation create-stack \
        --stack-name demo-postgres-stack \
        --template-body file://aws-rds-postgres-deploy.yaml \
        --profile your-profile

The `--profile flag` is important only if you have more than one set of aws cli profiles.


### Describing A stack (to see what has been created)

        aws cloudformation describe-stacks --stack-name my-stack

### Validating  a Stack

        aws cloudformation validate-template --template-body file://rds/aws-rds-postgres-deploy.yaml

### Updating a Stack

To Update a Stack eg; your nested step function and lambda workflow after a previous deployment, run.

            aws cloudformation update-stack \
        --stack-name demo-sf-yaml-nested-stack \
        --template-body file://step-funcs-and-lambda/nested_step_funcs_with_lambdas.yaml \
        --capabilities CAPABILITY_NAMED_IAM

The `--capabilities` argument is necesssary because we would be creating IAM roles and giving them names.


### Deleting a Stack

        aws cloudformation delete-stack  --stack-name my-stack


### Amazon State Language - ASL 
Simply Saving your yaml files of a step function using the `.asl.yaml` file extension enables VSCode (if the AWS Toolkit is installed) to identify it as an asl template giving you the ability to easily click to either create a state machine or update an existing one.
Note: This can also be written in Json.
