# Домашнее задание к занятию "`#«Средство визуализации Grafana» - Ощепков Дмитрий`"

## Задание повышенной сложности

При решении задания 1 не используйте директорию help для сборки проекта. Самостоятельно разверните grafana, где в роли источника данных будет выступать prometheus, 
а сборщиком данных будет node-exporter:

grafana;
prometheus-server;
prometheus node-exporter.

За дополнительными материалами можете обратиться в официальную документацию grafana и prometheus.
В решении к домашнему заданию также приведите все конфигурации, скрипты, манифесты, которые вы использовали в процессе решения задания.

При решении задания 3 вы должны самостоятельно завести удобный для вас канал нотификации, например, Telegram или email, и отправить туда тестовые события.

В решении приведите скриншоты тестовых событий из каналов нотификаций.

Ответ: Скриншот оповещения на личную почту от Alert_Grafana
![TestAlert_Grafana](https://github.com/OshchepkovDP/Grafana-visualization-tool/blob/main/img/TestAlert_Grafana.jpg)

## Обязательные задания

# Задание 1

Используя директорию help внутри этого домашнего задания, запустите связку prometheus-grafana.
Зайдите в веб-интерфейс grafana, используя авторизационные данные, указанные в манифесте docker-compose.
Подключите поднятый вами prometheus, как источник данных.
Решение домашнего задания — скриншот веб-интерфейса grafana со списком подключенных Datasource.

Ответ:
Скриншот веб-интерфейса grafana с подключённым prometheus 
![Grafana](https://github.com/OshchepkovDP/Grafana-visualization-tool/blob/main/img/Grafana.jpg)

# Задание 2

Изучите самостоятельно ресурсы:

PromQL tutorial for beginners and humans.
Understanding Machine CPU usage.
Introduction to PromQL, the Prometheus query language.
Создайте Dashboard и в ней создайте Panels:

утилизация CPU для nodeexporter (в процентах, 100-idle);
CPULA 1/5/15;
количество свободной оперативной памяти;
количество места на файловой системе.
Для решения этого задания приведите promql-запросы для выдачи этих метрик, а также скриншот получившейся Dashboard.

Ответ: 

promql-запросы

```
Утилизация CPU (в процентах, 100 − idle)
100 - (avg by (instance) (rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)

CPULA 1/5/15
node_load1
node_load5
node_load15

Количество свободной оперативной памяти
node_memory_MemFree_bytes + node_memory_Buffers_bytes + node_memory_Cached_bytes

Количество места на файловой системе
node_filesystem_avail_bytes{fstype!~"tmpfs|squashfs|overlay"}

```

Скриншот получившейся Dashboard 
![Dashboard](https://github.com/OshchepkovDP/Grafana-visualization-tool/blob/main/img/Dashboard.jpg)


# Задание 3

Создайте для каждой Dashboard подходящее правило alert — можно обратиться к первой лекции в блоке «Мониторинг».
В качестве решения задания приведите скриншот вашей итоговой Dashboard.

Ответ: Скриншот правила alert, как видно из скриншота, alert привязан к Dashboard с названием panel
![Alert-panel](https://github.com/OshchepkovDP/Grafana-visualization-tool/blob/main/img/Alert-panel.jpg)


# Задание 4

Сохраните ваш Dashboard.Для этого перейдите в настройки Dashboard, выберите в боковом меню «JSON MODEL». Далее скопируйте отображаемое json-содержимое в отдельный файл и сохраните его.
В качестве решения задания приведите листинг этого файла.

Ответ:
Скриншот содержимого файла с JSON MODEL
![my-dashboard_json](https://github.com/OshchepkovDP/Grafana-visualization-tool/blob/main/img/my-dashboard_json.jpg)
