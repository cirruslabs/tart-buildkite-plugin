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
      - cirruslabs/tart#v0.1.0:
          image: ghcr.io/cirruslabs/macos-sonoma-base:latest
```

## Configuration

### `image` (`string`, required)

Tart VM image to use.

### `ssh_username` (`string`, optional, defaults to `admin`)

Username to use when connecting to the VM via SSH.

### `ssh_password` (`string`, optional, defaults to `admin`)

Password to use when connecting to the VM via SSH.
