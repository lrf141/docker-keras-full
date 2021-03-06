docker-keras-full
=================

***docker-keras-full*** is a [*Docker*](http://www.docker.com/) image built from *Debian 9* (amd64) with a deep learning research environment based on [*Keras*](http://keras.io/) and [*Jupyter*](http://jupyter.org/). It supports CPU and GPU processing with [*TensorFlow*](http://www.tensorflow.org/), [*Theano*](http://deeplearning.net/software/theano/) and [*CNTK*](https://docs.microsoft.com/en-us/cognitive-toolkit/) backends. It features *Jupyter Notebook* with *Python 2 and 3* support and uses only Debian and Python packages (no manual installations).

Open source project:

- <i class="fa fa-fw fa-home"></i> home: <http://gw.tnode.com/docker/keras-full/>
- <i class="fa fa-fw fa-github-square"></i> github: <http://github.com/gw0/docker-keras-full/>
- <i class="fa fa-fw fa-laptop"></i> technology: *debian*, *keras*, *theano*, *tensorflow*, *cntk*, *openblas*, *cuda toolkit*, *python*, *python3*, *numpy*, *h5py*, *jupyter*, *tensorboard*, *matplotlib*, *pillow*, *pandas*, *scikit-learn*, *statsmodels*
- <i class="fa fa-fw fa-database"></i> docker hub: <http://hub.docker.com/r/gw000/keras-full/>

Available tags:

- `2.1.4`, `latest` [2018-02-15]: *Python 2.7/3.5* + *Keras* <small>(2.1.4)</small> + *TensorFlow* <small>(1.5.0)</small> + *Theano* <small>(1.0.1)</small> + *CNTK* <small>(2.4)</small> on CPU/GPU
- `2.1.1` [2017-12-01]: *Python 2.7/3.5* + *Keras* <small>(2.1.1)</small> + *TensorFlow* <small>(1.4.0)</small> + *Theano* <small>(1.0.0)</small> + *CNTK* <small>(2.3)</small> on CPU/GPU
- `2.0.2` [2017-03-27]: *Python 2.7/3.5* + *Keras* <small>(2.0.2)</small> + *TensorFlow* <small>(1.0.1)</small> + *Theano* <small>(0.9.0)</small> on CPU/GPU
- `1.2.0` [2016-12-21]: *Python 2.7/3.5* + *Keras* <small>(1.2.0)</small> + *TensorFlow* <small>(0.12.0)</small> + *Theano* <small>(0.8.2)</small> on CPU/GPU
- `1.1.0` [2016-09-20]: *Python 2.7/3.5* + *Keras* <small>(1.1.0)</small> + *TensorFlow* <small>(0.10.0)</small> + *Theano* <small>(0.8.2)</small> on CPU/GPU
- `1.0.8` [2016-08-28]: *Python 2.7/3.5* + *Keras* <small>(1.0.8)</small> + *TensorFlow* <small>(0.9.0)</small> + *Theano* <small>(0.8.2)</small> on CPU/GPU
- `1.0.6` [2016-07-20]: *Python 2.7/3.5* + *Keras* <small>(1.0.6)</small> + *TensorFlow* <small>(0.9.0)</small> + *Theano* <small>(0.8.2)</small> on CPU/GPU
- `1.0.4` [2016-06-16]: *Python 2.7/3.5* + *Keras* <small>(1.0.4)</small> + *TensorFlow* <small>(0.8.0)</small> + *Theano* <small>(0.8.2)</small> on CPU/GPU


Usage
=====

Quick experiment from console with IPython 2.7 or 3.5:

```bash
$ docker run -it --rm gw000/keras-full ipython2
$ docker run -it --rm gw000/keras-full ipython3
```

To start the Jupyter web interface on `http://<ip>:8888/` (password: `keras`) and notebooks stored in current directory (will be mapped to `/srv`):

```bash
$ docker run -d -p 8888:8888 -v $(pwd):/srv gw000/keras-full
```

To utilize your GPUs this Docker image needs access to your `/dev/nvidia*` devices and *CUDA Driver* libraries (see [docker-debian-cuda](http://gw.tnode.com/docker/debian-cuda/)), like:

```bash
$ docker run -d $(ls /dev/nvidia* | xargs -I{} echo '--device={}') $(ls /usr/lib/*-linux-gnu/{libcuda,libnvidia}* | xargs -I{} echo '-v {}:{}:ro') -p 8888:8888 -v $(pwd):/srv gw000/keras-full
```

To change the default password and token authentication, prepare [a new hashed password](https://jupyter-notebook.readthedocs.io/en/latest/public_server.html#preparing-a-hashed-password) and a token string and pass it as environment variables:

```bash
$ docker run -d -p 8888:8888 -e PASSWD="sha1:..." -e TOKEN="..." -v $(pwd):/srv gw000/keras-full
```

If the TensorFlow backend is used, it is possible to start the TensorBoard visualization tool directly from the Jupyter web interface ([see usage](https://github.com/lspvic/jupyter_tensorboard)).


Feedback
========

If you encounter any bugs or have feature requests, please file them in the [issue tracker](http://github.com/gw0/docker-keras-full/issues/) or even develop it yourself and submit a pull request over [GitHub](http://github.com/gw0/docker-keras-full/).


License
=======

Copyright &copy; 2016-2018 *gw0* [<http://gw.tnode.com/>] &lt;<gw.2018@ena.one>&gt;

All code is licensed under the [GNU Affero General Public License 3.0+](LICENSE_AGPL-3.0.txt) (AGPL-3.0+). Note that it is mandatory to make all modifications and complete source code publicly available to any user.
