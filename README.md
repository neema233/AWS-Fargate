# Starting with AWS-Fargate

### 1- Build your image
`docker build -t imagename:version .`

### 2- Run with AWS credential to test your image 
`docker run -e AWS_ACCESS_KEY_ID=your_accesskey -e AWS_SECRET_ACCESS_KEY=your_secretkey-e AWS_DEFAULT_REGION=your_region task_app:v1`

### 3- Log to AWS ECR
`aws ecr get-login-password --region your_region | docker login --username AWS --password-stdin acount_id.dkr.ecr.your_region.amazonaws.com`

### 4- Create ECR repository
`aws ecr create-repository --repository-name etl_task`

### 5- Tag the repository
`docker tag task_app:v1 acount_id.dkr.ecr.region.amazonaws.com/etl_task:v1`

### 6- Push your image 
`docker push acount_id.dkr.ecr.region.amazonaws.com/etl_task:v1`

