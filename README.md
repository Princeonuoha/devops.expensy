💰 Expensy | Cloud-Native Expense TrackerExpensy is a high-performance, full-stack expense tracking suite. Engineered with a microservices mindset, it leverages Redis caching, MongoDB persistence, and Prometheus monitoring, all orchestrated within a robust Kubernetes environment.🏗️ System ArchitectureExpensy follows a modern cloud-native flow designed for high availability and observability.Code snippetgraph TD
    User((User)) --> Ing[Azure Ingress]
    Ing --> Front[Next.js Frontend]
    Front --> Back[Express API]
    Back --> Cache[(Redis Cache)]
    Back --> DB[(MongoDB)]
    Back --> Prom[Prometheus Metrics]
    Prom --> Graf[Grafana Dashboard]
🚀 Tech StackLayerTechnologiesFrontendNext.js 14 (App Router), React 18, Tailwind CSS, RechartsBackendNode.js, Express, TypeScript, ioredis, prom-clientData & CacheMongoDB (Persistence), Redis (L1 Caching)InfrastructureDocker, Kubernetes (AKS), HelmCI/CDGitHub Actions, Docker HubObservabilityPrometheus, Grafana🛠️ Getting StartedLocal Development (Docker Compose)The quickest way to get the entire stack running locally:Bashdocker compose up --build
Frontend: http://localhost:3000Backend API: http://localhost:8706Metrics: http://localhost:8706/metricsKubernetes DeploymentTo deploy the production-ready manifests to Azure Kubernetes Service (AKS):Bash# Apply all manifests in the student-prince namespace
kubectl apply -f k8s/ -n student-prince

# Check deployment status
kubectl get pods -n student-prince -w
📈 Monitoring & ObservabilityWe don't just ship code; we monitor it. Expensy includes a built-in monitoring stack:Custom Metrics: Tracks total expenses recorded and MongoDB connection health.Prometheus: Scrapes the /metrics endpoint every 15s.Grafana: Visualizes request latency, 5xx errors, and system resource usage.📑 API ReferenceMethodEndpointDescriptionCacheGET/api/expensesFetch all records✅ 5 minPOST/api/expensesAdd new record🔄 InvalidatesGET/metricsPrometheus Export❌ N/A🔒 Security ImplementationsSecrets Management: Sensitive URIs and passwords are moved out of code into Kubernetes Secrets.Namespace Isolation: Resources are scoped to specific namespaces to prevent cross-app interference.CI/CD Hardening: Uses GitHub Encrypted Secrets for Docker Hub and Azure credentials.🛤️ Roadmap[ ] HPA: Implement Horizontal Pod Autoscaling based on CPU/RAM.[ ] Vault: Integrate Azure Key Vault for enterprise-grade secret management.[ ] Tracing: Add OpenTelemetry/Jaeger for distributed request tracing.👤 AuthorPrince OnuohaDevOps Engineer | Cloud Infrastructure | Kubernetes Specialist"Automating the world, one manifest at a time."Would you like me to generate a CONTRIBUTING.md or a SECURITY.md file to go along with this?