# Neo4j with APOC Docker Setup

This project provides a Dockerized Neo4j instance with the APOC plugin included.

## Usage

### 1. Build the Docker image

```sh
docker build -t neo4j-with-apoc .
```

### 2. Run the container

```sh
docker run -d --name neo4j-apoc -p7474:7474 -p7687:7687 -e NEO4J_AUTH=neo4j/password neo4j-with-apoc
```

### 3. Verify APOC installation

In the Neo4j browser, run:

```cypher
RETURN apoc.version();
```

Delete schema

```cypher
CALL apoc.schema.assert({}, {}, true) YIELD label, key, keys, unique, action;
```

---

## Notes

- The `local-package/` directory contains custom scripts and the APOC jar.
- Default credentials are `neo4j/password` (change as needed).
- Ports 7474 (HTTP) and 7687 (Bolt) are exposed.
