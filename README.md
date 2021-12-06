# Repository of Helm Charts for use with Meltano

This repo is hosted on GitLab Pages.

## Releasing a new Helm Chart version

After making edits to either the `airflow/` or `meltano/` helm charts, be sure to increment the chart version number in the respective `Chart.yaml` file. This will be used below to create a new package version.

```sh
# From the top level dir, create a new package bundle from the latest Chart version:
helm package meltano

# Move the new bundle into the `public` folder for hosting on GitLab Pages:
mv meltano-0.1.1.tgz public/meltano

# Update the hosted index.yaml to include the new version:
cd public
helm repo index meltano --merge index.yaml --url "https://meltano.gitlab.io/infra/helm-meltano/meltano"
```

This should result in a new `meltano` entry in `public/meltano/index.yaml`:

```yaml
apiVersion: v1
entries:
  meltano:
  - apiVersion: v2
    appVersion: 1.89.0
    created: "2021-12-06T12:09:02.010899Z"
    description: A Helm chart for Kubernetes
    digest: f454c87334a26f26bd55a0fb219a641cd79f4dc48904c0ad7ee6b9793cbe38bb
    name: meltano
    type: application
    urls:
    - https://meltano.gitlab.io/infra/helm-meltano/meltano/meltano-0.1.1.tgz
    version: 0.1.1
  - apiVersion: v2
    appVersion: 1.16.0
    created: "2021-12-06T12:09:02.0104Z"
    description: A Helm chart for Kubernetes
    digest: 5e533092d37629d6bc0f5d766782a96873df25b4a3c284c52e0cfdf3cdf2672e
    name: meltano
    type: application
    urls:
    - https://meltano.gitlab.io/infra/helm-meltano/meltano/meltano-0.1.0.tgz
    version: 0.1.0
generated: "2021-12-06T12:09:02.009386Z"
```