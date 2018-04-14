# Bash-YAML
[![Build Status](https://travis-ci.org/ArtBIT/bash-yaml.svg)](https://travis-ci.org/ArtBIT/bash-yaml) [![GitHub license](https://img.shields.io/github/license/ArtBIT/bash-yaml.svg)](https://github.com/ArtBIT/bash-yaml) [![GitHub stars](https://img.shields.io/github/stars/ArtBIT/bash-yaml.svg)](https://github.com/ArtBIT/bash-yaml)  [![awesomeness](https://img.shields.io/badge/awesomeness-maximum-red.svg)](https://github.com/ArtBIT/bash-yaml)

Bash-YAML is a simple YAML parser.

# Installation

## Manually
```
git clone https://github.com/ArtBIT/bash-yaml.git
source path/to/bash-yaml/src/yaml
```

## Using [bash-clam](https://github.com/ArtBIT/bash-clam)
```
clam install ArtBIT/bash-yaml --source src/yaml
```

# Usage


## Example 1: Get yaml value
```bash
# (Contents of example1.yml)
# | some:
# |   deeply:
# |     nested:
# |       option: 1
#

cat example1.yml | yaml_get_value some.deeply.nested.option
# Outputs 1
```

## Example 2: convert yaml to bash variables
```bash
# (Contents of example2.yml)
# | app:
# |   settings:
# |     title: My Awesome App
# |     color: #DADADA
# |     language: en
#

eval "$(cat example2.yml | yaml_parse app.settings)"
# Defines the following bash variables
# app_settings=""
# app_settings_title="My Awesome App"
# app_settings_color="#DADADA"
# app_settings_language="en"

eval "$(cat example.yml | yaml_parse app.settings --prefix noconflict)"
# Defines the following bash variables
# noconflict_app_settings=""
# noconflict_app_settings_title="My Awesome App"
# noconflict_app_settings_color="#DADADA"
# noconflict_app_settings_language="en"
```

## Example 3: replace yaml values
```bash
# (Contents of example3.yml)
# | app:
# |   settings:
# |     title: My Awesome App
# |     color: #DADADA
# |     language: en
#

cat example3.yml | 
  yaml_replace app.settings.color "#FFF" |
  yaml_replace app.settings.language "rs" |
  yaml_replace app.settings.title "My Other App"

# Will output: 
app:
  settings:
    title: My Awesome App
    color: #DADADA
    language: en

# The source file is not automatically updated, if you
# want to update the original filename, please use 
# `sponge` to wait for the stdin to dry-out 
# before writing to original file, to avoid race conditions.
cat example3.yml | 
  yaml_replace app.settings.color "#FFF" |
  yaml_replace app.settings.language "rs" |
  yaml_replace app.settings.title "My Other App" |
  sponge example3.yml
```


# License

[MIT](LICENSE.md)
