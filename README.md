# Customer API Integration

## Overview

Customer API Integration is a MuleSoft application built using API-led connectivity principles.  
It exposes RESTful services for managing customer data and integrates with backend systems such as databases and external API.

---

## Architecture

This project follows a layered API architecture:

- **Experience Layer** – Exposes REST endpoints to clients
- **Process Layer** – Handles business logic and orchestration
- **System Layer** – Connects to backend systems (Database, Salesforce, etc.)

---

## Project Structure

```
customer-api/
│
├── src/main/mule/                
├── src/main/resources/
│   ├── api/                       
│   ├── properties/                
│   │   ├── dev.yaml
│   │   ├── qa.yaml
│   │   └── prod.yaml
│
├── src/test/munit/                
├── pom.xml                        
└── README.md
```

---

## Prerequisites

- Anypoint Studio (latest version)
- Java 17
- Maven 3.8+
- Access to Anypoint Platform
- CloudHub or Runtime Fabric access (for deployment)

---

## Environment Configuration

Environment-specific configuration files are located in:

```
src/main/resources/properties/
```

Supported environments:
- `dev`
- `qa`
- `prod`

Sensitive values must be externalized using secure properties.  
Do not commit credentials to the repository.

---

## Running the Application Locally

1. Clone the repository:
   ```
   git clone <repository-url>
   ```

2. Open the project in Anypoint Studio.

3. Run the application:
   ```
   Run As → Mule Application
   ```

4. Access the API locally:
   ```
   http://localhost:8081/api/customers
   ```

---

## Testing

MUnit test cases are located in:

```
src/test/munit/
```

Run tests using:

```
mvn clean test
```

Code coverage thresholds are enforced via CI pipeline.

---

## Deployment

### CloudHub Deployment

Deploy using Maven:

```
mvn clean deploy -Dmule.env=dev
```

Supported deployment environments:
- Dev
- QA
- Production

Production deployments require version tagging.

---

## CI/CD

The CI pipeline includes:

- Maven build validation
- MUnit test execution
- Code coverage checks
- Artifact packaging
- Deployment to target environment

Merges to the `main` branch trigger automated deployment workflows.

---

## Branching Strategy

This project follows a Feature Branch workflow:

- `main` → Production-ready code
- `feature/*` → New feature development
- `hotfix/*` → Production fixes

Pull Requests are mandatory before merging into `main`.

---

## Logging & Monitoring

- Logging is configured using Log4j2.
- Global error handling is implemented.
- Logs are monitored via CloudHub dashboard.

---

## Security

- Secrets are managed using secure properties.
- HTTPS is enforced for all endpoints.
- No credentials are stored in source control.

---

## Versioning

This project follows Semantic Versioning:

```
MAJOR.MINOR.PATCH
```

Example:
```
v1.0.0
```

Tags must be created for production releases.

---

## Maintainers

Integration Team  
integration-team@company.com

---


