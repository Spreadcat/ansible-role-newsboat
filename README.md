# spreadcat.newsboat

A Role that installs [newsboat][#newsboat] on the local system.

## Requirements

* The newsboat package must be either available through the package system or available on the [github][#github] repository.
* The role requires `gathered_facts: true` to be set.

## Role Variables

```yaml
newsboat_config: list
```

* List of entries for the configuration file for newsboat.

```yaml
newsboat_package_version: str
```

* Newsboat version to install as a package. Defaults to `newsboat_version`.

```yaml
newsboat_packages: list
```

* List of packages to install for newsboat.

```yaml
newsboat_urls: list
```

* List of URL entries for the newsboat URL file.

## Other Variables

```yaml
newsboat_build: dict
```

* Dictionary with packages to install when building newsboat from the URL sources.

```yaml
newsboat_directories: list
```

* List of directories required for newsboat to be installed.

```yaml
newsboat_download_url: str
```

* URL for downloading newsboat when using newsboat_install_type: url.

```yaml
newsboat_group: str
```

* Group-name of the group owning the newsboat configuration and URL files.

```yaml
newsboat_home: str
```

* Path to the home directory of the user running newsboat.

```yaml
newsboat_owner: str
```

* Username of the owner of the newsboat configuration and URL files.

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
