### SRE Challenge - Part 2

Your second task is to enrich the logs by adding a field that contains the country ISO code from where the log just came from.

In order to know the country ISO code for a given IP, you can use the GeoLite2 database.

You can download it from the following URL:

`https://fa-devops-challenge.s3-eu-west-1.amazonaws.com/geolitedb/GeoLite2-City.mmdb`

Now you can run the GeoLite2 API by running a docker container as follows:

`docker run --rm -p 3000:5000 -v $(pwd)/GeoLite2-City.mmdb:/data/geodb.mmdb hugohenley/geoip-service:latest`

PS: the docker image was forked from `klauspost/geoip-service` so you can use it as a reference in case of need. 

You will be able to request a local API running on the port 3000 and you can request it as follows:

`GET http://localhost:3000/169.43.192.15`

Expected response:
```
{
  "Data": {
    "City": {
      "GeoNameID": 0,
      "Names": null
    },
    "Continent": {
      "Code": "EU",
      "GeoNameID": 6255148,
      "Names": {
        "fr": "Europe",
        "ja": "ヨーロッパ",
        "pt-BR": "Europa",
        "ru": "Европа",
        "zh-CN": "欧洲",
        "de": "Europa",
        "en": "Europe",
        "es": "Europa"
      }
    },
    "Country": {
      "GeoNameID": 2658434,
      "IsoCode": "CH",
      "Names": {
        "ru": "Швейцария",
        "zh-CN": "瑞士",
        "de": "Schweiz",
        "en": "Switzerland",
        "es": "Suiza",
        "fr": "Suisse",
        "ja": "スイス連邦",
        "pt-BR": "Suíça"
      }
    },
    "Location": {
      "Latitude": 47.1449,
      "Longitude": 8.1551,
      "MetroCode": 0,
      "TimeZone": "Europe/Zurich"
    },
    "Postal": {
      "Code": ""
    },
    "RegisteredCountry": {
      "GeoNameID": 2658434,
      "IsoCode": "CH",
      "Names": {
        "fr": "Suisse",
        "ja": "スイス連邦",
        "pt-BR": "Suíça",
        "ru": "Швейцария",
        "zh-CN": "瑞士",
        "de": "Schweiz",
        "en": "Switzerland",
        "es": "Suiza"
      }
    },
    "RepresentedCountry": {
      "GeoNameID": 0,
      "IsoCode": "",
      "Names": null,
      "Type": ""
    },
    "Subdivisions": null,
    "Traits": {
      "IsAnonymousProxy": false,
      "IsSatelliteProvider": false
    }
  }
}
```

Processing the log file should now output a JSON with the following format:

```
{ logs :
    [ 
        type: 'https',
        date: '2019-08-30'
        source_ip: '224.176.175.199'
        response_time: '476'
        target_url: 'example.com/session'
        http_code: 200,
        iso_code: ''
    ],
    [ 
        type: 'https',
        date: '2019-08-29'
        source_ip: '169.43.192.15'
        response_time: '325'
        target_url: 'example.com/logs'
        http_code: 200,
        iso_code: 'CH'
    ],
    ...    
}
```

Please be aware that the GeoLite2 API might not be able to return the country code for some IPs. 
On that case, you can just consider it as _empty_.

You can go to the Part 3 now.