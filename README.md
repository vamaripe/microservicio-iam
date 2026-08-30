# microservicio-iam

Ejecutar contrato.

```
.\mvnw.cmd -pl contracts generate-sources
```

Compilamos proyecto 

```
cd "c:\Users\mvale\Desktop\reporteQa\design-software-iam-service"
mvn package
```

Asignamos variables de entorno localmente

```
$env:IAM_DB_DSN="jdbc:postgresql://localhost:5432/design-software-develop"
$env:IAM_DB_USERNAME="design_software_user"
$env:IAM_DB_PASSWORD="contrasena"
```
Corremos la api

```
cd "c:\Users\mvale\Desktop\reporteQa\design-software-iam-service"
mvn -pl iam-api spring-boot:run
````
Levantamos la bd 

```
cd "c:\Users\mvale\Desktop\reporteQa\docker-infra"
Copy-Item .env.develop .env
docker compose --env-file .env.develop up -d postgres
```

Limpiamos 
```
docker compose -p design-software-db down --volumes --remove-orphans
docker compose -p design-software-db up -d postgres
docker compose -p design-software-db --profile tooling run --rm liquibase-iam validate
docker compose -p design-software-db --profile tooling run --rm liquibase-iam update
```
