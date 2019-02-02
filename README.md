 # This version

This version is specifically to replicate the work at
https://github.com/neulab/word-embeddings-for-nmt

That paper says that the authors used
[commit 38044b3](https://github.com/neulab/xnmt/tree/38044b36e6263b2608bede28b4e5cf3e4e7accda)
but doing so results in this traceback:

```
   initialized DefaultTranslator({'attender': <xnmt.attender.MlpAttender object at 0x146005208>, 'decoder': <xnmt.decoder.MlpSoftmaxDecoder object at 0x146005048>, 'encoder': <xnmt.lstm.LSTMSeqTransducer object at 0x146005128>, 'src_embedder': <xnmt.embedder.PretrainedSimpleWordEmbedder object at 0x1460050f0>, 'trg_embedder': <xnmt.embedder.PretrainedSimpleWordEmbedder object at 0x146005320>})   
   Traceback (most recent call last):
     File "/usr/local/Cellar/python/3.7.1/Frameworks/Python.framework/Versions/3.7/lib/python3.7/runpy.py", line 193, in _run_module_as_main
          "__main__", mod_spec)   
     File "/usr/local/Cellar/python/3.7.1/Frameworks/Python.framework/Versions/3.7/lib/python3.7/runpy.py", line 85, in _run_code
          exec(code, run_globals)   
     File "/Users/marcin/Downloads/replication/xnmtvenv/lib/python3.7/site-packages/xnmt-0.0.1-py3.7-macosx-10.12-x86_64.egg/xnmt/xnmt_run_experiments.py", line 170, in <module>
          sys.exit(main())   
     File "/Users/marcin/Downloads/replication/xnmtvenv/lib/python3.7/site-packages/xnmt-0.0.1-py3.7-macosx-10.12-x86_64.egg/xnmt/xnmt_run_experiments.py", line 131, in main
          xnmt_trainer.run_epoch()   
     File "/Users/marcin/Downloads/replication/xnmtvenv/lib/python3.7/site-packages/xnmt-0.0.1-py3.7-macosx-10.12-x86_64.egg/xnmt/xnmt_train.py", line 229, in run_epoch
          standard_loss = self.model.calc_loss(src, trg)   
     File "/Users/marcin/Downloads/replication/xnmtvenv/lib/python3.7/site-packages/xnmt-0.0.1-py3.7-macosx-10.12-x86_64.egg/xnmt/translator.py", line 113, in calc_loss
          embeddings = self.src_embedder.embed_sent(src)   
     File "/Users/marcin/Downloads/replication/xnmtvenv/lib/python3.7/site-packages/xnmt-0.0.1-py3.7-macosx-10.12-x86_64.egg/xnmt/embedder.py", line 109, in embed_sent
          embeddings.append(self.embed(batch))   
     File "/Users/marcin/Downloads/replication/xnmtvenv/lib/python3.7/site-packages/xnmt-0.0.1-py3.7-macosx-10.12-x86_64.egg/xnmt/embedder.py", line 87, in embed
          if self.fix_norm != None:   
   AttributeError   :    'PretrainedSimpleWordEmbedder' object has no attribute 'fix_norm'   
```

The change in this commit fixes that error, and it is presumed that
this fix was also applied in the version used in that paper. 


eXtensible Neural Machine Translation
=====================================

This is a repository for the extensible neural machine translation toolkit `xnmt`.
The over-arching goal of `xnmt` is that it be easy to use for research, and thus it supports
a modular design that means that new methods should be easy to implement by adding new modules.
It is coded in Python based on [DyNet](http://github.com/clab/dynet).

More information can be found in the [documentation](http://xnmt.readthedocs.io).

[![Build Status](https://travis-ci.org/neulab/xnmt.svg?branch=master)](https://travis-ci.org/neulab/xnmt)
[![Documentation Status](http://readthedocs.org/projects/xnmt/badge/?version=latest)](http://xnmt.readthedocs.io/en/latest/?badge=latest)
