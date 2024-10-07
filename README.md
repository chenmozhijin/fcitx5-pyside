
# Add fcitx5 Support to PySide

This GitHub Action adds support for fcitx5 input method to the PySide6 library or applications based on it.

## Inputs

- **`plugins-path`**:  
  **Required**  
  The path to the Qt plugins directory where the fcitx5 platform input context plugin will be installed.

- **`PySide-version`**:  
  **Optional**  
  The version of the PySide library (e.g., `6.7.3`). If not provided, the version will be automatically detected from the installed PySide6 package.

## Usage

Below is an example of how to use this Action in your workflow:

```yaml
name: Add fcitx5 Support to PySide6
on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/setup-python@v5
        with:
          python-version: 3.12

      - name: Prepare
        run: |
            pip install -U PySide6

      - name: Add fcitx5 Support to PySide
        uses: chenmozhijin/fcitx5-pyside@master
        with:
          plugins-path: ${{ env.Python_ROOT_DIR }}/lib/python3.12/site-packages/PySide6/plugins
          PySide-version: "6.7.3" # Optional, can be omitted for auto-detection
```