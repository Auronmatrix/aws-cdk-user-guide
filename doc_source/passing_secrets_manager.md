--------

This documentation is for the developer preview release \(public beta\) of the AWS Cloud Development Kit \(CDK\)\. Releases might lack important features and might have future breaking changes\.

--------

# Get a Value from AWS Secrets Manager<a name="passing_secrets_manager"></a>

To use values from AWS Secrets Manager in your CDK app, use the [Secret](https://awslabs.github.io/aws-cdk/refs/_aws-cdk_aws-secretsmanager.html#secret) class's `import` method\. It represents a value that is retrieved from Secrets Manager and used at AWS CloudFormation deployment time\.

```
import sm = require("@aws-cdk/aws-secretsmanager");

export class SecretsManagerStack extends cdk.Stack {
  constructor(scope: cdk.App, id: string, props?: cdk.StackProps) {
    super(scope, id, props);

    const secret = sm.Secret.import(this, "ImportedSecret", {
      secretArn:
        "arn:aws:secretsmanager:<region>:<account-id-number>:secret:<secret-name>-<random-6-characters>"
      // If the secret is encrypted using a KMS-hosted CMK, either import or reference that key:
      // encryptionKey,
    });
```