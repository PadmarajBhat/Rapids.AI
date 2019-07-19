# Rapids.AI
To Explore the next generation of Spark


##### Key Hacks used to run Rapids notebook
* to access a csv file in the google drive : https://stackoverflow.com/a/47744465/8693106
  ```
  from google.colab import drive
  drive.mount('/content/drive')
  !ls -l "/content/drive/My Drive/Colab Notebooks/TrainData_PA.csv"
  ```
* !pip install nvstrings
  * but the problem here is it requires libcudart.so.9.2
  
  * Finally, below installation step fixed nvstrings error
  ```
  !conda install -q -y --prefix /usr/local -c nvidia -c rapidsai \
  -c numba -c conda-forge -c defaults nvstrings=0.8 python=3.6 cudatoolkit=10.0
  ```

  * Having 2 conda install in a cell, one after another is causing some issue:
  ```
  # install RAPIDS packages
!conda install -q -y --prefix /usr/local -c conda-forge \
  -c rapidsai-nightly/label/cuda10.0 -c nvidia/label/cuda10.0 \
  cudf cuml


!conda install -q -y --prefix /usr/local -c nvidia -c rapidsai \
  -c numba -c conda-forge -c defaults nvstrings=0.8 python=3.6 cudatoolkit=10.0

  ```
  For the second conda command it throws conda command does not exist. However, re running the same cell successfully installs the 2nd install(nvidia)


* At times colab allocates the K80 gpu and our second cell check fails; we need to reset the environment (at times couple of times) and get ourself "Tesla T4"
