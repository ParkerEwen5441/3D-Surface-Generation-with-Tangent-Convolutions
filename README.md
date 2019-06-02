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
