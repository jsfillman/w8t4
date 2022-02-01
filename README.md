# w8s4
A simple Bash script is used to manage startup dependencies in the Rancher 2 environment.
This script is used by the KBase [init-sidecar](https://github.com/kbase/init-sidecar/) image.

### Usage

```
usage: w8s4 [-d <ConfigMap Path>]
```

**Note:** The ConfigMap path will default to `/kb/init/w8s4` if not specified.

### Process

1. Reads all key=value pairs from a Kubernetes [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/), mounted as a volume.
1. Runs [wait-for-it.sh](https://github.com/vishnubob/wait-for-it) on every key/value in a mounted K8s ConfigMap.

### ConfigMap Format

The YAML formatting for the required ConfigMap should include a `data` section with `key`:`value` pairs for `host`:`port`

```yaml
apiVersion: v1
kind: ConfigMap
data:
  auth2: "8080"
  blobstore: "8080"
  hs2: "5000"
  mongo: "27017"

```
