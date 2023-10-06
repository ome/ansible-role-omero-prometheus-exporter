OMERO Prometheus Exporter
=========================

[![Actions Status](https://github.com/ome/ansible-role-omero-prometheus-exporter/workflows/Molecule/badge.svg)](https://github.com/ome/ansible-role-omero-prometheus-exporter/actions)
[![Ansible Role](https://img.shields.io/ansible/role/41332.svg)](https://galaxy.ansible.com/ome/omero_prometheus_exporter/)

Configures services for exporting prometheus-compatible metrics from OMERO.server.
Uses the OMERO API, so can be run remotely from OMERO.
Requires the OMERO.server to be configured with a certificate

See https://github.com/ome/omero-prometheus-tools

Note: metric endpoints are not authenticated.


Role Variables
--------------

Required:

- `omero_prometheus_exporter_omero_user`: OMERO user (a read-only light admin)
- `omero_prometheus_exporter_omero_password`: OMERO user password

Optional:

- `omero_prometheus_tools_version`: version of the OMERO monitoring tool, default `0.2.3`
- `omero_prometheus_exporter_omero_host`: OMERO server, default `localhost`
- `omero_prometheus_exporter_system_user`: System account for running services
- `omero_prometheus_exporter_port`: Publish metrics on this port, default `9449`
- `omero_prometheus_exporter_interval`: Calculate metrics at this interval, default 60 seconds
- `omero_prometheus_exporter_counts_query_files`: List of query files for counts metrics, default is `[/opt/prometheus-omero-tools/venv3/etc/prometheus-omero-counts.yml]` which is included in omero-prometheus-tools


Example playbook
----------------

    - hosts: localhost
      roles:
      - role: ome.omero_prometheus_exporter
        omero_prometheus_exporter_omero_user: omero-monitoring
        omero_prometheus_exporter_omero_password: omero-monitoring
        omero_prometheus_exporter_omero_host: omero.example.org


Author Information
------------------

ome-devel@lists.openmicroscopy.org.uk
