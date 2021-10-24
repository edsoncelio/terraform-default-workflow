# terraform-default-workflow
Terraform workflow to be reused in your project, with commom Terraform steps and static analysis with [tfsec](https://github.com/aquasecurity/tfsec).

## Actions
* https://github.com/marketplace/actions/hashicorp-setup-terraform
* https://github.com/marketplace/actions/run-tfsec-pr-commenter



## How it works

This workflow will setup a CI with the following jobs (and steps):

### `jobs_teraform`
A job triggered at all `push` events with the steps:
* checkout the code
* setup Terraform
* Run Terraform fmt
* Run Terraform init
* Run Terraform validate

### `jobs_tfsec`
A job triggered at all `pull_request` events with the steps:
* checkout the code
* setup tfsec
* run checkcov static analysis
* If a vulnerability is found, create a comment in PR


## Inputs

* `command_wrk_dir`: Working dir (optional, type: string, default: `'./'`)
* `command_continue_on_error`: If a job will continue on error (optional, type: boolean, default: `false`)
* `tf_version`: Terraform version (optional, type: string, default: `1.0.0`)
* `tf_wrapper`: If will use the Terraform wrapper (toptional, ype: boolean, default: `false`)
* `token`: Github secret token, available by default (type: secret, required)

If you want override the defaults Terraform commands, you can use:
* `tf_command_fmt`: Terraform fmt command (optional, type: string, default: `'terraform fmt -check'`)
* `tf_command_init`: Terraform init command (optional, type: string, default: `'terraform init'`)
* `tf_command_validate`: Terraform validate command (optional, type: string, default: `'terraform validate -no-color'`)



## Usage
In your caller workflow, first set your trigger (see the [docs](https://docs.github.com/en/actions/learn-github-actions/events-that-trigger-workflows))

Calling the workflow with all the default inputs:
```
...

jobs:
  my-terraform-workflow:
    uses: edsoncelio/terraform-default-workflow/.github/workflows/terraform.yml@v2
    secrets:
        token: ${{ secrets.GITHUB_TOKEN }}
```
And with customized inputs:
```
...

jobs:
  my-terraform-workflow:
    uses: edsoncelio/terraform-default-workflow/.github/workflows/terraform.yml@v2
    with:
        command_wrk_dir: './infra-code-dir'
    secrets:
        token: ${{ secrets.GITHUB_TOKEN }}
```


## Contributing
Just open a PR or issue :D

## License
Distributed under the MIT License. See `LICENSE` for more information.
