# Flux CD

This repository holds helm charts that will be deployed to your cluster and be kept in sync with the definitions set out in k8s_infra folder.

## Bootstrap the cluster

```shell
flux bootstrap github \
  --owner=<github_username> \
  --repository=<repo_name> \
  --branch=main \
  --path=./clusters/<path> \
  --personal
```
Set up a PAT token with necessary permissions to the repo.

## Helm charts

The helm chart definitions are using config maps that are created as part of an initial terraform deployment for any override values.

## Useful debugging

```shell

# If a release hasn't installed as expected
$ kubectl describe helmrelease  <release_name> -n <namespace>

# Check the status of a release
$ flux get helmrelease <release_name> -n <namespace>

```