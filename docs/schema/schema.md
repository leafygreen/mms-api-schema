# MMS Public API

## Alert
Working with MMS Alerts

### Attributes
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><strong>acknowledgedUntil</strong></td>
    <td><em>date-time</em></td>
    <td>The date through which the alert has been acknowledged. Will not be present if the alert has never been acknowledged.</td>
    <td><code>"OPEN"</code></td>
  </tr>
  <tr>
    <td><strong>created</strong></td>
    <td><em>date-time</em></td>
    <td>When the alert was opened.</td>
    <td><code>"OPEN"</code></td>
  </tr>
  <tr>
    <td><strong>currentValue:number</strong></td>
    <td><em>number</em></td>
    <td>The value of the metric.</td>
    <td><code>"100.0"</code></td>
  </tr>
  <tr>
    <td><strong>currentValue:units</strong></td>
    <td><em>string</em></td>
    <td>The units for the value. Depends on the type of metric. For example, a metric that measures memory consumption would have a byte measurement, while a metric that measures time would have a time unit. Possible values are: BITS KILOBITS MEGABITS GIGABITS BYTES KILOBYTES MEGABYTES GIGABYTES TERABYTES PETABYTES MILLISECONDS SECONDS MINUTES HOURS DAYS RAW</td>
    <td><code>"BITS"</code></td>
  </tr>
  <tr>
    <td><strong>eventTypeName</strong></td>
    <td><em>string</em></td>
    <td>The name of the event that triggered the alert.</td>
    <td><code>"MONITORING_AGENT_DOWN"</code></td>
  </tr>
  <tr>
    <td><strong>groupId</strong></td>
    <td><em>uuid</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>id</strong></td>
    <td><em>uuid</em></td>
    <td>Unique identifier</td>
    <td><code>"5196d3628d022db4cbc26d9e"</code></td>
  </tr>
  <tr>
    <td><strong>lastNotified</strong></td>
    <td><em>date-time</em></td>
    <td>When the last notification was sent for this alert. Only present if notifications have been sent.</td>
    <td><code>"OPEN"</code></td>
  </tr>
  <tr>
    <td><strong>metricName</strong></td>
    <td><em>string</em></td>
    <td>The name of the metric whose value went outside the threshold. Only present for alerts of type HOST_METRIC</td>
    <td><code>"ASSERT_REGULAR"</code></td>
  </tr>
  <tr>
    <td><strong>resolved</strong></td>
    <td><em>date-time</em></td>
    <td>When the alert was closed. Only present if the status is CLOSED.</td>
    <td><code>"OPEN"</code></td>
  </tr>
  <tr>
    <td><strong>status</strong></td>
    <td><em>string</em></td>
    <td>The current state of the alert. Possible values are: OPEN CLOSED</td>
    <td><code>"OPEN"</code></td>
  </tr>
  <tr>
    <td><strong>typeName</strong></td>
    <td><em>string</em></td>
    <td>The type of alert. Possible values are: AGENT BACKUP HOST HOST_METRIC REPLICA_SET</td>
    <td><code>"AGENT"</code></td>
  </tr>
  <tr>
    <td><strong>updated</strong></td>
    <td><em>date-time</em></td>
    <td>When the alert was last updated.</td>
    <td><code>"OPEN"</code></td>
  </tr>
</table>

### Alert Info
Info for existing alert.

```
GET /groups/{group_id}/alerts/{alert_id}
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/alerts/$ALERT_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "groupId": "API Example",
  "typeName": "AGENT",
  "eventTypeName": "MONITORING_AGENT_DOWN",
  "status": "OPEN",
  "acknowledgedUntil": "OPEN",
  "created": "OPEN",
  "updated": "OPEN",
  "resolved": "OPEN",
  "lastNotified": "OPEN",
  "metricName": "ASSERT_REGULAR",
  "currentValue": {
    "number": "100.0",
    "units": "BITS"
  }
}
```

### Alert List
List existing alerts.

```
GET /groups/{group_id}/alerts
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/alerts
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
[
  {
    "id": "5196d3628d022db4cbc26d9e",
    "groupId": "API Example",
    "typeName": "AGENT",
    "eventTypeName": "MONITORING_AGENT_DOWN",
    "status": "OPEN",
    "acknowledgedUntil": "OPEN",
    "created": "OPEN",
    "updated": "OPEN",
    "resolved": "OPEN",
    "lastNotified": "OPEN",
    "metricName": "ASSERT_REGULAR",
    "currentValue": {
      "number": "100.0",
      "units": "BITS"
    }
  }
]
```

