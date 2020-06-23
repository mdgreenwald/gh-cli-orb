# gh-cli-orb
Install and configure the GitHub command-line interface (gh)

## Usage

See [this orb's listing in CircleCI's Orbs Registry](https://circleci.com/orbs/registry/orb/mdgreenwald/gh-cli) for details on usage, or see below example:

## Example

In this example `config.yml` snippet, the required GitHub secret (GitHub Token) is stored, via [Contexts](https://circleci.com/docs/2.0/contexts), as environment variables in the `ci` context and then read as default parameter values by the `gh-cli/install` command.

```yaml
  version: 2.1

  orbs:
    gh-cli: mdgreenwald/gh-cli@x.y

  jobs:
    gh-cli-example:
      executor: gh-cli/default
      steps:
        - checkout
        - gh-cli/install:
            version: latest
        - run: echo "Run your code here"

  workflows:
    gh-cli:
      jobs:
        - gh-cli-example:
            context: ci
```