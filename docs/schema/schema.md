# MMS Public API

## Group
Working with MMS Groups

### Attributes
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><strong>activeAgentCount</strong></td>
    <td><em>integer</em></td>
    <td>Number of monitoring agents sending regular pings to MMS.</td>
    <td><code>"1"</code></td>
  </tr>
  <tr>
    <td><strong>hostsCounts:arbiter</strong></td>
    <td><em>integer</em></td>
    <td>Number of arbiters in hostsCounts</td>
    <td><code>"1"</code></td>
  </tr>
  <tr>
    <td><strong>hostsCounts:config</strong></td>
    <td><em>integer</em></td>
    <td>Number of configs in hostsCounts</td>
    <td><code>"1"</code></td>
  </tr>
  <tr>
    <td><strong>hostsCounts:master</strong></td>
    <td><em>integer</em></td>
    <td>Number of masters in hostsCounts</td>
    <td><code>"1"</code></td>
  </tr>
  <tr>
    <td><strong>hostsCounts:mongos</strong></td>
    <td><em>integer</em></td>
    <td>Number of mongoss in hostsCounts</td>
    <td><code>"1"</code></td>
  </tr>
  <tr>
    <td><strong>hostsCounts:primary</strong></td>
    <td><em>integer</em></td>
    <td>Number of primaries in hostsCounts</td>
    <td><code>"1"</code></td>
  </tr>
  <tr>
    <td><strong>hostsCounts:secondary</strong></td>
    <td><em>integer</em></td>
    <td>Number of secondaries in hostsCounts</td>
    <td><code>"1"</code></td>
  </tr>
  <tr>
    <td><strong>hostsCounts:slave</strong></td>
    <td><em>integer</em></td>
    <td>Number of slaves in hostsCounts</td>
    <td><code>"1"</code></td>
  </tr>
  <tr>
    <td><strong>id</strong></td>
    <td><em>uuid</em></td>
    <td>Unique identifier</td>
    <td><code>"5196d3628d022db4cbc26d9e"</code></td>
  </tr>
  <tr>
    <td><strong>lastActiveAgent</strong></td>
    <td><em>date-time</em></td>
    <td>Date that a ping was last received from one of the group’s monitoring agents.</td>
    <td><code>"2012-01-01T12:00:00Z"</code></td>
  </tr>
  <tr>
    <td><strong>name</strong></td>
    <td><em>string</em></td>
    <td>Display name for the group</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>publicApiEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>Is the Public API enabled for this group? This is a read-only field that will always be true for groups created with the API. Note that for groups created in the MMS UI, the only way to set this flag to true is by enabling the Public API for the group in the Settings tab.</td>
    <td><code>"true"</code></td>
  </tr>
  <tr>
    <td><strong>replicaSetCount</strong></td>
    <td><em>integer</em></td>
    <td>Total number of replica sets for this group.</td>
    <td><code>"1"</code></td>
  </tr>
  <tr>
    <td><strong>shardCount</strong></td>
    <td><em>integer</em></td>
    <td>Total number of shards for this group.</td>
    <td><code>"1"</code></td>
  </tr>
</table>

### Group Create
Create a new group.

```
POST /groups
```


#### Curl Example
```term
$ curl -n -X POST https://mms.mongodb.com/api/public/v1.0/groups
```


#### Response Example
```
HTTP/1.1 201 Created
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "name": "API Example",
  "hostsCounts": {
    "arbiter": "1",
    "config": "1",
    "primary": "1",
    "secondary": "1",
    "mongos": "1",
    "master": "1",
    "slave": "1"
  },
  "lastActiveAgent": "2012-01-01T12:00:00Z",
  "activeAgentCount": "1",
  "replicaSetCount": "1",
  "shardCount": "1",
  "publicApiEnabled": "true"
}
```

### Group Delete
Delete an existing group.

```
DELETE /groups/{group_id}
```


#### Curl Example
```term
$ curl -n -X DELETE https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "name": "API Example",
  "hostsCounts": {
    "arbiter": "1",
    "config": "1",
    "primary": "1",
    "secondary": "1",
    "mongos": "1",
    "master": "1",
    "slave": "1"
  },
  "lastActiveAgent": "2012-01-01T12:00:00Z",
  "activeAgentCount": "1",
  "replicaSetCount": "1",
  "shardCount": "1",
  "publicApiEnabled": "true"
}
```

### Group Info
Info for existing groups.

```
GET /groups/{group_id}
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "name": "API Example",
  "hostsCounts": {
    "arbiter": "1",
    "config": "1",
    "primary": "1",
    "secondary": "1",
    "mongos": "1",
    "master": "1",
    "slave": "1"
  },
  "lastActiveAgent": "2012-01-01T12:00:00Z",
  "activeAgentCount": "1",
  "replicaSetCount": "1",
  "shardCount": "1",
  "publicApiEnabled": "true"
}
```

### Group List
List existing groups.

```
GET /groups
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
[
  {
    "id": "5196d3628d022db4cbc26d9e",
    "name": "API Example",
    "hostsCounts": {
      "arbiter": "1",
      "config": "1",
      "primary": "1",
      "secondary": "1",
      "mongos": "1",
      "master": "1",
      "slave": "1"
    },
    "lastActiveAgent": "2012-01-01T12:00:00Z",
    "activeAgentCount": "1",
    "replicaSetCount": "1",
    "shardCount": "1",
    "publicApiEnabled": "true"
  }
]
```



