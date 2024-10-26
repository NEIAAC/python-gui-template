# Python, now with 39% more GUI 🐍💻

Template for pythons apps with a GUI. Features automated builds on release with binaries for Windows, MacOS and Linux users to download. Contains linting, formatting and testing tools.

Although this template is meant to be a base for bigger projects, there are some limitations and annoyances that derive from using python bindings with Qt. To name a few, testing can be cumbersome with PyTest-Qt and the API is not always easy to work with or well documented. Other than that, there is also no tooling for using Qt translations with ease so this template essencially provides a non-localized app, this is not to say that it can't be added when building upon it.

With the exception of the points above, we believe this template to be decently production ready.

## Usage 🚀

- The app is automatically built by a pipeline with every release, so we provide **direct download links** for most operating systems.

  ### Windows 🪟

  - Use this [link](https://github.com/NEIAAC/python-gui-template/releases/latest/Windows.zip) to start the download.

  - Run the `main.exe` file inside the extracted folder, you can create a shortcut with any name you like for this file.

  ### Linux 🐧

  - Use this [link](https://github.com/NEIAAC/python-gui-template/releases/latest/Linux.zip) to start the download.

  - Run the `main.bin` file inside the extracted folder. Note that compilation is targeted at Ubuntu (Wayland), other distributions may need additional actions to run the app.

  ### MacOS 🍎

  - Use this [link](https://github.com/NEIAAC/python-gui-template/releases/latest/MacOS.zip) to start the download.

  - Run the bundle installer extracted from the `.zip` file.

- Depending on your operating system, you _may_ get a **security warning** due to the app not being signed. You can **safely ignore it** as our builds are automated from the open sourced codebase.

- Inside the app you can find a guide page with a few more flow details.

## Development 🛠️

- ### Requirements 📋

  - Python 3.12.0+

- ### Setup ⚙️

  - Clone the repository and open a terminal **inside** it.

  - Install the dependencies:

    ```shell
    # It is it recommend that a virtual environment is set before doing this!

    pip install .
    ```

  - Start the app:

    ```shell
    python src/main.py
    ```

- ### Tooling 🧰

  - Ruff is used as a linter and formatter:

    ```shell
    pip install .[check]
    ruff check --fix
    ruff format

    # To automatically lint and format on every commit install the pre-commit hooks:
    pre-commit install

    # Note that when using pre-commit the git command will fail if any files are lint fixed or formatted.
    # You will have to add the changed files to the staged area and commit again to apply the changes.
    ```

  - PyTest and PyTest-Qt are used for testing:

    ```shell
    pip install .[test]
    pytest
    ```

  - Nuitka is used for cross-compiling to all supported platforms:

    ```shell
    pip install .[build]
    nuitka <options>
    ```

    See the build [workflow](./.github/workflows/build.yaml) for a list of options used for each platform.

## Notes 📝

When using this repository as a template make sure to:

- Edit the project name and version in the `pyproject.toml` file.

- Edit the constants that refer to the app in the `utils/constants.py` file.

- Make sure the string in the `version.py` file matches the project version in the `pyproject.toml` file. This is only needed for the initial setup, after that the `release.yaml` workflow will ensure they are always both incremented and kept in sync.

- Update most of the `env` variables in the `build.yaml` workflow for the final build manifest.

- Update the description and hard coded links in this `README.md`, specifically the download links.

- Delete these notes.
