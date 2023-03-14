# Склады и товары

## Техническая задача: реализовать CRUD-логику для продуктов и складов, используя Django Rest Framework.


## Описание

Есть продукты, которыми торгует компания. Продукты описываются названием и необязательным описанием (см. `models.py`). Также компания имеет ряд складов, на которых эти продукты хранятся. У продукта на складе есть стоимость хранения, поэтому один и тот же продукт может иметь разные стоимости на разных складах.

- Реализовано REST API для создания/получения/обновления/удаления продуктов и складов. Так как склады имеют информацию о своих продуктах (через связанную таблицу) - необходимо переопределить методы создания и обновления объектов в сериализаторе (см. `serializers.py`).

- Реализован поиск продуктов по названиям и описанию. И поиск складов, в которых есть определенный продукт (по идентификатору). Подробности в файле `requests-examples.http`.

- Реализована пагинация для вывода списков.

- Реализован поиск складов, в которых есть определенный продукт, но при этом указывать хочется не идентификатор продукта, а название (или его часть) или часть описания.

Пример запроса:

```
# поиск складов, где есть определенный продукт
GET {{baseUrl}}/stocks/?products=помид
Content-Type: application/json
```

## Документация по проекту

Для запуска проекта необходимо:

Установить зависимости:

```bash
pip install -r requirements.txt
```

Вам необходимо будет создать базу в postgres и прогнать миграции:

```base
manage.py migrate
```

Выполнить команду:

```bash
python manage.py runserver
```
