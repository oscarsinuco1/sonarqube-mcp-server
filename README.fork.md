# SonarQube MCP Server - Branch Support Fork

Fork del [SonarQube MCP Server oficial](https://github.com/SonarSource/sonarqube-mcp-server) con soporte para consultar ramas específicas en todas las herramientas.

## ¿Qué cambia?

El servidor MCP oficial solo consulta la rama principal. Este fork añade el parámetro `branch` a las siguientes herramientas:

| Tool | Descripción |
|------|-------------|
| `search_sonar_issues_in_projects` | Buscar issues en una rama específica |
| `search_security_hotspots` | Buscar security hotspots por rama |
| `get_component_measures` | Obtener métricas (coverage, bugs, etc.) de una rama |
| `get_duplications` | Ver duplicaciones de código por rama |
| `search_duplicated_files` | Buscar archivos duplicados en una rama |
| `search_files_by_coverage` | Buscar archivos por cobertura en una rama |
| `get_file_coverage_details` | Detalles de cobertura línea por línea por rama |
| `get_raw_source` | Obtener código fuente de una rama |

## Uso

El parámetro `branch` es **opcional**. Simplemente puedes pedirlo en el chat:

> "Dame el coverage del proyecto X en la rama feature/mi-rama"

El agente enviará automáticamente el parámetro `branch` a SonarQube.

## Build local con Docker

```bash
docker build -f Dockerfile.local -t sonarqube-mcp-server:local .
```

## Configuración MCP

```json
{
  "servers": {
    "sonarqube": {
      "command": "docker",
      "args": [
        "run",
        "-i",
        "--rm",
        "-e",
        "SONARQUBE_TOKEN",
        "-e",
        "SONARQUBE_URL",
        "sonarqube-mcp-server:local"
      ],
      "env": {
        "SONARQUBE_TOKEN": "tu-token",
        "SONARQUBE_URL": "http://tu-sonarqube:9000"
      }
    }
  }
}
```

## Créditos

Basado en [SonarQube MCP Server](https://github.com/SonarSource/sonarqube-mcp-server) de SonarSource.
