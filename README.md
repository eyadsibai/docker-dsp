Machine Learning/Data Science Platform (Docker Image)
=====================

Requirements
------------

- docker
- docker-machine (to deploy to google cloud)

How to use (in Google Cloud)
----------------------------

```bash
docker-machine create docker-dsp -d google --google-project={project_id} --google-machine-type n1-highmem-8	--google-disk-size "10" --google-disk-type "pd-standard" --google-preemptible --google-machine-image ubuntu-os-cloud/global/images/family/ubuntu-1404-lts --google-scopes "https://www.googleapis.com/auth/cloud-platform"
```

```bash
eval $(docker-machine env docker-dsp)
```

```bash
docker run -d -p 8888:8080 -e "PROJECT_ID={project_id}" eyadsibai/docker-dsp start.sh jupyter lab --NotebookApp.token=''
```

- get the ip address of the machine

```bash
docker-machine ip docker-dsp
```

- open the site http://{docker-machine ip docker-dsp}:8080
- to stop the machine

```bash
docker-machine stop docker-dsp
docker-machine start docker-dsp
```

- to delete the instance

```bash
docker-machine rm docker-dsp
```

### Note
when you stop the machine, it would cost you nothing except for the disk that you have it attached. For Google cloud (10GB of disk would cost ~0.4$/month)


How to use (Locally)
--------------------

```bash
docker run -d -p 8888:8888 -v <local path>:/home/jovyan/work eyadsibai/docker-dsp start.sh jupyter lab --NotebookApp.token=''
```

TODO
----

- access local files (whether running locally or on google machine)


Gear included
-------------
- Python 3.6
- aws packages and tools
- data analysis and data manipulation/data storage
pandas/fastparquet/
- distributed/out-of-core/data workflow
numba/luigi/airflow
- multipurpose machine learning libraries
scikit-learn/orange3
- nlp
nltk
- network analysis
networkx
- visualization
matplotlib/seaborn/holoviews/ggplot/bokeh


name: root
dependencies:
  - python=3.6
  - pandas>=0.2.1
  - boto
  - boto3
  - lxml>=3.6.0
  - fastparquet
  - cloudpickle>=0.2.*
  - dask>=0.13.*
  - distributed
  - h5py>=2.6.*
  - hdf5>=1.8.*
  - ipywidgets>=5.2*
  - luigi>=2.*
  - matplotlib>=2.*
  - mccabe
  - numba
  - numexpr>=2.6.*
  - numpy
  - requests>=2.*
  - orange3
  - pyomo
  - pyomo.extras
  - orange3-text
  - bottleneck
  - scikit-learn>=0.18.1
  - scikit-image>=0.12.*
  - scipy>=0.19.*
  - nltk
  - statsmodels>=0.6.*
  - patsy>=0.4.*
  - cython=0.25.2
  - bcolz
  - pysal
  - datashader
  - conda-forge::pymc3
  - glemaitre::imbalanced-learn
  - conda-forge::altair
  - blaze
  - prettytable
  - gdal
  - SimpleITK::SimpleITK
  - ggplot
  - Pillow
  - Proj4
  - cytoolz
  - toolz
  - plotly
  - haversine
  - textacy
  - mpld3
  - mplleaflet
  - arrow
  - graphviz
  - gpxpy
  - python-igraph
  - line_profiler
  - george
  - pandas-profiling
  - matplotlib-venn
  - pystan
  - ImageHash
  - tifffile
  - descartes
  - biopython
  - cartopy>=0.14.2
  - shapely>=1.5.*
  - cvxopt
  - opencv
  - snowballstemmer
  - babel
  - hdbscan
  - spacy
  - rpy2
  - sklearn-contrib-lightning
  - pyshp
  - geoplot
  - pyproj
  - bqplot
  - basemap
  - pip>=9.0.1
  - google-api-python-client
  - geopy
  - gensim
  - imagesize>=0.7.1
  - pytools
  - pyparsing
  - plotnine
  - ezyang::onnx
  - setuptools>=32.3.1
  - python-dotenv
  - soumith::pytorch
  - soumith::torchvision
  - bokeh::colorcet
  - fiona
  - poliastro
  - dask-searchcv
  - damianavila82::rise
  - theano
  - spotlight
  - pygridgen
  - swig
  - odo
  - fbprophet
  - glueviz::glueviz
  - gstreamer
#  - vida-nyu::vistrails
  - hyperspy
  - bioconda::nanoplot
  - python-annoy
  - fire
  - jupyter_nbextensions_configurator
  - jupyter_contrib_nbextensions
  - nxviz
  - geojson
  - sympy
 # - nusdbsystem::singa
