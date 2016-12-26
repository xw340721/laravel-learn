##ServierProvider 写法


```php

<?php



class YourProvider extends ServiceProvider{

	public function boot()
    {
       //该方法在所有服务提供者被注册以后才会被调用，这就是说我们可以在其中访问框架已注册的所有其它服务
       //也就是注册之后调用的一些方法
    }


	public function register()
    {
        //唯一要做的事情就是绑事物到服务容器，不要尝试在其中注册事件监听器，路由或者任何其它功能。
        //也就是进行注册组件


        /**
		 *  常用方法为
		 *  $this->app->singleton('name',callback) 创建单例
		 *
		 *  $this->app->bind(
		 *		YourInterface::class,
		 *		YourImplement::class
		 *	);
		 *  这样 你可以在你的控制器种写入 function YourAction( YourInterface $youmodle) 
		 *  这样会注入一个YourImplement的方法进去
		 *  
		 *	$this->app->boot(callback) 处理一些注册的事物
		 *
		 *
		 */

    }
}


