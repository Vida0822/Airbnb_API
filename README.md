# :pushpin: Procedure를 활용한 Airbnb 기능구현 

> Oracle의 PLSQL(Procedure)을 활용한 에어비엔비 기능 구현 (데이터베이스 기반 프로그래밍) 

</br> 

### 목차

1. 제작기간 & 참여 인원  <br>
2. 사용 기술  <br>
3. 프로젝트 개요<br>
4. 개발단계 및 일정  <br>
5. 요구분석 
6. DB 모델링 : ERD / EXERD 설계    <br>
8. 핵심기능 코딩: Use-case Diagram    <br>
9. 트러블 슈팅  <br>
10. 발표영상 (본인 발표) 
11. 프로젝트 회고 <br>

</br></br>



## 1. 제작 기간 & 참여 인원 

👩‍👧‍👧 팀 프로젝트 (7인)<br>

📆 2023 3월 31일 ~ 4월 10일 (10일)  <br>

</br>

## 2. 사용 기술  

- PL/SQL <br>
- 툴 : Oracle Database 19c (sql plus) / SQL Developer    <br>

</br>



## 3. 프로젝트 개요

​	이 프로젝트는 데이터베이스 기반 프로그래밍으로 구현한 sql 프로젝트이다. 프론트앤드와 백앤드 기술 없이, 즉 화면 구현 및 서버 코딩을 하지 않고 특정 기능을 실행했을 때 발생하는 db의 변화(쿼리 실행결과)만 확인한다. 세계 최대의 숙박 공유 서비스, 'airbnb'의 웹 사이트를 주제로 선정하였으며 요구분석을 바탕으로 DB를 설계한 후 해당 기능을 수행하는 쿼리를 작성했다. 프로젝트 쿼리는 Oracle의 pl/sql(procedure)로만 작성되었다. 

</br>



## 4. 개발단계 및 일정 

​	 이번 데이터베이스 기반 기능구현을 위해, 우리는 개발 단계 및 업무를 크게 3가지로 나누었다.  <br>

1. 요구분석  <br>

2. DB 모델링  <br>

3. CRUD 기능구현  <br> </br>

   

<details>
<summary><b> 개발단계 3 steps 상세</b></summary>
<div markdown="1">

**1st step : [요구분석]** <br>

1. **핵심 업무 프로세스 파악** : 사이트 전체적인 흐름 파악 => 액터 도출  <br>
2. **디테일한 기능 파악** : 각 액터별&기능별 상세한 기능/화면구성 파악  <br>
3. **요구분석서 작성** : 팀원들과 충분한 논의 후 최종적인 요구분석 취합본 작성 <br> </br>


**2nd step : [DB 모델링]** (**다같이)*<br>

1) **개념적 DB 모델링**<br>

    : 1-개체(entity) 추출 2-속성(Attribute)추출 3-관계(R)정의 => ERD *<br>

2) **논리적 DB 모델링** <br>

   1- ERD를 보고 1:1로 매칭시키는 매핑규칙(mapping rule)에 따라 스키마를 설계 => eXERD * <br>

   2- 정규화 <br>

   3- 사용할 DBMS 결정 	<br>

3) **물리적 DB 모델링** : 자료형, 크기, 역정규화 <br>

   - 컬럼 확정: 타입, 크기 <br>

   - 데이터의 사용량 분석해서 효율적인 데이터베이스가 될 수 있도록 역정규화 작업 <br>

   - 성능위해 인덱스 처리 <br>

 4) **DB 구축** : 테이블 생성 및 데이터 입력 <br>

    * 설계한 스키마에 따라 테이블을 생성한다</br>

      

**3rd step : [쿼리 작성: CRUD 기능구현]** (**3팀으로 나눠서 분담작업)*  <br>

: 데이터 처리 과정  (**상세한 요구분석 바탕**으로 실제로 그 작업을 쿼리로 구현)  <br>

* **데이터 조회** : 프로세스상 중요한 필수 표시 페이지를 구현, 데이터를 조회한다 - **SELECT** <br>

