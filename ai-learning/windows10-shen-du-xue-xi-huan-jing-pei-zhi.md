# windows10深度學習環境配置

自己配置深度學習環境的時候出了很多問題，最主要自己以前是雙系統，ubuntu刪了，不太好重裝，win10踩了好多坑，最後終於成功了，記錄一下過程。

先放一張成果圖

成果圖

1.anaconda下載，從官網正常下，用迅雷速度挺快。附上下載地址 anaconda for windows

需註意：安裝過程中，有個Add anaconda to my PATH environment variable,記得選上。

anaconda

最後，在開始菜單搜索anaconda，有的話就可了，安裝成功。

2.安裝CUDA和cudnn，這個需要科學上網，得有谷歌號（別著急關掉），很麻煩，我自己搞了個科學上網，這倆下了下來，但不能全部適用。

GPU

首先找到你的英偉達驅動，查看gpu型號所對應的CUDA，這個是向下兼容的，也就是說，他說適應的版本及其以下都行，我給的這個鏈接11.0以下都可以用。打開它

找到組件，這裏顯示的是 CUDA 11.1.114 說明這個版本以下都可以用。鏈接：CUDA 和cudnn 提取碼：2qkx

cuda的安裝，我自己安裝的時候出了點問題，第一次安裝電腦自動重啟了，第二次裝就好了。

CUDA

cmd 命令行 敲 nvcc -V

如果出現上圖這樣就成功了。

接下來是cudnn，下載完成後，將壓縮包解壓後，把裏面的三個文件夾裏面的文件放到CUDA9安裝目錄相應文件夾下即可\(一般安裝的目錄是C:\Program Files\NVIDIA GPU Computing Toolkit\)。這三個是完全覆蓋掉裏面的，也就是替換。我在這個裝C盤的，

這是博主的路徑，第一次裝的時候留下了遺留文件，一直沒找到那個路徑，在C盤裏搜的關鍵字 NVIDA GPU 找到了。替換完成之後，在cmd裏面 cd C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v10.1\extras\demo\_suite（就是剛才替換文件夾的路徑了），然後分別敲兩個 deviceQuery.exe 和 bandwithTest.exe。如果以上兩步都返回了Result=PASS，那麽就算成功了！

到此，cuda和cudnn的安裝結束。

3.安裝pytorch，tensorflow等等，這個需要給windows換個源，具體是

\(1\)在windows文件管理器中,輸入 %APPDATA%

\(2\)會定位到一個新的目錄下，在該目錄下新建pip文件夾，然後到pip文件夾裏面去新建個pip.ini文件

\(3\)在新建的pip.ini文件中輸入以下內容

\[global\]

timeout = 6000

index-url = https://pypi.tuna.tsinghua.edu.cn/simple

trusted-host = pypi.tuna.tsinghua.edu.cn

或者是 阿裏的源 我用的是阿裏的

\[global\]

index-url=http://mirrors.aliyun.com/pypi/simple/

\[install\]

trusted-host=mirrors.aliyun.com

換好之後 reboot

reboot之後，cmd 敲 pip install tensorflow

或者打開 pytroch 官網 https://pytorch.org/

cmd敲 PIP下的你裝的CUDA版本

安裝完成之後，敲 import torch

 print（torch.\_\_version\_\_\)

 print\(‘ gpu ：’，torch.cuda.is\_available\(\)\)

得到正確的輸出就行了 ，True。

這裏需要註意一點，有的需要安裝VC的缺失內容，你根據報錯提示的鏈接內容下載就行，速度很快

至此，安裝結束。

4.為vscode設置工作區

打開之後shift+ctrl+p找到你的anaconda的路徑，

正常設置，博主這裏是python3.8.5,至此全部完成。

註意：我這裏把我自己電腦裏裝的python卸載裝的anaconda裏面的python，所以用的話設置的話也是anaconda裏面的python.exe。有人用pycharm，我的pycharm弄了很多回，總是弄不好，就想到了用vscode來設置。

