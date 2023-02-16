# domains

This AWS CloudFormation application configures AWS Route 53 hosted zones for custom domains. It utilizes CloudFormation StackSets to configure region-specific resources required for DNS logging and cross-region CloudFormation exports of the created hosted zone ID and domain name to help define CloudFormation stack and application lineage.

## Prerequisites

- You must enable self-managed CloudFormation StackSet execution in your AWS Account, by [creating all required IAM roles](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/stacksets-prereqs-self-managed.html): `AWSCloudFormationStackSetAdministrationRole` and `AWSCloudFormationStackSetExecutionRole`.

## Installation

### Software prerequisites

- [**AWS CLI**](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html);
- [**AWS SAM CLI**](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-getting-started.html).

### CloudFormation / SAM configuration

#### Template parameters

This CloudFormation template requires the following parameters to be overwritten:

Parameter name                 | Required |             Value(s)             |                                                                                                                           Description
:----------------------------- | :------: | :------------------------------: | ------------------------------------------------------------------------------------------------------------------------------------:
`TagApplication`               |    No    |      **Default:** domains        |                                                            A unique, friendly name used to identify resources deployed by this stack.
`TagEnvironment`               |   Yes    |  **Allowed values:** dev / prod  | The target environment name will be tagged to all deployed resources and used to determine environment-specific configurations.

### Deploying the application

- Build and deploy the stack with AWS SAM CLI:
  ```sh
  sam build
  sam deploy --guided
  ```
