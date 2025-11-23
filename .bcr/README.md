# Bazel Central Registry Publishing Configuration

This directory contains the configuration files for publishing brotli to the Bazel Central Registry (BCR).

## Files

- **config.yml**: Configuration file for publish-to-bcr (using defaults)
- **metadata.template.json**: Metadata about the brotli module including homepage, maintainers, and repository location
- **presubmit.yml**: BCR CI configuration that defines build and test tasks to validate the module
- **source.template.json**: Template for generating source archive URLs for releases

## Setup (One-time)

Before you can publish to BCR, you need to set up the following:

1. **Fork the Bazel Central Registry**
   - Fork https://github.com/bazelbuild/bazel-central-registry to your GitHub account

2. **Create a Personal Access Token**
   - Go to GitHub Settings > Developer settings > Personal access tokens > Tokens (classic)
   - Click "Generate new token (classic)"
   - Select scopes: `repo` and `workflow`
   - Generate the token and copy it

3. **Add the token to repository secrets**
   - Go to the brotli repository Settings > Secrets and variables > Actions
   - Click "New repository secret"
   - Name: `BCR_PUBLISH_TOKEN`
   - Value: Paste the token from step 2
   - Click "Add secret"

## Publishing Process

To publish a new version to BCR:

1. Create a GitHub release with a tag (e.g., `v1.2.1`)
2. Go to the Actions tab in GitHub
3. Select the "Publish to BCR" workflow
4. Click "Run workflow"
5. Enter the release tag name (e.g., `v1.2.1`)
6. Click "Run workflow"

The workflow will automatically create a pull request to the Bazel Central Registry.

## References

- [Bazel Central Registry](https://github.com/bazelbuild/bazel-central-registry)
- [publish-to-bcr Documentation](https://github.com/bazel-contrib/publish-to-bcr)
- [Bzlmod User Guide](https://bazel.build/external/module)
