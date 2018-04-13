# Bash-YAML
[![GitHub license](https://img.shields.io/github/license/ArtBIT/bash-yaml.svg)](https://github.com/ArtBIT/bash-yaml) [![GitHub stars](https://img.shields.io/github/stars/ArtBIT/bash-yaml.svg)](https://github.com/ArtBIT/bash-yaml)  [![awesomeness](https://img.shields.io/badge/awesomeness-maximum-red.svg)](https://github.com/ArtBIT/bash-yaml)

Bash-YAML is a simple YAML parser.

# Installation
```
git clone https://github.com/ArtBIT/bash-yaml.git
source path/to/bash-yaml/src/yaml
```

# Usage

```bash
# Example:
# (Contents of example.yml)
# | some:
# |   deeply:
# |     nested:
# |       option: 1
#

cat example.yml | yaml_get_value some.deeply.nested.option
# Outputs 1
```

# License

[MIT](LICENSE.md)
