# Git 基本介紹
### 1. 版本控制系統 (如遊戲存檔功能)
### 2. 共同開發 (提供中央的 Repository)
---

# Git 基本常用指令
### 1. Git Init 用於初始化一個新的 Git Repository
```zsh
# 初始化一個新的 Git Repository
$ git init
```
```zsh
# 在儲存庫的根目錄下刪除 .git 目錄, 取消初始化 (不可逆)
$ rm -rf .git
```

### 2. Git Status 用於顯示當前 Git 儲存庫的 "未提交更改" 狀態訊息
```zsh
# 查看當前 Git 儲存庫的狀態
$ git status
```

### 3. Git Add 用於將文件的更改添加到 "暫存區"
```zsh
# 將所有已修改或新建的檔案添加到暫存區
$ git add .

# 將指定檔案添加到暫存區
$ git add [檔案名稱]
```
```zsh
# 將所有已添加到暫存區的檔案移除
$ git reset

# 將指定檔案從暫存區移除
$ git add [檔案名稱]
```

### 4. Git Commit 用於創建新的提交到版本控制 Repository
```zsh
# 使用此命令提交更改到儲存庫, 會打開 "預設編輯器" 以輸入提交訊息
$ git commit

# 使用此命令提交更改到儲存庫, 並使用 "-m" 選項直接在命令中提供提交訊息, 無需打開編輯器
$ git commit -m "修改訊息"
```

### 5. Git Log 用於查看儲存庫的提交歷史記錄
```zsh
# 查看 Repository 的提交歷史
$ git log
```

### 6. Git Restore 用於管理工作目錄中更改命令, 回到最後一次提交相同狀態
```zsh
# 恢復指定文件的更改
$ git restore <file>

# 恢復所有已修改但未暫存的文件的更改
$ git restore .
```

### 7. Git Reset & Git Revert 用於修改 Git 儲存庫中提交歷史 (commits)
```zsh
# 將 HEAD、索引和工作目錄 "重置到指定提交"
$ git reset --hard <commit-hash>

# 將 HEAD 移動到指定提交, 但 "保留更改在索引中"
$ git reset --soft <commit-hash>

# 創建一個反轉指定提交更改的新提交
$ git revert <commit-hash>
```

### 8. Git Cherry-Pick 用於選擇性地應用特定提交的更改 (按照時間順序)
```zsh
# 從指定分支中選擇性地應用單個提交到當前分支
$ git cherry-pick <commit-hash>

# 從指定分支中選擇性地應用多個提交到當前分支
$ git cherry-pick <commit-hash-1> <commit-hash-2> <commit-hash-3>
```

### 9. Git Branch 用於管理分支, 分支是儲存庫中不同的 "開發線"
#### 1. 本地分支：
```zsh
# 查看所有本地分支
$ git branch

# 創建一個新的本地分支
$ git branch [分支名稱]

# 切換到指定的本地分支
$ git checkout [分支名稱]

# 刪除指定的本地分支
$ git branch -d [分支名稱]
```

#### 2. 遠端分支：
```zsh
# 查看所有遠端分支
$ git branch -r

# 查看所有分支, 包括本地分支和遠端分支
$ git branch -a
```
---

# GitHub 基本介紹
### 1. 遠端 Hosting, 進行開發 (如 Google Drive、OneDrive)
---

# Git 與 GitHub 連接常用指令
### 1. Git Remote 用於管理遠端儲存庫的連接
```zsh
# 顯示所有遠端 Repository 的連接
$ git remote -v
```
```zsh
# 添加一個新的遠端儲存庫並指定名稱和 URL
$ git remote add [遠端儲存庫名稱] [遠端儲存庫URL]
```
```zsh
# 重命名遠端儲存庫的名稱
$ git remote rename [遠端儲存庫舊名稱] [遠端儲存庫新名稱]
```
```zsh
# 刪除指定名稱的遠端儲存庫連接
$ git remote remove [遠端儲存庫名稱]
```

### 2. Git Push 用於將本地 Repository 的提交推送到<br>遠端 Repository, 便團隊協作和版本控制

```zsh
# 創建新的遠端分支並推送本地分支的更改 (遠端分支不存在)
$ git push [遠端儲存庫名稱] [本地分支名稱]

# 推送本地分支的更改到遠端分支 (遠端分支已存在)
$ git push [遠端儲存庫名稱] [本地分支名稱]:[遠端分支名稱]
```
```zsh
# 推送當前分支的更改到遠端分支 (通常使用 "-u" 選項以設置上游分支)
$ git push -u [遠端儲存庫名稱] [本地分支名稱]

# 設置上游分支後, 可直接使用即可推送
$ git push
```

