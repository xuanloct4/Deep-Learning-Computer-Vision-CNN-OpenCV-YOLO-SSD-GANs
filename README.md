
source activate cv
sudo apt-get install protobuf-compiler python-pil python-lxml python-tk
python -m pip install pip==10.0.1
python -m pip install tensorflow==1.13.1
python -m pip install Keras==2.2.4
python -m pip install absl-py 
python -m pip install tf_slim 
conda install scikit-learn
python -m pip install Pillow
conda install -c conda-forge opencv
python -m pip install -U matplotlib
python -m pip install pandas
python -m pip install tqdm
python -m pip install pydot
python -m pip install scikit-image
python -m pip install graphviz
python -m pip install absl-py 
python -m pip install tf_slim 

cd
mkdir models
git clone https://github.com/tensorflow/models.git
cd
git clone https://github.com/cocodataset/cocoapi.git
cd cocoapi/PythonAPI
make
cp -r pycocotools ./tensorflow/models/models/research
# From tensorflow/models/research/
wget -O protobuf.zip https://github.com/google/protobuf/releases/download/v3.0.0/protoc-3.0.0-linux-x86_64.zip
unzip protobuf.zip
./protobuf/bin/protoc object_detection/protos/*.proto --python_out=.
# From tensorflow/models/research/
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
python object_detection/builders/model_builder_test.py