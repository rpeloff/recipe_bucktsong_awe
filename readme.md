Acoustic Word Embeddings on Buckeye English and NCHLT Xitsonga
==============================================================


Overview
--------
Unsupervised acoustic word embedding (AWE) approaches are implemented and
evaluated on the Buckeye English and NCHLT Xitsonga speech datasets.



Disclaimer
----------
The code provided here is not pretty. But I believe that research should be
reproducible. I provide no guarantees with the code, but please let me know if
you have any problems, find bugs or have general comments.



Datasets
--------
Portions of the Buckeye English and NCHLT Xitsonga corpora are used. The whole
Buckeye corpus will be required to execute the steps here, and the portion of
the NCHLT data. These can be downloaded from:

- Buckeye corpus:
  [buckeyecorpus.osu.edu](http://buckeyecorpus.osu.edu/)
- NCHLT Xitsonga portion: [www.zerospeech.com](http://www.lscp.net/persons/dupo
  ux/bootphon/zerospeech2014/website/page_4.html). This requires registration
  for the challenge.

From the complete Buckeye corpus we split off several subsets. The most
important are the sets labelled as `devpart1` and `zs` in the code here. These
sets respectively correspond to `English1` and `English2` in [Kamper et al.,
2016](http://arxiv.org/abs/1606.06950), so see the paper for more details. More
details of which speakers are found in which set is also given at the end of
[features/readme.md](features/readme.md). We use the entire Xitsonga dataset
provided as part of the Zero Speech Challenge 2015 (this is already a subset of
the NCHLT data).



Preliminaries
-------------
Obtain all the datasets as described in the Datasets section above. Install all
the standalone dependencies (see Dependencies section below). Then clone the
required GitHub repositories into `../src/` as follows:

    mkdir ../src/
    git clone https://github.com/kamperh/speech_dtw.git ../src/speech_dtw/

For `speech_dtw` you need to run `make` to build. Unit tests can be performed
by running `make test`. See the readmes for more details.



Testing
-------
Run `make test` to run unit tests.



Feature extraction
------------------
Update the paths in `paths.py`. Extract filterbank and MFCC features by running
the steps in [features/readme.md](features/readme.md).



Frame-level same-different evaluation
-------------------------------------
To perform frame-level same-different evaluation based on dynamic time warping
(DTW), follow the steps in [samediff/readme.md](samediff/readme.md).



Downsampled acoustic word embeddings
------------------------------------
Extract and evaluate downsampled acoustic word embeddings by running the steps
in [downsample/readme.md](downsample/readme.md).



Dependencies
------------

Standalone packages:

- [Python](https://www.python.org/)
- [NumPy](http://www.numpy.org/) and [SciPy](http://www.scipy.org/)
- [HTK](http://htk.eng.cam.ac.uk/): Used for MFCC feature extraction.
- [TensorFlow](https://www.tensorflow.org/)

Repositories from GitHub:

- [speech_dtw](https://github.com/kamperh/speech_dtw/): Used for same-different
  evaluation.  Should be cloned into the directory `../src/speech_dtw/`, as
  done in the Preliminary section above.
