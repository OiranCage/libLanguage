# libLanguage
Simple and easy language library to support plugin-side i18n.

## API example
```php
use oirancage\liblanguage\libLanguage;

class Main extends PluginBase{
    private libLanguage $libLang;

    public function onEnable(){
        $path = "path/to/lang";
        $this->libLang = libLanguage::load($this, $path, "en_US");
    }
}
```

The `\oirancage\liblanguage\libLanguage::load()` method accepts 2 parameter.
- (required) `PluginBase $plugin`: your plugin.
- (required) `string $path`: path to languages used in plugin.
- (optional) `string $serverLocate`: locale used in server side.

## language format
The language format must be based on Minecraft Bedrock style.
See [Minecraft Bedrock Vanilla Resource Pack/texts](https://github.com/ZtechNetwork/MCBVanillaResourcePack/tree/master/texts)

### .lang file
```ini
## See document and example
## - https://github.com/ZtechNetwork/MCBVanillaResourcePack/blob/master/texts/en_US.lang
## - https://wiki.bedrock.dev/concepts/text-and-translations.html
player.join.message=welcome %1!
player.join.broadcast=%1 joined the game!
```


### Manifest.json
```json
{
    "format_version": 2,
    "header": {
        "description": "libLanguage Pack",
        "name": "libLanguage",
        "uuid": "uuid-generated",
        "version": [0, 0, 1],
        "min_engine_version": [ 1, 18, 0 ]
    },
    "modules": [
        {
            "description": "libLanguage resource pack",
            "type": "resources",
            "uuid": "uuid-generated",
            "version": [0, 0, 1]
        }
    ]
}
```

## Language directory
All lang files should be in the same directory and end with `.lang`.
```
lang
├ manifest.json
├ en_US.lang
└ ja_JP.lang
```

If you want to use `plugin_data/YourPlugin/lang` as root directory of language.
