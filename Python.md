# Python 開發時會遇到的問題

### I.　[Jupyter 輸出內容過大時當機，以至於檔案開不起來](https://blog.csdn.net/CherryChenieth/article/details/123571444)
- 至該檔路徑位置輸入下列指令其一 </br>
- 要用支援 jupyter 做前綴的命令列 ex: `Anaconda Prompt` </br>
- 檔名不能有特殊符號 ex: `. / ) (` </br>

將 `xxx.ipynb` 輸出內容清除 
```
jupyter nbconvert --ClearOutputPreprocessor.enabled=True --inplace xxx.ipynb
```

將 `xxx.ipynb` 輸出內容清除 ，並將處理結果另存新檔為 `test.ipynb` 。
```
jupyter nbconvert --ClearOutputPreprocessor.enabled=True --to notebook --output=test xxx.ipynb
```