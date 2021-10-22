# terraform-default-workflow
Terraform workflow to be reused in your project.

## Actions
* https://github.com/marketplace/actions/hashicorp-setup-terraform
* https://github.com/marketplace/actions/run-tfsec-pr-commenter


## Inputs
* `tf_version`: Terraform version (type: string, default: 1.0.0)]
* `tf_wrapper`: If will use the Terraform wrapper (type: boolean, default: `false`)

## Usage
In your caller workflow, first set your trigger (see the [docs](https://docs.github.com/en/actions/learn-github-actions/events-that-trigger-workflows))

Calling the workflow with all the default inputs:
```
...

jobs:
  my-terraform-workflow:
    uses: edsoncelio/terraform-default-workflow/.github/workflows/terraform.yml@v1
```

## Contributing
TODO

## License
Distributed under the MIT License. See `LICENSE` for more information.