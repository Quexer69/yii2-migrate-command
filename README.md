Extended Migration Command
==========================

Console Migration Command with multiple paths/aliases support

This extension was created from this [Pull Request](https://github.com/yiisoft/yii2/pull/3273) on GitHub, which became unmergeable.
Until this feature will be reimplemented into the core, you can use this extension if you need to handle multiple migration paths.

> Note! If using `dmstr/yii2-migrate-command` in an existing project, you may have to remove your *migration* table, due to a schema change.

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

```
php composer.phar require dmstr/yii2-migrate-command "*"
```

Usage
-----

Configure the command in your `main` application configuration:

```php
'controllerMap'       => [
    'migrate' => [
        'class' => 'dmstr\console\controllers\MigrateController'
    ],
],
```

Add additional migration paths via application `params`:

```php
"yii.migrations"=> [
    "@dektrium/user/migrations",
],
```

You can also add migrations in your module bootstrap process:

```
public function bootstrap($app)
{
    $app->params['yii.migrations'][] = '@vendorname/packagename/migrations';
}
```    

Once the extension is installed and configured, simply use it on your command line

```
./yii migrate
```

If you want to specify an additional path directly with the command, use

```
./yii migrate --migrationLookup=@somewhere/migrations/data1,@somewhere/migrations/data2
```
