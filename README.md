# jukebox-tutorial

```
cd Documents/Personal\ Projects/
mkdir jukebox-tutorial
cd jukebox-tutorial
git clone git@github.com:openai/jukebox.git
```

Install Anaconda
- https://www.anaconda.com/products/individual

Install Miniconda
- https://docs.conda.io/en/latest/miniconda.html

```
sudo su
cd /Users/macbook/Documents/Personal\ Projects/jukebox-tutorial/jukebox
conda create --name jukebox python=3.7.5
conda activate jukebox
conda install mpi4py=3.0.3 # if this fails, try: pip install mpi4py==3.0.3
conda install pytorch=1.4 torchvision=0.5 cudatoolkit=10.0 -c pytorch
pip install -r requirements.txt
pip install -e .

# Required: Training
conda install av=7.0.01 -c conda-forge 
pip install ./tensorboardX
```

ERROR
RuntimeError: Failed to initialize NCCL

## Using tensorflow
```
docker pull tensorflow/tensorflow
docker run -it --rm tensorflow/tensorflow
```

## Using docker image with anaconda

```
docker pull continuumio/conda-ci-linux-64-python3.7
docker run -it --rm continuumio/conda-ci-linux-64-python3.7
nano .bashrc
```

Prepend this line to the bashrc file:

```
eval "$(command conda 'shell.bash' 'hook' 2> /dev/null)"
```

```
apt-get install libsndfile-dev
source .bashrc
git clone https://github.com/openai/jukebox.git
cd jukebox
conda create --name jukebox python=3.7.5
conda activate jukebox
conda install mpi4py=3.0.3 # if this fails, try: pip install mpi4py==3.0.3
conda install pytorch=1.4 torchvision=0.5 cudatoolkit=10.0 -c pytorch
pip install -r requirements.txt
pip install -e .
```

AssertionError: 
Found no NVIDIA driver on your system. Please check that you
have an NVIDIA GPU and installed a driver from
http://www.nvidia.com/Download/index.aspx

## Using docker image with anaconda and tensorflow

```
docker pull mikewright/anaconda-tensorflow
docker run -it --rm mikewright/anaconda-tensorflow
sudo apt install nano
nano .bashrc
```

Prepend this line to the bashrc file:

```
eval "$(command conda 'shell.bash' 'hook' 2> /dev/null)"
```

```
apt-get install libsndfile-dev
source .bashrc
git clone https://github.com/openai/jukebox.git
cd jukebox
conda create --name jukebox python=3.7.5
conda activate jukebox
conda install mpi4py=3.0.3 # if this fails, try: pip install mpi4py==3.0.3
conda install pytorch=1.4 torchvision=0.5 cudatoolkit=10.0 -c pytorch
pip install -r requirements.txt
pip install -e .
```

## RUNNING SAMPLES

Move a .WAV file inside the folder


Sample
```
python jukebox/sample.py --model=5b_lyrics --name=sample_5b_prompted --levels=3 --mode=primed \
--audio_file=path/to/recording.wav,awesome-mix.wav,fav-song.wav,etc.wav --prompt_length_in_seconds=12 \
--sample_length_in_seconds=20 --total_sample_length_in_seconds=180 --sr=44100 --n_samples=6 --hop_fraction=0.5,0.5,0.125
```

```
python jukebox/sample.py --model=1b_lyrics --name=sample_1b_prompted --levels=3 --mode=primed \
--audio_file=walk-on-water.wav --prompt_length_in_seconds=12 \
--sample_length_in_seconds=20 --total_sample_length_in_seconds=180 --sr=44100 --n_samples=6 --hop_fraction=0.5,0.5,0.125
```
