## COnvert to json

yq -o json policy.yaml > policy.json


# Create iam policy
aws iam create-policy \
--policy-name my-fun-policy \ 
--policy-document file://policy.json