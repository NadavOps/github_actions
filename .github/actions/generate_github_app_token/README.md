# Usage Example
# Currently support only contents read permissions

```yml
name: "Test workflow that will make use of the action"

on:
  workflow_dispatch:

jobs:
  generate_token_action:
    runs-on: ubuntu
    steps:
    - name: Generate token using github helper app
      id: generate_token_using_github_helper_app
      uses: NadavOps/github_actions/.github/actions/generate_github_app_token@master
      with:
        github_app_id: "change_github_app_id"
        github_app_installation_id: "change_github_app_installation_id"
        github_app_private_key: ${{ secrets.CHANGE_GITHUB_APP_PRIVATE_KEY }}
        repo_name_for_token_authorization: "change_name_of_the_repo_which_the_token_is_being_generated_to"

    - name: Using token for clone repo
      run: |
        short_lived_access_token="${{ steps.generate_token_using_github_helper_app.outputs.short_lived_access_token }}"
        git clone "https://$short_lived_access_token:$short_lived_access_token@github.com/NadavOps/github_actions.git" test_repo
        ls -lah
        ls -lah test_repo
```