# gitops-manifests

Repo chứa Helm chart + ArgoCD Application manifests cho các microservice của CoCoCoffeeCode.

## Cấu trúc
- `apps/<app-name>/` — Helm chart (Chart.yaml, templates/, values.yaml)
- `apps/<app-name>/<env>/values.yaml` — override theo môi trường, được CI tự động cập nhật `image.tag`
- `argocd/apps/<app-name>-<env>.yaml` — Application CR, ArgoCD root-app tự phát hiện

## Thêm app mới
1. Copy structure `apps/demo-app/` sang `apps/<tên-app-mới>/`
2. Thêm file `argocd/apps/<tên-app-mới>-<env>.yaml` theo mẫu `demo-app-dev.yaml`
3. Push lên main — ArgoCD root-app tự tạo Application mới, không cần thao tác thủ công trên cluster