### Alert Update
Update an existing alert.

```
PATCH /groups/{group_id}/alerts/{alert_id}
```


#### Curl Example
```term
$ curl -n -X PATCH https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/alerts/$ALERT_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "groupId": "API Example",
  "typeName": "AGENT",
  "eventTypeName": "MONITORING_AGENT_DOWN",
  "status": "OPEN",
  "acknowledgedUntil": "OPEN",
  "created": "OPEN",
  "updated": "OPEN",
  "resolved": "OPEN",
  "lastNotified": "OPEN",
  "metricName": "ASSERT_REGULAR",
  "currentValue": {
    "number": "100.0",
    "units": "BITS"
  }
}
```


## Backup Configurations
Working with MMS Backup Configurations

### Attributes
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><strong>clusterId</strong></td>
    <td><em>uuid</em></td>
    <td>ID of the cluster that this backup configuration is for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>excludedNamespaces</strong></td>
    <td><em>string</em></td>
    <td>The username to use to connect to the sync source database. Only present when auth is required to connect to the mongod being backed up.</td>
    <td><code>"12!@hello"</code></td>
  </tr>
  <tr>
    <td><strong>groupId</strong></td>
    <td><em>uuid</em></td>
    <td>ID of the group that owns this host.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>password</strong></td>
    <td><em>string</em></td>
    <td>The username to use to connect to the sync source database. Only present when auth is required to connect to the mongod being backed up.</td>
    <td><code>"12!@hello"</code></td>
  </tr>
  <tr>
    <td><strong>sslEnabled</strong></td>
    <td><em>string</em></td>
    <td>The username to use to connect to the sync source database. Only present when auth is required to connect to the mongod being backed up.</td>
    <td><code>"12!@hello"</code></td>
  </tr>
  <tr>
    <td><strong>statusName</strong></td>
    <td><em>string</em></td>
    <td>The current (or desired) status of the backup configuration. Possible values are: INACTIVE PROVISIONING STARTED STOPPED TERMINATING</td>
    <td><code>"INACTIVE"</code></td>
  </tr>
  <tr>
    <td><strong>syncSource</strong></td>
    <td><em>string</em></td>
    <td>The username to use to connect to the sync source database. Only present when auth is required to connect to the mongod being backed up.</td>
    <td><code>"12!@hello"</code></td>
  </tr>
  <tr>
    <td><strong>username</strong></td>
    <td><em>string</em></td>
    <td>The username to use to connect to the sync source database. Only present when auth is required to connect to the mongod being backed up.</td>
    <td><code>"bob@gmail.com"</code></td>
  </tr>
</table>

### Backup Configurations Info
Info for existing backupConfig.

```
GET /groups/{group_id}/backupConfigs/{backupConfig_clusterId}
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/backupConfigs/$BACKUPCONFIG_CLUSTERID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "clusterId": "API Example",
  "groupId": "API Example",
  "statusName": "INACTIVE",
  "username": "bob@gmail.com",
  "password": "12!@hello",
  "sslEnabled": "12!@hello",
  "syncSource": "12!@hello",
  "excludedNamespaces": "12!@hello"
}
```

### Backup Configurations List
List existing backupConfigs.

```
GET /groups/{group_id}/backupConfigs
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/backupConfigs
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
[
  {
    "clusterId": "API Example",
    "groupId": "API Example",
    "statusName": "INACTIVE",
    "username": "bob@gmail.com",
    "password": "12!@hello",
    "sslEnabled": "12!@hello",
    "syncSource": "12!@hello",
    "excludedNamespaces": "12!@hello"
  }
]
```

### Backup Configurations Update
Update an existing backupConfig.

```
PATCH /groups/{group_id}/backupConfigs/{backupConfig_clusterId}
```


#### Curl Example
```term
$ curl -n -X PATCH https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/backupConfigs/$BACKUPCONFIG_CLUSTERID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "clusterId": "API Example",
  "groupId": "API Example",
  "statusName": "INACTIVE",
  "username": "bob@gmail.com",
  "password": "12!@hello",
  "sslEnabled": "12!@hello",
  "syncSource": "12!@hello",
  "excludedNamespaces": "12!@hello"
}
```


## Cluster
Working with MMS Clusters

