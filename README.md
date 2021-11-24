Forked from 

- https://github.com/google-research/google-research/tree/master/depth_and_motion_learning

and

- https://github.com/PhilippSchmaelzle/mono_depth/tree/inference_with_original_code_structure


## Struttura cartella
In depth_and_motion_learning sono presenti tutti i file python che vengono chiamati dai 2 script bash presenti nella directory principale.


## Installazione 

- Scaricare repo da: 
https://github.com/google-research/google-research/tree/master/depth_and_motion_learning
- Vedere file [tensorflow-from-source-guide.md](https://github.com/carloradice/tesi/blob/main/tensorflow-from-source-guide.md)
- CUDA 10.1.243 
- CUDNN versione 7.6.5
- In tensorflow/config.py quando viene fatto il build di tensorflow aggiungere questo codice alla riga 1357

`  config = {
'cublas_include_dir': '/home/radice/customCuda/cuda-10.1.243/include',
'cublas_library_dir': '/usr/lib/x86_64-linux-gnu',
'cuda_binary_dir': '/home/radice/customCuda/cuda-10.1.243/bin',
'cuda_include_dir': '/home/radice/customCuda/cuda-10.1.243/include',
'cuda_library_dir': '/home/radice/customCuda/cuda-10.1.243/lib64',
'cuda_toolkit_path': '/home/radice/customCuda/cuda-10.1.243/', 
'cuda_version': '10.1', 
'cudnn_include_dir': '/home/radice/customCuda/cuda-10.1.243/include',
'cudnn_library_dir': '/home/radice/customCuda/cuda-10.1.243/lib64',
'cudnn_version': '7.6.5',
'cupti_include_dir': '/home/radice/customCuda/cuda-10.1.243/extras/CUPTI/include',
'cupti_library_dir': '/home/radice/customCuda/cuda-10.1.243/extras/CUPTI/lib64',
'nvvm_library_dir': '/home/radice/customCuda/cuda-10.1.243/nvvm/libdevice'
}
`

### Requirements

- python 3.6 
- pip conda (https://anaconda.org/anaconda/pip)

Tramite pip conda:

- bazel conda 0.26.1 (https://anaconda.org/conda-forge/bazel)
- numpy 18.5
- matplotlib==3.3.0            
- tensorflow-graphics==1.0.0   

### Scaricare checkpoint Imagenet 

Seguendo la guida di :
https://github.com/google-research/google-research/issues/589

#### Requirements
Tramite conda:

- python < 3.7
- tensorflow==1.8.0 (conda install -c conda-forge tensorflow==1.8)
- torchfile (conda install -c conda-forge torchfile)

#### Modifiche
- cambiare: import cPickle as pickle --> import pickle as pickle


## Generazione file di train

Guardare: 
https://github.com/tensorflow/models/tree/archive/research/struct2depth
per generare file .txt di train, è necesario prima avere i dati nel formato struct2depth e poi 
generare il file .txt contenente il percorso ai dati.

Esempio:

1. python gen_data_oxford.py --folder 2014-05-06-12-54-54
2. python train_file_generator.py --folder 2014-05-06-12-54-54 --dataset OXFORD


## Training

- eseguire run_train.sh

## Testing

- eseguire run_predict.sh 