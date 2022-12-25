ansible-role-macos-homebrew
===========================

A role to add homebrew taps and install/update formulae and casks.

Requirements
------------

macOS as running operating system and homebrew installed.

Role Variables
--------------

| Variable                | Description               |
|-------------------------|---------------------------|
| macos_homebrew_taps     | List of homebrew taps     |
| macos_homebrew_formulae | List of homebrew formulae |
| macos_homebrew_casks    | List of homebrew casks    |

Format for homebrew taps
------------------------

One object per tap with just the name.

Example:
```yaml
- { name: "<cask-name>" }
```

Format for homebrew formulae
----------------------------

One object per formulae with the **name**, state and install_options. Refer to the documentation of **community.general.homebrew** for possible paramters. Setting state to "absent" will make sure the formulae is not installed.

Defaults:
- **state**: "latest"
- **install_options**: ""

Example:
```yaml
- { name: "<formulae-name>"}
- { name: "<formulae-name>", state: "<state>", install_options: "<install_options>" }
```

Format for homebrew casks
-------------------------

One object per cask with the **name**, state, install_options and greedy. Refer to the documentation of **community.general.homebrew** for possible paramters. Setting state to "absent" will make sure the cask is not installed.

Defaults:
- **state**: "latest"
- **install_options**: ""
- **greedy**: "yes"

Example:
```yaml
- { name: "<cask-name" }
- { name: "<cask-name>", state: "<state>", install_options: "<install_options>", greedy: "<greedy>" }
```

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - macos-homebrew
```

License
-------

MIT
