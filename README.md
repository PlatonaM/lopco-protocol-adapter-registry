#### /protocol-adapters

**GET**

_List protocol-adapter IDs._

    # Example

    curl http://host:8000/protocol-adapter-registry/protocol-adapters
    [
        "5e674298-49d5-4723-926c-cf062dd9c141"
    ]

**POST**

_Add new protocol-adapter._

    # Example

    cat pa_data.json
    {
        "name": "HTTP Protocol Adapter",
        "description": null,
        "image": "http-adapter",
        "data_cache_path": "/data_cache",
        "configs": {
            "CONF_LOGGER_LEVEL": "debug"
        },
        "ports": {
            "80": {
                "protocol": "tcp",
                "host_interface": null,
                "host_ports": 7000
            }
        }
    }

    curl \
    -d @pa_data.json \
    -H 'Content-Type: application/json' \
    -X POST http://host:8000/protocol-adapter-registry/protocol-adapters
    {
        "resource": "5e674298-49d5-4723-926c-cf062dd9c141"
    }

----

#### /protocol-adapters/{protocol-adapter-id}

**GET**

_Retrieve protocol-adapters data._

    # Example

    curl http://host:8000/protocol-adapter-registry/protocol-adapters/5e674298-49d5-4723-926c-cf062dd9c141
    {
        "name": "HTTP Protocol Adapter",
        "description": null,
        "image": "http-adapter",
        "data_cache_path": "/data_cache",
        "configs": {
            "CONF_LOGGER_LEVEL": "debug"
        },
        "ports": {
            "80": {
                "protocol": "tcp",
                "host_interface": null,
                "host_ports": 7000
            }
        }
    }

**PUT**

_Update a protocol-adapter._

    # Example

    cat pa_data.json
    {
        "name": "HTTP Protocol Adapter",
        "description": null,
        "image": "http-adapter",
        "data_cache_path": "/data_cache",
        "configs": {
            "CONF_LOGGER_LEVEL": "info"
        },
        "ports": {
            "80": {
                "protocol": "tcp",
                "host_interface": null,
                "host_ports": 7000
            }
        }
    }

    curl \
    -d @pa_data.json \
    -H 'Content-Type: application/json' \
    -X PUT http://host:8000/protocol-adapter-registry/protocol-adapters/5e674298-49d5-4723-926c-cf062dd9c141

**DELETE**

_Remove a protocol-adapter_

    # Example

    curl -X DELETE http://host:8000/protocol-adapter-registry/protocol-adapters/5e674298-49d5-4723-926c-cf062dd9c141
