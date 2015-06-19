# Небольшой курс лекций по Elastic Search

[План лекций](https://docs.google.com/a/ria.com/document/d/1elQ5KLu-8UyaRsdJfhIN_BuxjQrMHgW5kVVU7xDw4TQ/edit?usp=sharing)

## Установка и настройка

Для ОС Fedora есть свой репозиторий. Для того, чтобы установить себе Elastic Search версии 1.4, необходимо добавить в файл `/etc/yum.repos.d/` следующие настройки:

```ini
[elasticsearch-1.4]
name=Elasticsearch repository for 1.4.x packages
baseurl=http://packages.elasticsearch.org/elasticsearch/1.4/centos
gpgcheck=1
gpgkey=http://packages.elasticsearch.org/GPG-KEY-elasticsearch
enabled=1
```

После этого установить его можно командой: 

```bash
yum install elasticsearch
```

### С чего начать?

Elastic Search - база данных с открытым исходным кодом предназначенная для полнотекстового поиска. Она позволяет хранить, анализировать и получать большие объемы данных в режиме реального времени.

Для анализа и поиска Elastic Search использует библиотеку [Apache Lucene](http://lucene.apache.org/core/). Его можно применять при реализации следующих задач:

- Полнотекстовый поиск
- Поиск по параметрам
- Агрегация данных для статистики и их последующая визуализация
- Генерация вариантов для автокомплита

Для работы с данными у Elastic Search есть специальное REST API. 

#### Основные параметры REST API

Если в запросе передать `?pretty=true`, то JSON в ответе будет отформатирован таким образом, что его можно будет прочитать.

Добавив параметр `?format=yaml`, ответ получим в yaml.

#### Терминология

В Elastic Search используются такие понятия, как индекс (index), тип (type) и документ (document). Если проводить аналогию с MySQL, то это база данных (database), таблица (table) и рядок (row)

#### Создание нового индекса

Самый простой вариант создания индекса приведен ниже:

```bash
curl -XPUT 'http://localhost:9200/twitter/'
```

Если все прошло нормально, то в ответе мы получим сообщение:

```json
{"acknowledged":true}
```

Также при создании индекса можно описать все типы документов, которые будут в нем хранится:

```bash
curl -XPOST localhost:9200/test -d '{
    "mappings" : {
        "type1" : {
            "properties" : {
                "field1" : { "type" : "string"}
            }
        }
    }
}'
```

#### Создание нового документа







### Инструменты для работы с Elastic Search

### Прогнозирование нагрузки

