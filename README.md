# node_exporter

This role installs Prometheus' [Node exporter](https://github.com/prometheus/node_exporter) on Linux hosts, and configures a systemd unit file so the service can run and be controlled by systemd.

## Requirements

Systemd or openrc init system.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

    node_exporter_version: 'v1.10.2'

The version of Node exporter to install. Available releases can be found on the [tags](https://github.com/prometheus/node_exporter/tags) listing in the Node exporter repository.

If you change the version, the `node_exporter` binary will be replaced with the updated version, and the service will be restarted.

    node_exporter_arch: 'amd64'
    node_exporter_download_url: https://github.com/prometheus/node_exporter/releases/download/v{{ node_exporter_version }}/node_exporter-{{ node_exporter_version }}.linux-{{ node_exporter_arch }}.tar.gz

The architecture and download URL for Node exporter.

    node_exporter_bin_path: /usr/local/bin/node_exporter

The path where the `node_exporter` binary will be installed.

    node_exporter_host: 'localhost'
    node_exporter_port: 9100

Host and port on which node exporter will listen.

    node_exporter_options: ''

Any additional options to pass to `node_exporter` when it starts, e.g. `--no-collector.wifi` if you want to ignore any WiFi data.

    node_exporter_state: started
    node_exporter_enabled: true

Controls for the `node_exporter` service.

## Dependencies

None.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: all
      roles:
        - role: wittdennis.node_exporter

## License

MIT
