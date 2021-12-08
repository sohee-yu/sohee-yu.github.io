---
layout: single
title: "[Oracle]Data Schema와 export - SQLDeveloper"
---

# Data Schema와 export

사담 :
Oracle DB를 사용하는 개발자들이 주로 사용하는것 같은 툴로는 SqlDeveloper 또는 Orange for Oracle이 있는것 같은데...
사실 Orange는 사용 안해봤고, 코딩학원때도 썻던 SqlDeveloper 사용중...

--작성된 테이블 목록 확인
SELECT _ FROM tab; -- tabs보다 간단하게
SELECT _ FROM tabs;

--테이블의 구조 확인(스키마)
SELECT _ FROM col WHERE tname='테이블명'; --간단히 출력
SELECT _ FROM cols WHERE table name='테이블명';

=> 홑따옴표에 테이블명 대문자로 입력해야한다
( 그냥 데이터 조회 할때 소문자로 쓰던 습관이 있다면 잉?포인트)

-- sqlplus, sql developer에서는 다음과 같이 스키마를 확인 가능

DESC 테이블명;

- 스키마와 데이터를 같이 달라고 요청하는 경우가 있기때문에 추가해 봄

* export 하는 방법은 굉장히 간단함

1. 조회
2. 데이터 우클릭
3. export
4. 'xlsx' 파일로 export 하려면 Excel 2003 선택하고 파일명, 시트명 입력 후 , 저장 위치확인 -> 다음 -> 완료

하면 끝!
