# microservicio-iam

HU-07

Levantamos la bd. 

```
cd "c:\Users\mvale\Desktop\reporteQa\design-software-iam-db"
docker compose up --build -d
```

Compilamos proyecto y generamos contratos automáticamente

```
cd "c:\Users\mvale\Desktop\reporteQa\design-software-iam-service"
mvn clean install -DskipTests
```

Generar clave solo si no existe.

```
openssl genpkey -algorithm RSA -pkeyopt rsa_keygen_bits:2048 -out iam-dev-key.pem
```

Asignamos variables de entorno localmente

```
cd "C:\Users\mvale\Desktop\reporteQa\design-software-iam-service"

$env:IAM_DB_DSN="jdbc:postgresql://localhost:5446/iam_db"
$env:IAM_DB_USERNAME="postgres"
$env:IAM_DB_PASSWORD="postgres"

$env:IAM_JWT_PRIVATE_KEY = Get-Content ".\iam-dev-key.pem" -Raw
$env:IAM_JWT_ISSUER = "design-software-iam"
$env:IAM_JWT_KEY_ID = "iam-rsa-1"

mvn -pl iam-api spring-boot:run
```

Corremos la api

```
cd "c:\Users\mvale\Desktop\reporteQa\design-software-iam-service"
mvn -pl iam-api spring-boot:run
````
o

```
cd "C:\Users\mvale\Desktop\reporteQa\design-software-iam-service\iam-api"
mvn spring-boot:run
```
