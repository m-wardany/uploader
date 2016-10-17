uploader behavior
=================
uploader behavior based on mohorev/yii2-upload-behavior

Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
php composer.phar require --prefer-dist wardany/uploader "*"
```

or add

```
"wardany/uploader": "*"
```

to the require section of your `composer.json` file.


Usage
-----

Once the extension is installed, simply use it in your code by  :

```php
function behaviors()
    {
        $baseurl = isset(Yii::$app->components['frontend']) ? Yii::$app->urlManagerFrontEnd->baseUrl : Yii::$app->urlManager->baseUrl ;
        return [
            [
                'class' => UploadImageBehavior::className(),
                'attribute' => 'image',
                'scenarios' => ['insert', 'update'],
                'path' => '@frontend/web/media/images/{id}',
                'url' => "$baseurl/media/images/{id}",                
                'unlinkOnDelete'=>true,
                'thumbPath' => '@frontend/web/media/images/{id}/thumbnail',
                'thumbUrl' => "$baseurl/media/images/{id}/thumbnail",
                'thumbs' => [
                    'header' => ['width' => 1536, 'height' => 600, 'mode'=>ImageInterface::THUMBNAIL_OUTBOUND],
                    'thumb' => ['width' => 300, 'height' => 300, 'mode'=>ImageInterface::THUMBNAIL_OUTBOUND],
                    'preview' => ['width' => 100, 'height' => 100, 'mode'=>ImageInterface::THUMBNAIL_OUTBOUND],
               ],
            ],
        ];
    }```