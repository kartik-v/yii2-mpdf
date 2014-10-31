yii2-mpdf
=============

The **yii2-mpdf**  is a Yii2 wrapper component for the mPDF library which generates PDF files from UTF-8 encoded HTML.

### _ Extension is under development _

### Demo
You can see detailed [documentation](http://demos.krajee.com/mpdf) or view a [complete demo](http://demos.krajee.com/mpdf-demo) on usage of the extension.

## Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

> Note: You must set the `minimum-stability` to `dev` in the **composer.json** file in your application root folder before installation of this extension.

Either run

```
$ php composer.phar require kartik-v/yii2-mpdf "dev-master"
```

or add

```
"kartik-v/yii2-mpdf": "dev-master"
```

to the ```require``` section of your `composer.json` file.

## Usage


Setup the component in your Yii configuration file with a name `mpdf` as shown below. In addition, you must also register 
the `mpdf` component as described in the [yii2-grid documentation](http://demos.krajee.com/mpdf).

```php
'components'=>[
   'mpdf'=>[
        'class'=>'\kartik\mpdf\mpdf',
        // other settings (refer documentation)
    ],
],
```

## License

**yii2-mpdf** is released under the BSD 3-Clause License. See the bundled `LICENSE.md` for details.
