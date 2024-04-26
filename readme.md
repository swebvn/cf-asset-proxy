# The proxy for loading assets for Lunar merch

This worker will dynamically load assets from each Lunar merch store and serve them to the client. So we could use the cache of Cloudflare to store the assets and serve them to the client faster.

## Usage
https://lunar-assets.customedge.co/{domain}/{path}

## For laravel
Setup the asset url on production to the proxy url

File `config/app.php`

```php

//...
'asset_url' => env('ASSET_URL')
        ? env('ASSET_URL')
        : (env('APP_ENV') === 'production'
            ? 'https://lunar-assets.customedge.co/' . parse_url(env('APP_URL'), PHP_URL_HOST)
            : null),
//
