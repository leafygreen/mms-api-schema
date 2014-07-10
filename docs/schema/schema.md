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


## User
Working with MMS Users

### Attributes
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><strong>emailAddress</strong></td>
    <td><em>string</em></td>
    <td>Email address</td>
    <td><code>"jane.doe@gmail.com"</code></td>
  </tr>
  <tr>
    <td><strong>firstName</strong></td>
    <td><em>string</em></td>
    <td>First name</td>
    <td><code>"Jane"</code></td>
  </tr>
  <tr>
    <td><strong>id</strong></td>
    <td><em>uuid</em></td>
    <td>Unique identifier</td>
    <td><code>"5196d3628d022db4cbc26d9e"</code></td>
  </tr>
  <tr>
    <td><strong>lastName</strong></td>
    <td><em>string</em></td>
    <td>Last name</td>
    <td><code>"Doe"</code></td>
  </tr>
  <tr>
    <td><strong>mobileNumber</strong></td>
    <td><em>string</em></td>
    <td>Mobile number. This field can only be set or edited using the MMS UI because it is tied to two factor authentication</td>
    <td><code>"555-555-5555"</code></td>
  </tr>
  <tr>
    <td><strong>password</strong></td>
    <td><em>string</em></td>
    <td>Password. This field is NOT included in the entity returned from the server. It can only be sent in the entity body when creating a new user.</td>
    <td></td>
  </tr>
  <tr>
    <td><strong>roles:groupId</strong></td>
    <td><em>string</em></td>
    <td>The groupId in which the user has the specified role. Note that for the “global” roles (those whose name starts with GLOBAL_) there is no groupId since these roles are not tied to a group.</td>
    <td><code>"533daa30879bb2da07807696"</code></td>
  </tr>
  <tr>
    <td><strong>roles:roleName</strong></td>
    <td><em>string</em></td>
    <td>The name of the role. Possible values are: GLOBAL_AUTOMATION_ADMIN GLOBAL_BACKUP_ADMIN GLOBAL_MONITORING_ADMIN GLOBAL_OWNER GLOBAL_READ_ONLY GLOBAL_USER_ADMIN GROUP_AUTOMATION_ADMIN GROUP_BACKUP_ADMIN GROUP_MONITORING_ADMIN GROUP_OWNER GROUP_READ_ONLY GROUP_USER_ADMIN</td>
    <td><code>"GROUP_USER_ADMIN"</code></td>
  </tr>
  <tr>
    <td><strong>username</strong></td>
    <td><em>string</em></td>
    <td>MMS username</td>
    <td><code>"jane.doe@mongodb.com"</code></td>
  </tr>
</table>

### User Create
Create a new user.

```
POST /users
```


#### Curl Example
```term
$ curl -n -X POST https://mms.mongodb.com/api/public/v1.0/users
```


#### Response Example
```
HTTP/1.1 201 Created
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "username": "jane.doe@mongodb.com",
  "password": null,
  "emailAddress": "jane.doe@gmail.com",
  "mobileNumber": "555-555-5555",
  "firstName": "Jane",
  "lastName": "Doe",
  "roles": {
    "groupId": "533daa30879bb2da07807696",
    "roleName": "GROUP_USER_ADMIN"
  }
}
```

### User Add
Add a user to an existing group.

```
POST /groups/{group_id}/users
```


#### Curl Example
```term
$ curl -n -X POST https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/users
```


#### Response Example
```
HTTP/1.1 201 Created
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "username": "jane.doe@mongodb.com",
  "password": null,
  "emailAddress": "jane.doe@gmail.com",
  "mobileNumber": "555-555-5555",
  "firstName": "Jane",
  "lastName": "Doe",
  "roles": {
    "groupId": "533daa30879bb2da07807696",
    "roleName": "GROUP_USER_ADMIN"
  }
}
```

### User Info
Info for existing user.

```
GET /users/{user_id}
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/users/$USER_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "username": "jane.doe@mongodb.com",
  "password": null,
  "emailAddress": "jane.doe@gmail.com",
  "mobileNumber": "555-555-5555",
  "firstName": "Jane",
  "lastName": "Doe",
  "roles": {
    "groupId": "533daa30879bb2da07807696",
    "roleName": "GROUP_USER_ADMIN"
  }
}
```

### User List
List existing users.

```
GET /groups/{group_id}/users
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/users
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
[
  {
    "id": "5196d3628d022db4cbc26d9e",
    "username": "jane.doe@mongodb.com",
    "password": null,
    "emailAddress": "jane.doe@gmail.com",
    "mobileNumber": "555-555-5555",
    "firstName": "Jane",
    "lastName": "Doe",
    "roles": {
      "groupId": "533daa30879bb2da07807696",
      "roleName": "GROUP_USER_ADMIN"
    }
  }
]
```

### User Delete
Delete an existing user.

```
DELETE /groups/{group_id}/users/{user_id}
```


#### Curl Example
```term
$ curl -n -X DELETE https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/users/$USER_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
[
  {
    "id": "5196d3628d022db4cbc26d9e",
    "username": "jane.doe@mongodb.com",
    "password": null,
    "emailAddress": "jane.doe@gmail.com",
    "mobileNumber": "555-555-5555",
    "firstName": "Jane",
    "lastName": "Doe",
    "roles": {
      "groupId": "533daa30879bb2da07807696",
      "roleName": "GROUP_USER_ADMIN"
    }
  }
]
```

### User Update
Update an existing user.

```
PATCH /users/{user_id}
```


#### Curl Example
```term
$ curl -n -X PATCH https://mms.mongodb.com/api/public/v1.0/users/$USER_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "username": "jane.doe@mongodb.com",
  "password": null,
  "emailAddress": "jane.doe@gmail.com",
  "mobileNumber": "555-555-5555",
  "firstName": "Jane",
  "lastName": "Doe",
  "roles": {
    "groupId": "533daa30879bb2da07807696",
    "roleName": "GROUP_USER_ADMIN"
  }
}
```