* **데이터 입력** : 각 스키마에 맞는 데이터를 입력하여 테이블을 채운다 -**INSERT** <br>

* **데이터 수정** : 변경사항을 반영하는 기능을 구현한다 - **UPDATE**  <br>

* **데이터 삭제** : 등록한 데이터들을 다시 삭제하는 기능을 구현한다 - **DELETE** <br>

* **권한 처리** : 각 사용자에 따라 권한(사용가능한 기능)을 설정해 부여한다 - **기능 구현 후 권한설정코딩 추가**<br>

</div>
</details>

</br>

<details>
<summary><b> 개발일정 펼치기</b></summary>
<div markdown="1">

​	위의 개발 단계 및 각 업무 내용을 기반해 개발일정을 다음과 같이 수립했다. 

**03/31 (금)** 각자 전반적인 프로세스 파악 후 요구분석 양식 채워오기 

**04/01 (토)** 요구분석 완료 

**04/02 (일)** 요구분석서 취합본 작성  

------------- *요구분석(서)* ----------------- 

**04/03 (월)** 개념적 DB 모델링 (ERD 작성) 

**04/04 (화)** 물리적 DB 모델링 (eXERD 작성) 

**04/05 (수)** DB 구축 (테이블 생성&데이터 엑셀로 정리 후 임포트)  +  구현할 페이지와 기능정리 & 쿼리 역할분담 

-------------*DB 모델링* ----------------------

**04/06 (목)** 기능구현(쿼리작업) 

**04/07 (금)** 기능구현(쿼리작업) 

----------------*쿼리작업* ---------------

**04/08 (토)** 기능구현(쿼리작업완료) + 발표준비 병행 

**04/09 (일)** 발표준비

---------------*ppt+ 발표준비* ---------------- 

**04/10 (월)** 발표일! 

</div>
</details>

</br>

## 5. 요구분석  

​	첫 단계로, 다같이 사이트를 분석하며 전체적인 흐름을 파악해 액터를 도출한 후, 각 액터별&기능별 상세기능과 화면구성을 파악하여 최종적인 요구분석 취합본을 작성하였다.

<details>
<summary><b> 요구사항문서 펼치기</b></summary>
<div markdown="1">
<img width="625" alt="요구분석1" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/4199f32d-01ff-44a1-b1ad-e42fc912dd7c">
<img width="625" alt="요구분석2" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/fb136df1-4c2b-46fd-8b7f-10a32eec5f8f">
<img width="625" alt="요구분석3" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/e648d9eb-82b4-4262-b770-5d712d7458b8">
<img width="625" alt="요구분석4" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/4e2428f0-a9c5-4773-814a-6e581b142df5">
<img width="625" alt="요구분석5" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/306c2004-5c89-470d-a111-c6cc6ae933a9">
<img width="625" alt="요구분석6" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/91c88ad9-2c0b-496e-8fa8-c82758836624">
<img width="625" alt="요구분석7" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/5922653f-048c-4ea8-aa10-01e57dab9626">
<img width="625" alt="요구분석8" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/863153b3-aba8-451d-9f9c-9ace24e17289">
<img width="625" alt="요구분석9" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/4cb59dba-659b-4d31-81ee-6951e13001bb">
<img width="625" alt="요구분석10" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/8bc11931-e3ee-4ac9-8428-954b2d38046a">
<img width="625" alt="요구분석11" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/6ad4876a-769c-4a45-bb83-3792ea2d2f40">
<img width="625" alt="요구분석12" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/bc013c4b-782e-4dca-8ca2-e7765d019a4b">
<img width="625" alt="요구분석13" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/53183c9c-47b8-41ae-860d-9305a2c6f094">

</div>
</details>

</br>


## 6. DB 모델링 : ERD / EXERD 설계

<details>
<summary><b> 모델링 펼치기 </b></summary>
<div markdown="1">

### 6.1. 개체 및 속성 정리 

