---
layout: post
title:  "change the home directory for jupyter notebook(mac)"
date:   2019-04-22 12:00:00
categories: jupyter
tags: jupyter notebook ipython home directory mac
author: ehan831
mathjax: true
---

# 쥬피터 노트북 홈 디렉토리 변경하기
---

<br>

>change the home directory for jupyter notebook(mac)

>아나콘다 홈 디렉토리 변경하기(맥)

<br>

### 1. 주피터 노트북 프로파일 만들기
---

`$ jupyter notebook --generate-config` 을 터미널에서 실행 <br>
- 실행 디렉토리 위치와는 상관이 없음
- 주피터 노트북 폴더에 알아서 만듬
- 자동으로 안되면, PATH 설정 확인하기

아나콘다 기본 경로 기준
`username/.jupyter/jupyter_notebook_config.py` <br>
파일이 만들어진다. 


### 2. jupyter_notebook_config.py 에서 홈 경로 바꾸기
---
<img src = "http://blogfiles.naver.net/MjAxOTAzMTJfMTEy/MDAxNTUyMzkxMzc0MzY3.XM41PfiUQIUpKCyP5P7HU3pOmtSggU6IvdBpQiyzfhIg.dr9FB0a_Ayt1MozVUR2zlbnJg75K88-Fsn4pprA7xNwg.PNG.ehan831/SE-a049db7c-e55f-4e9a-9c91-951979bcb7f4.png">
<br>
<br>

- 214번째 줄에서 주석 # 삭제하고,
- `c.NotebookApp.notebook_dir = ''` 에
- '원하는 경로'에 홈 경로를 입력하기 
<br>
​

저장 후 주피터 노트북을 실행하면 잘 바뀌어 있는 것을 확인할 수 있다.
<br>

### config.py 로 다양한 설정이 가능
---

> [config.py로 패스워드 설정 링크 - plusjune님](https://financedata.github.io/posts/jupyter-notebook-authentication.html)