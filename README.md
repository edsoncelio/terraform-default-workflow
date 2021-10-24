# terraform-default-workflow
Terraform workflow to be reused in your project.

## Actions
* https://github.com/marketplace/actions/hashicorp-setup-terraform
* https://github.com/marketplace/actions/run-tfsec-pr-commenter

**Disclaimer:** The tfsec commenter job will run ONLY in pull requests

## Inputs

* `command_wrk_dir`: Working dir (optional, type: string, default: `'./'`)
* `tf_version`: Terraform version (optional, type: string, default: `1.0.0`)
* `tf_wrapper`: If will use the Terraform wrapper (toptional, ype: boolean, default: `false`)
* `token`: Github secret token, available by default (type: secret, required)

If you want override the defaults Terraform commands, you can use:
* `tf_command_fmt`: Terraform fmt command (optional, type: string, default: `'terraform fmt -check'`)
* `tf_command_init`: Terraform init command (optional, type: string, default: `'terraform init'`)
* `tf_command_validate`: Terraform validate command (optional, type: string, default: `'terraform validate -no-color'`)
* `tf_command_plan`: Terraform plan command (optional, type: string, default: `'terraform plan -no-color'`)


## Usage
In your caller workflow, first set your trigger (see the [docs](https://docs.github.com/en/actions/learn-github-actions/events-that-trigger-workflows))

Calling the workflow with all the default inputs:
```
...

jobs:
  my-terraform-workflow:
    uses: edsoncelio/terraform-default-workflow/.github/workflows/terraform.yml@v1
    secrets:
        token: ${{ secrets.GITHUB_TOKEN }}
```

## Contributing
Just open a PR or issue :D

## License
Distributed under the MIT License. See `LICENSE` for more information.
