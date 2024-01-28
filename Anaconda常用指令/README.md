# Anaconda 常用指令

### I.　創建名為 env 的環境 ; Python版本指定為 3.12.0
```py
conda create --name env python=3.12.0
```
</br>

### II.　命令列切換環境至 env 環境
```py
conda activate env
```
</br>

### III.　查看當前所有虛擬環境清單
```py
conda env list
```
</br>

### IV.　刪除子虛擬環境 ; 譬如刪除 env
```py
conda env remove --name env
```
</br>

### V.　安裝常用的應用
- Jupyter Notebook
  ```py
  pip install notebook
  ```
  - 啟動 `jupyter notebook`
</br>

- Spyder　
  ```py
  pip install spyder
  ```
  - 啟動 `spyder`
</br>

### VI.　安裝套件應用
ex : 安裝 numpy / requests
```py
pip install numpy==1.26.2
pip install requests==2.31.0
```
</br>

### VII.　套件升級
ex : 升級 pip / numpy / requests
```py
pip install --upgrade pip
pip install --upgrade numpy
pip install --upgrade requests
```

### VIII 移除套件
ex : 移除 numpy / requests
```py
pip uninstall numpy
pip uninstall requests
```

### IX.　依據清單(requirements.txt)來安裝套件</br>
可以將需要的套件都寫進 [requirements.txt](./requirements.txt) 裡面，不須任何標點符號，也可以不設定版本</br>
- ex:
- notebook
- spyder
- numpy==1.26.2
- Pillow==10.1.0
- requests==2.31.0
- beautifulsoup4==4.12.2
- argumentparser==1.2.1

接著輸入下方語句即可導入安裝 requirements.txt 內所有設定之套件
```py
pip install -r requirements.txt
```
</br>

### X.　備份環境
```py
conda env export > C:\Users\xxx\environment.yaml
```
</br>

### XI.　匯入 [environment.yaml](./environment.yaml)
```py
conda env create -f C:\Users\xxx\environment.yaml
```
- 環境名稱 : `trysomething`
- 只安裝常用應用 : `jupyter notebook` `spyder` `powershell`
- 若要改環境名稱，須改
  ```py
  # trysomething -> name you want
  name: trysomething
  ...
  prefix: C:\Users\xxx\anaconda3\envs\trysomething
  ```
- 使用者名稱也須變更
  ```py
  # xxx -> your user name
  prefix: C:\Users\xxx\anaconda3\envs\trysomething
  ```
</br>