### Attributes
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><strong>clusterName</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>groupId</strong></td>
    <td><em>uuid</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>id</strong></td>
    <td><em>uuid</em></td>
    <td>Unique identifier</td>
    <td><code>"5196d3628d022db4cbc26d9e"</code></td>
  </tr>
  <tr>
    <td><strong>lastHeartbeat</strong></td>
    <td><em>date-time</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>replicaSetName</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>shardName</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>typeName</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
</table>

### Cluster Info
Info for existing cluster.

```
GET /groups/{group_id}/clusters/{cluster_id}
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/clusters/$CLUSTER_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "groupId": "API Example",
  "typeName": "API Example",
  "clusterName": "API Example",
  "shardName": "API Example",
  "replicaSetName": "API Example",
  "lastHeartbeat": "API Example"
}
```

### Cluster List
List existing clusters.

```
GET /groups/{group_id}/clusters
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/clusters
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
[
  {
    "id": "5196d3628d022db4cbc26d9e",
    "groupId": "API Example",
    "typeName": "API Example",
    "clusterName": "API Example",
    "shardName": "API Example",
    "replicaSetName": "API Example",
    "lastHeartbeat": "API Example"
  }
]
```

### Cluster Update
Update an existing cluster.

```
PATCH /groups/{group_id}/clusters/{cluster_id}
```


#### Curl Example
```term
$ curl -n -X PATCH https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/clusters/$CLUSTER_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "groupId": "API Example",
  "typeName": "API Example",
  "clusterName": "API Example",
  "shardName": "API Example",
  "replicaSetName": "API Example",
  "lastHeartbeat": "API Example"
}
```


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
    <td>Date that a ping was last received from one of the group's monitoring agents.</td>
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


## Host
Working with MMS Hosts

### Attributes
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><strong>alertsEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>authMechanismName</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>created</strong></td>
    <td><em>date-time</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>deactivated</strong></td>
    <td><em>boolean</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>groupId</strong></td>
    <td><em>uuid</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>hasStartupWarnings</strong></td>
    <td><em>boolean</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>hidden</strong></td>
    <td><em>boolean</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>hostEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>hostname</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>id</strong></td>
    <td><em>uuid</em></td>
    <td>Unique identifier</td>
    <td><code>"5196d3628d022db4cbc26d9e"</code></td>
  </tr>
  <tr>
    <td><strong>journalingEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>lastPing</strong></td>
    <td><em>date-time</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>lastReactivated</strong></td>
    <td><em>date-time</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>lastRestart</strong></td>
    <td><em>date-time</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>logsEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>lowUlimit</strong></td>
    <td><em>boolean</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>muninEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>muninPort</strong></td>
    <td><em>integer</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>password</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>port</strong></td>
    <td><em>integer</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>profilerEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>replicaSetName</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>replicaStateName</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>shardName</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>sslEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>uptimeMsec</strong></td>
    <td><em>number</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>username</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
  <tr>
    <td><strong>version</strong></td>
    <td><em>string</em></td>
    <td>ID of the group that this alert was opened for.</td>
    <td><code>"API Example"</code></td>
  </tr>
</table>

### Host Create
Create a new host.

```
POST /groups/{group_id}/hosts
```


#### Curl Example
```term
$ curl -n -X POST https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/hosts
```


#### Response Example
```
HTTP/1.1 201 Created
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "groupId": "API Example",
  "hostname": "API Example",
  "port": "API Example",
  "lastPing": "API Example",
  "version": "API Example",
  "deactivated": "API Example",
  "hasStartupWarnings": "API Example",
  "sslEnabled": "API Example",
  "logsEnabled": "API Example",
  "lastReactivated": "API Example",
  "uptimeMsec": "API Example",
  "lastRestart": "API Example",
  "shardName": "API Example",
  "replicaSetName": "API Example",
  "replicaStateName": "API Example",
  "created": "API Example",
  "hostEnabled": "API Example",
  "journalingEnabled": "API Example",
  "alertsEnabled": "API Example",
  "muninEnabled": "API Example",
  "hidden": "API Example",
  "profilerEnabled": "API Example",
  "lowUlimit": "API Example",
  "muninPort": "API Example",
  "authMechanismName": "API Example",
  "username": "API Example",
  "password": "API Example"
}
```

### Host Delete
Delete an existing host.

```
DELETE /groups/{group_id}/hosts/{host_id}
```


