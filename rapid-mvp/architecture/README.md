# Architecture Release Manifest

This folder contains the release artifacts for the cloud-deployed version of the project. It documents how the system moved from a local prototype to a production-oriented release, how the deployment pipeline is structured, and what feedback-driven changes shaped the final architecture.

Live application: https://mvp.dm3yb2zf1rkq0.amplifyapp.com

## Artifact Index

- [reflections.md](reflections.md) - A synthesis of the A2 peer feedback and CUJ findings, with an explanation of how those inputs pushed the project from a local prototype toward a production-grade system.
- [workflow.md](workflow.md) - A technical summary of the deployment logic, including the relationship between AWS Amplify, GitHub Actions, and Terraform.
- [diagram.jpg](diagram.jpg) - The cloud architecture diagram for the release, using standard cloud architecture notation.
- [rationale.md](rationale.md) - Optional supporting rationale for the system topology, MVP scope, and future scalability path.

## Release Summary

The release is built around a simple but production-minded split of responsibilities. AWS Amplify handles the hosted frontend and provides managed CI/CD for the live application. GitHub Actions coordinates the repository-side automation, including the Terraform workflow for infrastructure changes and the Lambda/ECR workflow for image build and deployment steps. Terraform keeps the cloud infrastructure declarative and repeatable, while GitHub Secrets protect any sensitive values used by the workflows.

The goal of this release package is to make the system easy to review at a glance: the diagram shows the architecture, the workflow explains how deployment happens, and the reflections document shows how feedback and CUJ analysis shaped the final product direction.