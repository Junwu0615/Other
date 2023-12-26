# 遇到的經典問題 :</br>'pip' 不是內部或外部命令、可執行的程式或批次檔。

- 檢查 C:\Users\xxx\AppData\Local\Programs\Python
- 是否有檔案，若無，則去 [Python](https://www.python.org/downloads/) 官網下載並安裝。
- 再次執行程序，若一樣出現同樣錯誤。
- 在系統環境變數當中，新增 2 個路徑。
  - C:\Users\xxx\AppData\Local\Programs\Python\Python版本
  - C:\Users\xxx\AppData\Local\Programs\Python\Python版本\Scripts
- 再次執行指令即可。
