# Graph-tree storage

## Goal:
Create Graph-tree storage with API interface that implements 2 features inserting graphs nodes and getting graphs by any node.

The application should give the ability to add one or more nodes with specified in them parents and to build from them chains.

For any of the nodes can obtain the set of chains which pass through this vertex

## Tech stack:
You can use any python framework and library what you want.

Storage should be any **relational** database.

The speed of work will not be evaluated only code quality, best practice and correct work of application 


## Inserting nodes:

This call adds the nodes to database 

## POST /nodes

### Body:
```
{
    "nodes": [
        {
            "id": "ea846905f2a146c0acdfb48b4b79ff4a",
            "parent": "eb17b279d87c46c090dec77564d28ebf"
        },
        {
            "id": "eb17b279d87c46c090dec77564d28ebf",
            "parent": null
        }
    ]
}
```
### Schema:
```
{
    "type": "object",
    "properties": {
        "nodes": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "id": {
                        "type": "string"
                    },
                    "parents": {
                        "type": "string"
                    }
                }
            }
        }
    }
}
```

### Response:
## 201
```
{}
```
### Validation:
If some of node already exist just update it with new relation

### Loop:
The system should not to allow create loops in the chains


## GET /threes/:node_id

Return list of trees that related to this node id

### Response:
## 200

```
{
    "trees": [
        ["eb17b279d87c46c090dec77564d28ebf", "ea846905f2a146c0acdfb48b4b79ff4a"]
    ]
}
```

[Examples](EXAMPLES.md)
