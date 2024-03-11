# Week 0 — Billing and Architecture
## setup MFA
## create IAM user
## installing AWS CLI 
[installing for linux](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```
from aws console the below commands is to use cli prompt to help auto completting the command
and the example command is to get the identity of the used user
```bash
$ aws --cli-auto-prompt
> aws sts get-caller-identity
```
### you can set ENV for IAM/ user credential after creating access key from IAM
these ENV can be added to .profile or in the without saving it permenatly
```bash
export AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAM****
export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLE***
export AWS_DEFAULT_REGION=us-wes***
```
## you can set gitpos env for the AWS varible so they are inherted in each pod

### set AWS budget 
- [AWS create budget example](https://docs.aws.amazon.com/cli/latest/reference/budgets/create-budget.html#examples)
Get 
