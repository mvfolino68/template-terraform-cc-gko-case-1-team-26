# Terraform Template for GKO Case 1

[Architecture Diagram](https://lucid.app/lucidchart/261b8c05-21bd-4d05-9c4d-c1b257ecb61a/edit?viewport_loc=-10096%2C-5802%2C9681%2C5887%2C0_0&invitationId=inv_193805e2-f890-4fd7-913b-fe567191907a)

## Before you get started

Before you get started, you're going to need a few things.

- Terraform (**_obviously_**)
- Confluent Cloud account
- AWS account
- Confluent Cloud **Cloud API Key & Secret**
- AWS API Key & Secret (ideally with some kind of admin permission)

If you don't have these things, create and collect them.

## Getting started

To begin, the absolute first thing you'll need to do is clone this repo.

```bash
git clone <repo name> && cd <repo name>
```

Next, you should create a secrets file to store you keys and secrets.

```bash
cat <<EOF > env.sh
export TF_VAR_CONFLUENT_CLOUD_API_KEY="<replace>"
export TF_VAR_CONFLUENT_CLOUD_API_SECRET="<replace>"
EOF
```

After copying your secrets into the file (replacing `<replace>`), you should export them to the console.

```bash
source env.sh
```

## Provisioning almost everything

Provisioning should be easy. This example is meant to create an **almost** end-to-end setup of components in AWS and Confluent Cloud (still waiting on the Ksql Query part). To provision everything follow the next few steps.

Initialize Terraform in the `/terraform` directory.

```bash
terraform init
```

Create a plan.

```bash
terraform plan
```

Apply the whole thing!

```bash
terraform apply -auto-approve
```

> **_Note:_** _the `-auto-approve` flag automagically accepts the implicit plan created by `apply`_.

Give your configuration some time to create. When it's done, head to the Confluent UI and check out what was provisioned.

## Ksql queries

To create the streaming topology, paste the following into you Ksql editor. **Be sure to set `auto.offset.reset` to `earliest`!**

**TBD**

Once everything has been created, go check out Stream Lineage to see your topology in action.

## Cleanup

Once you're satisfied with what you've built, do ahead and destroy it.

```bash
terraform destroy
```
