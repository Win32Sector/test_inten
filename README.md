## ABOUT

Пример чарта с deployment, job-migrator, ingress.

## Installation

Установить можно примерно так:

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
## Немного подробностей и что бы я сделал лучше и по другому

Я не совсем понял, почему нельзя выводить логи в stdout контейнера, а потом флюентом экранировать чувствительные данные и разделять индексы по какому-то ключевому слов.

Некоторые переменные в values указаны как null специально. Так как я предполагаю, что версии и коннеккшнсстринги к базе задаются выше чарта, например, в CI, где мы определяем, на какой стенд деплоим чарт и, в зависимости от этого, подтягиваются эти переменные.