# Hitch GitHub Actions

Reusable GitHub Actions workflows for Hitch applet deployments.

Generated Hitch workspaces call `.github/workflows/deploy.yml` by its approved
commit SHA. The workflow uses GitHub OIDC and requires no Hitch repository
secret.

Hitch verifies the workflow path and `job_workflow_sha` claim before it accepts
a deployment.
