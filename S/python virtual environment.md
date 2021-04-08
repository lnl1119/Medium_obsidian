---
date: 2021/04/04 
tags: ["#python", "#medium"] 
aliases: 
- [python#01]在macOS終端機用pip建立python虛擬環境(step by step tutorial)
---
# [python#01]在macOS終端機用pip建立python虛擬環境(step by step tutorial)
#python #terminal #Mac

**（此篇以macOS 系統為例）**

**目錄**  
[0\. 前言](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#80d3)  
[1\. 為什麼要建立虛擬環境(Virtual Environment)](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#6b1c)  
[2\. 開始建立你的虛擬環境](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#f37d)  
  [2.1 建立新的虛擬環境](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#0a62)  
  [2.2 啟動已建立虛擬環境的SOP](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#e2b0)  
[3\. 懶人包](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#e21b)

# **0\. 前言**

開始碰機器學習至今，經歷過最一開始的安裝Anaconda，找不到套件的路徑後被折騰到電腦重灌，因此立志要奪回對所有套件位置和自己電腦的掌控權力，畢竟平常真的會用到的套件不多。在macOS上主要會用 **terminal** 進行操作，因此如果希望完全掌握整個環境的話，其實是要從Linux的bash開始(推[鳥哥的Linux私房菜第十章](http://linux.vbird.org/linux_basic/0320bash.php))，不過這裡就直接懶人包取用。

![](https://miro.medium.com/max/60/1*m8MURCq1z0CnKoRrWW6PjQ.png?q=20)

![](https://miro.medium.com/max/1966/1*m8MURCq1z0CnKoRrWW6PjQ.png)

## 0.1 Anaconda 不好嗎？

半路出家機器學習，不論是線上課還是實體課，老師們的起手式都是直接放出我們的**綠大蟒Anaconda**(先別走～這裡不會講anaconda)

![](https://miro.medium.com/max/60/1*S2kkcLC8IExHKkhvmpw_Lg.png?q=20)

![](https://miro.medium.com/max/894/1*S2kkcLC8IExHKkhvmpw_Lg.png)

一頓安裝後，根據老師的說法：

> 你的電腦已經具備**入門**機器學習需要的**所有**東西，不用擔心**套件**和**環境囉！**

不過他沒告訴你的是，什麼都有的同時（還不包含Tensorflow和Keras），也有一隻3GB大的蟒蛇散布在電腦的各個地方。哪天你被機器學習打敗想把他請走，他會向分靈體一樣，你以為已經是最後一個了，換了一個系統清理軟體，依舊可以找到殘存的檔案，也因此會有下面這種教你如何「手動」將anaconda清乾淨的大神文。（目前還沒看到mac版本的教學）

[

## 還我乾淨環境！怒砍Anaconda ! 手動移除windows Anaconda 殘留檔案！

### 相關文章：為什麼我的Python 總是學不好? 入門必看！Windows 懶人搭建Anaconda Python 學習環境

medium.com



](https://medium.com/%E8%AA%A4%E9%97%96%E6%95%B8%E6%93%9A%E5%8F%A2%E6%9E%97%E7%9A%84%E5%95%86%E7%AE%A1%E4%BA%BAzino/%E9%82%84%E6%88%91%E4%B9%BE%E6%B7%A8%E7%92%B0%E5%A2%83-%E6%80%92%E7%A0%8Danaconda-%E6%89%8B%E5%8B%95%E7%A7%BB%E9%99%A4windows-anaconda-%E6%AE%98%E7%95%99%E6%AA%94%E6%A1%88-666d88eae69d)

總結來說，我不能否定Anaconda強大的**一鍵入門**，但如果你符合以下任何一點，歡迎你繼續看下去：

1.  電腦跟我一樣只有最低的128GB，且[Anaconda附贈的諸多套件](https://docs.continuum.io/anaconda/packages/pkg-docs/)你其實都不太會用到。
2.  安裝Anaconda沒有的套件（例如TensorFlow）卻怎麼import也沒用，網路爬文說是路徑問題，但照著解決後下次遇到的問題好像同一個方法又不適用。

# 1\. 為什麼要建立虛擬環境(Virtual Environment)

## **1.1 避免跟mac原本的環境搞混**

macOS系統本身有內建 python2.7.16，最新的 python 截至現在更新到了 python3.9.2。當你打開 terminal 直接輸入 `python --version` ，沒意外會吃到 macOS 自帶的 python2.7.16。如果想要有最新的 python3，可以到 python 的官網下載，然後輸入`python3 --version`，就會看到我的版本是`python3.8.2` 。如過對 terminal 和路徑不熟，在你完全不知道 terminal 預設呼叫的 python 是哪個版本的前提下，你非常有可能會用錯python版本。

![](https://miro.medium.com/max/60/1*qajwZiHXTb9Q8SbZQ2kFJQ.png?q=20)

![](https://miro.medium.com/max/1632/1*qajwZiHXTb9Q8SbZQ2kFJQ.png)

## **1.2 需要使用不同版本的套件**

進行不同專案的時候會用到不同套件，甚至是同一個套件的不同版本。可能是python一些狀況只支援 python2，也有可能是你需要的pandas是pandas0.19.2，但你目前是最新的pandas1.2.3。當然都是有辦法降級或升級的，但如果你同時需要用到兩種版本，虛擬環境可以很輕鬆地將兩者分開。

> 簡單來說，虛擬環境就是一個資料夾，很直觀地包著你安裝的所有套件，與電腦獨立。

# 2\. 開始建立你的虛擬環境

在不裝Anaconda的前提下，這裡會使用最常見的`pip`來管理python環境，也會用最常見的虛擬環境 `venv`(virtual environment的縮寫)。

以下將分成兩個部分：

1.  建立新的虛擬環境
2.  啟動已建立虛擬環境的SOP

第一部分只要做一次就好，之後就只要執行第二部分就可以了。

## 2.1 建立新的虛擬環境

我的習慣是會先建立一個**空的資料夾**當作虛擬環境的領地，可以將 **虛擬環境** 以及 **會用到它的專案** 放在同一層資料夾中。以下包含

[2.1.1 到你想要建新資料夾的地方](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#431b)  
[2.1.2 建立新資料夾](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#2ee7)  
[2.1.3 進去你剛建的資料夾](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#bcec)  
[2.1.4 建立虛擬環境](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#01cf)

## 2.1.1 到你想要建新資料夾的地方

打開terminal，直接輸入你想要到的資料夾的地址（這裡以「文件」為例）

cd /Users/你的電腦名稱/Documents

> 如何得到資料夾地址

`/Users/電腦名稱/Documents`的由來可以參考下面影片。

![](https://miro.medium.com/freeze/max/60/1*O2GB0sgBcLxW1UouJyKrew.gif?q=20)

![](https://miro.medium.com/max/2160/1*O2GB0sgBcLxW1UouJyKrew.gif)

\[影片文字描述，看懂影片可跳過\]  
找到任何你想要知道地址的資料夾(以「文件」為例)，對資料夾點右鍵（觸控板預設是兩指同時點）會跳出選單，按住 **option⌥** 會有隱藏菜單，點 **拷貝「」做為路徑名稱** 就算成功複製，接著就可以直接**貼到terminal的****cd＋空格****後面**，按下 enter 。

## 2.1.2 建立新資料夾

> 當然，你可以**直接「右鍵→建立新資料夾」**

不過在terminal的方法就會是

mkdir newfolder\_name

資料夾名稱自己取囉～不過

> 不要用**中文，**也不要 `**-**` `**?**` `**:**` `**>**` `**<**`，最好是**單純英文配** `**_**`

## 2.1.3 進去你剛建的資料夾

> 不是從資料夾點進去！！
> 
> 是在terminal的路徑要進去

在terminal輸入

cd newfolder\_name

按enter後，如果你有一路跟著，現在你的terminal 如圖

![](https://miro.medium.com/max/60/1*OZqbbmyIXfPIDi9BGJmOkQ.png?q=20)

![](https://miro.medium.com/max/1014/1*OZqbbmyIXfPIDi9BGJmOkQ.png)

接下來要進到重頭戲囉！要正式建立虛擬環境囉！

## 2.1.4 建立虛擬環境

在terminal輸入

python3 -m venv name\_env

`name_env` 是虛擬環境的名稱，可以隨便取，一樣不要有中文或奇怪符號。按下 `enter` 後會小等一下，接著輸入 `ls` 來顯示這個資料夾裡面有什麼，如圖，現在裡面有你的虛擬環境囉～

![](https://miro.medium.com/max/60/1*G4WhXyB1ko7j6rWAHckLIw.png?q=20)

![](https://miro.medium.com/max/1322/1*G4WhXyB1ko7j6rWAHckLIw.png)

以上就是 **2.1 建立新的虛擬環境**，目前只有**建立**，接下來要介紹**啟動。**

[**返回總目錄**](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#d3a8)**｜**[**返回 2.1 建立新的虛擬環境目錄**](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#0a62)

## 2.2 啟動已建立虛擬環境的SOP

[2.2.1 啟動虛擬環境](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#b5a3)  
[2.2.2 小小確認有沒有啟動](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#faa0)  
[2.2.3 查看已有哪些套件](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#fcfe)  
[2.2.4 安裝套件](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#45e9)  
[2.2.5 關閉虛擬環境](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#781b)

## 2.2.1 啟動虛擬環境

source name\_env/bin/activate

> 恭喜你，你已經啟動你的虛擬環境了

## 2.2.2 小小確認有沒有啟動

確認你已經啟動虛擬環境的方式：

1.  如圖，最前面會出現(name\_env)，代表你已經在這個虛擬環境中。

![](https://miro.medium.com/max/60/1*_6G4ICZmko_oDg6O1NYsgQ.png?q=20)

![](https://miro.medium.com/max/1400/1*_6G4ICZmko_oDg6O1NYsgQ.png)

2\. 輸入 `which python3` ，會得到你現在使用的python3是從哪來的，而顯示的就會是你虛擬環境的地址。

![](https://miro.medium.com/max/60/1*pAzxSyuNBjwtKx1R4sGw2A.png?q=20)

![](https://miro.medium.com/max/2656/1*pAzxSyuNBjwtKx1R4sGw2A.png)

## 2.2.3 查看已有哪些套件

會使用python最主要的原因就是因為他功能強大的套件，所以我們現在來處理套件的部分。 `pip3 list` 可以顯示出你目前這個虛擬環境中有哪些套件。如圖，最原始版本只有pip和setuptools。下一步我們來安裝吧！

![](https://miro.medium.com/max/60/1*nl9nV2f1ANNUjIdi2j-s_Q.png?q=20)

![](https://miro.medium.com/max/2536/1*nl9nV2f1ANNUjIdi2j-s_Q.png)

## 2.2.4 安裝套件

由於我們的虛擬環境是用 `pip` 建立的，所以安裝套件就是用 `pip install` 為開頭。以 `pandas` 為例就是`pip install pandas` ，想確定的話可以google pip install pandas，跳出[pipy官方網站](https://pypi.org/)，可以直接點copy to clipboard再貼到terminal。

![](https://miro.medium.com/max/60/1*0hW3Q15plaOC8-Bqa4Ljkg.png?q=20)

![](https://miro.medium.com/max/3804/1*0hW3Q15plaOC8-Bqa4Ljkg.png)

以下整理基本上一定會用到的套件：

pip install pandas  
pip install numpy  
pip install matplotlib  
pip install jupyterlabpip install seaborn  
pip install — upgrade tensorflow  
pip install scikit-learn  
pip install Keras

## 2.2.5 關閉虛擬環境

假設你是用jupyter notebook 或是 jupyter lab，結束的時候要先在terminal輸入 `control⌃+c` 終止jupyter，接著輸入 `deactivate` 來關閉虛擬環境。如下圖最前面(name\_env)消失了，那就代表你關閉虛擬環境了。

![](https://miro.medium.com/max/60/1*jV4Ix177ehz6SUioAlT-dg.png?q=20)

![](https://miro.medium.com/max/2552/1*jV4Ix177ehz6SUioAlT-dg.png)

[返回**總目錄**](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#d3a8)｜[返回 **2.2 啟動已建立虛擬環境的SOP目錄**](https://medium.com/%E6%B7%B7%E8%A1%80%E6%A9%9F%E5%99%A8%E5%AD%B8%E7%BF%92%E7%AD%86%E8%A8%98/python-01-%E5%9C%A8macos%E7%B5%82%E7%AB%AF%E6%A9%9F%E7%94%A8pip%E5%BB%BA%E7%AB%8Bpython%E8%99%9B%E6%93%AC%E7%92%B0%E5%A2%83-step-by-step-tutorial-628719bdc7e3#e2b0)

## 3\. 懶人包

3.1 建立虛擬環境

cd /Users/你的電腦名稱/Documents #到你要的資料夾  
mkdir newfolder\_name #新增資料夾  
cd newfolder\_name #進到資料夾  
python3 -m venv name\_env #建立虛擬環境

3.2 開啟虛擬環境SOP

cd /Users/你的電腦名稱/Documents/newfolder\_name #到有虛擬環境的資料夾  
source name\_env/bin/activate #開啟虛擬環境  
jupyter lab #開啟jupyter lab，接著就可以開始使用