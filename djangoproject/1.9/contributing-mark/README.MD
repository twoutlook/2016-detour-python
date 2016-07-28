
#  take note of <b>Writing your first patch for Django¶</b>
Reference, https://docs.djangoproject.com/en/1.9/intro/contributing/

## 準備工作
- 獲得 django 有 git 版本控制的代碼 
  - git clone https://github.com/django/django.git
  - 這將在目前的工作目錄新建一個名為 django 的目錄
  - 除了 django 代碼以外，還有些是屬於 git 的
    - .git 有著版本控制的基礎數據
    - .gitignore 裡每一行沒有#註釋掉的，表示不列入 git 管控的目錄或檔案
  - 整個 django 資料夾可以直接複製有效。 
  
- 創建本地的 python 虛擬環境
  - Ubuntu 16.04, 直接使用 python3 
    ```
    python3 -m venv virtual01
    ```
    
  - Win10, Git BASH, 先安裝 virtualenv, 再用 virtualenv
    ```
    $ pip install virtualenv
    $ virtualenv ~/.virtualenvs/djangodev
    ```
- 啟用 python 虛擬環境
  - Ubuntu 16.04, 使用 source
    ```
    $ source bin/activate
    ```
    
  - Win10, Git BASH, 居然也可以使用 source
    ```
    $ source Scripts/activate
    ```
