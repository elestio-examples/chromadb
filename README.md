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

Once you have created a collection, you can add text to it.

Before adding, you'll have to get the collection ID. You can list all collections with the following command and find the ID:

    curl -X 'GET' \
        'https://[CI_CD_DOMAIN]/api/v1/collections' \
        -u root:[ADMIN_PASSWORD] \
        -H 'accept: application/json'

Use the following curl command to add text to your collection:

    curl -X 'POST' \
        'https://[CI_CD_DOMAIN]/api/v1/collections/<COLLECTION_ID>/add' \
        -u root:[ADMIN_PASSWORD] \
        -H 'accept: application/json' \
        -H 'Content-Type: application/json' \
        -d '{
            "documents": [
                "This is a document about pineapple",
                "This is a document about oranges"
            ],
            "ids": [
                "id1", "id2"
            ]
         }'

Additional Information
For more detailed information and advanced usage, refer to the <a href="https://[CI_CD_DOMAIN]/docs" target="_blank">ChromaDB Documentation</a>.
