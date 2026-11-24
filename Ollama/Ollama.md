# Ollama WSL2 Installation Guide

### *Requirements*
```
sudo apt-get update && sudo apt-get install -y zstd
```

### *安裝 Ollama 主程式*
```
curl -fsSL https://ollama.com/install.sh -o install.sh
less install.sh
sh install.sh
```

### *下載模型（只需執行一次）*
```
ollama pull qwen2.5-coder:3b
```

### *確認是否生效*
```
$ ollama list
# 在終端機輸入 ollama list，只要看到列表裡有 qwen2.5-coder:3b，就代表隨時可以被 gcm 腳本呼叫了。

NAME                ID              SIZE      MODIFIED           
qwen2.5-coder:3b    f72c60cabf62    1.9 GB    About a minute ago 
```

---

### *設定 gcm 腳本*
```
nano ~/.bashrc
# 把 gcm 函式貼到家目錄下的 ~/.bashrc（macOS 或部分環境若用 zsh 則是 ~/.zshrc）：

source ~/.bashrc
# 立刻生效
```

