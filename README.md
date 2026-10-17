# MSKazemi/homebrew-kube-q

Homebrew tap for **`kq`** — the terminal client for
[KubeIntellect](https://github.com/MSKazemi/kubeintellect), an AI SRE for
Kubernetes.

```bash
brew tap MSKazemi/kube-q
brew install kube-q
kq --version
```

`kq` is a client: it talks over HTTPS to a KubeIntellect server that you
self-host. Point it at one with `KUBE_Q_URL` (and `KUBE_Q_API_KEY` if the server
has auth enabled), then run `kq`.

Deploy a server with the Helm chart:

```bash
helm install kubeintellect oci://ghcr.io/mskazemi/charts/kubeintellect \
  --namespace kubeintellect --create-namespace
```

## Other ways to install the client

| Method | Command |
|---|---|
| pipx / uv (any OS with Python) | `pipx install kube-q` or `uv tool install kube-q` |
| kubectl plugin | `kubectl krew install kq` |
| Standalone binary | Download from the [releases](https://github.com/MSKazemi/kubeintellect/releases) |

## How this tap stays current

`.github/workflows/bump.yml` checks PyPI daily. When a newer `kube-q` is
published it rewrites the formula's `url` and `sha256`, then — before committing
anything — runs `brew audit --strict --online` and actually builds and runs the
formula with `brew install --build-from-source`. A bump that does not install is
never committed, so this tap cannot drift into the state where the formula looks
right but cannot be installed.

Source of truth for the formula is this repository. Issues and pull requests
belong on the [main repo](https://github.com/MSKazemi/kubeintellect/issues).

Licensed AGPL-3.0-or-later, matching the software it installs.

<!-- legal-notice: start -->
### Legal notice and responsible use

The materials in this repository are made available without warranties to the extent permitted by applicable law. **Please read the [Disclaimer and Responsible-Use Notice](DISCLAIMER.md)** before relying on or deploying them. This notice does not change any existing software license or limit rights that cannot legally be waived.
<!-- legal-notice: end -->
