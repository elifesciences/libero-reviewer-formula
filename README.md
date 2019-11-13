# Libero Reviewer Formula

## Setup

Configure your aws credentials, then configure you kubectl configuration
```sh
aws eks update-kubeconfig --name kubernetes-aws--test --role arn:aws:iam::512686554592:role/kubernetes-aws--test--AmazonEKSUserRole
```

Replace the name and role values with the appropriate ones

Install the chart dependencies:

```sh
helm dependency build ./helm/libero-reviewer
```

## Operate

Note: Change the 'libero-reviewer--test' to your chosen release name

To deploy a new release:

```sh
helm install libero-reviewer--test ./helm/libero-reviewer
```

Update a release

```sh
helm upgrade libero-reviewer--test ./helm/libero-reviewer
```

Delete a release

```sh
helm del --purge libero-reviewer--test
```