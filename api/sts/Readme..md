## Create a user with no permissions

aws iam create-user --user-name AviTest

aws iam create-access-key --user-name AviTest --output table

aws configure

open ~/.aws/credentials

aws sts get-caller-identity --profile sts

## Use new creds and assume role

# GIve policy

aws iam put-user-policy \
--user-name AviTest \
--policy-name StsAssumePolicy \
--policy-document file://policy.json


## Assume role

aws sts assume-role \
    --role-arn arn:aws:iam::730335237557:role/my-sts-stack-StsRole-3pSFjlJCe4g5 \
    --role-session-name s3-sts-fun \
    --profile sts

# Clean up

aws iam delete-user-policy --user-name AviTest --policy-name StsAssumePolicy

aws iam delete-access-key --access-key-id  --user-name AviTest

aws iam delete-user --user-name AviTest

