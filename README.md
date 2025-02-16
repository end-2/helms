# Kubernetes LAB - Helms

## Required
1. helm
```bash
curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
chmod 700 get_helm.sh
./get_helm.sh
```

2. kind
```bash
# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.26.0/kind-linux-amd64
# For ARM64
[ $(uname -m) = aarch64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.26.0/kind-linux-arm64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

3. gomplate
```bash
go install github.com/hairyhenderson/gomplate/v4/cmd/gomplate@latest
```

4. helmfile
https://github.com/helmfile/helmfile?tab=readme-ov-file#installation

## Deploy kind cluster
```bash
gomplate --file ./kind/TARGET_FILE.yaml.tmpl > ./kind/OUTPUT_FILE_NAME.yaml
kind create cluster --config ./OUTPUT_FILE_NAME.yaml
```

## Deploy helmfile
```bash
helmfile sync
```
