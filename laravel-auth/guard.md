## 自己gurad配置


###guard 门卫

在config的gurads中添加

```php
<?php
return [
	...
	'guards' => [
		...
		'your-guard'=>[
			'driver'=>'' 	//门卫的保存驱动
			'provider'=>'' 	//启动的提供者	下面的provider	
		]
	]
]
?>
```

* driver中可以是session 或者自己提供的driver 

> 在provider的boot中自定义guard

```php
	...
	 Auth::extend('jwt', function($app, $name, array $config) {
            // Return an instance of Illuminate\Contracts\Auth\Guard...
            return new JwtGuard(Auth::createUserProvider($config['provider']));
        }); 
 ```

* provider则是下面自提供的provider

###provider 提供

```php
<?php
return [
	...
	'providers' => [
		...
		'your-provider'=>[
			'driver'=>'' 	//提供者的驱动
			'model'=>'' 	//提供者的model方法	
		]
	]
]
?>
```

* dirver 也是提供者提供的驱动 可以是 eloquent 也可以是自己的构建的provider的dirver

```php
	Auth::provider('riak', function($app, array $config) {
	            // Return an instance of Illuminate\Contracts\Auth\UserProvider...
	            return new RiakUserProvider($app->make('riak.connection'));
	        });
```

* model 是为提供的方法 注意 方法要继承 AuthenticatableContract 

