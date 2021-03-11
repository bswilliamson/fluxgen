These files were initially created with:
```
fluxctl install --git-branch='${GIT_BRANCH}' --git-email=flux --git-label='flux-${NAMESPACE}' --git-path='${GIT_PATH}' --git-url='https://${GIT_USER}:${GIT_PASS}@${GIT_REPO}' --manifest-generation --namespace='${NAMESPACE}' -o k8s
```

They were then adapted in the following way:
* All resources were namespace and/or prefixed with the namespace.
* The following flux options were added: `--k8s-default-namespace=${NAMESPACE}, --sync-garbage-collection, --git-ci-skip`.
* The flux ClusterRole permissions were removed.
* A flux Role for the namespace was added and all permissions granted.
