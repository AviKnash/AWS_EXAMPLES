# Create webiste 1
## Create a bucket

aws s3 mb s3://cors-fun-test

## Change block public access
aws s3api put-public-access-block \
    --bucket cors-fun-test \
    --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"

## Create  a bucket policy 

aws s3api put-bucket-policy --bucket cors-fun-test --policy file://bucket-policy.json

## Turn on static web hosting

aws s3api put-bucket-website --bucket cors-fun-test --website-configuration file://website.json

## Upload our index.html file and include a cross-origin resource

aws s3 cp index.html s3://cors-fun-test

## View website

http://cors-fun-test.s3-website-us-east-1.amazonaws.com


## Create website 2:
## Create bucket
aws s3 mb s3://cors-fun-test-2

## Change block public access
aws s3api put-public-access-block \
    --bucket cors-fun-test-2 \
    --public-access-block-configuration "BlockPublicAcls=true,IgnorePublicAcls=true,BlockPublicPolicy=false,RestrictPublicBuckets=false"

## Create  a bucket policy 

aws s3api put-bucket-policy --bucket cors-fun-test-2 --policy file://bucket-policy-2.json

## Turn on static web hosting

aws s3api put-bucket-website --bucket cors-fun-test-2 --website-configuration file://website.json

## Upload our javascript file

aws s3 cp hello.js s3://cors-fun-test-2


## Apply cors policy