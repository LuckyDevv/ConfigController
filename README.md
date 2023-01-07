<h1 align='center'>ConfigController</h1>

<h2 align='center'>This script is designed to create, edit and save configuration files. This can serve as a replacement for databases. Currently, only 4 types of configurations are supported: YAML, JSON, SERIALIZE, ENUM.</h2>
<h1 align='center'>Content</h1>

- <h3><a href='#file-extensions'>File Extensions</a></h3>
- <h3><a href='#the-following-options-are-used-to-save-in-json'>The following options are used to save in JSON</a></h3>
- <h3><a href='#functions'>Functions</a></h3>
- <h3><a href='#constants'>Constants</a></h3>
- <h3><a href='#code-examples'>Code Examples</a></h3>
- <h3><a href='#feedback'>Feedback</a></h3>

<h1 align='center'>File Extensions:</h1>

### If you use YAML: `*.yml, *.yaml`
### If you use JSON: `*.js, *.json`
### If you use SERIALIZE: `*.sl, *.serialize`
### If you use ENUM: `Any extension`

<h1>The following options are used to save in JSON:</h3>

> JSON_PRETTY_PRINT<br>
JSON_BIGINT_AS_STRING<br>
JSON_UNESCAPED_UNICODE
### These options can be changed via the script code. A constant with these options is called «JSON_OPS»

<h1 align='center'>Functions</h1>

### Class construction: `$filename, $type, $default`

> $filename - this is the path to the file that will become the configuration. By default = 'default.txt'<br>
$type - this is the configuration type: YAML, JSON, SERIALIZE, ENUM. By default = ConfigController::DETECT<br>
$default - this is the value that will be set in the config if its file does not exist. By default = []<br>
>> If the specified file does not exist, it will be automatically created


`set($key, $value = true): void` - Creates an entry in the config whose name is __$key__, and its value is __$value__. If __$value__ is not passed, then __true__ is set

`setAll($value): void` - Erases all records and sets _$value_ instead

`get($key, bool $default = false): mixed` - Returns the required record with the name __$key__. If the record does not exist, it returns __$default___

`getAll(): array` - Returns __all entries__ from the configuration in the array

`remove($key): void` - Deletes an existing record named __$key__

`exists($key): bool` - If a record with the name $key exists, then __true__ will be returned. Otherwise, __false__ will be returned

`getFileName(): string` - Returns the path to the file

<h1 align='center'>Constants</h1>

`ConfigController::DETECT = 0` - Automatically detects the configuration type by file extension

`ConfigController::YAML = 1` - YAML configuration type

`ConfigController::JSON = 2` - JSON configuration type

`ConfigController::SERIALIZE = 3` - SERIALIZE configuration type

`ConfigController::ENUM = 4` - ENUM configuration type

<h1 align='center'>Code Examples</h1>

```php
<?php
require_once 'ConfigController.php'; // Initialize the script
$jsonConfig = new ConfigController('example.json', ConfigController::JSON); // Creating a configuration file with the JSON type
$jsonConfig->set('LuckyDev', 'Hi, I`m LuckyDev, an IT developer from Russia'); // We write down the value we need
$jsonConfig->save(); // Save it. This is very important!
if($jsonConfig->exists('LuckyDev')){ // Checking if the record exists
    echo $jsonConfig->get('LuckyDev'); // Output the value of the desired record
    $jsonConfig->remove('LuckyDev'); // Deleting an entry
    $jsonConfig->save(); // Save it. This is very important!!!
}else{
    echo "Oops, something went wrong"; // We output an error message if the record is not found
}
?>
```
### The JSON type configuration looks like this:
![image](https://user-images.githubusercontent.com/92075158/211166569-2e30f7c7-9865-4c40-8c33-55ed783856d3.png)

<h1 align='center'>Feedback</h1>

### If you have any ideas how I can improve this script or you want to notice my mistakes, then write to me on social networks: <a href='https://vk.com/luckydevv'>VK</a>, <a href='https://t.me/luckydevv'>Telegram</a>
