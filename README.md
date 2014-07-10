# MMS API Schema

[Documentation](/docs/schema/schema.md)

To Generate:

`gem install prmd`

`cd docs/schema`
`prmd combine --meta meta.json schemata/ > schema.json`
`prmd verify schema.json`
`prmd doc schema.json --prepend overview.md > schema.md`
