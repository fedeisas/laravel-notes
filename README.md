Laravel 4 Artisan Notes Management
==================================

Inpired by Rails Rake notes, Laravel Notes helps you manage your notes when developing an application. It will search comment begin with TODO, FIXME, or OPTIMIZE.

## Installation

+ Update your composer.json to require `"rahmatawaludin/laravel-notes": "dev-master"`
```json
{
  "require": {
    "laravel/framework": "4.1.*",
    "rahmatawaludin/laravel-notes": "dev-master"
  },
  ...
}
```

+ Run `composer update` in the Terminal
+ Add the LaravelNotesServiceProvider `'Rahmatawaludin\LaravelNotes\LaravelNotesServiceProvider'` to the laravel providers array in the file `app/config/app.php`

```
'providers' => array(
    ...
    'Rahmatawaludin\LaravelNotes\LaravelNotesServiceProvider'
  )
```

## Usage

Add your comment to file within `app` directory begin with @TODO, @FIXME, or @OPTIMIZE.
example:

app/controllers/HomeController.php:
```
...
// @TODO create different layout
...
```

app/routes.php
```
// @FIXME missing controller for router
```

app/models/User.php
```
/**
 * This is really important
 * @OPTIMIZE better looping for this model
 * @var string
 */
```

Then use `notes` in terminal to view all notes:
```
$ php artisan notes
```

## Options

+ To filter only one type
```bash
$ php artisan notes todo
```

+ To add custom types to the default ones
```bash
$ php artisan notes --extra-filters=foo,bar
```

+ To search only within a directory *(defaults: app)*
```bash
$ php artisan notes --include-path=app/views
```

+ To exclude a directory *(defaults: storage)*
```bash
$ php artisan notes --exclude-path=app/views
```

## Under the hood
Laravel Notes will check your plataform and run `grep` of you are on a UNIX system. For Windows users it will use PHP to read and parse files. Non-formal tests have found that grep is 2x faster.

## Screenshot

![alt text](https://raw.github.com/rahmatawaludin/laravel-notes/master/screenshot.png "Notes Screenshot")

## Roadmap
Version | Feature
--- | ---
~~1.0~ | ~~Basic viewing notes~~
1.1 | Filter notes by type
1.2 | Filter notes by custom type
2.0 | Use git to speedup notes lookup
2.1 | View notes on specific directory
2.2 | Any idea?

## Contribute
1. Fork
2. Work on dev branch
3. Pull
4. Repeat.. :)
