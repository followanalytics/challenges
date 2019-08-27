### SRE Challenge - Part 1

Your first task is to parse our Load Balancer logs and to export its data as a JSON file on a certain local path.

The log file has the following structure:

```
https,2019-08-30,224.176.175.199,476,example.com/auth,200
https,2019-08-23,49.68.79.176,673,example.com/logs,200
https,2019-08-4,174.10.254.200,583,example.com/auth,200
https,2019-08-8,221.107.162.203,659,example.com/auth,200
https,2019-08-2,156.49.6.218,127,example.com/logs,200
https,2019-08-21,233.110.178.222,581,example.com/auth,200
https,2019-08-20,152.193.204.222,180,example.com/logs,200
https,2019-08-8,239.77.70.119,263,example.com/logs,200
https,2019-08-22,113.66.45.100,496,example.com/session,200
https,2019-08-10,200.98.105.41,249,example.com/session,200
```

The following table describes the fields of an access log entry, in order. All fields are delimited by commas.

```
| type          | The type of request or connection. Ex: https            |
| date          | The date with the format yyyy/mm/dd                     |
| source_ip     | The IP address of the requesting client.                |
| response_time | Response time in ms                                     |
| target_url    |  The target URL                                         |
| http_code     | The status code of the response from the load balancer. |

```
 
You can download it from [here](https://fa-devops-challenge.s3-eu-west-1.amazonaws.com/lb_logs/partial.logs).


The expected output is the following:

```
{ logs :
    [ 
        type: 'https',
        date: '2019-08-30'
        source_ip: '224.176.175.199'
        response_time: '476'
        target_url: 'example.com/session'
        http_code: 200
    ],
    [ 
        type: 'https',
        date: '2019-08-29'
        source_ip: '169.43.192.15'
        response_time: '325'
        target_url: 'example.com/logs'
        http_code: 200
    ],
    ...    
}

```

After implementing the solution for the Part 1, you can move to the Part 2.