<img width="625" alt="개체정리1" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/3b487bb8-6578-4893-a69e-6dd0eb424b88">
<img width="625" alt="개체정리2" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/55ba9768-a04f-4f93-b270-05be7164b6eb">
<img width="625" alt="개체정리3" src="https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/90a26990-7e10-42d8-ad5f-1dcdb2a1db9e">

</br>



### 6.2. 개념적 모델링 : ERD 설계  

​	위와 같은 요구분석을 바탕으로, 우리는 개체 및 속성을 추출한후 개체간의 관계를 정의하는 개념적 모델링을 통해 erd를 설계했다. 개체와 속성을 필기?로 정리할 땐 테이블간 관계를 명확히 파악하기 위해 편의상 기본키 및 외래키를 PK,FK로 표시하며 모두 작성해주었고 erd는 설계 규칙에 따라 외래키를 생략하고 PK대신 밑줄로 기본키임을 나타냈다. 

![에어비앤비_DB모델링_개념적모델링(erd)](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/98d5d17e-12c1-4607-b9c4-d28d2783b4a2)








### 6.3. 물리적, 논리적 모델링 : eXERD 설계  

​	개념적 모델링을 마친 후 설계한 ERD를 1:1로 매칭시키는 매핑규칙(mapping rule)에 따라 DBMS가 지원하는 스키마로 설계하는 정규화 과정(논리적 모델링)과 세부적인 칼럼의 종류 및 자료형과 크기를 확정하고 효율적인 데이터베이스가 되도록 역정규화하는 물리적 모델링을 진행했다. <br>

​	

- **사용 툴: eXERD**

![eXERD](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/78875f7e-b042-4304-8b68-0eafcc9b614b)

​	


### 6.4. DB 구축 : 테이블 생성 , 데이터 임포트 

1. 테이블 생성

exerd의 '포워드 엔지니어링' 기능을 사용하여 SQL Developer의 계정에 쉽게 데이터베이스를 설계했습니다.

2. 데이터 임포트

eXERD로 설계한 데이터베이스에 실제 사이트의 데이터를 엑셀로 정리한 후, SQL Developer의 '데이터 임포트' 기능을 활용하여 각 테이블에 맞게 데이터를 삽입했습니다.

![데이터 임포트](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/04ea32cf-e4e3-4d94-8145-4a2d36141c11)

</div>
</details>

</br>



## 7. 핵심 기능 (Use-case Diagram)


![use-diagram](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/assets/132312673/35208397-a982-4d9a-aaf2-9b9f3cfe20de)

* **고객**(Actor) : 사이트 처음 방문한 사람이 숙소를 조회하고 회원가입/ 로그인하기까지의 프로세스 <br>

* **회원**(Actor): 회원으로서 가능한  회원정보관리, 탈퇴하기까지의 프로세스   <br>

* **호스트**(Actor) : 호스트 계정 등록 -> 숙소를 등록하고 손님을 받을때까지 프로세스<br>

* **게스트**(Actor) : 숙소를 예약하고 여행을 다녀온 후 후기까지 남기는 프로세스 <br>



<details>
<summary><b>핵심 기능 설명 펼치기</b></summary>
<div markdown="1">


### 7.1. 액터 : 사용자

![핵심기능](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/76f2e20b-0c59-4eeb-914e-828974d0aaac)

* **숙소 목록조회** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L5)

  - 숙소유형으로 검색한 숙소들의 사진, 이름, 위치, 1박당 요금을 조회한 결과를 담을 cursor을 선언한다.

  - LOOP 반복문으로 커서에서 레코드를 하나씩 읽어와 검색된 숙소정보를 형식에 맞춰 출력하며 더 이상 레코드가 없을 때 종료한다. 

    

