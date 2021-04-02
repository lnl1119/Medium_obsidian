---
date: 2021/03/30 
tags: "#python" 
aliases: 
- python#1在mac的終端機用pip建立python虛擬環境 
---
# [python#1]在mac終端機用pip建立python虛擬環境
#python #terminal #Mac

首先，這篇只針對Mac用戶做介紹。

Terminal 請看這邊

# 1. 為什麼要建立虛擬環境(Virtual Environment)

---

首先，要了解為什麼要建立**虛擬環境**(Virtual Environment)，主要可以分成兩個：

1.  **避免跟原本環境的套件干擾**：Python 在應用的時候常會用到不在標準函式庫的套件和模組，例如最近就開始碰到Anaconda沒有一起下載到的。這時候就會需要某個特定版本的函式庫，而**需要的函式庫可能會跟既有的環境相衝突或是套件互相干擾**，建立虛擬環境能避免相關的問題。
2.  **需要使用不同版本的套件**：有時候不同專案可能會用到不同版本的同一個套件，比方說兩個專案因不同需求分別要用到pandas0.19跟pandas0.23兩個版本的pandas，但是一個虛擬環境裡只能安裝一個版本的套件，不能同時使用兩個版本的套件，**建立不同虛擬環境就可以分別使用不同版本的同一套件**。

虛擬環境可以想成一個獨立的資料夾，裡面安裝了專案應用需要用到的特定版本的套件，也可以建立多個虛擬環境供不同專案可以使用。

---

# 2. 建立虛擬環境

用來建立與管理虛擬環境的機制叫做 venv，安裝Python就預設可以使用，這個要在terminal中執行，若有其他還在跑的terminal就要開一個新的。在建立虛擬環境的時候，在決定要放該虛擬環境的資料夾之後，在 script 中執行 venv 模組並且給定資料夾 path：

python3 -m venv tutorial-env

建立了一個虛擬環境，可以使用以下方法啟動。


# 3. 改變環境內容或刪除環境

如果有想要移除的套件可以使用下面語法

pip uninstall 一個或是多個套件名稱

刪除虛擬環境

conda remove — name tutorial-env numpy


---

直接 `pip3 list` 可以叫出 整台電腦有的package

建立資料夾

進到資料夾

建立venv

`ls`可以看到name\_env在裡面

activate name\_env

確認有沒有盡到name\_env

看name\_env裡面的package(目前只有pip)

開始install packages

將環境固定

將設定好的環境輸出成txt檔

確定txt內容

deactivate venv

如果要delete environment

另一個方式：

建資料夾

在資料夾內直接建立venv，命名venv

activate

把之前弄好的環境requirements.txt叫進來

可以看到都叫進來了～

檔案不要放在環境中：

到my\_project資料夾

ls 看現在只有venv一個東西

建立script.py檔

ls可以看到script.py跟venv是分開的

將整台電腦有的package弄進venv：

建立系統套件的環境

activate

系統的套件都進來了

後來安裝的

新安裝的不會影響原本系統的

mkdir folder\_name

cd folder\_name

python3 -m venv name\_env

ls

source name\_env/bin/activate

which python

pip list

pip install numpy...

pip freeze

pip freeze > requirements.txt

cat requirements.txt

deactivate

rm -rf name\_env/

mkdir my\_project

python3 -m venv my\_project

source pipmy\_project/venv/bin/activate

pip install -r requirements.txt

pip list

cd my\_project

ls

touch [script.py](http://script.py)

ls

python3 -m venv name\_env —system-site-packages

source venv/bin/activate

pip list

pip list —local

[](https://www.youtube.com/watch?v=Kg1Yvry_Ydk)[https://www.youtube.com/watch?v=Kg1Yvry\_Ydk](https://www.youtube.com/watch?v=Kg1Yvry_Ydk)

## python2 env

sudo /usr/bin/easy\_install virtualenv # 安裝virtualenv

cd 你要的資料夾路徑

virtualenv name --python=python2.7

## packages

pip install numpy

pip install matplotlib

pip install pandas

pip install --upgrade tensorflow

pip install jupyterlab

pip install scikit-learn

## add virtual environment to Jupyter lab

python -m ipykernel install --user --name=package\_env

[Using Virtual Environments in Jupyter Notebook and Python](https://janakiev.com/blog/jupyter-virtual-envs/)

## pip3 --version

pip 19.2.3 from /Users/lnl/Documents/pythontest/test1213\_venv/lib/python3.8/site-packages/pip (python 3.8)

## upgrade pip

sudo python -m pip install --upgrade pip

pip3 —version

pip 20.3.1 from /Users/lnl/Documents/pythontest/test1213\_venv/lib/python3.8/site-packages/pip (python 3.8)

which pip # 顯示現在pip在哪裏

`pip list` # 顯示裡面有什麼套件

deactivate

pip --version

pip 20.3.1 from/Library/Frameworks/Python.framework/Versions/3.8/lib/python3.8/site-packages/pip (python 3.8)

## **跑了 pip install，那東西到底被裝到哪裡去了？ 😕**

`pip install` 會有預設安裝的 dir，也會因為各種參數去改變，像是：`--target`, `--user`, `--prefix`, `--root` 等等。

有兩個方法可以看被裝在哪：

1.  最簡單的方法是剛才講到的，`pip --version` (或是`pip -V`)會顯示目前這個 pip 是跑哪一個 `site-packages` 下的 `pip` package ，這個路徑就是 install 時會放的 dir
2.  或，比較間接的方法，先用 `pip list` 列出所有已經安裝的 pkg，然後用 `pip show [某pkg]` 就會寫 Location 在哪

## How to fix ‘“ERROR: Command errored out with exit status 1:” when trying to install \_\_\_\_\_\_\_ using pip

You need to upgrade `setuptools` and pip

```python
pip install -U pip setuptools
```