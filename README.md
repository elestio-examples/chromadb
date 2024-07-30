# ChromaDB on Elestio with CI/CD

<a href="https://dash.elest.io/deploy?source=cicd&social=dockerCompose&url=https://github.com/elestio-examples/postgres"><img src="deploy-on-elestio.png" alt="Deploy on Elest.io" width="180px" /></a>

Deploy ChromaDB server with CI/CD on Elestio

<img src="chromadb.png" style='width: 100%;'/>
<br/>
<br/>

# Once deployed ...

You can open ChromaDB here:

    URL: https://[CI_CD_DOMAIN]
    login: "admin"
    password: "[ADMIN_PASSWORD]"

You can open pgAdmin here:

    URL: "https://[CI_CD_DOMAIN]:12513"
    login: "[ADMIN_EMAIL]"
    password: "[ADMIN_PASSWORD]"

# ChromaDB API Usage Guide

This guide will help you create a collection, add text to a collection, and query the collection in ChromaDB using curl commands.

## Creating a Collection

Open your terminal.

Use the following curl command to create a collection:

    curl -X POST https://[CI_CD_DOMAIN]/api/v1/collections \
        -u root:[ADMIN_PASSWORD] \
        -H "Content-Type: application/json" \
        -d '{"name": "test_collection"}'

## Adding Text to a Collection

Once you have created a collection, you can add text to it. Use the following curl command to add text to your collection:

    curl -X POST https://[CI_CD_DOMAIN]/api/v1/collections/test_collection/items \
        -u root:[ADMIN_PASSWORD] \
        -H "Content-Type: application/json" \
        -d '{
            "texts": ["Your first text here","Your second text here"],
            "metadatas": [{"key": "value"}],
            "ids": ["id1", "id2"]
            }'

## Querying the Collection

To query the collection, use the following curl command:

    curl -X POST https://[CI_CD_DOMAIN]/api/v1/collections/test_collection/query \
        -u root:[ADMIN_PASSWORD] \
        -H "Content-Type: application/json" \
        -d '{
            "query_texts": ["Your query text here"],
            "n_results": 5
            }'

Additional Information
For more detailed information and advanced usage, refer to the <a href="https://docs.trychroma.com/getting-started" target="_blank">ChromaDB Documentation</a>.
