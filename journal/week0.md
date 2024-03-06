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
test
