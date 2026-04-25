# Jenkins CI/CD with Maven & Master-Slave Architecture

A mini-project demonstrating a distributed CI/CD pipeline. The setup uses a Jenkins Master to manage jobs and a dedicated Linux Agent (Slave) to perform Maven builds.

## 🏗 Architecture
- **Jenkins Master:** Orchestrates builds, manages plugins, and schedules tasks.
- **Jenkins Slave:** Executes the pipeline stages (Build, Test, Package).
- **Maven:** Build automation tool for Java.
- **GitHub:** Version control and source code trigger via Webhooks.
