# imaj dalı: NextStage için MinIO imajı

Bu dal MinIO kaynağı taşımaz. İçinde yalnız iki şey var:

- `Dockerfile.imaj`: MinIO'yu forkun kaynak ağacından derleyip ubi9 micro tabanına koyar (eski resmi imajla aynı taban, giriş betiği ve ortam değişkenleri).
- `.github/workflows/imaj.yml`: etiketi checkout eder, imajı amd64 ve arm64 için derler, `ghcr.io/furkaanboraa/minio:<etiket>` adıyla basar ve basılanı sınar.

Neden: MinIO'nun açık kaynak deposu 25 Eyl 2026'da arşivlendi; `minio/minio` imajı artık hiçbir kayıt defterinden çekilemiyor. NextStage'in compose dosyaları imajı buradan çeker (NextStage K-148).

Yeni bir etiket basmak: Actions sekmesinde "MinIO imajı (forktan GHCR'a)" iş akışını `imaj` dalında elle çalıştır, etiket ve beklenen commit'i gir. Bu dala push varsayılan etiketi (RELEASE.2025-09-07T16-13-09Z) yeniden basar.

`master` dalına dokunulmaz; MinIO kaynağı orada ve etiketlerde olduğu gibi durur.
