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
    <td><code>"2014-03-01T12:00:00Z"</code></td>
  </tr>
  <tr>
    <td><strong>created</strong></td>
    <td><em>date-time</em></td>
    <td>When the alert was opened.</td>
    <td><code>"2014-03-01T12:00:00Z"</code></td>
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
    <td><code>"5196d3628d022db4cbc26d9e"</code></td>
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
    <td><code>"2014-03-01T12:00:00Z"</code></td>
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
    <td><code>"2014-03-01T12:00:00Z"</code></td>
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
    <td><code>"2014-03-01T12:00:00Z"</code></td>
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
  "groupId": "5196d3628d022db4cbc26d9e",
  "typeName": "AGENT",
  "eventTypeName": "MONITORING_AGENT_DOWN",
  "status": "OPEN",
  "acknowledgedUntil": "2014-03-01T12:00:00Z",
  "created": "2014-03-01T12:00:00Z",
  "updated": "2014-03-01T12:00:00Z",
  "resolved": "2014-03-01T12:00:00Z",
  "lastNotified": "2014-03-01T12:00:00Z",
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
    "groupId": "5196d3628d022db4cbc26d9e",
    "typeName": "AGENT",
    "eventTypeName": "MONITORING_AGENT_DOWN",
    "status": "OPEN",
    "acknowledgedUntil": "2014-03-01T12:00:00Z",
    "created": "2014-03-01T12:00:00Z",
    "updated": "2014-03-01T12:00:00Z",
    "resolved": "2014-03-01T12:00:00Z",
    "lastNotified": "2014-03-01T12:00:00Z",
    "metricName": "ASSERT_REGULAR",
    "currentValue": {
      "number": "100.0",
      "units": "BITS"
    }
  }
]
```

### Alert List
List existing alerts for specified alert config.

```
GET /groups/{group_id}/alertConfigs/{alertConfig_id}/alerts
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/alertConfigs/$ALERTCONFIG_ID/alerts
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
[
  {
    "id": "5196d3628d022db4cbc26d9e",
    "groupId": "5196d3628d022db4cbc26d9e",
    "typeName": "AGENT",
    "eventTypeName": "MONITORING_AGENT_DOWN",
    "status": "OPEN",
    "acknowledgedUntil": "2014-03-01T12:00:00Z",
    "created": "2014-03-01T12:00:00Z",
    "updated": "2014-03-01T12:00:00Z",
    "resolved": "2014-03-01T12:00:00Z",
    "lastNotified": "2014-03-01T12:00:00Z",
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
  "groupId": "5196d3628d022db4cbc26d9e",
  "typeName": "AGENT",
  "eventTypeName": "MONITORING_AGENT_DOWN",
  "status": "OPEN",
  "acknowledgedUntil": "2014-03-01T12:00:00Z",
  "created": "2014-03-01T12:00:00Z",
  "updated": "2014-03-01T12:00:00Z",
  "resolved": "2014-03-01T12:00:00Z",
  "lastNotified": "2014-03-01T12:00:00Z",
  "metricName": "ASSERT_REGULAR",
  "currentValue": {
    "number": "100.0",
    "units": "BITS"
  }
}
```


## AlertConfig
Working with MMS Alert Configurations

### Attributes
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><strong>created</strong></td>
    <td><em>date-time</em></td>
    <td>When this alert configuration was created.</td>
    <td><code>"2012-01-01T12:00:00Z"</code></td>
  </tr>
  <tr>
    <td><strong>enabled</strong></td>
    <td><em>boolean</em></td>
    <td>Is this alert configuration enabled?</td>
    <td><code>"true"</code></td>
  </tr>
  <tr>
    <td><strong>eventTypeName</strong></td>
    <td><em>string</em></td>
    <td>The type of event that will trigger an alert. Supports the same values as the eventTypeName field of the alerts resource.</td>
    <td><code>"OUTSIDE_METRIC_THRESHOLD"</code></td>
  </tr>
  <tr>
    <td><strong>groupId</strong></td>
    <td><em>uuid</em></td>
    <td>ID of the group that owns this alert configuration.</td>
    <td><code>"5196d3628d022db4cbc26d9e"</code></td>
  </tr>
  <tr>
    <td><strong>id</strong></td>
    <td><em>uuid</em></td>
    <td>Unique identifier.</td>
    <td><code>"533dc40ae4b00835ff81eaee"</code></td>
  </tr>
  <tr>
    <td><strong>matchers:fieldName</strong></td>
    <td><em>string</em></td>
    <td>The name of the field in the target object to match on. The available fields depend on the typeName:</td>
    <td><code>"hostnameAndPort"</code></td>
  </tr>
  <tr>
    <td><strong>matchers:operator</strong></td>
    <td><em>string</em></td>
    <td>The operator to test the field's value. Possible values are: EQUALS NOT_EQUALS CONTAINS NOT_CONTAINS STARTS_WITH ENDS_WITH REGEX</td>
    <td><code>"EQUALS"</code></td>
  </tr>
  <tr>
    <td><strong>matchers:value</strong></td>
    <td><em>string</em></td>
    <td>The value to test with the specified operator. When matching on the TYPE_NAME field for a HOST or HOST_METRIC alert, the possible typeName values are: PRIMARY SECONDARY STANDALONE CONFIG MONGOS</td>
    <td><code>"mongo.babypearfoo.com:27017"</code></td>
  </tr>
  <tr>
    <td><strong>metricThreshold:metricName</strong></td>
    <td><em>string</em></td>
    <td>The name of the metric to check. Supports the same values as the metricName field of the alerts resource.</td>
    <td><code>"MEMORY_RESIDENT"</code></td>
  </tr>
  <tr>
    <td><strong>metricThreshold:mode</strong></td>
    <td><em>string</em></td>
    <td>The mode to use when computing the current metric value. Possible values are: AVERAGE TOTAL</td>
    <td><code>"TOTAL"</code></td>
  </tr>
  <tr>
    <td><strong>metricThreshold:operator</strong></td>
    <td><em>string</em></td>
    <td>The operator to apply when checking the current metric value against the threshold value. Possible values are: GREATER_THAN LESS_THAN</td>
    <td><code>"GREATER_THAN"</code></td>
  </tr>
  <tr>
    <td><strong>metricThreshold:threshold</strong></td>
    <td><em>integer</em></td>
    <td>The threshold value outside of which an alert will be triggered.</td>
    <td><code>"7"</code></td>
  </tr>
  <tr>
    <td><strong>metricThreshold:units</strong></td>
    <td><em>string</em></td>
    <td>The units for the threshold value. Supports the same values as the currentValue.units field of the alerts resource.</td>
    <td><code>"GIGABYTES"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:delayMin</strong></td>
    <td><em>integer</em></td>
    <td>The number of minutes to wait after an alert condition is detected before sending out the first notification.</td>
    <td><code>"5"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:emailAddress</strong></td>
    <td><em>string</em></td>
    <td>The email address to which to send notification. Only present for notifications of type EMAIL.</td>
    <td><code>"jane.doe@gmail.com"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:emailEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>Should email notifications be sent? Only present for notifications of type GROUP and USER.</td>
    <td><code>"true"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:intervalMin</strong></td>
    <td><em>integer</em></td>
    <td>The number of minutes to wait between succcessive notifications for unacknowledged alerts that are not resolved.</td>
    <td><code>"0"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:mobileNumber</strong></td>
    <td><em>string</em></td>
    <td>Mobile number to send SMS messages to. Only present for notifications of type SMS.</td>
    <td><code>"(212) 212-1212"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:notificationToken</strong></td>
    <td><em>string</em></td>
    <td>A HipChat API token. Only present for notifications of type HIP_CHAT.</td>
    <td><code>"123456abcdef"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:roomName</strong></td>
    <td><em>string</em></td>
    <td>HipChat room name. Only present for notifications of type HIP_CHAT.</td>
    <td><code>"Test Chat Room"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:serviceKey</strong></td>
    <td><em>string</em></td>
    <td>PagerDuty service key.</td>
    <td><code>"123456abcdef"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:smsEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>Should SMS notifications be sent? Only present for notifications of type GROUP and USER.</td>
    <td><code>"true"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:snmpAddress</strong></td>
    <td><em>string</em></td>
    <td>Hostname and port to send SNMP traps to. Note that SNMP is only supported for On Premise MMS; also, at this time MMS is only able to send SNMP traps to the standard SNMP port (161).</td>
    <td><code>"somedomain.com:161"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:typeName</strong></td>
    <td><em>string</em></td>
    <td>The type of alert notification. Possible values are: GROUP USER SMS EMAIL PAGER_DUTY HIPCHAT SNMP. Note that SNMP notifications are not available in the cloud version of MMS. This feature is only available to On Premise installations.</td>
    <td><code>"SMS"</code></td>
  </tr>
  <tr>
    <td><strong>notifications:username</strong></td>
    <td><em>string</em></td>
    <td>The name of an MMS user to which to send notifications. Only a user in the group that owns the alert configuration is allowed here.</td>
    <td><code>"jane.doe@gmail.com"</code></td>
  </tr>
  <tr>
    <td><strong>typeName</strong></td>
    <td><em>string</em></td>
    <td>The type of this alert configuration. Supports the same values as the typeName field of the alerts resource.</td>
    <td><code>"HOST_METRIC"</code></td>
  </tr>
  <tr>
    <td><strong>updated</strong></td>
    <td><em>date-time</em></td>
    <td>When this alert configuration was last updated.</td>
    <td><code>"2012-01-01T12:00:00Z"</code></td>
  </tr>
</table>

### AlertConfig Create
Create a new alertConfig.

```
POST /groups/{group_id}/alertConfigs
```


#### Curl Example
```term
$ curl -n -X POST https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/alertConfigs
```


#### Response Example
```
HTTP/1.1 201 Created
```
```json
{
  "id": "533dc40ae4b00835ff81eaee",
  "groupId": "5196d3628d022db4cbc26d9e",
  "typeName": "HOST_METRIC",
  "eventTypeName": "OUTSIDE_METRIC_THRESHOLD",
  "created": "2012-01-01T12:00:00Z",
  "updated": "2012-01-01T12:00:00Z",
  "enabled": "true",
  "matchers": {
    "fieldName": "hostnameAndPort",
    "operator": "EQUALS",
    "value": "mongo.babypearfoo.com:27017"
  },
  "notifications": {
    "typeName": "SMS",
    "delayMin": "5",
    "intervalMin": "0",
    "emailAddress": "jane.doe@gmail.com",
    "notificationToken": "123456abcdef",
    "roomName": "Test Chat Room",
    "emailEnabled": "true",
    "smsEnabled": "true",
    "username": "jane.doe@gmail.com",
    "mobileNumber": "(212) 212-1212",
    "snmpAddress": "somedomain.com:161",
    "serviceKey": "123456abcdef"
  },
  "metricThreshold": {
    "metricName": "MEMORY_RESIDENT",
    "operator": "GREATER_THAN",
    "threshold": "7",
    "units": "GIGABYTES",
    "mode": "TOTAL"
  }
}
```

### AlertConfig Delete
Delete an existing alertConfig.

```
DELETE /groups/{group_id}/alertConfigs/{alertConfig_id}
```


#### Curl Example
```term
$ curl -n -X DELETE https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/alertConfigs/$ALERTCONFIG_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "533dc40ae4b00835ff81eaee",
  "groupId": "5196d3628d022db4cbc26d9e",
  "typeName": "HOST_METRIC",
  "eventTypeName": "OUTSIDE_METRIC_THRESHOLD",
  "created": "2012-01-01T12:00:00Z",
  "updated": "2012-01-01T12:00:00Z",
  "enabled": "true",
  "matchers": {
    "fieldName": "hostnameAndPort",
    "operator": "EQUALS",
    "value": "mongo.babypearfoo.com:27017"
  },
  "notifications": {
    "typeName": "SMS",
    "delayMin": "5",
    "intervalMin": "0",
    "emailAddress": "jane.doe@gmail.com",
    "notificationToken": "123456abcdef",
    "roomName": "Test Chat Room",
    "emailEnabled": "true",
    "smsEnabled": "true",
    "username": "jane.doe@gmail.com",
    "mobileNumber": "(212) 212-1212",
    "snmpAddress": "somedomain.com:161",
    "serviceKey": "123456abcdef"
  },
  "metricThreshold": {
    "metricName": "MEMORY_RESIDENT",
    "operator": "GREATER_THAN",
    "threshold": "7",
    "units": "GIGABYTES",
    "mode": "TOTAL"
  }
}
```

### AlertConfig Info
Info for existing alertConfig.

```
GET /groups/{group_id}/alertConfigs/{alertConfig_id}
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/alertConfigs/$ALERTCONFIG_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "533dc40ae4b00835ff81eaee",
  "groupId": "5196d3628d022db4cbc26d9e",
  "typeName": "HOST_METRIC",
  "eventTypeName": "OUTSIDE_METRIC_THRESHOLD",
  "created": "2012-01-01T12:00:00Z",
  "updated": "2012-01-01T12:00:00Z",
  "enabled": "true",
  "matchers": {
    "fieldName": "hostnameAndPort",
    "operator": "EQUALS",
    "value": "mongo.babypearfoo.com:27017"
  },
  "notifications": {
    "typeName": "SMS",
    "delayMin": "5",
    "intervalMin": "0",
    "emailAddress": "jane.doe@gmail.com",
    "notificationToken": "123456abcdef",
    "roomName": "Test Chat Room",
    "emailEnabled": "true",
    "smsEnabled": "true",
    "username": "jane.doe@gmail.com",
    "mobileNumber": "(212) 212-1212",
    "snmpAddress": "somedomain.com:161",
    "serviceKey": "123456abcdef"
  },
  "metricThreshold": {
    "metricName": "MEMORY_RESIDENT",
    "operator": "GREATER_THAN",
    "threshold": "7",
    "units": "GIGABYTES",
    "mode": "TOTAL"
  }
}
```

### AlertConfig List
List existing alertConfigs.

```
GET /groups/{group_id}/alertConfigs
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/alertConfigs
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
[
  {
    "id": "533dc40ae4b00835ff81eaee",
    "groupId": "5196d3628d022db4cbc26d9e",
    "typeName": "HOST_METRIC",
    "eventTypeName": "OUTSIDE_METRIC_THRESHOLD",
    "created": "2012-01-01T12:00:00Z",
    "updated": "2012-01-01T12:00:00Z",
    "enabled": "true",
    "matchers": {
      "fieldName": "hostnameAndPort",
      "operator": "EQUALS",
      "value": "mongo.babypearfoo.com:27017"
    },
    "notifications": {
      "typeName": "SMS",
      "delayMin": "5",
      "intervalMin": "0",
      "emailAddress": "jane.doe@gmail.com",
      "notificationToken": "123456abcdef",
      "roomName": "Test Chat Room",
      "emailEnabled": "true",
      "smsEnabled": "true",
      "username": "jane.doe@gmail.com",
      "mobileNumber": "(212) 212-1212",
      "snmpAddress": "somedomain.com:161",
      "serviceKey": "123456abcdef"
    },
    "metricThreshold": {
      "metricName": "MEMORY_RESIDENT",
      "operator": "GREATER_THAN",
      "threshold": "7",
      "units": "GIGABYTES",
      "mode": "TOTAL"
    }
  }
]
```

### AlertConfig Replace
Replace an existing alertConfig.

```
PUT /groups/{group_id}/alertConfigs/{alertConfig_id}
```


#### Curl Example
```term
$ curl -n -X PUT https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/alertConfigs/$ALERTCONFIG_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "533dc40ae4b00835ff81eaee",
  "groupId": "5196d3628d022db4cbc26d9e",
  "typeName": "HOST_METRIC",
  "eventTypeName": "OUTSIDE_METRIC_THRESHOLD",
  "created": "2012-01-01T12:00:00Z",
  "updated": "2012-01-01T12:00:00Z",
  "enabled": "true",
  "matchers": {
    "fieldName": "hostnameAndPort",
    "operator": "EQUALS",
    "value": "mongo.babypearfoo.com:27017"
  },
  "notifications": {
    "typeName": "SMS",
    "delayMin": "5",
    "intervalMin": "0",
    "emailAddress": "jane.doe@gmail.com",
    "notificationToken": "123456abcdef",
    "roomName": "Test Chat Room",
    "emailEnabled": "true",
    "smsEnabled": "true",
    "username": "jane.doe@gmail.com",
    "mobileNumber": "(212) 212-1212",
    "snmpAddress": "somedomain.com:161",
    "serviceKey": "123456abcdef"
  },
  "metricThreshold": {
    "metricName": "MEMORY_RESIDENT",
    "operator": "GREATER_THAN",
    "threshold": "7",
    "units": "GIGABYTES",
    "mode": "TOTAL"
  }
}
```

### AlertConfig Update
Update an existing alertConfig.

```
PATCH /groups/{group_id}/alertConfigs/{alertConfig_id}
```


#### Curl Example
```term
$ curl -n -X PATCH https://mms.mongodb.com/api/public/v1.0/groups/$GROUP_ID/alertConfigs/$ALERTCONFIG_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "id": "533dc40ae4b00835ff81eaee",
  "groupId": "5196d3628d022db4cbc26d9e",
  "typeName": "HOST_METRIC",
  "eventTypeName": "OUTSIDE_METRIC_THRESHOLD",
  "created": "2012-01-01T12:00:00Z",
  "updated": "2012-01-01T12:00:00Z",
  "enabled": "true",
  "matchers": {
    "fieldName": "hostnameAndPort",
    "operator": "EQUALS",
    "value": "mongo.babypearfoo.com:27017"
  },
  "notifications": {
    "typeName": "SMS",
    "delayMin": "5",
    "intervalMin": "0",
    "emailAddress": "jane.doe@gmail.com",
    "notificationToken": "123456abcdef",
    "roomName": "Test Chat Room",
    "emailEnabled": "true",
    "smsEnabled": "true",
    "username": "jane.doe@gmail.com",
    "mobileNumber": "(212) 212-1212",
    "snmpAddress": "somedomain.com:161",
    "serviceKey": "123456abcdef"
  },
  "metricThreshold": {
    "metricName": "MEMORY_RESIDENT",
    "operator": "GREATER_THAN",
    "threshold": "7",
    "units": "GIGABYTES",
    "mode": "TOTAL"
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
    <td><code>"5196e5b0e4b0fca9cc88334a"</code></td>
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
    <td><code>"5196d3628d022db4cbc26d9e"</code></td>
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
    <td><code>"STARTED"</code></td>
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
  "clusterId": "5196e5b0e4b0fca9cc88334a",
  "groupId": "5196d3628d022db4cbc26d9e",
  "statusName": "STARTED",
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
    "clusterId": "5196e5b0e4b0fca9cc88334a",
    "groupId": "5196d3628d022db4cbc26d9e",
    "statusName": "STARTED",
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
  "clusterId": "5196e5b0e4b0fca9cc88334a",
  "groupId": "5196d3628d022db4cbc26d9e",
  "statusName": "STARTED",
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
    <td>Display name of the cluster. Only applies to sharded clusters. Note that mongod itself doesn't allow you to name a cluster; this name is supplied by (and editable within) MMS. For a replica set within a sharded cluster, the cluster name is the name of its parent cluster.</td>
    <td><code>"Cluster 0"</code></td>
  </tr>
  <tr>
    <td><strong>groupId</strong></td>
    <td><em>uuid</em></td>
    <td>ID of the group that owns this cluster.</td>
    <td><code>"533d7d4730040be257defe88"</code></td>
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
    <td>The approximate last time MMS processed a ping from this cluster.</td>
    <td><code>"2014-02-26T17:32:45Z"</code></td>
  </tr>
  <tr>
    <td><strong>replicaSetName</strong></td>
    <td><em>string</em></td>
    <td>Name of the replica set. Only present for a cluster of type REPLICA_SET.</td>
    <td><code>"rs1"</code></td>
  </tr>
  <tr>
    <td><strong>shardName</strong></td>
    <td><em>string</em></td>
    <td>Name of the shard. Only present for a cluster of type SHARDED or REPLICA_SET that is part of a sharded cluster.</td>
    <td><code>"shard001"</code></td>
  </tr>
  <tr>
    <td><strong>typeName</strong></td>
    <td><em>string</em></td>
    <td>Specifies what kind of cluster this is. Possible values are: MASTER_SLAVE REPLICA_SET SHARDED SHARDED_REPLICA_SET</td>
    <td><code>"REPLICA_SET"</code></td>
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
  "groupId": "533d7d4730040be257defe88",
  "typeName": "REPLICA_SET",
  "clusterName": "Cluster 0",
  "shardName": "shard001",
  "replicaSetName": "rs1",
  "lastHeartbeat": "2014-02-26T17:32:45Z"
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
    "groupId": "533d7d4730040be257defe88",
    "typeName": "REPLICA_SET",
    "clusterName": "Cluster 0",
    "shardName": "shard001",
    "replicaSetName": "rs1",
    "lastHeartbeat": "2014-02-26T17:32:45Z"
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
  "groupId": "533d7d4730040be257defe88",
  "typeName": "REPLICA_SET",
  "clusterName": "Cluster 0",
  "shardName": "shard001",
  "replicaSetName": "rs1",
  "lastHeartbeat": "2014-02-26T17:32:45Z"
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
    <td><code>"My Group"</code></td>
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
  "name": "My Group",
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
  "name": "My Group",
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
  "name": "My Group",
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
    "name": "My Group",
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
    <td>Are alerts enabled for this host?</td>
    <td><code>"true"</code></td>
  </tr>
  <tr>
    <td><strong>authMechanismName</strong></td>
    <td><em>string</em></td>
    <td>The authentication mechanism used to connect to this host. Possible values are: MONGODB_CR GSSAPI NONE</td>
    <td><code>"MONGODB_CR"</code></td>
  </tr>
  <tr>
    <td><strong>created</strong></td>
    <td><em>date-time</em></td>
    <td>Date this host was created or first discovered by MMS.</td>
    <td><code>"2013-12-15T09:17:23Z"</code></td>
  </tr>
  <tr>
    <td><strong>deactivated</strong></td>
    <td><em>boolean</em></td>
    <td>Has this host been deactivated by MMS? A host will be marked as deactivated when MMS hasn't received a ping from it in several days.</td>
    <td><code>"false"</code></td>
  </tr>
  <tr>
    <td><strong>groupId</strong></td>
    <td><em>uuid</em></td>
    <td>ID of the group that owns this host.</td>
    <td><code>"5196d3628d022db4cbc26d9e"</code></td>
  </tr>
  <tr>
    <td><strong>hasStartupWarnings</strong></td>
    <td><em>boolean</em></td>
    <td>Are there startup warnings for this host?</td>
    <td><code>"false"</code></td>
  </tr>
  <tr>
    <td><strong>hidden</strong></td>
    <td><em>boolean</em></td>
    <td>Is this host currently hidden? When MMS deactivates a host, it will also mark it as hidden.</td>
    <td><code>"false"</code></td>
  </tr>
  <tr>
    <td><strong>hostEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>Is this host currently enabled? Hosts can be manually disabled in the MMS UI.</td>
    <td><code>"true"</code></td>
  </tr>
  <tr>
    <td><strong>hostname</strong></td>
    <td><em>string</em></td>
    <td>Primary hostname. A host typically has several aliases, so the primary is the best available name as decided by MMS.</td>
    <td><code>"localhost"</code></td>
  </tr>
  <tr>
    <td><strong>id</strong></td>
    <td><em>uuid</em></td>
    <td>Unique identifier</td>
    <td><code>"4059580c20c4581872ef24d0b8f5dca0"</code></td>
  </tr>
  <tr>
    <td><strong>journalingEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>Is journaling enabled for this host?</td>
    <td><code>"true"</code></td>
  </tr>
  <tr>
    <td><strong>lastPing</strong></td>
    <td><em>date-time</em></td>
    <td>When the last ping for this host was received.</td>
    <td><code>"2014-04-22T19:56:50Z"</code></td>
  </tr>
  <tr>
    <td><strong>lastReactivated</strong></td>
    <td><em>date-time</em></td>
    <td>The last time this has was manually reactivated.</td>
    <td><code>"2014-04-22T19:56:50Z"</code></td>
  </tr>
  <tr>
    <td><strong>lastRestart</strong></td>
    <td><em>date-time</em></td>
    <td>Date this host was last restarted.</td>
    <td><code>"2014-04-22T19:56:50Z"</code></td>
  </tr>
  <tr>
    <td><strong>logsEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>Is MMS collecting logs for this host?</td>
    <td><code>"false"</code></td>
  </tr>
  <tr>
    <td><strong>lowUlimit</strong></td>
    <td><em>boolean</em></td>
    <td>Does this host have a low ulimit setting?</td>
    <td><code>"false"</code></td>
  </tr>
  <tr>
    <td><strong>muninEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>Are Munin stats being collected for this host?</td>
    <td><code>"true"</code></td>
  </tr>
  <tr>
    <td><strong>muninPort</strong></td>
    <td><em>integer</em></td>
    <td>What port should be used to collect Munin stats from this host?</td>
    <td><code>"4949"</code></td>
  </tr>
  <tr>
    <td><strong>password</strong></td>
    <td><em>string</em></td>
    <td>Password for connecting to this host. If a host's authMechanismName is MONGODB_CR, then you must include this field when creating the host or updating its credentials. However, it will never be exposed when a host entity is returned.</td>
    <td><code>"myM0NGO0!"</code></td>
  </tr>
  <tr>
    <td><strong>port</strong></td>
    <td><em>integer</em></td>
    <td>Port that MongoDB process (mongod or mongos) listens on.</td>
    <td><code>"27017"</code></td>
  </tr>
  <tr>
    <td><strong>profilerEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>Is MMS collecting profile information from this host?</td>
    <td><code>"true"</code></td>
  </tr>
  <tr>
    <td><strong>replicaSetName</strong></td>
    <td><em>string</em></td>
    <td>Name of the replica set this host belongs to. Only present if this host is part of a replica set.</td>
    <td><code>"rs0"</code></td>
  </tr>
  <tr>
    <td><strong>replicaStateName</strong></td>
    <td><em>string</em></td>
    <td>Current state of this host within a replica set. Only present if this host is part of a replica set. See Replica Set Member States for possible values.</td>
    <td><code>"SECONDARY"</code></td>
  </tr>
  <tr>
    <td><strong>shardName</strong></td>
    <td><em>string</em></td>
    <td>Name of the shard this host belongs to. Only present if the host is part of a sharded cluster.</td>
    <td><code>"myShard0"</code></td>
  </tr>
  <tr>
    <td><strong>sslEnabled</strong></td>
    <td><em>boolean</em></td>
    <td>Is SSL enabled for this host?</td>
    <td><code>"false"</code></td>
  </tr>
  <tr>
    <td><strong>uptimeMsec</strong></td>
    <td><em>number</em></td>
    <td>Number of milliseconds since this host's last restart.</td>
    <td><code>"1024"</code></td>
  </tr>
  <tr>
    <td><strong>username</strong></td>
    <td><em>string</em></td>
    <td>Username for connecting to this host. Only present when the authMechanismName is MONGODB_CR.</td>
    <td><code>"mongo"</code></td>
  </tr>
  <tr>
    <td><strong>version</strong></td>
    <td><em>string</em></td>
    <td>Version of MongoDB running on this host.</td>
    <td><code>"2.6.3"</code></td>
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
  "id": "4059580c20c4581872ef24d0b8f5dca0",
  "groupId": "5196d3628d022db4cbc26d9e",
  "hostname": "localhost",
  "port": "27017",
  "lastPing": "2014-04-22T19:56:50Z",
  "version": "2.6.3",
  "deactivated": "false",
  "hasStartupWarnings": "false",
  "sslEnabled": "false",
  "logsEnabled": "false",
  "lastReactivated": "2014-04-22T19:56:50Z",
  "uptimeMsec": "1024",
  "lastRestart": "2014-04-22T19:56:50Z",
  "shardName": "myShard0",
  "replicaSetName": "rs0",
  "replicaStateName": "SECONDARY",
  "created": "2013-12-15T09:17:23Z",
  "hostEnabled": "true",
  "journalingEnabled": "true",
  "alertsEnabled": "true",
  "muninEnabled": "true",
  "hidden": "false",
  "profilerEnabled": "true",
  "lowUlimit": "false",
  "muninPort": "4949",
  "authMechanismName": "MONGODB_CR",
  "username": "mongo",
  "password": "myM0NGO0!"
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
  "id": "4059580c20c4581872ef24d0b8f5dca0",
  "groupId": "5196d3628d022db4cbc26d9e",
  "hostname": "localhost",
  "port": "27017",
  "lastPing": "2014-04-22T19:56:50Z",
  "version": "2.6.3",
  "deactivated": "false",
  "hasStartupWarnings": "false",
  "sslEnabled": "false",
  "logsEnabled": "false",
  "lastReactivated": "2014-04-22T19:56:50Z",
  "uptimeMsec": "1024",
  "lastRestart": "2014-04-22T19:56:50Z",
  "shardName": "myShard0",
  "replicaSetName": "rs0",
  "replicaStateName": "SECONDARY",
  "created": "2013-12-15T09:17:23Z",
  "hostEnabled": "true",
  "journalingEnabled": "true",
  "alertsEnabled": "true",
  "muninEnabled": "true",
  "hidden": "false",
  "profilerEnabled": "true",
  "lowUlimit": "false",
  "muninPort": "4949",
  "authMechanismName": "MONGODB_CR",
  "username": "mongo",
  "password": "myM0NGO0!"
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
  "id": "4059580c20c4581872ef24d0b8f5dca0",
  "groupId": "5196d3628d022db4cbc26d9e",
  "hostname": "localhost",
  "port": "27017",
  "lastPing": "2014-04-22T19:56:50Z",
  "version": "2.6.3",
  "deactivated": "false",
  "hasStartupWarnings": "false",
  "sslEnabled": "false",
  "logsEnabled": "false",
  "lastReactivated": "2014-04-22T19:56:50Z",
  "uptimeMsec": "1024",
  "lastRestart": "2014-04-22T19:56:50Z",
  "shardName": "myShard0",
  "replicaSetName": "rs0",
  "replicaStateName": "SECONDARY",
  "created": "2013-12-15T09:17:23Z",
  "hostEnabled": "true",
  "journalingEnabled": "true",
  "alertsEnabled": "true",
  "muninEnabled": "true",
  "hidden": "false",
  "profilerEnabled": "true",
  "lowUlimit": "false",
  "muninPort": "4949",
  "authMechanismName": "MONGODB_CR",
  "username": "mongo",
  "password": "myM0NGO0!"
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
    "id": "4059580c20c4581872ef24d0b8f5dca0",
    "groupId": "5196d3628d022db4cbc26d9e",
    "hostname": "localhost",
    "port": "27017",
    "lastPing": "2014-04-22T19:56:50Z",
    "version": "2.6.3",
    "deactivated": "false",
    "hasStartupWarnings": "false",
    "sslEnabled": "false",
    "logsEnabled": "false",
    "lastReactivated": "2014-04-22T19:56:50Z",
    "uptimeMsec": "1024",
    "lastRestart": "2014-04-22T19:56:50Z",
    "shardName": "myShard0",
    "replicaSetName": "rs0",
    "replicaStateName": "SECONDARY",
    "created": "2013-12-15T09:17:23Z",
    "hostEnabled": "true",
    "journalingEnabled": "true",
    "alertsEnabled": "true",
    "muninEnabled": "true",
    "hidden": "false",
    "profilerEnabled": "true",
    "lowUlimit": "false",
    "muninPort": "4949",
    "authMechanismName": "MONGODB_CR",
    "username": "mongo",
    "password": "myM0NGO0!"
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
  "id": "4059580c20c4581872ef24d0b8f5dca0",
  "groupId": "5196d3628d022db4cbc26d9e",
  "hostname": "localhost",
  "port": "27017",
  "lastPing": "2014-04-22T19:56:50Z",
  "version": "2.6.3",
  "deactivated": "false",
  "hasStartupWarnings": "false",
  "sslEnabled": "false",
  "logsEnabled": "false",
  "lastReactivated": "2014-04-22T19:56:50Z",
  "uptimeMsec": "1024",
  "lastRestart": "2014-04-22T19:56:50Z",
  "shardName": "myShard0",
  "replicaSetName": "rs0",
  "replicaStateName": "SECONDARY",
  "created": "2013-12-15T09:17:23Z",
  "hostEnabled": "true",
  "journalingEnabled": "true",
  "alertsEnabled": "true",
  "muninEnabled": "true",
  "hidden": "false",
  "profilerEnabled": "true",
  "lowUlimit": "false",
  "muninPort": "4949",
  "authMechanismName": "MONGODB_CR",
  "username": "mongo",
  "password": "myM0NGO0!"
}
```


## Root
MMS API Information

### Attributes
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><strong>throttling</strong></td>
    <td><em>boolean</em></td>
    <td>Tells whether or not MMS is throttling data. This can be used as a simple indicator of the current health of MMS, since throttling is generally enabled when MMS is in an unhealthy state.</td>
    <td><code>"false"</code></td>
  </tr>
</table>

### Root Info
Info for existing root.

```
GET 
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "throttling": "false"
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
    <td><code>"somebody@somewhere-else.com"</code></td>
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
    <td><code>"abc123"</code></td>
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
  "password": "abc123",
  "emailAddress": "somebody@somewhere-else.com",
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
  "password": "abc123",
  "emailAddress": "somebody@somewhere-else.com",
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
  "password": "abc123",
  "emailAddress": "somebody@somewhere-else.com",
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
    "password": "abc123",
    "emailAddress": "somebody@somewhere-else.com",
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
    "password": "abc123",
    "emailAddress": "somebody@somewhere-else.com",
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
  "password": "abc123",
  "emailAddress": "somebody@somewhere-else.com",
  "mobileNumber": "555-555-5555",
  "firstName": "Jane",
  "lastName": "Doe",
  "roles": {
    "groupId": "533daa30879bb2da07807696",
    "roleName": "GROUP_USER_ADMIN"
  }
}
```


## Whitelist
Working with MMS Whitelists

### Attributes
<table>
  <tr>
    <th>Name</th>
    <th>Type</th>
    <th>Description</th>
    <th>Example</th>
  </tr>
  <tr>
    <td><strong>count</strong></td>
    <td><em>integer</em></td>
    <td>The total number of requests that originated from this IP address. Note that this field is only updated when a resource that is protected by the whitelist is accessed.</td>
    <td><code>"1"</code></td>
  </tr>
  <tr>
    <td><strong>created</strong></td>
    <td><em>date-time</em></td>
    <td>The date this IP address was added to the whitelist.</td>
    <td><code>"2012-01-01T12:00:00Z"</code></td>
  </tr>
  <tr>
    <td><strong>ipAddress</strong></td>
    <td><em>string</em></td>
    <td>A whitelisted IP address.</td>
    <td><code>"12.34.56.78"</code></td>
  </tr>
  <tr>
    <td><strong>lastUsed</strong></td>
    <td><em>date-time</em></td>
    <td>The date of the most recent request that originated from this IP address. Note that this field is only updated when a resource that is protected by the whitelist is accessed.</td>
    <td><code>"2012-01-01T12:00:00Z"</code></td>
  </tr>
</table>

### Whitelist Create
Create a new whitelist.

```
POST /users/{user_id}/whitelist
```


#### Curl Example
```term
$ curl -n -X POST https://mms.mongodb.com/api/public/v1.0/users/$USER_ID/whitelist
```


#### Response Example
```
HTTP/1.1 201 Created
```
```json
{
  "ipAddress": "12.34.56.78",
  "created": "2012-01-01T12:00:00Z",
  "lastUsed": "2012-01-01T12:00:00Z",
  "count": "1"
}
```

### Whitelist Delete
Delete an existing whitelist.

```
DELETE /users/{user_id}/whitelist/{whitelist_id}
```


#### Curl Example
```term
$ curl -n -X DELETE https://mms.mongodb.com/api/public/v1.0/users/$USER_ID/whitelist/$WHITELIST_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "ipAddress": "12.34.56.78",
  "created": "2012-01-01T12:00:00Z",
  "lastUsed": "2012-01-01T12:00:00Z",
  "count": "1"
}
```

### Whitelist Info
Info for existing whitelist.

```
GET /users/{user_id}/whitelist/{whitelist_id}
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/users/$USER_ID/whitelist/$WHITELIST_ID
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
{
  "ipAddress": "12.34.56.78",
  "created": "2012-01-01T12:00:00Z",
  "lastUsed": "2012-01-01T12:00:00Z",
  "count": "1"
}
```

### Whitelist List
List existing whitelists.

```
GET /users/{user_id}/whitelist
```


#### Curl Example
```term
$ curl -n -X GET https://mms.mongodb.com/api/public/v1.0/users/$USER_ID/whitelist
```


#### Response Example
```
HTTP/1.1 200 OK
```
```json
[
  {
    "ipAddress": "12.34.56.78",
    "created": "2012-01-01T12:00:00Z",
    "lastUsed": "2012-01-01T12:00:00Z",
    "count": "1"
  }
]
```



