Hot Fix
```
#@data/values
---
namespace: default
scanner:
  image: dcir.fcbcore-tt.com.tw/tap_package/tap@sha256:0166dbd011d6f5a3f7e67ef5b88656994a77ffdd994512546c8d05f3beb8982d
  pullSecret: scanner-secret-ref
  docker:
    username:
    password:
    server:
  serviceAccount: grype-scanner
  serviceAccountAnnotations:
metadataStore:
  image: dcir.fcbcore-tt.com.tw/tap_package/tap@sha256:bb2ad1aa211fd5a183fbb88d76011e3e6296017288b895472c61b7b82b604907
  url: https://metadata-store-app.metadata-store.svc.cluster.local:8443
  caSecret:
    name: app-tls-cert
    importFromNamespace: metadata-store
  authSecret:
    name:
    importFromNamespace:
  clusterRole: metadata-store-read-write
policy:
  image: dcir.fcbcore-tt.com.tw/tap_package/tap@sha256:141937d7e28a198ffa8c6bb6bea26de064ebebbffcc331d4e2d58b4a6dacddd8
syft:
  schema:
    version: 6.0.0
  failOnSchemaErrors: true
summary:
  image: dcir.fcbcore-tt.com.tw/tap_package/tap@sha256:5a28d4c025ff4b07df74c6105b3178b498cf8edc1bb338f9d2504a3eabc1af21
targetImagePullSecret: tap-registry
targetSourceSshSecret:
resources:
  limits:
    cpu: 1000m
  requests:
    cpu: 250m
    memory: 128Mi
```
```
---
apiVersion: imgpkg.carvel.dev/v1alpha1
images:
- annotations:
    kbld.carvel.dev/id: dev.registry.tanzu.vmware.com/vse-dev/grype-templates-image-1.3.x@sha256:0166dbd011d6f5a3f7e67ef5b88656994a77ffdd994512546c8d05f3beb8982d
  image: tl-core-dev01-cir.firstbank.com.tw/tap_package/tap@sha256:0166dbd011d6f5a3f7e67ef5b88656994a77ffdd994512546c8d05f3beb8982d
- annotations:
    kbld.carvel.dev/id: dev.registry.tanzu.vmware.com/vse-dev/compliance-check-image@sha256:141937d7e28a198ffa8c6bb6bea26de064ebebbffcc331d4e2d58b4a6dacddd8
  image: tl-core-dev01-cir.firstbank.com.tw/tap_package/tap@sha256:141937d7e28a198ffa8c6bb6bea26de064ebebbffcc331d4e2d58b4a6dacddd8
- annotations:
    kbld.carvel.dev/id: dev.registry.tanzu.vmware.com/vse-dev/insight-cli-integration-image:latest@sha256:bb2ad1aa211fd5a183fbb88d76011e3e6296017288b895472c61b7b82b604907
  image: tl-core-dev01-cir.firstbank.com.tw/tap_package/tap@sha256:bb2ad1aa211fd5a183fbb88d76011e3e6296017288b895472c61b7b82b604907
- annotations:
    kbld.carvel.dev/id: dev.registry.tanzu.vmware.com/vse-dev/scan-results-aggregator-image:latest@sha256:5a28d4c025ff4b07df74c6105b3178b498cf8edc1bb338f9d2504a3eabc1af21
  image: tl-core-dev01-cir.firstbank.com.tw/tap_package/tap@sha256:5a28d4c025ff4b07df74c6105b3178b498cf8edc1bb338f9d2504a3eabc1af21
kind: ImagesLock
```
