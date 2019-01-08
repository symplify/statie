<p align="center">
    <img src="docs/logo.svg">
</p>

<h1 align="center">Statie - Modern and Simple Static Site Generator in PHP</h1>

[![Build Status](https://img.shields.io/travis/Symplify/Statie/master.svg?style=flat-square)](https://travis-ci.org/Symplify/Statie)
[![Downloads](https://img.shields.io/packagist/dt/symplify/statie.svg?style=flat-square)](https://packagist.org/packages/symplify/statie/stats)

Statie takes HTML, Markdown and Twig or Latte files and generates static HTML page.

## Install

```bash
composer require symplify/statie
```

## How to Generate and See the Website?

1. Prepare content for Statie

```bash
vendor/bin/statie init
```

Do you prefer [Latte](https://github.com/nette/latte)?

```bash
vendor/bin/statie init --templating latte
```

This will generate config, templates, layouts and gulp code, so you can enjoy live preview.

Last step is install node dependencies:

```
npm install
```

2. Generate static site from `/source` (argument) to `/output` (default value) in HTML:

```bash
vendor/bin/statie generate source
```

3. Run website locally

```bash
gulp
```

4. And see web in browser [localhost:8000](http://localhost:8000).

## Configuration

### `statie.yml` Config

This is basically Symfony Kernel `config.yml` that you know from Symfony application. You can:

- [add parameters](https://symfony.com/doc/current/service_container/parameters.html)
- [import configs](http://symfony.com/doc/current/service_container/import.html)
- [register services](https://symfony.com/doc/current/service_container.html)

```yaml
# statie.yml
imports:
    - { resource: 'data/favorite_links.yml' }

parameters:
    site_url: 'http://github.com'
    socials:
        facebook: 'http://facebook.com/github'

services:
    App\SomeService: ~
```

Parameters are available in every template:

```twig
{# source/_layouts/default.twig #}

<p>Welcome to: {{ site_url }}</p>

<p>Checkout my FB page: {{ socials.facebook }}</p>
```

### Do You Write Posts?

Create a new empty `.md` file with date, webalized title and ID:

```bash
vendor/bin/statie create-post "My new post"
```

Statie privides default template:

```twig
id: __ID__
title: "__TITLE__"
---

```

Do you want your own template? Configure path to it:

```yaml
# statie.yaml
parameters:
    post_template_path: 'templates/my_own_post.twig'
```

That's it!

## Documentation

Thanks to [@crazko](https://github.com/crazko) you can enjoy neat documentation and see projects that use Statie at [statie.org](https://www.statie.org).

- [How to Tweet your Posts with Travis](/docs/tweeting.md)
- [How to Thank your Contributors](/docs/gratitude.md)

## Contributing

Open an [issue](https://github.com/Symplify/Symplify/issues) or send a [pull-request](https://github.com/Symplify/Symplify/pulls) to main repository.
