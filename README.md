# Hitch GitHub Actions

Reusable GitHub Actions workflows for Hitch applet deployments.

Generated Hitch workspaces call `.github/workflows/deploy.yml` by its approved
commit SHA. The workflow runs `applet deploy` through the SDK version pinned in
`hitch.config.ts`, and caches the pnpm store between runs. The SDK reads the
job's OIDC token, skips applets whose folder and shared files match the source
of their current release (from CI or a local `applet deploy`), then installs
once and builds and uploads the rest concurrently. The workflow requires no
Hitch repository secret.

Existing workspaces must remove `push.paths` from `.github/workflows/hitch.yml`
so changes to shared files trigger the job. Bootstrap preserves existing
workflow files.

Hitch verifies the workflow path and `job_workflow_sha` claim before it accepts
a deployment. Publish a workflow change to the public `hitch-42/actions`
repository, then pin its commit SHA in `GITHUB_DEPLOY_WORKFLOW_SHA`.
Ship the CI applet lookup route first, then the SDK. The new workflow requires
that SDK; publish and approve the workflow before updating workspace workflow pins.
