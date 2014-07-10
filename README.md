# MMS API Schema

[Documentation](/docs/schema/schema.md)

Inspired by
* https://blog.heroku.com/archives/2014/1/8/json_schema_for_heroku_platform_api
* http://json-schema.org/
* https://github.com/interagent/prmd

To Generate:

`gem install prmd`

```
cd docs/schema
prmd combine --meta meta.json schemata/ > schema.json
prmd verify schema.json
prmd doc schema.json --prepend overview.md > schema.md
```
