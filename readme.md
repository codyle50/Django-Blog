Welcome to Django Blog
====================

## Features

Django Blog is a blog system with following features:

- Powered by django and bootstrap
- Deployed by docker
- Multiple deployment setting files
- Search engine optimized
- Blog features:
    - multi-user
    - multi-role
    - posts, pages, tags, and categories
    - markdown support
    - admin interface
    - RESTful API (under development)


## Preview Django Blog

- [Frontend Website](http://blog.igevin.info/)
- [Backend Admin Screenshot](preview.md)

## How to run it ?

### Run from source code

If you want to see more about the source code, checkout the [source code readme](blog)


### Run by docker(recommended)

Run Django Blog by docker is recommended, here are some instruction：

#### First Run

1\. Use Django Blog image

```bash
(sudo) docker pull gevin/Django Blog
```

Or you can build your own Django Blog image
```bash
(sudo) docker build -t Django Blog .

# Now you can take a cup of coffee and wait for a few minutes :)
```

2\. Run Django Blog

```bash
(sudo) docker-compose up -d
```

3\. Get into Django Blog container and migrate database

```bash
# Specify Django Blog container ID, eg:12345678
(sudo) docker ps

# Get into Django Blog container
(sudo) docker exec -it 12345678 bash

# Migrate datebase
python manage.py migrate
```

#### After first run

- Start Django Blog

```bash
(sudo) docker-compose start
```

- Stop Django Blog

```bash
(sudo) docker-compose stop
```


### Initialize Django Blog

When the blog is run, checkout `http://host:port/init` to initialize the system

It will create the superuser, user groups(administrator, editor, writer, contributor, and reader), and assign permissions for each group.

## License

Django Blog is under [GPL2](LICENSE)

