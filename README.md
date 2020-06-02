# codeceptjs-influxdbhelper
CodeceptJS helper to collect Test Execution Metrics with the help of CodeceptJS test events, these metrics can be used to create test metrics dashboards.

## Installation
Install the helper and use it with your tests.

`npm i codeceptjs-influxdbhelper --save-dev`

## Configuration

This helper should be added in the codeceptjs configuration file

Example:
```editorconfig
{
    "helpers": {
        InfluxDBHelper: {
              require: 'codeceptjs-influxdbhelper',
              username: process.env.INFLUXDB_USERNAME || root,
              password: process.env.INFLUXDB_PASSWORD || root,
              host: process.env.INFLUXDB_HOST || localhost,
              port: process.env.INFLUXDB_PORT || '8086',
              dbname: process.env.INFLUXDB_DBNAME || 'codeceptjs',
              measurement: process.env.INFLUXDB_MEASUREMENT || 'testMethod'
         },
    }
}
```
## How It Works

The helper makes use of [CodeceptJS Hooks](https://codecept.io/hooks/#event-listeners) Every Scenario after the execution is complete, triggers an insertion into the influxDB.

Following information is collected by Default:

1) Test Execution Duration
2) Test Result
3) Test Tags
4) Test Title

The measurement name is added right into the configuration file and field of measurement is `duration`.
