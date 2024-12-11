# fleet-helm-issue
example repo to reproduce a fleet/helm issue

## Fleet issue

## Underlying Helm issue

Pulling the external-dns chart from the bitnami repo without
specifying a version fails (since late 2024. November)

```
helm pull external-dns --repo https://charts.bitnami.com/bitnami 
```


```
>yq '.entries.external-dns[]|[.created,.version,.urls[0]]' bitnami-index.yaml -o json|jq -c|head -5

["2024-12-10","8.7.0","oci://registry-1.docker.io/bitnamicharts/external-dns:8.7.0"]
["2024-12-04","8.6.1","oci://registry-1.docker.io/bitnamicharts/external-dns:8.6.1"]
["2024-11-19","8.6.0","oci://registry-1.docker.io/bitnamicharts/external-dns:8.6.0"]
["2024-11-07","8.5.1","https://charts.bitnami.com/bitnami/external-dns-8.5.1.tgz"]
["2024-11-05","8.5.0","https://charts.bitnami.com/bitnami/external-dns-8.5.0.tgz"]
```
### Note

Actulay bitnami has anounced the change to oci repo: https://blog.bitnami.com/2024/10/bitnami-helm-charts-moving-to-oci.html
