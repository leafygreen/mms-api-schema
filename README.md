# MMS API Schema

This repository contains a JSON Schema / Hyper-Schema representation of the [MongoDB Management Service Public API](http://mms.mongodb.com/help/core/api/).

This project is inspired by the work Heroku is doing their public API.
* https://blog.heroku.com/archives/2014/1/8/json_schema_for_heroku_platform_api


## Documentation

[Auto-Generated Documentation](/docs/schema/schema.md)


## Consumers

* [node-mms-client](https://github.com/leafygreen/node-mms-client)


## Generating Schema and Documentation

Schema files are generated using the [prmd](https://github.com/interagent/prmd) tool.

`gem install prmd`

```
cd docs/schema
prmd combine --meta meta.json schemata/ > schema.json
prmd verify schema.json
prmd doc schema.json --prepend overview.md > schema.md
```


## License
Licensed under the [MIT license](LICENSE-MIT "MIT License").


## Shout Outs

mms-api-schema is a [MongoDB](http://www.mongodb.com) Skunkworks Project
![Friendly Skunk](http://s12.postimg.org/fxmtcosx9/skunkworks2.jpg)

