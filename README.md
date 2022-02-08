## ABOUT

Example chart with deployment, job-migrator, ingress.

## Installation

For example we can install this chart with command

```
helm upgrade --install $releaseName-api intento_test/api \
  -f intento_test/api/values.$mode.yaml \
  --set image.containerRegisterName=$containerRegisterName \
  --set image.containerRegisterSecret=$containerRegisterSecret \
  --set image.tag=$imageTag \
  --set infrastructure.ingress.host=$host \
  --set database.connectionString=$PGconnectionString \
  --timeout 15m0s --debug --logtostderr > $logfilePath-api \
  -n $Namespace
```
