# Ansible Role: otel_collector_contrib

An Ansible role that installs and configures the OpenTelemetry Collector Contrib distribution.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
otel_collector_contrib_version: "0.119.0"
otel_collector_contrib_state: "present"
```

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  roles:
    - role: otel_collector_contrib
```

## License

MIT

## Author Information

This role was created in 2024.
