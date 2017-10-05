# Pip (Python Package Index)

Master: [![Build Status](https://travis-ci.org/ansible-lab/pip.svg?branch=master)](https://travis-ci.org/ansible-lab/pip)  
Develop: [![Build Status](https://travis-ci.org/ansible-lab/pip.svg?branch=develop)](https://travis-ci.org/ansible-lab/pip)

* [ansible.cfg](#ansiblecfg)
* [Installation and Dependencies](#installation-and-dependencies)
* [Tags](#tags)
* [Examples](#examples)
* [Dependencies](#dependencies)
* [License](#license)

This role installs [Pip](https://pip.pypa.io)

**Note** Supports Python 2 and 3


## ansible.cfg

This role is designed to work with merge "hash_behaviour". Make sure your
ansible.cfg contains these settings

```INI
[defaults]
hash_behaviour = merge
```


## Installation and Dependencies

To install run `ansible-galaxy install ansible-lab.pip` or add this to your
`roles.yml`

```YAML
- name: ansible-lab.pip
  version: v1.0
```

And run `ansible-galaxy install -p ./roles -r roles.yml`


## Tags

This role uses two tags: **build** and **configure**

* `build` - Installs Pip
* `configure` - Ensures `pip_packages` are installed



## Examples

To just install pip `playbook.yml`:

```YAML
- name: Python
  hosts: "{{ hosts }}"

  roles:
    - role: ansible-lab.pip
```

To install a list of required Pip packages

```YAML
- name: Python
  hosts: "{{ hosts }}"

  roles:
    - role: ansible-lab.pip
      pip_packages:
        # Specify names and versions
        - name: flask
          version: "0.12.2"
        # Or specify state (present, absent, latest, forcereinstall)
        - name: requests
          state: absent
        - name: django
          version: "1.11.5"
          state: forcereinstall
        # Packages to get the latest release
        - docker
```


## Dependencies

None


## License

MIT / BSD