* **숙소 상세조회** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L46)

  - **편의시설목록 조회**
    : 편의시설 카테고리, 편의시설 이름을 cursor를 사용해 반복문으로 출력한다. 

  - **이용규칙목록 조회**
    : 게스트정원, 반려동물 동반여부, 체크인&체크아웃 시간을 cursor를 사용해 반복문으로 출력한다. 

  - **후기 목록 조회**

    * 미리 선언해둔 프로시저로 총 평점과 후기 수를 출력한다. 

    * 청결도, 정확성, 의사소통, 위치, 체크인, 가격대비 만족도를 cursor를 사용해 반복문으로 출력한다.

* **회원가입** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L247)

  - 사용자의 이름, 생년월일, 이메일, 전화번호, 지역을 입력받아 회원 테이블에 삽입한다.   
  - 전화번호를 길게 입력했을 경우 VALUE_ERROR  예외를 발생시킨다. 

* **로그인** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L282)

  - 사용자는 전화번호 또는 이메일로 로그인 할 수 있다. 
  - 회원 테이블에서 입력값으로 조회한 레코드개수가 한개면 로그인 성공이다. 
  - 로그인 실패 시 회원가입 안내 메세지를 출력한다.  
  
  

</br>

### 7.2. 액터 : 회원

![TennisMain](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/c1eac4bc-5e04-463a-b47c-f44d5680cfed)



- **회원정보 수정** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L345)
  
  - 이름, 이메일, 전화번호, 주소, 계좌 등 수정할 정보들을 매개변수(p-)로 입력 받는다.  
  
  - 회원 테이블의 칼럼들을 v-형 변수로 선언하여 수정하기 전 정보를 저장한다. 
  
  - NVL 함수를 사용해 수정 요청한 값은 입력한 값(p-)로, 요청하지 않은 값은 기존의 데이터(v-)로 Set하여 수정(update)한다 
  
    
  
- **회원 탈퇴** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L406)

  - 회원의 전화번호를 전달받아 조회한 레코드를 삭제(delete)한다.
  
  

</br>  

### 7.3. 액터 : 호스트

![scoreBoard](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/7410cb17-8dad-4a06-8fbb-d95e875b0611)

- **숙소 등록** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L436)

  - **숙소 기본정보 작성** : 위치, 정책, 숙소유형, 공간특징, 이름, 설명, 최대인원수, 1박당 가격, 위치, 침실&침대&욕실개수를 입력 받아 숙소 테이블(Room)에 삽입(insert)한다.

  - **사진 등록**: 5장의 사진 경로를 매개변수로 받아 현재 가입하고 있는 숙소의 코드를 외래키로 사진 테이블(photo)에 삽입(insert)한다.

  - 사진을 등록하면 숙소가 등록되며 숙소 상태는 '운영 정지'가 기본값으로 설정된다. 

    

- **숙소 기본정보 관리** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L542)

  - **숙소명 수정** : 입력된 숙소이름이 50자를 넘으면 VALUE_ERROR를 발생시킨다. 
  - **설명 수정** : 입력된 숙소설명이 200자를 넘으면 VALUE_ERROR를 발생시킨다. 
  - **게스트 수 수정** : 버튼 종류(+ 또는 -)를 매개변수로 받아 버튼을 누를때마다 즉각적으로 기존 게스트 수를 1명씩 증가/감소시킨다.
  - 주소 수정 : 주소를 입력받아 수정한다. 
  - 숙소유형 & 예약가능공간 수정 : 한 화면에서 동시에 수정하기 때문에 두 정보를 같이 매개변수로 받아 NVL 함수를 사용해 수정 요청한 값만 수정한다. 
  - 침실&침대&욕실 수 수정 : +,- 버튼으로 각각 수를 조절한 후 동시에 수정하기 때문에 버튼 클릭 횟수를 매개변수로 각각 받아 기존 값에 더해준다. 
  - 1박당 요금 수정 : 요금을 입력받아 수정한 후, 다른 숙소의 평균가격과 비교해 입력값이 높으면 낮추라는, 낮으면 높이라는 권고 메세지를 출력한다. 
  - 환불정책 수정 : '유연, 일반, 비교적 엄격, 엄격, 매우 엄격 30일, 매우 엄격 60일'로 수정할 수 있으며 이 정보는 환불 금액 산정 때 반영된다. 
  - 사업자 등록번호 수정 : 사업자 등록번호를 입력받아 수정한다.
  - 체크인, 체크아웃 시간 수정 : 시간을 입력받아 수정하되 입력된 체크아웃 시간이 1시~7시라면 v_cannot_reserve_exception 예외를 발생시킨다. 

  

