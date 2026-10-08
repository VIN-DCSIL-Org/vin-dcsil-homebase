# Deployment Workflow

Our deployment strategy is split across three layers so the release is automated, repeatable, and easy to reason about. The application frontend is hosted on AWS Amplify, which gives us managed CI/CD for the user-facing build. When code is pushed to the connected branch or released through the repository workflow, Amplify handles the build-and-deploy cycle automatically, so the live web app stays in sync with the main codebase without manual publishing steps.

For the deployment pipeline itself, we use GitHub Actions to orchestrate the release process. The automation lives in [.github/workflows/terraform.yml](../.github/workflows/terraform.yml) and [.github/workflows/lambda-ecr.yml](../.github/workflows/lambda-ecr.yml), which keeps the process explicit and version-controlled. These workflows handle the infrastructure and image-deployment steps from the repository side so the application can move from source changes to an updated cloud environment in a predictable way.

Infrastructure is managed separately with Terraform, also driven through GitHub Actions. That keeps the cloud resources defined as code instead of being created or edited manually in a console. Terraform is used for the broader infrastructure layer, while Amplify focuses on the app delivery path. This separation makes the system easier to maintain because application releases and infrastructure changes are handled through the same automated workflow model, but with different responsibilities.

In practice, the flow is:

1. A change is merged or released in GitHub.
2. GitHub Actions runs the Terraform workflow when infrastructure changes are needed.
3. GitHub Actions runs the Lambda/ECR workflow to build and publish the container image.
4. Amplify rebuilds and deploys the live frontend automatically.

This setup gives us a production-friendly release path without hardcoding secrets or depending on manual steps. GitHub Secrets handle sensitive values, GitHub Actions provides the automation, Terraform keeps the infrastructure declarative, and Amplify supplies managed CI/CD for the live application.