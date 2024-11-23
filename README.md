# ansible-pihole

An Ansible role to install Pi-hole on GNU/Linux systems.

## Credits

This `pihol` role was adapted from [danylomikula/ansible-pihole-cluster](https://github.com/danylomikula/ansible-pihole-cluster) and modified to integrate also the `pihole_updatelists` role and be a standalone role with minimal changes.

## Requirements

- Ansible 2.9 or higher
- Supported operating systems:
      - Debian
      - Ubuntu
      - Fedora
      - CentOS
      - RedHat
      - ArchLinux

## Role Variables

### Pi-hole initial configuration (`setupVars.conf`)

- `pihole_version`: Version of Pi-hole to install (default: `5.18.3`)
- `pihole_install_web_interface`: Install the web interface (default: `"true"`)
- `pihole_install_web_server`: Install the web server (default: `"true"`)
- `pihole_lighthttpd_enabled`: Enable Lighttpd (default: `"true"`)
- `pihole_privacy_level`: Privacy level (default: `"0"`)
- `pihole_interface`: Network interface to listen on (default: `"eth0"`)
- `pihole_query_logging`: Enable query logging (default: `"true"`)
- `pihole_dnsmasq_listening`: DNSMasq listening mode (default: `"all"`)
- `pihole_dns_1`: Primary DNS server (default: `"1.1.1.1"`)
- `pihole_dns_2`: Secondary DNS server (default: `"1.0.0.1"`)
- `pihole_fqdn_required`: Require FQDN (default: `"true"`)
- `pihole_bogus_priv`: Enable bogus private reverse lookups (default: `"true"`)
- `pihole_dns_cache_size`: DNS cache size (default: `"10000"`)
- `pihole_dnssec_enabled`: Enable DNSSEC support (default: `"false"`)
- `pihole_rev_server`: Enable DNS conditional forwarding (default: `false`)
- `pihole_rev_server_domain`: Conditional forwarding domain (default: `"pihole.local"`)
- `pihole_rev_server_target`: Conditional forwarding target (default: `"192.168.0.1"`)
- `pihole_rev_server_cidr`: Conditional forwarding CIDR (default: `"192.168.0.0/24"`)

### Pi-hole general configuration (`pihole-FTL.conf`)

- `pihole_webpassword`: Web interface password (default: `"changeme"`)
- `pihole_rate_limit`: Rate limit (default: `"1000/60"`)
- `pihole_reply_when_busy`: Reply when busy (default: `"DROP"`)
- `pihole_block_icloud_pr`: Block iCloud Private Relay (default: `"true"`)
- `pihole_socket_listening`: Socket listening mode (default: `"all"`)
- `pihole_ptr`: PTR record (default: `"HOSTNAMEFQDN"`)

### Pi-hole IPv6 configuration

- `pihole_enable_ipv6_support`: Enable IPv6 support (default: `false`)

### Pi-hole Update Lists configuration

- `pihole_updatelists_enable`: Enable pihole-updatelists (default: `true`)
- `pihole_updatelists_adlists_url`: URL for adlists (default: `"https://v.firebog.net/hosts/lists.php?type=nocross"`)
- `pihole_updatelists_whitelist_url`: URL for whitelist (default: `"https://raw.githubusercontent.com/anudeepND/whitelist/master/domains/whitelist.txt"`)
- `pihole_updatelists_regex_blacklist_url`: URL for regex blacklist (default: `"https://raw.githubusercontent.com/mmotti/pihole-regex/master/regex.list"`)
- `pihole_updatelists_regex_whitelist_url`: URL for regex whitelist (default: `"https://raw.githubusercontent.com/mmotti/pihole-regex/master/whitelist.list"`)
- `pihole_updatelists_update_gravity`: Update gravity after lists update (default: `false`)

## Dependencies

None

## Example Playbook

### How to include the role into a project

To include the `ansible-pihole` role in your project, add the following to your `requirements.yml` file:

```yaml
- src: https://github.com/mmassari/ansible-pihole.git
        scm: git
        version: master
        name: pihole
```

Then, run the following command:

```bash
ansible-galaxy install -r requirements.yml
```

### How to use the role in a playbook

```yaml
- hosts: all
    roles:
        - role: pihole
            vars:
                pihole_version: "5.18.3"
                pihole_install_web_interface: "true"
                pihole_install_web_server: "true"
                pihole_lighthttpd_enabled: "true"
                pihole_privacy_level: "0"
                pihole_interface: "eth0"
                pihole_query_logging: "true"
                pihole_dnsmasq_listening: "all"
                pihole_dns_1: "1.1.1.1"
                pihole_dns_2: "1.0.0.1"
                pihole_fqdn_required: "true"
                pihole_bogus_priv: "true"
                pihole_dns_cache_size: "10000"
                pihole_dnssec_enabled: "false"
                pihole_rev_server: false
                pihole_rev_server_domain: "pihole.local"
                pihole_rev_server_target: "192.168.0.1"
                pihole_rev_server_cidr: "192.168.0.0/24"
                pihole_webpassword: "changeme"
                pihole_rate_limit: "1000/60"
                pihole_reply_when_busy: "DROP"
                pihole_block_icloud_pr: "true"
                pihole_socket_listening: "all"
                pihole_ptr: "HOSTNAMEFQDN"
                pihole_enable_ipv6_support: false
                pihole_updatelists_enable: true
                pihole_updatelists_adlists_url: "https://v.firebog.net/hosts/lists.php?type=nocross"
                pihole_updatelists_whitelist_url: "https://raw.githubusercontent.com/anudeepND/whitelist/master/domains/whitelist.txt"
                pihole_updatelists_regex_blacklist_url: "https://raw.githubusercontent.com/mmotti/pihole-regex/master/regex.list"
                pihole_updatelists_regex_whitelist_url: "https://raw.githubusercontent.com/mmotti/pihole-regex/master/whitelist.list"
                pihole_updatelists_update_gravity: false
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Copyright

© 2023 Marco Massari Calderone <marco@marcomc.com>. All rights reserved.
