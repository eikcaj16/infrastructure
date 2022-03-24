# CSYE 6225 Infrastructure

*Yiqing Huang 001525629 huang.yiqin@northeastern.edu*

## Prerequisites

- AWS Command Line Interface (CLI)



## Usage

1. Go to the root directory of the repository.

   ```shell
   cd .../infrastructure
   ```

2. Assume that AWS configuration has already been set. Export the following 2 environment variables to make life easier.

   ```shell
   export AWS_PROFILE=[profile-name]
   export AWS_REGION=[region-name]
   ```

3. Create a VPC by using `csye6225-infra.json` (CloudFormation template).

   ```shell
   aws cloudformation create-stack --stack-name [stack-name] --template-body file://csye6225-infra.yaml --capabilities CAPABILITY_NAMED_IAM
   ```

   There are 5 parameters that users can input: `VpcCidrBlock`, `Subnet1CidrBlock`, `Subnet2CidrBlock`, `Subnet3CidrBlock`, `RouteDestinationCidrBlock`. If you would like to pass one or some of the parameters, use the following command.

   ```shell
   aws cloudformation create-stack --stack-name [stack-name] --template-body file://csye6225-infra.yaml --parameters ParameterKey=[key],ParameterValue=[value]
   ```

   For more details on the parameter, please refer to [AWS CloudFormation StackSets](https://docs.aws.amazon.com/codepipeline/latest/userguide/action-reference-StackSets.html).

4. [Optional] Update a VPC by using `csye6225-infra.json` (CloudFormation template).

   ```shell
   aws cloudformation update-stack --stack-name [stack-name] --template-body file://csye6225-infra.yaml
   ```

5. Delete a VPC.

   ```shell
   aws cloudformation delete-stack --stack-name [stack-name]
   ```