#### Curl Example
```term
$ curl -n -X DELETE https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/hosts/$HOST_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "groupId": "API Example",
  "hostname": "API Example",
  "port": "API Example",
  "lastPing": "API Example",
  "version": "API Example",
  "deactivated": "API Example",
  "hasStartupWarnings": "API Example",
  "sslEnabled": "API Example",
  "logsEnabled": "API Example",
  "lastReactivated": "API Example",
  "uptimeMsec": "API Example",
  "lastRestart": "API Example",
  "shardName": "API Example",
  "replicaSetName": "API Example",
  "replicaStateName": "API Example",
  "created": "API Example",
  "hostEnabled": "API Example",
  "journalingEnabled": "API Example",
  "alertsEnabled": "API Example",
  "muninEnabled": "API Example",
  "hidden": "API Example",
  "profilerEnabled": "API Example",
  "lowUlimit": "API Example",
  "muninPort": "API Example",
  "authMechanismName": "API Example",
  "username": "API Example",
  "password": "API Example"
}
```

### Host Info
Info for existing host.

```
GET /groups/{group_id}/hosts/{host_id}
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/hosts/$HOST_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "groupId": "API Example",
  "hostname": "API Example",
  "port": "API Example",
  "lastPing": "API Example",
  "version": "API Example",
  "deactivated": "API Example",
  "hasStartupWarnings": "API Example",
  "sslEnabled": "API Example",
  "logsEnabled": "API Example",
  "lastReactivated": "API Example",
  "uptimeMsec": "API Example",
  "lastRestart": "API Example",
  "shardName": "API Example",
  "replicaSetName": "API Example",
  "replicaStateName": "API Example",
  "created": "API Example",
  "hostEnabled": "API Example",
  "journalingEnabled": "API Example",
  "alertsEnabled": "API Example",
  "muninEnabled": "API Example",
  "hidden": "API Example",
  "profilerEnabled": "API Example",
  "lowUlimit": "API Example",
  "muninPort": "API Example",
  "authMechanismName": "API Example",
  "username": "API Example",
  "password": "API Example"
}
```

### Host List
List existing hosts.

```
GET /groups/{group_id}/hosts
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/hosts
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
[
  {
    "id": "5196d3628d022db4cbc26d9e",
    "groupId": "API Example",
    "hostname": "API Example",
    "port": "API Example",
    "lastPing": "API Example",
    "version": "API Example",
    "deactivated": "API Example",
    "hasStartupWarnings": "API Example",
    "sslEnabled": "API Example",
    "logsEnabled": "API Example",
    "lastReactivated": "API Example",
    "uptimeMsec": "API Example",
    "lastRestart": "API Example",
    "shardName": "API Example",
    "replicaSetName": "API Example",
    "replicaStateName": "API Example",
    "created": "API Example",
    "hostEnabled": "API Example",
    "journalingEnabled": "API Example",
    "alertsEnabled": "API Example",
    "muninEnabled": "API Example",
    "hidden": "API Example",
    "profilerEnabled": "API Example",
    "lowUlimit": "API Example",
    "muninPort": "API Example",
    "authMechanismName": "API Example",
    "username": "API Example",
    "password": "API Example"
  }
]
```

### Host Update
Update an existing host.

```
PATCH /groups/{group_id}/hosts/{host_id}
```


#### Curl Example
```term
$ curl -n -X PATCH https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/hosts/$HOST_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "5196d3628d022db4cbc26d9e",
  "groupId": "API Example",
  "hostname": "API Example",
  "port": "API Example",
  "lastPing": "API Example",
  "version": "API Example",
  "deactivated": "API Example",
  "hasStartupWarnings": "API Example",
  "sslEnabled": "API Example",
  "logsEnabled": "API Example",
  "lastReactivated": "API Example",
  "uptimeMsec": "API Example",
  "lastRestart": "API Example",
  "shardName": "API Example",
  "replicaSetName": "API Example",
  "replicaStateName": "API Example",
  "created": "API Example",
  "hostEnabled": "API Example",
  "journalingEnabled": "API Example",
  "alertsEnabled": "API Example",
  "muninEnabled": "API Example",
  "hidden": "API Example",
  "profilerEnabled": "API Example",
  "lowUlimit": "API Example",
  "muninPort": "API Example",
  "authMechanismName": "API Example",
  "username": "API Example",
  "password": "API Example"
}
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
    <td>The groupId in which the user has the specified role. Note that for the 'global' roles (those whose name starts with GLOBAL_) there is no groupId since these roles are not tied to a group.</td>
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



