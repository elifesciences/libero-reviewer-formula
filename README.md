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

Note: Change the 'libero-reviewer--staging' to your chosen release name

To deploy a new release:

```sh
helm install --name libero-reviewer--staging ./helm/libero-reviewer -f environments/staging.yaml
```

Update a release:

```sh
helm upgrade libero-reviewer--staging ./helm/libero-reviewer -f environments/staging.yaml
```

Get the status:
```sh
helm status libero-reviewer--staging
```

Delete a release:
```sh
helm del --purge libero-reviewer--staging
```

## Secrets

Temporary: change this once we have vault integration

Create a secret by creating a yaml file (not to be added to repo for obvious reasons):

secrets.yaml
```yaml
apiVersion: v1
kind: Secret
metadata:
  name: libero-reviewer--staging
type: Opaque
stringData:
  jwtSecret: "some_random_value"
```

Then run:
```sh
kubectl apply -f secrets.yaml
```

Update the release.