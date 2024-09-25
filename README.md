# uctl

[![Current Release](https://img.shields.io/github/release/unionai/uctl.svg)](https://github.com/unionai/uctl/releases/latest)
[![License](https://img.shields.io/badge/LICENSE-Apache2.0-ff69b4.svg)](http://www.apache.org/licenses/LICENSE-2.0.html)
[![Slack](https://img.shields.io/badge/slack-join_chat-white.svg?logo=slack&style=social)](https://slack.union.ai)

`uctl` is an enhanced version of `flytectl`, [the Flyte command-line tool](https://docs.flyte.org/en/latest/flytectl/docs_index.html),
that lets you manage not only Flyte entities (projects, domains, workflows, tasks, and launch plans)
but also Union-specific entities like users, roles, and Union configurations.

You can find full documentation [here](https://docs.union.ai/byoc/administration/uctl-cli).

## Installing `uctl`

To install `uctl`, you can use Homebrew on macOS or `curl` on macOS, Linux, or Windows.

To download manually, see the [`uctl` releases](https://github.com/unionai/uctl/releases).

### macOS

To use [Homebrew](https://brew.sh/), do this:

```shell
brew tap unionai/homebrew-tap
brew install uctl
```

If you already have `uctl` and want to upgrade to latest version:
```shell
brew update
brew upgrade uctl
```

To use `curl`, set `BINDIR` to the install location (it defaults to `./bin`) and run the following command:

```shell
curl -sL https://raw.githubusercontent.com/unionai/uctl/main/install.sh | bash
```

### Linux

To use `curl`, set `BINDIR` to the install location (it defaults to `./bin`) and run the following command:

```shell
curl -sL https://raw.githubusercontent.com/unionai/uctl/main/install.sh | bash
```

### Windows

To use `curl`, in a Linux shell (such as [WSL](https://learn.microsoft.com/en-us/windows/wsl/install)), set `BINDIR` to the install location (it defaults to `./bin`) and run the following command:

```shell
curl -sL https://raw.githubusercontent.com/unionai/uctl/main/install.sh | bash
```

## Configuring `uctl`

To configure `uctl` to connect to your Union instance, run the following command:

``` shell
uctl config init --host <union-host-url>
```

Where `<union-host-url>` is the URL of your Union instance.

This will create a new configuration file at `~/.union/config.yaml`:

```yaml
union:
  connection:
    host: dns:///<union-host-url>
    insecure: false
  auth:
    type: Pkce
admin:
  endpoint: dns:///<union-host-url>
  insecure: false
  authType: Pkce
```

The `uctl` CLI will use this configuration file to connect to your Union instance by default unless you override it.
The search order for finding the configuration file is:

* `--config <path-to-config>` flag.
* `UNION_CONFIG` environment variable: the same variable as used by the `union CLI`.
* `UCTL_CONFIG` environment variable: for backward compatibility with earlier versions of `uctl`.
* `~/.union/config.yaml`: the default, and the one created by the command above.
* `~/.uctl/config.yaml`: for backward compatibility with earlier versions of `uctl`.

For details on the parameters in the configuration file, see [CLI Authentication](https://docs.union.ai/byoc/administration/cli-authentication.html).

For details on the `union` CLI, see [union CLI](https://docs.union.ai/byoc/api/union-cli.html).
