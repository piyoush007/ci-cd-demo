# ci-cd-demo

Jenkins + GitHub + Maven + Docker CI/CD demonstration project.

## Local test

```powershell
mvn clean test
mvn clean package
docker build -t ci-cd-demo:1.0 .
docker run -d --name ci-cd-demo -p 8080:8080 ci-cd-demo:1.0
```

Open http://localhost:8080
