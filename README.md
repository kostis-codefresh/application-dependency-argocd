# Example for application depedencies in Argo CD

If you use the app-of-apps pattern in Argo CD all applications are deployed in parallel.
Sometimes however you want to deploy them in order

First instruct Argo CD that you want to monitor application health

```
$ kubectl patch cm/argocd-cm --type=merge -n argocd --patch-file patch-argocd-cm.yaml
```

Then put [sync waves](https://argo-cd.readthedocs.io/en/stable/user-guide/sync-waves/) on your apps. 
See the [example folder](apps).

Finally deploy all apps

```
kubectl apply -f all-apps.yml
```

For the full details read the blog post at [https://codefresh.io/blog/argo-cd-application-dependencies/](https://codefresh.io/blog/argo-cd-application-dependencies/).