### 3. Git Pull 用於將遠端 Repository 最新更改合併到當前分支
```zsh
# 拉取遠端分支的最新 "更改" 並合併到當前分支
$ git pull

# 拉取指定遠端分支的最新 "更改" 並合併到當前分支
$ git pull [遠端儲存庫名稱] [遠端分支名稱]
```

### 4. Git Clone 用於從遠端 Repository 克隆一份副本到本地
```zsh
# 克隆遠端儲存庫到本地目錄
$ git clone [遠端儲存庫URL]

# 克隆遠端儲存庫的特定分支到本地目錄
$ git clone -b [分支名稱] [遠端儲存庫URL]
```

### 5. Git Submodule 用於在一個 Git 儲存庫中包含<br>另一個 Git 儲存庫, 適用於依賴於其他專案的情況
```zsh
# 添加一個新的子模組到指定路徑
$ git submodule add [子模組儲存庫URL] [本地路徑]

# 初始化本地所有子模組
$ git submodule init
```
```zsh
# 更新子模組到主儲存庫記錄的特定提交版本
$ git submodule update

# 更新子模組到遠端儲存庫的最新提交版本
$ git submodule update --remote

# 克隆包含子模組的儲存庫, 並初始化和更新所有子模組
$ git clone --recurse-submodules [遠端儲存庫URL]
```
```zsh
# 從儲存庫中移除指定子模組
$ git submodule deinit -f -- [子模組路徑]
$ git rm -f [子模組路徑]
$ rm -rf .git/modules/[子模組路徑]
```
---

# Git Conflict 衝突
### 1. 衝突原因
1. 當兩個或以上的開發者同時修改了同一檔案的同一部分, <br/>並且某一方已將更改推送到遠端 Repository 時, 其他人在推送時就會遇到衝突
2. 在合併分支 (如將特定分支合併到主分支) 時, 如果有重疊的更改, 也會發生衝突

### 2. 衝突的識別
1. Git 會在執行操作 (如合併、拉取或重設) 時顯示衝突訊息
2. 衝突的檔案會被 Git 標記, 並在檔案內部顯示不同分支的更改內容

### 3. 解決衝突
1. 開發者需要 "手動檢查" 並 "編輯衝突的檔案", 合併不同分支的更改
2. 解決衝突後, 需要重新添加檔案 (git add), 然後完成合併操作 (如 git commit)

### 4. 避免衝突的最佳方法
1. "定期" 從遠端儲存庫拉取 "更新", 保持本地儲存庫與遠端 "同步"
2. 在推送更改之前, 先從遠端儲存庫拉取最新的更改並在本地進行合併
---

# .gitignore 文件的使用
### 1. 使用原因
1. .gitignore 文件用於指定 Git 應該忽略的文件和目錄
2. 在專案中, 可能會產生一些不需要添加到版本控制的文件<br/>(如編譯文件、日誌文件或特定於開發環境的配置文件)

### 2. 創建 .gitignore 文件
```zsh
# 在儲存庫的根目錄中創建 .gitignore 文件
$ touch .gitignore
```

### 3. 配置 .gitignore 文件
```
# 忽略所有 .log 文件
*.log

# 忽略特定目錄
node_modules/
temp/

# 忽略特定文件
.env
config.json
```

### 4. 檢查 .gitignore 的效果
```zsh
# 在添加規則後, 使用 git status 檢查忽略的文件是否不再出現在未追蹤文件列表中
$ git status
```

### 5. 提交 .gitignore 文件
```zsh
# 添加 .gitignore 文件到儲存庫
$ git add .gitignore

# 提交 .gitignore 文件
$ git commit -m "Add .gitignore"
```
---

# Git Large File Storage (LFS) 的使用
### 1. 使用原因
1. Git Large File Storage (LFS) 是一個用於處理 "大型二進制文件" 的工具, <br/>可以使 Git 更有效地處理這些文件
2. 當 Git 儲存庫需要跟蹤和管理大型文件, 如圖像、視頻、模型文件等, <br/>使用 Git LFS 可以幫助減少 Repository 大小, 提高性能, 並確保項目的版本控制流暢運作

### 2. 初始化 Git LFS
```zsh
# 啟用 Git LFS
$ git lfs install
```

### 3. 選擇要跟蹤的大型文件
```zsh
# 使用通配符選擇一類文件
$ git lfs track "*.extension"

# 針對單個文件指定
$ git lfs track "path/to/largefile.extension"
```

### 4. 其他操作指令：
1. 除了初始化和選擇要跟蹤的大型文件外, 其他 Git 操作指令<br/>(如 git add、git commit、git pull、git push 等) 的使用方式和正常的 Git 操作相同
2. Git LFS 會自動處理大型文件的上傳和下載, 能夠像平常一樣進行版本控制和協作
---