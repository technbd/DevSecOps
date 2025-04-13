
## DevSecOps: 

DevSecOps stands for **Development, Security, and Operations**, and it integrates security practices within the DevOps process. In a DevSecOps model, security is considered everyone's responsibility, rather than just being the domain of a separate security team. The goal is to address security issues as early as possible in the development lifecycle, ensuring that code is secure before it's deployed to production.


These tools help integrate security into every stage — from writing code to deploying and monitoring applications.

1. Code Security (Static Application Security Testing - SAST)
Analyzes source code for vulnerabilities before it's compiled or run.

    - SonarQube – Detects bugs, code smells, and security vulnerabilities.
    - Checkmarx – Focuses on security analysis during code development.
    - Fortify Static Code Analyzer – Deep static analysis for many languages.
    - Semgrep – Lightweight, fast, customizable SAST.


2. Dependency/Software Composition Analysis (SCA)
Scans open-source libraries and dependencies for known vulnerabilities.
    - Snyk – Scans dependencies and suggests fixes.
    - WhiteSource (now Mend) – Identifies and remediates open-source risks.
    - OWASP Dependency-Check – Free tool to detect vulnerable components.
    - FOSSA – Focuses on license and vulnerability management.


3. CI/CD Pipeline Security
Integrates security testing into build and deployment pipelines.
    - GitLab CI/CD Security Features – Built-in security scanning.
    - Jenkins + Security Plugins – Plugins like OWASP Dependency-Check or Aqua Trivy.
    - CircleCI Orbs – Prebuilt security scanning configurations.
    - Azure DevOps Security Extensions – Microsoft and 3rd-party integrations.


4. Container & Image Scanning
Analyzes Docker images and containers for vulnerabilities.
    - Aqua Trivy – Simple and fast vulnerability scanner for containers.
    - Clair – Used by Red Hat Quay for image scanning.
    - Anchore Engine – Policy-based image scanning and enforcement.
    - Grype – Vulnerability scanner for container images and filesystems.


5. Infrastructure as Code (IaC) Security
Secures Terraform, CloudFormation, Kubernetes, etc.
    - Checkov – Scans Terraform, Kubernetes, and more for misconfigurations.
    - Terraform Sentinel – HashiCorp's policy-as-code tool.
    - Open Policy Agent (OPA) – Policy engine for Cloud-native environments.
    - Kics (Keep Infrastructure as Code Secure) – Scans IaC for security flaws.


6. Dynamic Application Security Testing (DAST)
Scans running applications for vulnerabilities.
    - OWASP ZAP (Zed Attack Proxy) – Open-source and beginner-friendly.
    - Burp Suite – Comprehensive web app security testing.
    - AppSpider – Automates dynamic scanning and testing.


7. Runtime & Cloud Security
Monitors live systems and infrastructure for threats.
    - Falco – Cloud-native runtime security tool.
    - Aqua Security – Full-stack container security.
    - Sysdig Secure – Kubernetes and container security at runtime.
    - Datadog Security Monitoring – Integrates security into observability.

