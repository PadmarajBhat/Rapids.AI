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
