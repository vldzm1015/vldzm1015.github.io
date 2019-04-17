---
layout: post
title:  "how to import csv file to Mysql(character set) // csv파일을 Mysql에 import하면 한글이 깨진다 ? character set !!"
subtitle:   "MYSQL COL"
categories: db
tags: database, mysql, character set
comments: true
---
<br>

* Mysql에 csv파일로 데이터를 import 할 때, 제대로 한글 데이터가 들어가지 않는 경우가 종종 있다.
이럴 때는 보통 다음의 3가지를 확인해보아야 한다.

        1. csv 인코딩이 제대로 되었는지(특히 맥에서는)
        2. 데이터베이스 character set
        3. 해당 테이블-컬럼의 character set

* 1번 문제: 해당 문제의 경우는, 다른 텍스트 에디터를 사용해서 utf8로 인코딩해주면 해결됨
https://stackoverflow.com/questions/4221176/excel-to-csv-with-utf8-encoding
해당 링크를 참조해보자. 오래된 글이지만 여전히 맥에서는 문제가 되는 부분이다.

* 2번 문제: 데이터베이스의 character set을 확인하려면 다음의 쿼리를 실행해보자.

```
SHOW VARIABLES LIKE "c%";
```

하면 다음과 같은 결과물을 볼 수 있다.

<img src="https://github.com/ehan831/ehan831.github.io/blob/master/assets/img/180827_characterset/cs5.png?raw=true" weight="50%">
<br>
<br>

* csv 파일의 character set을 확인했고, 데이터베이스 설정도 확인했는데 한글 데이터가 제대로 import 안된다면 다음의 문제를 확인할 차례이다. 3번 문제!! 컬럼의 character set !!
<br>
<br>

## Mysql column character set & collation
<br>

* database의 전체에 적용되어 있는 character set과는 별개로 테이블의 컬럼마다 존재하고 있다.
<br>

* workbench를 사용해서 확인해보면 다음과 같이 확인 가능하다. 해당 테이블 선택 후 i 클릭

<img src="https://github.com/ehan831/ehan831.github.io/blob/master/assets/img/180827_characterset/cs1.png?raw=true">
<br>

* 해당 정보를 조회하는 쿼리는 다음과 같다.

```
SHOW FULL COLUMNS FROM {dbname}.{tablename};

예시: SHOW FULL COLUMNS FROM testdb.testtable;
```
<br>

* 컬럼 별로 character set을 변경하는 법은

```
ALTER TABLE {tablename} MODIFY {col name} {col type} CHARACTER SET {charset name};

예시: ALTER TABLE testtable MODIFY testcol CHAR(50) CHARACTER SET utf8;
```
[MYSQL 공식문서 링크](https://dev.mysql.com/doc/mysql-g11n-excerpt/5.7/en/charset-conversion.html)
<br>

* character set만 지정해줘도 collation은 자동 설정이 되네요.
<br>
<br>

## 테이블 생성 단계에서도 다음과 같이 설정이 가능함.
<br>

* 테이블 생성/수정

```
CREATE TABLE t1
  (
      col1 VARCHAR(5)
        CHARACTER SET latin1
        COLLATE latin1_german1_ci
  );
  
ALTER TABLE t1 MODIFY col1 
  VARCHAR(5)
  CHARACTER SET latin1
  COLLATE latin1_swedish_ci;
```
<br>
<br>

## 가능한 character set은 다음과 같이 확인 가능함

```
SHOW CHARACTER SET;
```
<br>

<img src="https://github.com/ehan831/ehan831.github.io/blob/master/assets/img/180827_characterset/cs3.png?raw=true">

## 쨔쟌. 여기까지 했는데도 계속 문제가 발생한다면, character set 말고 다른 부분을 고민해봐야 될 차례!! 