- **숙소 세부정보 관리** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L897)

  - 편의시설 관리 : 편의시설 종류와 숙소 조합을 편의시설 설정 테이블에 등록/삭제한다.
  - 이용규칙 관리: 이용규칙 종류와 숙소 조합을 이용규칙 설정 테이블에 등록/삭제한다.
    * '반려동물 허용' 규칙 설정 시 최대 반려동물 수를 추가적으로 입력받아 숙소 테이블에 반영한다.  
    * '반려동물 허용' 규칙 해제 시 숙소 테이블의 최대 반려동물 수를 0으로 초기화하고 추가요금설정 테이블에 설정해준 반려동물 추가 요금 정보를 삭제한다. 
  - 할인제도 관리 : 할인제도 종류와 그에 따른 할인율, 할인적용기준 (일수)를 할인설정 테이블에 등록/수정/삭제한다.
    * 설정한 할인 제도가 ''주간할인' 인경우 7일로,  '월간할인'이면 30일로  할인 적용기준을 자동 설정한다. 
    * 할인율을 0으로 설정하면 해당 할인제도는 할인설정 테이블에서 삭제한다. 
  - 추가요금 관리  : 추가요금 종류와 그에 따른 추가금액, 추가요금 적용 기준(일수)를 추가요금 설정 테이블에 등록/ 수정/ 삭제한다.
    * 반려동물 추가요금 설정 시 이용규칙설정 테이블에 반려동물 허용 규칙을 자동으로 설정한다. 
    * 추가금액을 0으로 수정하면 해당 추가요금제도는 삭제한다. 
  
  
  
- **숙소 상태 수정** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L1209)

  - 호스트는 숙소상태를 '운영중, 운영중지, 비활성화' 로 수정할 수 있다. 
  - 이미 '비활성화' 상태라면 해당 숙소는 조회할 수 없으므로 v_no_more_visible 예외를 발생시킨다.
  - '비활성화'로 변경 시 다른 테이블의 해당 숙소와 관련된 정보(위시리스트, 이용규칙 등)를 전체 삭제하며, 해당 숙소의 남은 예약건은 '예약 거절'로 예약 상태를 바꾼다. 

 

</br>   


### 7.4. 액터 : 게스트

![dispScoreBoard](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/5f83dcb4-2c7b-4d38-894b-7446e2d8dae0)



- **위시리스트 관리** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L1273)
  - 위시리스트 조회 : 회원이 위시리스트로 등록한 숙소의 사진, 위치, 타입, 숙소 이름 , 침대개수를 목록으로 출력한다. 
  - 위시리스트 추가 : 회원과 숙소 조합을 위시리스트 테이블에 삽입하며, 같은 숙소를 두번 추가할 수 없도록 트리거를 설정해준다. 
  - 위시리스트 삭제 : 회원코드와 숙소코드로 조회한 레코드를 삭제(delete)한다. 


- **예약 관리** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L1393)
  
  - 예약 목록 조회: 예약이 완료된 숙소의 체크인 체크아웃 시간, 주소, 예약일, 호스트 정보를 목록으로 출력한다.
  - 예약 상세 조회: 상세보기를 요청한 숙소의 기본정보와 게스트 수 , 예약 번호, 환불 정책 등 추가 세부적인 정보와 함께 출력한다. 
  - 예약하기 
    * 기본요금에 예약 일수, 할인율, 추가요금을 반영해 최종 요금을 도출한다.
    * 예약이 없는 날에만 예약이 가능하며 총인원은 최대인원을 넘을수 없고 반려동물은 최대반려동물을 넘을 수 없도록 트리거를 설정해준다. 
  - 예약 수정 :  예약 수정시 가장 최근에 update 된 할인율, 추가요금 제도 등을 반영해 다시 요금을 계산한다. 
  - 예약 삭제 : 예약코드로 예약 테이블에서 해당 레코드를 삭제하되 이미 결제가 되었다면 환불 신청을 하도록 v_no_res_cancel 예외를 발생시킨다. 
  