#  - pygridtools
  # - Quantopian::zipline (pandas 0.18.x)
  - pip:
    - git+git://github.com/scikit-learn-contrib/forest-confidence-interval.git #forestci
    - deap
    - tpot
    - joblib
    - scikit-dsp-comm[helpers]
    - perfplot
    - tdda
    - pystruct
    - airflow # needs 3.6 conda
    - nbdime
    - category_encoders
    - emcee
    - spectral
    - artemis-ml
    - git+https://github.com/jamesturk/jellyfish.git
    - lifelines
    - lsanomaly
    - skll
    - speedml
    - mlens
    - pandas_ml
    - scikit-neuralnetwork
    - causalinference
    - https://github.com/JamesRitchie/scikit-rvm/archive/master.zip
    - pomegranate
    - google-cloud
    - pyhsmm
    - dm-sonnet
    - bhtsne
    - tslearn
    - tqdm
    - tensorboard-pytorch
    - mpl-scatter-density
    - git+https://github.com/keunwoochoi/kapre.git
    - squarify
    - py_stringsimjoin
    - lifetimes
    - fuzzywuzzy
    - python-louvain
    - pyexcel-ods
    - geopandas
    - tsfresh
    - xcessiv
    - hypertools
    - futures>=3.0.5
    - seasonal
    - few
    - Skater
    - flurs
    - scikit-garden
    - lightgbm
    - mxnet
    - tensorflow>=1.0.1
    - scikit-plot
    - visualize_ML
    - workalendar
    - sigopt_sklearn[ensemble]
    - tdigest
    - sklearn-pandas
    - datacleaner
    - bambi
    - datatest
    - jieba
    - cvxpy
    - qgrid
    - categorical-distance>=1.9
    - quiver_engine
    - db.py
    - dedupe
    - dedupe-hcluster
    - parserator>=0.6.2
    - probableparsing>=0.0.1
    - probablepeople>=0.5.2
    - git+https://github.com/arogozhnikov/infiniteboost.git
    - git+https://github.com/tadejs/autokit.git
    - perfume-bench
    - omesa
    - cesium
    - thinc
    - eli5
    - sklearn-crfsuite
    - imgaug
    - pyalgotrade
    - husl
    - ml_metrics
    - pyflux
    - mne
    - alphapy
    - pyshp
    - metric-learn
    - pytagcloud
    - textblob
    - data_hacks
    - chainer
    - records
    - xgboost
    - usaddress
    - sexmachine
    - Geohash
    - sacred
    - tflearn
    - fitter
    - vowpalwabbit
    - langid
    - delorean
    - csvdedupe
    - affinegap
    - trueskill
    - heamy
    - vida
    - missingno
    - s2sphere
    - bayesian-optimization
    - face_recognition
    - pyldavis
    - lmfit
    - orderedmultidict
    - smhasher
    - nolearn
    - pynlpl
    - keras-vis
    - pybrain
    - stop-words
    - hep_ml
    - kaggle-cli
    - tfdebugger
    - fasttext
    - hmmlearn
    - wavio
    - terminalplot
    - jupyterthemes
    - lesscpy
    - mlxtend
    - keras-rl
    - h5py
    - scikit-optimize
    - bayespy
    - gplearn
    - keras
    - lime
    - fancyimpute
    - lightfm
    - lightgbm
    - searchgrid
    - git+git://github.com/mila-udem/fuel.git
    - hyperopt
    - boruta
    - yellowbrick
    - nilearn
    - featureforge
    - Dora
    - dflearn
    - vecstack
    - MarkovNetwork
    - bootstrapped
    - astroML
    - urlextract
    - git+https://github.com/kootenpv/xtoy.git
    - git+https://github.com/ianlini/feagen.git
    - git+https://github.com/mewwts/feng.git
    - fastFM
    - foolbox
    - sacred
    - pymongo
    - chainercv
    - tensorlayer
    - pdpipe
    - nnabla
    - linearmodels
    - edward
    - leven
    - rgf_python
    - catboost
    - mlbox
    - gmaps
    - ftfy
    - paramnb
    - cma
    - xgbfir
    - csvkit
    - folium
    - prince
    - sk-video
    - sklearn-compiledtrees
    - auto_ml
    - hyperas
    - disp
    - rtree
    - git+https://github.com/marinkaz/scikit-fusion.git
    - git+https://github.com/tensorflow/cleverhans.git#egg=cleverhans
    - git+https://github.com/AmazaspShumik/sklearn_bayes.git
    - git+https://github.com/ferrine/gelato.git
    - git+https://github.com/Lasagne/Lasagne.git
    - git+https://github.com/hyperopt/hyperopt-sklearn.git
    - git+https://github.com/amueller/word_cloud.git
    - git+https://github.com/nicta/dora.git
    - git+https://github.com/nicolashennetier/pyeconometrics.git
    - git+https://github.com/ztane/python-Levenshtein.git
    - git+https://github.com/NervanaSystems/neon.git@v1.9.0
    - git+https://github.com/vitruvianscience/opendeep.git
    - git+https://github.com/scikit-learn-contrib/py-earth.git
    - git+https://github.com/scikit-learn-contrib/polylearn.git
    - git+https://github.com/ioam/geoviews.git
    - git+https://github.com/erp12/pyshgp.git
    - git+https://github.com/pierreablin/faster-ica.git
    - git+https://github.com/cgevans/scikits-bootstrap.git
    - git+https://github.com/ceholden/yatsm.git
    - git+https://github.com/tariqdaouda/Mariana.git
    - git+https://github.com/automl/fanova.git
    - git+https://github.com/pgmpy/pgmpy.git
    - git+https://github.com/alshedivat/kgp.git
    - git+https://github.com/scikit-learn-contrib/polylearn.git
    - msaf
    - git+https://github.com/mattilyra/LSH.git
    - git+https://github.com/casperkaae/parmesan.git
    - gatspy
    - git+https://github.com/mpearmain/scikit-wrapRs.git
    - git+https://github.com/facebookresearch/pysparnn.git
    - git+https://github.com/jupyter/jupyter-drive.git
    - git+https://github.com/the-moliver/kfs.git
    - git+https://github.com/mattilyra/LSH.git
    - git+https://github.com/facebookresearch/DrQA.git
    - git+https://github.com/dnouri/inferno.git
    - git+https://github.com/guillemborrell/pyledger.git
    - git+https://github.com/lmcinnes/umap.git
    - git+https://github.com/rafguns/linkpred.git
    - git+https://github.com/deepnn/covfefe.git
    - visidata
    - git+https://github.com/austin-taylor/flare.git
    - persimmon
    - vania
    - scikit-surprise
    - git+https://github.com/dvaida/hallucinate.git
    - pymongo
    - keras-tqdm
    - rice
    - bayesian_bootstrap
    - quilt
    - flashtext
    - picasso-viz
    - autograd
    - py-heat
    - databench
    - elfi
    - git+https://github.com/timvieira/crf.git
    - implicit
    - knowledge-repo
    - https://cntk.ai/PythonWheel/CPU-Only/cntk-2.1-cp36-cp36m-linux_x86_64.whl
    - https://h2o-release.s3.amazonaws.com/h2o/rel-weierstrass/2/Python/h2o-3.14.0.2-py2.py3-none-any.whl
    - git+https://github.com/thtrieu/darkflow.git
    - chatterbot
    - salib
    - ethnicolr
    - git+git://github.com/ppwwyyxx/tensorpack
    - git+https://github.com/anttttti/Wordbatch.git
    - speechpy
    - nudepy
    - git+https://github.com/aarongarrett/inspyred
    - skyfield
    - minisom
    - kcbo
    - git+https://github.com/dmarx/Topological-Anomaly-Detection
    - sixpack
    - prophet
    - smac
    - hyperopt
    - pythran
    - features
    - street-address
    - messytables
    - tableschema
    - tabulator
    - git+https://github.com/garydoranjr/misvm.git#egg=misvm
    - git+https://github.com/tadejs/autokit.git
    - git+https://github.com/larsmans/seqlearn.git
    - lda
    - git+https://github.com/jmetzen/kernel_regression.git
    - pyprind
    - trendvis
    - git+https://github.com/automl/RoBO.git
    - rpforest
    - networkl
    - git+https://github.com/manahl/arctic.git
    - git+https://github.com/EESI/PyFeast.git
    - yapf
    - hypothesis
    - pytest
    - dataset
    - cerberus
    - pdftabextract
    - geoplotlib
    - petl
    - git+https://github.com/pixelogik/NearPy.git
    - meza
    - pymining
    - engarde
    - kmodes
    - rows
    - validictory
    - nutsml
    - nutsflow
    - gulpio
    - pandas-finance
    - git+https://github.com/mpearmain/gestalt
    - tdda
    - proof
    - yahoo-finance
    - quilt
    - ppca
    - barely_json
    - pypet
    - observations
    - gym
    - git+https://github.com/kalaidin/sketches
    - git+https://github.com/beltashazzer/jmpy.git
    - git+https://github.com/pierreablin/picard.git#egg=picard
    - git+https://github.com/thu-ml/zhusuan
    - optimuspyspark
    - git+https://github.com/jundongl/scikit-feature
    - py3_ortools
        - git+https://github.com/alshedivat/keras-gp

#    - git+https://github.com/zomux/deepy
#    - nupic
