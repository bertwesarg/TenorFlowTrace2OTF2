# ChromeTrace2Otf2

This tool is developed to convert files from [Chrome's Trace Event Format](https://docs.google.com/document/d/1CvAClvFfyA5R-PhYUmn5OOQtYMH4h6I0nSsKchNAySU) created by TensorFlow into OTF2 files.
Therefore, we only take care of features used by TensorFlow's traces at the moment.    


# Installation

This script requires the OTF2 Python bindings. These are installed with the OTF2 library. Bindings for Python 3 are included since OTF 2.3. If you install OTF2 to a custom location like `/opt`, you wil have to add the installed Python package to the `PYTHONPATH` like so:

```bash
wget http://perftools.pages.jsc.fz-juelich.de/cicd/otf2/tags/otf2-2.3/otf2-2.3.tar.gz
tar -xf otf2-2.3.tar.gz
cd otf2-2.3
./configure --prefix=/opt/otf2.3 && make && make install

export OTF2_ROOT=/opt/otf2.3
export PATH=$PATH:$OTF2_ROOT/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$OTF2_ROOT/lib
export PYTHON_PATH=$PYTHON_PATH:$OTF2_ROOT/lib/python3.8/site-packages

python3 -c 'import otf2; print(otf2.__version__)'  # 2.3
```


## TODO

 * Dataflow
 * Metric: Top allocations
 * Map new created processes for only collecting one metric to process with same name
 * If available, add memory trace as a custom metric
