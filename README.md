# robotont.github.io
[Documentation](https://robotont.github.io) for robotont

## Overview

This repository contains the source files for the documentation of the robotont project. The documentation is built using Sphinx and hosted on GitHub Pages.
Each time a new commit is pushed to any of the branches, the documentation is automatically built and deployed by GitHub Actions workflow.
The main branch serves as an entry point to other branches, which can be accessed via subfolders as follows:

[https://robotont.github.io](https://robotont.github.io)/ <branch_name>

├─ [/humble](https://robotont.github.io/humble) (ROS2)<br>
├─ [/humble-devel](https://robotont.github.io/humble-devel) (ROS2)<br>
├─ [/noetic](https://robotont.github.io/noetic) (ROS1)<br>
├─ [/noetic-devel](https://robotont.github.io/noetic-devel) (ROS1)<br>


## Rendering the docs locally

##### Update apt and pip
```
sudo apt update
pip3 install --upgrade pip
```

##### Getting dependencies
```
sudo apt install python3-sphinx
pip3 install sphinx_rtd_theme
```

* Make whatever changes you need to the docs files in `source/`
* Run `make html` to generate new docs
* Open `html/index.html` in your browser to see the changes
