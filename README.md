# Create PR on Dependent Project Action

This GitHub Action is designed to automate the process of creating a pull request in a dependent project's repository when a new release is made in a library. It updates the library version in the dependent project's `package.json` and generates a pull request with these changes.

## Inputs

- `libraryName`: The name of the library (e.g., `gisce/commitlint-rules`). This is used to identify which library's version needs to be updated in the dependent project.
- `dependentProject`: The GitHub repository name of the dependent project (e.g., `gisce/ooui.js`).
- `dependentProjectBranch`: The branch name in the dependent project repository where the changes will be made (e.g., `alpha`).
- `tagName`: The tag name of the release (e.g., `v1.0.0-alpha.0`). This is used to update the library version in the dependent project.

## Usage

To use this action, include it in your workflow configuration file. Here's an example of how to set it up:

```yaml
name: Your Workflow Name
on:
  release:
    types: [published]
  workflow_dispatch:

jobs:
  update-dependent-project:
    uses: gisce/create-update-version-pr
    with:
      libraryName: "your-library-name"
      dependentProject: "your-dependent-project"
      dependentProjectBranch: "your-branch"
      tagName: ${{ github.event.release.tag_name }}
```

## Additional information

- This action checks out the dependent project repository, updates the library version in `package.json`, and creates a pull request with these changes.
- Make sure that the `GH_PAT` (GitHub Personal Access Token) is set in your repository secrets with appropriate permissions to create pull requests.
- This action is designed to be triggered on a release event or manually via `workflow_dispatch`.

## Contributing

If you have suggestions for how this action could be improved, or want to report a bug, please open an issue or a pull request.

## License

MIT



