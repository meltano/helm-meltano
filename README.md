# Repository of Helm Charts for use with Meltano

This repo is hosted on GitLab Pages.

## Releasing a new Helm Chart version

After making edits to either the `airflow/` or `meltano/` helm charts, be sure to increment the chart version number in the respective `Chart.yaml` file. This will be used below to create a new package version.

```sh
# From the top level dir, create a new package bundle from the latest Chart version:
helm package meltano-ui

# Move the new bundle into the `public` folder for hosting on GitLab Pages:
mv meltano-0.1.1.tgz public/meltano-ui

# Update the hosted index.yaml to include the new version:
cd public
helm repo index meltano-ui --merge index.yaml --url "https://meltano.gitlab.io/infra/helm-meltano/meltano-ui"
```

This should result in a new `meltano-ui` entry in `public/meltano/index.yaml`:

```yaml
apiVersion: v1
entries:
  meltano-ui:
  - apiVersion: v2
    appVersion: 1.89.0
    created: "2022-02-07T10:34:14.42278Z"
    description: A Helm chart for Kubernetes
    digest: e7951d71cd8936d29c6c9de15845d198bb6240bbf9c603bd452dc77ffb5a76f6
    name: meltano-ui
    type: application
    urls:
    - https://meltano.gitlab.io/infra/helm-meltano/meltano-ui/meltano-ui-0.2.0.tgz
    version: 0.2.0
generated: "2022-02-07T10:34:14.422258Z"
```