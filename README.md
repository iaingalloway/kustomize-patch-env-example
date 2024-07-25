# Kustomize patch env example

This repository contains an example of how to patch environment variables into a deployment using Kustomize.

Patching environment variables into a deployment using Kustomize appears to have a few pitfalls.

- If we use a strategic merge patch, we have to know the name of the container we want to patch.
- If we use a JSON patch, the env node must already exist in the deployment manifest.
- If we use a configmap, we must use a configMapGenerator to ensure that the resources that reference it get updated when the configmap changes.

## Usage

To build the json patch version:

```bash
docker run --rm -it -v $(pwd):/workspace -w /workspace registry.k8s.io/kustomize/kustomize:v5.2.1 build json-patch
```

To build the strategic merge patch version:

```bash
docker run --rm -it -v $(pwd):/workspace -w /workspace registry.k8s.io/kustomize/kustomize:v5.2.1 build strategic-merge-patch
```

To build the config-map version:

```bash
docker run --rm -it -v $(pwd):/workspace -w /workspace registry.k8s.io/kustomize/kustomize:v5.2.1 build config-map
```
