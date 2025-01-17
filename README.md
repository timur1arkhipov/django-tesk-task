# Задание на тестирование: Модуль каталога на Django

## Описание задачи

Необходимо разработать модуль каталога товаров. Каталог включает в себя следующие элементы:

- **Товар**:
  - Название
  - Описание
  - Базовая стоимость
  - Порядок отображения

Каждый товар может содержать:

- **Изображения**:
  - Файл изображения
  - Подпись
  - Порядок сортировки

- **Параметры**:
  - Название параметра
  - Значение параметра
  - Стоимость параметра
  - Порядок сортировки

Администрирование каталога должно осуществляться через интерфейс Django Admin. Для вывода данных каталога следует использовать REST API:

- Список всех товаров
- Подробная информация о каждом товаре

## Требования к системе

- Версия Python: 3.8 и выше
- Версия Django: 3.2
- Допустимо использование любых общедоступных сторонних модулей
- СУБД: PostgreSQL версии 13 и выше
- Реализация должна включать фикстуры с тестовыми данными для модуля «каталог»
- Кэш-сервер: Redis версии 5 и выше

## Инструкция по запуску проекта

Для успешного запуска проекта создайте файл `settings/local.py`, содержащий следующую информацию:

```python
# Настройки Django
# База данных
from .core import DATABASES  # noqa
DATABASES['default']['PASSWORD'] = 'ВАША-ПАРОЛЬ-К-БАЗЕ-ДАННЫХ'

# Режим отладки
# https://docs.djangoproject.com/en/3.2/ref/settings/#debug
from .core import TEMPLATES  # noqa
DEBUG = True
INTERNAL_IPS = ('127.0.0.1', 'localhost')
TEMPLATES[0]['OPTIONS'].update({'debug': DEBUG})
ALLOWED_HOSTS = ['*']

# Настройка электронной почты
EMAIL_BACKEND = 'django.core.mail.backends.console.EmailBackend'
```

# Настройки сторонних сервисов
Этот файл потребуется настроить согласно вашему окружению.


# Как мы будем проверять ваше решение
Выполнение задания будет протестировано на операционной системе Linux.
Все используемые сторонние библиотеки должны быть указаны в файле requirements.txt.
Дополнительное задание (бонусы)

# Если вы хотите получить дополнительные баллы, выполните следующее:
Добавьте фильтрацию списка товаров по названиям и значениям параметров.
Разработайте отдельный эндпоинт для получения списка параметров, подходящих для фильтрации:
Параметры будут отображены только если они присутствуют хотя бы у одного товара.
Каждый параметр будет сопровождаться списком своих уникальных значений.
У каждого параметра будет указано количество товаров, которым он принадлежит.
Обеспечьте возможность просмотра вложенных страниц с параметрами и изображениями для каждого товара.