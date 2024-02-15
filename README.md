### Creating a Stack

            aws cloudformation create-stack \
        --stack-name demo-postgres-stack \
        --template-body file://aws-rds-postgres-deploy.yaml \
        --profile d2s


### Describing A stack (to see what has been created)

        aws cloudformation describe-stacks --stack-name my-stack


### Updating a Stack

To Update a Stack eg; your nested step function and lambda workflow, run.

            aws cloudformation update-stack \ 
        --stack-name demo-sf-yaml-nested-stack \
        --template-body file://nested_workflows_v2.yaml \
        --capabilities CAPABILITY_NAMED_IAM

### Deleting a Stack

        aws cloudformation delete-stack  --stack-name my-stack
