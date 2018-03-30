# Docker System Doc

Ce projet est constitué d'une base Docker pour application PHP.

## Requirements

* Serveur Apache 2.4
* PHP 7.1 avec extension opcache et APCu
* Mysql Ver 14.14 Distrib 5.6.37
* composer
* Docker (pour le développement)


## Configuration

### 1. Config de Docker (Uniquement pour l'environnement Dev)

```bash
cp docker-composer.override.dist.yml docker-composer.override.yml
```

- Config par défaut:

```yaml
apache:
  ports:
    - "80:80"

phpmyadmin:
  ports:
    - "8080:80"
```

- C'est mieux de changer les ports afin d'éviter des conflits avec d'autres projets, par exemple :

```yaml
apache:
  ports:
    - "8011:80"

phpmyadmin:
  ports:
    - "8012:80"
```
