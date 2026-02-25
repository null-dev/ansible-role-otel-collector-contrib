# Ansible Role: otel_collector_contrib

An Ansible role that installs and configures the OpenTelemetry Collector (contrib distribution).

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

### `otel_collector_contrib_version`
The [version](https://github.com/open-telemetry/opentelemetry-collector-contrib/releases) of the OpenTelemetry Collector (contrib distribution) to install.
Default: `"0.146.0"`

### `otel_collector_contrib_state`
The state of the installation. Can be `present` or `absent`.
Default: `"present"`
**Note:** When set to `absent`, the OpenTelemetry Collector is uninstalled, but the `otelcol-contrib` user and group are preserved.

### `otel_collector_contrib_install_method`
The installation method to use. This is automatically detected based on the OS family, but can be overridden.
- `deb`: Use `.deb` package (Debian/Ubuntu)
- `rpm`: Use `.rpm` package (RedHat/CentOS/Fedora)
- `pacman`: Build from source via PKGBUILD (Arch Linux)
- `binary`: Download binary and install systemd service (Other Linux distributions)

### `otel_collector_contrib_arch`
The architecture to install. Automatically detected.
Default: `amd64` or `arm64` based on system architecture.

### `otel_collector_contrib_user`
The system user to run the collector as.
Default: `"otelcol-contrib"`

### `otel_collector_contrib_service_name`
The name of the systemd service.
Default: `"otelcol-contrib"`

### `otel_collector_contrib_config`
The configuration for the OpenTelemetry Collector. This is a dictionary that maps directly to the collector's YAML configuration.
Default: A basic configuration with OTLP receivers (gRPC/HTTP), batch processor, and debug exporter. See [defaults/main.yml](defaults/main.yml) for the full default configuration.

## Supported Platforms

This role is supported on most systemd-based distributions.
The installation method is automatically detected based on the distribution, see: [`otel_collector_contrib_install_method`](#otel_collector_contrib_install_method).

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: otel_collector_contrib
      vars:
        otel_collector_contrib_version: "0.146.0"
```

## License

MIT
