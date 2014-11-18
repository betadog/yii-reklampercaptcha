yii-reklampercaptcha
====================

Try out [demonstration](http://reklamper.com/demo).

### How install captcha widget in your project ###
Extract files from archive to folder: `ext.reklamperCaptcha`


In model declare attribute and add validation rules:
```php
class Comments extends CActiveRecord
{
    public $reklamperCaptcha;
    
    public function rules()
    {
        return array_merge( parent::rules(), array(
            array('reklamperCaptcha','required',),
            array('reklamperCaptcha','ext.reklamperCaptcha.ReklamperCaptchaValidator',
                // custom error message:
                'message' => 'Validation code is incorrect',
            ),
        ));
    }
    
    // other functions
}
```

in view file show widget:
```php

<?php 
    // summon widget
    $this->widget(
        'ext.reklamperCaptcha.ReklamperCaptcha', 
        array( 
            'model' => $model, 
            'attribute' => 'reklamperCaptcha', // its attribute name
        )
    );
    
    //and error message
    echo CHtml::error($model,'parrotifyCaptcha');
?>

```

### Install via composer ###

Add package to `composer.json`:
```
"reklamper/yii-reklampercaptcha": "dev-master"
```

Add `vendor` alias into `/index.php`:
```php
...
$vendorPath = ABSOLUTE_PATH_TO_COMPOSER.'/vendor');
Yii::setPathOfAlias('vendor', $vendorPath);
...
```

In model declare attribute and add validation rules:
```php
array('reklamperCaptcha','vendor.reklamper.yii-reklampercaptcha.ReklamperCaptchaValidator',
    // custom error message:
    'message' => 'Validation code is incorrect',
),
```

in view file show widget:
```php
<?php 
    // summon widget
    $this->widget(
        'vendor.reklamper.yii-reklampercaptcha.ReklamperCaptcha', 
        array( 
            'model' => $model, 
            'attribute' => 'reklamperCaptcha', // its attribute name
        )
    );
    
    //and error message
    echo CHtml::error($model,'reklamperCaptcha');
?>
```
