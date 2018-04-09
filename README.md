# SquareCake
Integrate Square Connect API with Cakephp 2.x and accept credit card payments online

## Step 1 Set Up As Vendor

Create a folder in app/Vendor called SquareConnect.php with the following:

```
<?php
 	
if (!defined('SQUARE_ROOT')) {
    define('SQUARE_ROOT', dirname(__FILE__) . '/');
    require(SQUARE_ROOT . 'SquareConnect/autoload.php');
}
```

Create a folder in app/Vendor called SquareConnect and upload the library (lib folder only)  https://github.com/square/connect-php-sdk
Open autoloader.php and edit this line:

```
$base_dir = __DIR__ . '/lib/';
```

to read:

```
$base_dir = __DIR__;
```

## Step 2 Controller

In the controller you want to use Square put these lines above the class declaration:

```
App::import('Vendor', 'SquareConnect', array('file' => 'SquareConnect.php'));

 
spl_autoload_register(function ($class) {
	  foreach (App::path('Vendor') as $base) {
		    $path = $base . str_replace('\\', DS, $class) . '.php';
		        if (file_exists($path)) {
			        include $path;
			        return;
		    }
	   }
});
```
In your controller create a function called squareConnect

```
public function squareConnect() {
///put the contents of your connection file (see https://github.com/square/connect-api-examples) here
// remove line require 'vendor/autoload.php';
//fill in your access token
$access_token = 'sandbox-1234567qwert';
....
}
 
## Step 2 Controller
In your form use action="controller/squareConnect"
