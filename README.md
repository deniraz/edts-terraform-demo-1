Terraform Demo 1 — Init, Validate, Plan (Participant Guide)

SESSION GOAL
This demo focuses on understanding the Terraform workflow, not on creating real cloud resources.

You will learn how to:
- understand a basic Terraform project structure
- run terraform init
- run terraform validate
- read and interpret terraform plan

IMPORTANT:
No terraform apply is required or expected in this demo.
The AWS access used in this session is READ-ONLY by design.


PREREQUISITES
Before the session, please make sure you have:
- Terraform CLI v1.14+ installed
- Git installed

You do NOT need:
- a personal AWS account
- your own AWS credentials


PROJECT STRUCTURE
After cloning the repository, you should see a structure like this:

.
├── main.tf
├── variables.tf
├── versions.tf
├── outputs.tf
└── README.txt

Important note:
Terraform treats all .tf files in a directory as ONE logical configuration,
regardless of file order.


DEMO STEPS

STEP 1 — Clone the Repository
git clone https://github.com/deniraz/edts-terraform-demo-1.git
cd <REPO_FOLDER>


STEP 2 — Initialize Terraform
terraform init

What this does:
- prepares the working directory
- downloads required providers
- DOES NOT create any cloud resources


STEP 3 — Validate the Configuration
terraform validate

What Terraform checks:
- syntax correctness
- configuration structure
- references between resources

terraform validate does NOT interact with AWS.


STEP 4 — Preview Changes with Terraform Plan
terraform plan

What you will see:
- which resources WOULD be created
- dependency relationships between resources
- values marked as "known after apply"

Example output:
Plan: 7 to add, 0 to change, 0 to destroy.

This means Terraform successfully calculated the desired changes.


ABOUT PERMISSIONS & APPLY

The AWS credentials used in this demo:
- are READ-ONLY
- cannot create, modify, or delete resources
- are safe to use in a shared training environment

If you try to run:
terraform apply

You will see an authorization error.

This is EXPECTED behavior.
- No resources will be created
- No cost will be incurred
- This is intentional


KEY CONCEPTS TO UNDERSTAND

- terraform plan is NOT the same as terraform apply
- Terraform plans changes, AWS enforces permissions
- IAM permissions act as guardrails, not errors
- In real production environments:
  - plan is reviewed and approved
  - apply is executed by CI/CD pipelines, not developers


FAQ

Q: Why don’t we run terraform apply?
A: The goal is to understand Terraform’s workflow safely, without changing real infrastructure.

Q: Is this how Terraform is used in real projects?
A: Yes. In production, apply is usually restricted and automated via pipelines.

Q: Why do some values say "known after apply"?
A: Those values are only assigned by AWS after the resource is actually created.


SUMMARY
- Safe, read-only environment
- No AWS account required
- No risk of unexpected costs
- Focused on Terraform fundamentals

The session will continue with Demo 2, where we discuss Terraform State and Remote Backends.
