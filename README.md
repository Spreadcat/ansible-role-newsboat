# spreadcat.newsboat

A Role that installs [newsboat][#newsboat] on the local system.

## Requirements

The newsboat package must be either available through the package system or available on the [github][#github] repository.

## Role Variables

```yaml
newsboat_config: []
```

* List with configuration settings for newsboat. Each line contains one configuration entry for the newsboat configuraiton file.

```yaml
newsboat_install_type: package
```

* String defining the install method to use. Valid values are `package` (default) and `url`.

```yaml
newsboat_urls: []
```

* List of URLs for newsboat to fetch RSS from. Each entry contains one line from the URL file.

## Other variables

```yaml
newsboat_build: {}
```

* Pre-set dictionary with dependencies for building [newsboat][#newsboat] from the source code.

```yaml
newsboat_download_url: 'https://github.com/newsboat/newsboat.git'
```

* String with the URL to the [newsboat][#github] repository. Required when `newsboat_install_type` has been setup to `url`.

```yaml
newsboat_group: "{{ lookup('env', 'USER') }}"
```

* String with the group of the owner of the newsboat configuration. Default is being set to the user running the newsboat playbook.

```yaml
newsboat_home: "{{ lookup('env', 'HOME') }}"
```

* String with the path to the home directory of the current user. Default is being set to the user running the newsboat playbook.

```yaml
newsboat_owner: "{{ lookup('env', 'USER') }}"
```

* String with the owner of the newsboat configuration. Default is being set to the user running the newsboat playbook.

```yaml
newsboat_packages:
  - name: newsboat
    state: present
```

* List of packackages to install from the package repository for newsboat.

```yaml
newsboat_package_version: "{{ newsboat_version }}"
```

* String that defines the package version to be installed.

```yaml
newsboat_version: 2.28
```

String to define the newsboat version to install.

## Dependencies

* none

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  vars:
    newsboat_config:
      - auto-reload no
      - cleanup-on-quit yes
    newsboat_urls:
      - 'http://githubengineering.com/atom.xml tech blog'
  roles:
     - role: spreadcat.newsboat
```

## Limitations

The role does not support installation using `snap`. While this is available it seems that docker/podman containers to not support the required squashfs dependency.

## License

BSD

## Author Information

This role is developed and maintained by DBV (github@micronarrativ.org).

[#newsboat]: https://newsboat.org/
[#github]: https://github.com/newsboat/newsboat
