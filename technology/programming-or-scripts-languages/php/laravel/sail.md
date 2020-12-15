# Sail

## Recommended

* \*\*\*\*[**Documentation**](https://laravel.com/docs/8.x/sail)\*\*\*\*

## [Set an alias for sail](https://laravel.com/docs/8.x/sail#configuring-a-bash-alias)

* Open your `~/.profile` file
* Put these line below at the bottom of the file

```text
alias sail='bash vendor/bin/sail'
```

## [Executing Commands](https://laravel.com/docs/8.x/sail#executing-sail-commands)

```text
# Running Artisan commands locally...
php artisan queue:work

# Running Artisan commands within Laravel Sail...
sail artisan queue:work
```