- **결제 관리** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L1944)

  - 결제 목록 조회 : 결제가 완료된 예약건의 예약코드, 숙소 이름, 결제자 이름, 결제 날짜, 카드번호, 만료 날짜, 우편번호, 결제 금액을 목록으로 출력한다. 

  - 결제하기 : 결제 지역, 카드번호 , 만료기한 등의 정보를 입력받아 결제정보 테이블에 insert한다. 이때 예약상태가 '예정된 여행'이 아니면 결제를 할 수 없도록 트리거를 설정해준다. 

  - 결제 직접취소 방지 : 결제 후에는 환불절차를 거쳐야 결제 및 예약 취소를 할 수 있기 때문에 결제 테이블에서 직접적으로 레코드를 삭제할 수 없도록 트리거를 설정해준다. 

    

- **환불 관리** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L2067)

  - 환불 정보 조회:  환불이 완료된 결제건의 체크인 체크아웃 시간 , 주소, 예약일, 호스트 정보를 목록으로 출력한다.

  - 환불하기

    *  결제 테이블에 조회되는 값이 없으면 efund_cannot_exception  예외를 발생시키고 환불을 진행하지 않는다.
    * 환불금액을 계산하는 프로시저를 호출해 숙소의 환불정책을 적용한 최종 금액을 도출한다 
    * 환불 사유를 입력받아 환불 테이블에 삽입한다.
    * 환불이 추가한 뒤에는 예약의 예약상태가 취소한 여행으로 변경되도록 트리거를 설정한다.

    

- **후기 관리** :pushpin: [코드 확인](https://github.com/Vida0822/Airbnb_Oracle-PLSQL-Project/blob/f055b7a6074bbe3304f6fae73ab042c884d2c78a/%EC%97%90%EC%96%B4%EB%B9%84%EC%97%94%EB%B9%84%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8_%EA%B8%B0%EB%8A%A5%EA%B5%AC%ED%98%84(sql%20%EC%BF%BC%EB%A6%AC).sql#L2275)

  - 후기 작성
    * 후기 글과 함께 청결도, 정확성, 의사소통, 위치, 체크인, 가격대비만족도 각각의 항목에 별점을 매긴다.
    * 후기는 완료된 여행만, 그리고 한번만 작성하도록 트리거를 설정한다.
  - 후기 수정: NVL 함수로 수정한 항목별 점수만 반영한다. 
  - 후기 삭제: 삭제되기 전 예약정보의 후기 작성여부를 null로 변경되도록 트리거를 설정한다.  
  
  

</br>  



</div>
</details>

</br>

## 8. 핵심 트러블 슈팅

<details>
<summary><b>트러블 슈팅 설명 펼치기</b></summary>
<div markdown="1">

### 8.1. 역정규화: 호스트 테이블 삭제 

​	(추후 기입 예정) 

### 8.2. 숙소 세부정보 설정부분 erd 설계

&nbsp;&nbsp;&nbsp;&nbsp;(추후 기입 예정) 

### 8.3. 예약부분 erd 설계 

​	(추후 기입 예정) 

### 8.4. 시퀀스 대체 

​	(추후 기입 예정)    



</div>
</details>

</br>

## 9. 발표 영상 (발표자: 본인)

> 





## 10. 회고 / 느낀점

> '좋은 팀'에 대한 고민 : https://vida0822.github.io/memory/MR_TennisMemory/		</br> 

> 그래서, 그거 코딩할 수 있어? : https://vida0822.github.io/memory/MR_TennisMemory(2)/
