<h1 align="center">
    <a href="http://demos.krajee.com" title="Krajee Demos" target="_blank">
        <img src="http://kartik-v.github.io/bootstrap-fileinput-samples/samples/krajee-logo-b.png" alt="Krajee Logo"/>
    </a>
    <br>
    yii2-mpdf
    <hr>
    <a href="https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=DTP3NZQ6G2AYU"
       title="Donate via Paypal" target="_blank">
        <img src="http://kartik-v.github.io/bootstrap-fileinput-samples/samples/donate.png" alt="Donate"/>
    </a>
</h1>

[![Stable Version](https://poser.pugx.org/kartik-v/yii2-mpdf/v/stable)](https://packagist.org/packages/kartik-v/yii2-mpdf)
[![Unstable Version](https://poser.pugx.org/kartik-v/yii2-mpdf/v/unstable)](https://packagist.org/packages/kartik-v/yii2-mpdf)
[![License](https://poser.pugx.org/kartik-v/yii2-mpdf/license)](https://packagist.org/packages/kartik-v/yii2-mpdf)
[![Total Downloads](https://poser.pugx.org/kartik-v/yii2-mpdf/downloads)](https://packagist.org/packages/kartik-v/yii2-mpdf)
[![Monthly Downloads](https://poser.pugx.org/kartik-v/yii2-mpdf/d/monthly)](https://packagist.org/packages/kartik-v/yii2-mpdf)
[![Daily Downloads](https://poser.pugx.org/kartik-v/yii2-mpdf/d/daily)](https://packagist.org/packages/kartik-v/yii2-mpdf)

The **yii2-mpdf** extension is a Yii2 wrapper component for the [mPDF library](http://www.mpdf1.com/) with enhancements. The mPDF library offers ability to generate PDF files from UTF-8 encoded HTML. This library is based on [FPDF](http://www.fpdf.org/) and [HTML2FPDF](http://html2fpdf.sourceforge.net/), with a number of enhancements. The key features in the library are to be able to generate PDF files 'on-the-fly' from HTML content, handling different languages. Refer the [documentation manual](https://mpdf.github.io) or the [upstream mpdf site](http://mpdf1.com) for further details and understanding of the library. The yii2-mpdf extension offers an easy way to integrate and use the mPDF library within your Yii application with subtle enhancements. The key features offerred with this release are:

- Setup `pdf` component globally in your yii application configuration.
- Setup mPDF properties or call mPDF methods easily using simple array configuration.
- Enhances extension to setup your own custom CSS file for rendering the formatted HTML content.
- Extension has a built-in version of bootstrap.css (v3.3.0 modified for mPDF) to be applied by default. This will allow you to generate PDF content from bootstrap markup HTML easily.
- Offers easy way to prepend inline CSS in addition to your own CSS file.
- Offers easy to use object oriented methods to render complex PDF.
- Easy use of the extension like any Yii widget by using the render method with minimal configuration.
- The extension uses the latest development version (v6.0beta) of the mPDF library. It uses the composer repository `kartik-v/mpdf` on packagist as a source for this latest version. mPDF 6.0 can utilise OpenType layout tables to display complex scripts. This release (v6.0) contains fonts (open source) to cover almost every imaginable script / language. Includes support for Arabic or Indic scripts (as well as Khmer, Lao, Myanmar etc.). It also is expected to improve the display of Thai, Vietnamese and Hebrew. It also includes additional fonts for Chinese, Japanese, and Korean.
- Inbuilt integration with [yii2-grid](http://demos.krajee.com/grid) extension that allows you to export grid as PDF and even generate advanced PDF reports.

### Demo
Read the detailed [documentation and usage](http://demos.krajee.com/mpdf) of the extension.

## Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

> Note: Check the [composer.json](https://github.com/kartik-v/yii2-mpdf/blob/master/composer.json) for this extension's requirements and dependencies. 
Read this [web tip /wiki](http://webtips.krajee.com/setting-composer-minimum-stability-application/) on setting the `minimum-stability` settings for your application's composer.json.

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

### Widget Like Usage
The component can be used straightforward in a manner similar to any widget to render your HTML content as PDF. For example, you 
can call the component simply like below in your controller action:

```php
use kartik\mpdf\Pdf;

public function actionReport() {
    // get your HTML raw content without any layouts or scripts
    $content = $this->renderPartial('_reportView');
    
    // setup kartik\mpdf\Pdf component
    $pdf = new Pdf([
        // set to use core fonts only
        'mode' => Pdf::MODE_CORE, 
        // A4 paper format
        'format' => Pdf::FORMAT_A4, 
        // portrait orientation
        'orientation' => Pdf::ORIENT_PORTRAIT, 
        // stream to browser inline
        'destination' => Pdf::DEST_BROWSER, 
        // your html content input
        'content' => $content,  
        // format content from your own css file if needed or use the
        // enhanced bootstrap css built by Krajee for mPDF formatting 
        'cssFile' => '@vendor/kartik-v/yii2-mpdf/src/assets/kv-mpdf-bootstrap.min.css',
        // any css to be embedded if required
        'cssInline' => '.kv-heading-1{font-size:18px}', 
         // set mPDF properties on the fly
        'options' => ['title' => 'Krajee Report Title'],
         // call mPDF methods on the fly
        'methods' => [ 
            'SetHeader'=>['Krajee Report Header'], 
            'SetFooter'=>['{PAGENO}'],
        ]
    ]);
    
    // return the pdf output as per the destination setting
    return $pdf->render(); 
}
```

### Global Component

You can also setup the widget as a global component for use across your application with defaults preset. For example, setup the following in 
the components section of your Yii application configuration file:

```php
use kartik\mpdf\Pdf;
// ...
'components' => [
    // setup Krajee Pdf component
    'pdf' => [
        'class' => Pdf::classname(),
        'format' => Pdf::FORMAT_A4,
        'orientation' => Pdf::ORIENT_PORTRAIT,
        'destination' => Pdf::DEST_BROWSER,
        // refer settings section for all configuration options
    ]
]
```

Once you have setup the component, you can refer it across your application easily:

```php
$pdf = Yii::$app->pdf;
$pdf->content = $htmlContent;
return $pdf->render();
```

For other usage and details, read the detailed [documentation](http://demos.krajee.com/mpdf).

## Contributors

### Code Contributors

This project exists thanks to all the people who contribute. [[Contribute](CONTRIBUTING.md)].
<a href="https://github.com/kartik-v/yii2-mpdf/graphs/contributors"><img src="https://opencollective.com/yii2-mpdf/contributors.svg?width=890&button=false" /></a>

### Financial Contributors

Become a financial contributor and help us sustain our community. [[Contribute](https://opencollective.com/yii2-mpdf/contribute)]

#### Individuals

<a href="https://opencollective.com/yii2-mpdf"><img src="https://opencollective.com/yii2-mpdf/individuals.svg?width=890"></a>

#### Organizations

Support this project with your organization. Your logo will show up here with a link to your website. [[Contribute](https://opencollective.com/yii2-mpdf/contribute)]

<a href="https://opencollective.com/yii2-mpdf/organization/0/website"><img src="https://opencollective.com/yii2-mpdf/organization/0/avatar.svg"></a>
<a href="https://opencollective.com/yii2-mpdf/organization/1/website"><img src="https://opencollective.com/yii2-mpdf/organization/1/avatar.svg"></a>
<a href="https://opencollective.com/yii2-mpdf/organization/2/website"><img src="https://opencollective.com/yii2-mpdf/organization/2/avatar.svg"></a>
<a href="https://opencollective.com/yii2-mpdf/organization/3/website"><img src="https://opencollective.com/yii2-mpdf/organization/3/avatar.svg"></a>
<a href="https://opencollective.com/yii2-mpdf/organization/4/website"><img src="https://opencollective.com/yii2-mpdf/organization/4/avatar.svg"></a>
<a href="https://opencollective.com/yii2-mpdf/organization/5/website"><img src="https://opencollective.com/yii2-mpdf/organization/5/avatar.svg"></a>
<a href="https://opencollective.com/yii2-mpdf/organization/6/website"><img src="https://opencollective.com/yii2-mpdf/organization/6/avatar.svg"></a>
<a href="https://opencollective.com/yii2-mpdf/organization/7/website"><img src="https://opencollective.com/yii2-mpdf/organization/7/avatar.svg"></a>
<a href="https://opencollective.com/yii2-mpdf/organization/8/website"><img src="https://opencollective.com/yii2-mpdf/organization/8/avatar.svg"></a>
<a href="https://opencollective.com/yii2-mpdf/organization/9/website"><img src="https://opencollective.com/yii2-mpdf/organization/9/avatar.svg"></a>

## License

**yii2-mpdf** is released under the BSD-3-Clause License. See the bundled `LICENSE.md` for details.
