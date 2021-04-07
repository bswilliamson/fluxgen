A simple script to generate [flux v1](https://docs.fluxcd.io/en/1.21.2/) manifests that are namespaced to allow independent flux agents to run on the same cluster.

# Quick start
```
git clone https://github.com/bswilliamson/fluxgen # clone the repo
cd fluxgen
./fluxgen -n your-namespace > flux.yml           # generate the manifest
vim flux.yml                                     # add git URL, branch and user to flux deployment arguments
kubectl apply -f flux.yml
```

# Guide

Clone the repository and `cd` in to the directory.

```
git clone https://github.com/bswilliamson/fluxgen
cd fluxgen
```

Run the `fluxgen` script, providing the namespace that you want flux to be deployed into and redirect the output into a file.

```
./fluxgen -n your-namespace > flux.yml
```

Edit the the [flux daemon](https://docs.fluxcd.io/en/1.21.2/references/daemon/) arguments in the flux deployment manifest you just generated using your preferred editor. You need to add the `--git-url` (which must include the credentials flux will use) but the remainder of the options can be left as-is or adjusted as required.

Finally use `kubectl` to apply the manifest.
```
kubectl apply -f flux.yml
```

