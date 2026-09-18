# Hitch GitHub Actions

Reusable GitHub Actions workflows for Hitch applet deployments.

Generated Hitch workspaces call `.github/workflows/deploy.yml` by its approved
commit SHA. The workflow bootstraps the workspace with the SDK version pinned in
`hitch.config.ts`, then runs `applet deploy` in the workspace root. The SDK
reads the job's OIDC token, fetches the build inputs, builds every applet, and
uploads each release. The workflow requires no Hitch repository secret.

Hitch verifies the workflow path and `job_workflow_sha` claim before it accepts
a deployment. Publish a workflow change to the public `hitch-42/actions`
repository, then pin its commit SHA in `GITHUB_DEPLOY_WORKFLOW_SHA`.
