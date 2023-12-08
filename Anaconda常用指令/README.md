# Anaconda 常用指令

### 創建環境
```
conda create --name <env name> <python=3.11.5>
```
### 切換環境
```
conda activate + <env name>
```
### 環境清單
```
conda env list
```
### 刪除環境
```
conda env remove --name <env name>
```

### 安裝套件並指定版本
TensorFlow-GPU　`pip install tensorflow-gpu==1.14`</br>
Keras　`pip install keras==2.2.4`</br></br>

### 安裝應用
先進行pip版本升級 **(建議)**　`pip install — upgrade pip`</br>
安裝 jupyter / Spyder
```
pip install notebook==7.0.6
pip install spyder==5.4.3
```

### 依據清單(xxx.txt)來安裝套件</br>
將需要的套件都寫進xxx.txt裡面，不須任何標點符號</br>
- ex:
  - tensorflow-gpu==1.14
  - keras==2.2.4
```
pip install -r xxx.txt
```
此 txt 檔 [kit_list.txt](./kit_list.txt) 存放了 tensorflow-gpu / keras 之該指定套件。 </br></br>

### 備份環境
```
conda env export > <path ex: C:\Users\xxx\environment.yaml> 
```

### 匯入environment.yaml
記住 ! 本專案中該檔案已經命名環境名稱，若需要更改，請進去 `environment.yaml` 修正。
若重複的環境名稱將會噴錯。
```
conda env create -f C:\Users\xxx\environment.yaml
```
此環境清單 [environment.yaml](./environment.yaml) 只安裝 jupyter / Spyder。 </br></br>

### 解决【AssertionError Torch not compiled with CUDA enabled】問題
```
conda remove --name pytorch -all
conda activate <env name>
conda remove --name pytorch --all
conda deactivate
pip uninstall torch
conda install pytorch torchvision torchaudio cudatoolkit=10.2 -c pytorch
```
