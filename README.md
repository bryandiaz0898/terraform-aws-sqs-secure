# Terraform Module for Secure SQS Queue

This module creates a secure SQS queue with an optional Dead Letter Queue (DLQ) and encrypts it using a KMS key.

## Usage

```hcl
module "sqs_secure" {
  source = "app.terraform.io/<your-org-name>/sqs-secure/aws"
  version = "~> 1.0.0"
  queue_name_prefix = "my-queue"
  enable_dlq = true
  tags = {
    Name = "my-queue"
  }
}
```

## Inputs

- `queue_name_prefix` (string): Prefix for the SQS queue names (e.g., 'app-prod'). Will be used for main and DLQ if enabled.
- `enable_dlq` (bool): Set to true to create a Dead Letter Queue alongside the main SQS queue.
- `tags` (map(string)): A map of tags to apply to the SQS queues and KMS key.

## Outputs

- `main_queue_arn` (string): ARN of the main SQS queue.
- `main_queue_url` (string): URL of the main SQS queue.
- `dlq_arn` (string): ARN of the Dead Letter Queue (DLQ), if created.
- `kms_key_arn` (string): ARN of the KMS key used for queue encryption.
