# 3D-Surface-Generation-with-Tangent-Convolutions

Title: 3D Surface Generation with Tangent Convolutions <br />
Type of project: Semester Project <br />
Year: 2019 <br />
Supervisor(s): Sandro Lombardi <br />
Student: Parker Ewen <br />

# Setup
## AtlasNet
Follow steps provided by [original repo](https://github.com/ThibaultGROUEIX/AtlasNet).

## Tangent Convolutions
### Build Open3D
Following steps were provided by [original repo](https://github.com/tatarchm/tangent_conv) with some extra steps: <br />

Make sure venv is using Python 3.6 <br />
```shell
$ python -V
$ python3 -V    #depending on venv
```

Clone [this version of Open3D](https://github.com/tatarchm/Open3D)
```shell
$ cd Open3D/src/Python/
$ mkdir Helper
$ mkdir Test
$ cd ../../
$ util/scripts/install-deps-ubuntu.sh
$ mkdir build
$ cd build
$ cmake ../src
$ make
```
To test whether Open3D was built, test using the following:
```shell
$ cd Open3D/build/lib/
$ python
$ from py3d import *
```
There may be issues with building Open3D. If that is the case, check the following:
* Open CMakeCache.txt in _Open3D/build_ and make sure PYTHON_EXECUTABLE:FILEPATH and PYTHON_LIBRARY:FILEPATH= point to python3.6 and python3.6m.so respectively
* Python 3.6 isn't supported by Ubuntu 16.04. You need to recreate the virtual environment after you install the _python3.6-dev_ package
```shell
$ sudo add-apt-repository ppa:jonathonf/python-3.6
$ sudo apt update
$ sudo apt install python3.6 python3.6-dev
$ sudo apt remove python3-dev # to ensure the system's Python 3.5 wouldn't interfere

### Create new virtualenv with flag --python=/usr/bin/python3.6
# In new virtualenv...

$ pip install dlib
```

### Run Tangent Convolutions
Download one of the datasets specified [by their GitHub page](https://github.com/tatarchm/tangent_conv).  <br />
As an example:
```shell
$ python get_data.py <directory_where_zip_is> /path/to/tangent_conv/data/raw/stanford stanford
```
Follow their procedure, starting with precomputations. <br />
<experiment_config> refers to the .json config path. As an example:
```shell
$ python tc.py experiments/stanford/dhnrgb/config.json --precompute
```

# References:
[1] Groueix, Thibault, et al. "A papier-mâché approach to learning 3d surface generation." Proceedings of the IEEE conference on computer vision and pattern recognition. 2018. <br />
[2] Tatarchenko, Maxim, et al. "Tangent convolutions for dense prediction in 3d." Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition. 2018. <br />
