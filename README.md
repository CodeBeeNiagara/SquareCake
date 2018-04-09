# SquareCake
Integrate Square with Cakephp 2.x

## Step 1 Set Up As Vendor

Create a folder in app/Vendor called SquareConnect.php with the following:

```
<?php
 	
if (!defined('SQUARE_ROOT')) {
    define('SQUARE_ROOT', dirname(__FILE__) . '/');
    require(SQUARE_ROOT . 'SquareConnect/autoload.php');
}
```

Create a folder in app/Vendor called SquareConnect and upload the library https://github.com/square/connect-php-sdk



