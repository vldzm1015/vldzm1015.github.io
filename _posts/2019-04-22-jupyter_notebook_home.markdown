---
layout: post
title:  "change the home directory for jupyter notebook(mac) 쥬피터 노트북 홈 변경"
date:   2019-04-22 12:00:00
categories: jupyter
tags: jupyter notebook ipython home directory mac
author: ehan831
mathjax: true
---

# 쥬피터 노트북 홈 디렉토리 변경하기
---

<br>
아나콘다 설치 후, 주피터 노트북을 실행하면 손쉽게 실행 가능.
홈 경로를 바꾸고 싶다면 다음과 같이 하기
<br>

## 1. 주피터 노트북 프로파일 만들기
---

`$ jupyter notebook --generate-config`
을 터미널에서 실행하면 (실행 디렉토리 위치와는 상관이 없음. 알아서 주피터 노트북 해당 폴더에 만든다.)

아나콘다 기본 경로로 설치 시
username/.jupyter/jupyter_notebook_config.py 파일이 만들어진다. 


## 2. jupyter_notebook_config.py 에서 홈 경로 바꾸기
---
![config.py](https://blog.naver.com/PostList.nhn?blogId=ehan831&widgetTypeCall=true&directAccess=true#)

214번째 줄에서 
주석 # 삭제하고
c.NotebookApp.notebook_dir = '원하는 경로'
에 원하는 경로를 입력해주기.
<br>
​
저장 후 주피터 노트북을 실행하면 잘 바뀌어 있는 것을 확인할 수 있다.

## 해당 파일로 다양한 설정이 가능하다고 함
---

패스워드 설정까지 하신 분의 글 링크(plusjune님)
[password setting](https://financedata.github.io/posts/jupyter-notebook-authentication.html)