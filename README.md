yii2-image
==========

Imple to use Yii2 Framework extension for image manipulating using powerful Kohana Image Library.  Inspired by old yii extension 
http://www.yiiframework.com/extension/image/ and Kohana Image Library https://github.com/kohana/image

Installation
------------
```code
"repositories": [
		{
		    "type": "vcs",
		    "url": "http://github.com/yurkinx/yii2-image"
		}
	 ],
	 
"require": {
		"yurkinx/yii2-image": "master"
	 }
```

Configuration
-------------
In config file
```code
/config/web.php
```
Add image component
```code
'components' => array(
        ...
        'image' => array(
        	 		'class' => 'yii\image\ImageDriver',
        			 'driver' => 'GD',  //GD or Imagick
        		    ),
		    )
```

Usage
-----
```php
    $file=Yii::getAlias('@app/pass/to/file'); 
		$image=Yii::$app->image->load($file);
		header("Content-Type: image/png");
		echo 	$image->resize($width,$height)->rotate(30)->render();
```

Supported methods out of the box of Kohana Image Library:
```php
$image->resize($width = NULL, $height = NULL, $master = NULL);
$image->crop($width, $height, $offset_x = NULL, $offset_y = NULL);
$image->sharpen($amount);
$image->rotate($degrees);
$image->save($file = NULL, $quality = 100);
$image->render($type = NULL, $quality = 100);
$image->reflection($height = NULL, $opacity = 100, $fade_in = FALSE);
$image->flip($direction);
$image->background($color, $opacity = 100);
$image->watermark(Image $watermark, $offset_x = NULL, $offset_y = NULL, $opacity = 100);

 // Resizing constraints ($master)
    const NONE    = 0x01;
    const WIDTH   = 0x02;
    const HEIGHT  = 0x03;
    const AUTO    = 0x04;
    const INVERSE = 0x05;
    const PRECISE = 0x06;

  // Flipping directions ($direction)
     const HORIZONTAL = 0x11;
     const VERTICAL   = 0x12;
```

