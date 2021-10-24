# hotdog-localstack-PoC
PoC for running AWS services(kinesis, dynamodb, lambdas) locally with Localstack

https://dev.to/mrwormhole/localstack-with-terraform-and-docker-for-running-aws-locally-3a6d

```
alias awslocal="aws --endpoint-url=http://localhost:4566 --region ap-southeast-2"
```

```
docker network create localstack-tutorial
docker-compose up -d --build
sudo apt install golang-go
./zip-it.sh
terraform init
aws configure # Optional fake credentials see https://dev.to/goodidea/how-to-fake-aws-locally-with-localstack-27me
terraform apply --auto-approve
awslocal lambda list-functions
awslocal dynamodb list-tables
awslocal kinesis list-streams
```

Note: Make sure you are matching your AWS REGION in docker-compose.yml, terraform provider's region and session.NewSession(). They all need to be the same region.
