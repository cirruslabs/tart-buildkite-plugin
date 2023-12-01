# Tart Buildkite Plugin

A [Buildkite plugin](https://buildkite.com/docs/plugins) for running pipeline steps in [Tart](https://github.com/cirruslabs/tart) Virtual Machines.

## Prequisites

This plugin assumes that your pipeline is running on an Apple Silicon host with [Tart](https://tart.run/) installed:

```
brew install cirruslabs/cli/tart
```

You'll also need to install the `sshpass` utility program, so that the plugin will be able to connect to the Tart VMs using password-based authentication:

```
brew install cirruslabs/cli/sshpass
```

## Example

Add the following to your `pipeline.yml`:

```yml
steps:
  - command: uname -a
    plugins:
      - cirruslabs/tart#v0.2.0:
          image: ghcr.io/cirruslabs/macos-sonoma-base:latest
```

## Configuration

### `image` (`string`, required)

Tart VM image to use.

### `ssh_username` (`string`, optional)

Username to use when connecting to the VM via SSH.

Defaults to `admin`.

### `ssh_password` (`string`, optional)

Password to use when connecting to the VM via SSH.

Defaults to `admin`.

### `headless` (`boolean`, optional)

Whether to run the VM in headless mode (`true`) or with GUI (`false`).

Defaults to `true`.

### `always_pull` (`boolean`, optional)

Whether to always pull the VM using `tart pull` before `tart clone` (`true`) or not (`false`).

Defaults to `true`.

### `softnet` (`boolean`, optional)

Whether to enable [software networking isolation for Tart](https://github.com/cirruslabs/softnet) (`true`) or not (`false`).

Defaults to `false`.
