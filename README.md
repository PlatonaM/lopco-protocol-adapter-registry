### Protocol-Adapter Data Structure

{
    "name": <string>,
    "image": <string>,
    "data_cache_path": <string>,
    "description": <string>,
    "configs": {
        <string>: <string>,
        ...
    },
    "ports": [
        {
            "port": <number>,
            "protocol": <string>("tcp" / "udp" / "sctp")
        },
        ...
    ]
}

### API

#### /protocol-adapters

**GET**

_List protocol-adapters._

    # Example

    curl http://<host>/protocol-adapters
    {
        "5e674298-49d5-4723-926c-cf062dd9c141": "{\"name\": \"HTTP Protocol Adapter\", \"image\": \"platonam/lopco-http-protocol-adapter:dev\", \"data_cache_path\": \"/data_cache\", \"description\": \"Upload files via HTTP.\", \"configs\": {\"CONF_LOGGER_LEVEL\": \"info\"}, \"ports\": [{\"port\": 80, \"protocol\": \"tcp\"}]}",
        "adf55c15-4c0b-4878-91a4-f5025718a008": "{\"name\":\"Raw Socket Protocol Adapter \",\"image\":\"platonam/lopco-raw-soc-protocol-adapter:dev\",\"data_cache_path\":\"/datacache\",\"description\":\"Transmit data via raw TCP socket.\",\"configs\":{\"LOGGING_LVL\":\"1\"},\"ports\":[{\"port\":1000,\"protocol\":\"tcp\"}]}"
    }

**POST**

_Add new protocol-adapter._

    # Example

    cat pa_data.json
    {
        "name": "HTTP Protocol Adapter 2",
        "image": "platonam/lopco-http-protocol-adapter-2:dev",
        "data_cache_path": "/data_cache",
        "description": "Upload files via HTTP.",
        "configs": {
            "LOG_LVL": "1"
        },
        "ports": [
            {
                "port": 80,
                "protocol": "tcp"
            }
        ]
    }

    curl \
    -d @pa_data.json \
    -H 'Content-Type: application/json' \
    -X POST http://<host>/protocol-adapters
    {
        "resource": "e8ec7744-3f9a-4c6f-980f-4ec9e6808150"
    }

----

#### /protocol-adapters/{protocol-adapter-id}

**GET**

_Retrieve protocol-adapters data._

    # Example

    curl http://<host>/protocol-adapters/e8ec7744-3f9a-4c6f-980f-4ec9e6808150
    {
        "name": "HTTP Protocol Adapter 2",
        "image": "platonam/lopco-http-protocol-adapter-2:dev",
        "data_cache_path": "/data_cache",
        "description": "Upload files via HTTP.",
        "configs": {
            "LOG_LVL": "1"
        },
        "ports": [
            {
                "port": 80,
                "protocol": "tcp"
            }
        ]
    }

**PUT**

_Update a protocol-adapter._

    # Example

    cat pa_data.json
    {
        "name": "HTTP Protocol Adapter 2",
        "image": "platonam/lopco-http-protocol-adapter-2:dev",
        "data_cache_path": "/data_cache",
        "description": "Upload files via HTTP.",
        "configs": {
            "LOG_LVL": "1",
            "TIMEOUT": "60"
        },
        "ports": [
            {
                "port": 80,
                "protocol": "tcp"
            }
        ]
    }

    curl \
    -d @pa_data.json \
    -H 'Content-Type: application/json' \
    -X PUT http://<host>/protocol-adapters/e8ec7744-3f9a-4c6f-980f-4ec9e6808150

**DELETE**

_Remove a protocol-adapter_

    # Example

    curl -X DELETE http://<host>/protocol-adapters/e8ec7744-3f9a-4c6f-980f-4ec9e6808150
