# microservicio-iam

Levantamos la bd 

```
cd "c:\Users\mvale\Desktop\reporteQa\design-software-iam-db"
docker compose up --build -d
```

Ejecutar contrato.

```
cd "C:\Users\mvale\Desktop\reporteQa\design-software-iam-service"
.\mvnw.cmd -pl contracts generate-sources
```

Compilamos proyecto 

```
cd "c:\Users\mvale\Desktop\reporteQa\design-software-iam-service"
mvn package
```

Asignamos variables de entorno localmente

```
cd "C:\Users\mvale\Desktop\reporteQa\design-software-iam-service"

$env:IAM_DB_DSN="jdbc:postgresql://localhost:5446/iam_db"
$env:IAM_DB_USERNAME="postgres"
$env:IAM_DB_PASSWORD="postgres"

mvn -pl iam-api spring-boot:run
```

Corremos la api

```
cd "c:\Users\mvale\Desktop\reporteQa\design-software-iam-service"
mvn -pl iam-api spring-boot:run
````
