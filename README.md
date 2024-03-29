# freelansim.ru.269761
https://freelansim.ru/tasks/269761


Пример конфигурации
```php
'components' => [
    'telegram' => [
        'class' => 'aki\telegram\TelegramBot',
        'botToken' => 'ТОКЕН_БОТА',
        'output' => [
            //Есть возможность расширить вывод ошибок допустим в базу или на почту
            'class' => 'aki\telegram\FileOutput',
             //Ошибки логируются в файл
            'fileName' => __DIR__ . '/../telegram.log',
        ],
    ],
]
```


Получение информации о боте
```php
Yii::$app->telegram->getMe();
```

Отравка сообщения
```php
Yii::$app->telegram->sendMessage([
	'chat_id' => 123456789,
	'text' => 'Тестовое сообщение',
]);
```

Пример загрузки нового файла. Проверяется по file_exists
```php
Yii::$app->telegram->sendAudio([
	'chat_id' => 123456789,
	'audio' => '/home/coin/Downloads/test.mp3', //путь к файлу
	'caption' => 'Создание Файла',
	'duration' => 0,
]);
```

Пример загрузки существующего файла. Проверяется по file_exists
```php
Yii::$app->telegram->sendAudio([
	'chat_id' => 123456789,
	'audio' => 'CQADAgADxgQAAluH0Ui880sYZ9eVgBYE', //file_id
	'caption' => 'Создание Файла',
	'duration' => 0,
]);
```

Пример загрузки медиа группы

```php
Yii::$app->telegram->sendMediaGroup([
    'chat_id' => 123456789,
    'media' => [
        [
            'type' => 'photo',
            'media' =>'/home/coin/Downloads/test.png',
        ],
        [
            'type' => 'photo',
            'media' => 'AgADAgADfqwxG1uH0UiUZPD1RWskV7cDuA8ABAEAAwIAA3gAA2C6BAABFgQ',
        ],
        [
            'type' => 'video',
            'media' => '/home/coin/Downloads/test.mp4', 
        ],
    ],
]);
```

Настройка **composer.json** для установки в обход packagist.org
```php
  "require": {
	"co-in/freelansim.ru.269761": "dev-master"
  },
  "repositories": [
	{
	  "type": "github",
	  "url": "https://github.com/co-in/freelansim.ru.269761"
	}
  ]
```
