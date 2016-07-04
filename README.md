# Akeneo Test Install

Every time:

```bash
docker-compose up -d
```

The first time:

```bash
docker exec -ti akeneo bash
php app/console pim:install
```

Akeneo should be running on port 90, you can login with "admin:admin".
