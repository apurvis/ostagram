# Ostagram

Данное web-приложение является web надстройкой над программой по обработке изображения нейронными сетями. Для создания картин используется сверточные
нейронные сети и алгоритм художественно стиля by Leon A. Gatys, Alexander S. Ecker, and Matthias Bethge. Более подробно с этим можно ознакомиться по ссылке на GitHub ниже.

This program presents web-service for algorithm combining the content of one image with the style of another image using convolutional neural networks.

## Requirements

Test with Rails 4.2

## Installation

Russian: Для работы web-приложения необходимо создать config.secret в папке config примерно со следующим содержанием:

English: You  must create a config.secret with approximately the following content:

```yaml
token:
  production: <Insert a secret key here; you can generate one with bundle exec rake secret>
workservers:
  server1:
    host: "deploy" - адрес удаленного сервера для обработки
    username: "deploy" - логин
    password: "пароль"
    remote_neural_path: "/home/deploy/neural-style" - путь где распологается сеть
    init_params: "-gpu -1 -image_size 100" - строка инициализации для сети
    iteration_count: 10 - количество итераций обработки
    admin_email: "почта_админа@gmail.com"
smtp_settings:
  address: 'smtp.gmail.com'
  port: 587
  domain: 'gmail.com'
  user_name: 'почта_отправки_результата@gmail.com'
  password: 'пароль'
  authentication: 'plain'
  enable_starttls_auto: true
```

You can start with an example file for both `config.secret` and `database.yml`:

```bash
$ cp config/config.secret.example config/config.secret
$ cp config/database.yml.secret database.yml
```

Create a postgresql user and grant privileges
```bash
$ createuser -d ostagram
```

## More Information

Для обработки используется данный алгоритм https://github.com/jcjohnson/neural-style