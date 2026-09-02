# gitops-manifests

Repo chứa Helm chart + ArgoCD Application manifests cho các microservice của CoCoCoffeeCode.

## Cấu trúc
- `apps/<app-name>/` — Helm chart (Chart.yaml, templates/, values.yaml). `<app-name>` khớp đúng tên repo GitHub của app đó (= `image_name` truyền vào CI)
- `apps/<app-name>/<env>/values.yaml` — override theo môi trường, được CI tự động cập nhật `image.tag`
- `argocd/apps/<app-name>/<env>.yaml` — Application CR, ArgoCD root-app tự phát hiện (recurse toàn bộ `argocd/apps/`)

## Thêm app mới
1. Copy structure `apps/application-demo-git-workflow/` sang `apps/<tên-app-mới>/`
2. Thêm file `argocd/apps/<tên-app-mới>/<env>.yaml` theo mẫu `argocd/apps/application-demo-git-workflow/dev.yaml`
3. Push lên main — ArgoCD root-app tự tạo Application mới, không cần thao tác thủ công trên cluster
