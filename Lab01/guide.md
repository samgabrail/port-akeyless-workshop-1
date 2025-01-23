# Environment Setup


<!-- @import "[TOC]" {cmd="toc" depthFrom=1 depthTo=6 orderedList=false} -->

<!-- code_chunk_output -->

- [Environment Setup](#environment-setup)
  - [1. Fork GitHub Repo](#1-fork-github-repo)
  - [2. Start a Codespace](#2-start-a-codespace)
  - [3. Get AWS Access](#3-get-aws-access)
  - [4. Run minikube](#4-run-minikube)
  - [5. Run a keep alive for the codespace](#5-run-a-keep-alive-for-the-codespace)

<!-- /code_chunk_output -->



## 1. Fork GitHub Repo

Go to this repo and fork it to your own GitHub account so you have full control over the CI/CD pipeline.

> DISCLAIMER: Please use a DUMMY GITHUB ACCOUNT for this lab as you will be asked to create a personal access token for the GitHub API which will be visible to the instructor and to other participants. You also will be asked to attach your github account to Port.

## 2. Start a Codespace

Start a GitHub Codespace on your forked repo.

## 3. Get AWS Access

> Note that this section is only if you are subscribed to the TeKanAid Premium subscription as we will provide you with AWS credentials. If you are not subscribed to TeKanAid Premium, you can skip this step and use your own AWS credentials for your own AWS account.

If you are working on this workshop live then ask your instructor to provide the `AKEYLESS_ACCESS_ID` and `AKEYLESS_ACCESS_KEY` credentials. If you are working on this workshop on your own and you are a premium subscriber then get your Akeyless creds from the TeKanAid lesson text in `Lab01-Environment Setup`.

When you run the `Lab01/start.sh` script you will be asked to enter these credentials.

```bash
Lab01/start.sh
```

The script will create your AWS credentials using Akeyless' Dynamic AWS Secrets. It will configure programmatic access (`AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`) by writing to ~/.aws/credentials.

You can also see all the credentials including the ones that allow you to log into the AWS console at `/tmp/aws-credentials` which looks like this:

```json
{
  "access_key_id": "xxx",
  "id": "tmp.p-hoz17m5u765ram.J7L87",
  "password": "xxx",
  "secret_access_key": "xxx",
  "ttl_in_minutes": "180",
  "type": "aws_dynamic_user",
  "user": "tmp.p-hoz17m5u765ram.J7L87"
}
```

Finally, use the URL below to access the AWS Console:

```bash
https://047709130171.signin.aws.amazon.com/console/
```

your IAM user name is the same as the "user" above and your Password is the "password" above.

## 4. Run minikube

```bash
minikube start --cpus 3 --memory 8g
```
Wait for minikube to be ready. Then run the follwing command to check nodes:

```bash
kubectl get nodes
```

You should see something like this:

```
NAME       STATUS   ROLES           AGE   VERSION
minikube   Ready    control-plane   12s   v1.31.0
```

## 5. Run a keep alive for the codespace

In a new terminal, run the following command to keep the codespace alive.

```bash
while true; do date; sleep 60; done
```

> You've reached the end of the lab.