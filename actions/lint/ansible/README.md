# ansible

Lint Ansible content (playbooks, roles, collections) with
[ansible-lint](https://github.com/ansible/ansible-lint). Wraps the official
[`ansible/ansible-lint`](https://github.com/ansible/ansible-lint) action and
pins its version centrally so consumer repositories bump it in one place.

ansible-lint auto-discovers a `.ansible-lint` config in the working directory;
use it to set the profile and rule selection per repo.

## Usage

```yaml
steps:
  - uses: actions/checkout@v4
  - uses: sophotechlabs/reusable-actions/actions/lint/ansible@v0.1.0
```

### Install collection/role dependencies first

```yaml
steps:
  - uses: actions/checkout@v4
  - uses: sophotechlabs/reusable-actions/actions/lint/ansible@v0.1.0
    with:
      requirements_file: requirements.yml
      args: --profile production
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `args` | Arguments passed to ansible-lint (paths, `--profile`, …) | No | |
| `requirements_file` | `requirements.yml` to install roles/collections before linting | No | |
| `working_directory` | Directory to run ansible-lint from | No | _(workspace root)_ |
| `setup_python` | Set up Python (`false` uses the runner's) | No | `true` |
| `python_version` | Python version when `setup_python` is true | No | `3.14` |
| `override_version` | ansible-lint branch/tag/commit to install | No | _(action default)_ |
