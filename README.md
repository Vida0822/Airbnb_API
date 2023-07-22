# :pushpin: Java로 테니스 계수기 만들기 

> Java의 interface 개념을 활용한 테니스 계수기 구현과 파일 출력기능  

</br> 

### 목차

1. 제작기간 & 참여 인원  <br>

2. 사용 기술  <br>

3. 요구 분석    <br>

4. 순서도 (프로그램 흐름)  <br>

5. 클래스 다이어그램 (부제: Interface의 개념과 특징)  <br>

6. 핵심기능 코딩 <br>

7. 트러블 슈팅  <br>

8. 프로젝트 회고 <br>

</br></br>

## 1. 제작 기간 & 참여 인원 

👩‍👧‍👧 팀 프로젝트 (7인)<br>

📆 2023 3월 7일 ~ 3월 10일 (4일)  <br>

</br>

## 2. 사용 기술  

- Java 8 사용  <br>
- 툴 : eclipse 사용   <br>

</br>

## 3. 요구 분석 

<details>
<summary><b> 요구분석 펼치기</b></summary>
<div markdown="1">

① 두 선수 중 득점한 선수의 게임 포인트를 증가시킨다. 득점할 때마다 득점 포인트는 0→15→30→40 순으로 표현한다.  <br>
② 게임 점수가 40인 선수가 포인트를 획득하면 그 게임을 승리한다. 단, 두 선수가 모두 40점인 경우는 듀스가 된다. 듀스가 된 후에는 상대방보다 두 포인트를 더 획득한 선수가 그 게임을 승리한다.  <br>
③ 상대방보다 2게임 이상 차이를 두고 6게임 이상을 먼저 획득한 선수가 그 세트를 승리한다.   <br>
④ 경기 세트 수의 반 이상을 먼저 승리한 선수가 최종 승자이다.  <br> <br>

👏 정리하면,  <br>
포인트 > 게임 > 세트 > 매치 (게임종료)   <br>

1. 포인트  <br>
   0(0점) > 15(1점) > 30(2점) > 40(3점)  <br>
   => 40점(3점)인 선수가 한번더 득점시 (4포인트 획득 시) 1게임 획득   <br>

 ✔  듀스 : 40:40 > 어드벤티지룰 : 두포인트 더 획득시 한게임 획득   <br>

2. 게임<br>
   6 게임 승리시 한세트 획득  <br>

✔ 듀스 : 5:5 > 어드벤티지룰 : 두 게임 연속으로 이겨야 한 세트 획득   <br>
✔ 테이브레이크 : 6:6이 되면 2 게임을 더 얻는 방식 (고려 X)  <br>

3. 세트 

✔ 여성 단식/ 복식 / 혼합복식 : 3세트 => 2세트 획득시 매치(승리)  <br>

✔ 남성 단식/ 복식 : 5세트 => 3세트 획득시 매치(승리) <br><br>

</div>
</details>

</br>
  

## 4. 순서도 (프로그램 흐름) 

<details>
<summary><b> 순서도 펼치기</b></summary>
<div markdown="1">


​	&nbsp;&nbsp;&nbsp;&nbsp;이 서비스의 핵심 기능은 포인트를 획득해 전체적인 경기 점수에 반영하는 계수기 기능과 현재 게임 스코어를 출력하는 점수판 기능이다. 사용자는 경기수와 경기자를 설정하고 실행을 하면 반복적으로 승자를 도출하며 테니스 경기를 자동으로 실행하고 경기 종료시 파일에 그 결과를 출력한다. <br><br>
	&nbsp;&nbsp;&nbsp;&nbsp;이 단순한 기능의 흐름을 보면, 서비스가 어떻게 동작하는지 알 수 있다.
	

![프로그램 순서도](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/ca69b4e2-d887-4b01-980f-35fa1cdda3e5)

</div>
</details>

</br>

## 5. 클래스 다이어그램 설계

<details>
<summary><b>클래스 다이어그램 설명 펼치기</b></summary>
<div markdown="1">

### 5.1. Interface 개념 및 특징

​	&nbsp;&nbsp;&nbsp;&nbsp;**인터페이스(interface)** 는 추상 클래스(미완성 설계도)와 유사하지만 일반 메서드도 포함할 수 있는 다른 일반 추상 클래스와 달리 **오로지 추상 메서드와 상수**로만 이루어진다 (※ jdk 1.8 버전부턴 'default method' 형태로 포함 가능). 즉 해당 interface 안에는 오로지 **메서드의 선언부만** 작성된다.

​	&nbsp;&nbsp;&nbsp;&nbsp;이러한 인터페이스의 특징은 다음과 같다.

1. **다형성** : 조상 타입, 즉 인터페이스 타입 참조변수로 구현된 **자손 인스턴스를 대입**하여 사용할 수 있다. 

2. **강제성**: 자손 클래스은 해당 기능에 필수적인 메서드를 **강제로 오버라이딩** 하게한다. 

3. **has-a**: 다중 상속, 즉 하나의 조상클래스만 가질 수 있는 것과 달리 **여러개의 interface를 implement** 할 수 있다.

   

​	&nbsp;&nbsp;&nbsp;&nbsp;interface의 특징을 고려해, 우리의 **인터페이스의 활용방안**은 다음 두가지였다.

1. **기본 설계도**로서의 interface 
2. **협업(분담)을 용이**하게 하는 interface 

</br>

### 5.2. 클래스 다이어그램 

##### 2023-03

![클래스 다이어그램(팀)](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/a577be0c-b065-45c3-9f97-6867740cc92e)



​	&nbsp;&nbsp;&nbsp;&nbsp;*"인터페이스는 **기본 설계도**이다."*

​	&nbsp;&nbsp;&nbsp;&nbsp;세상엔 **수많은 경기 종목**이 있고 각 규칙을 하나의 클래스에서 다 고려할 순 없다. 따라서 계수기라면 포함해야할 기본적인 기능인 **득점 처리** 기능과 **점수 출력**기능을 반드시 구현하도록, 즉 **최소한의 메서드**를 Interface에 선언하고 이를 자손 클래스에서 상속받아 **각 경기 종목에 맞춰 알아서 구현**하게끔 하는 **기본 설계도**로서 기능하게 한다. 

​	&nbsp;&nbsp;&nbsp;&nbsp;따라서 우린 '계수기' 기본 설계도로 **인터페이스 I**를 선언하고 이를 상속받은 테니스 계수기인 클래스 **ScoreCounter**는 해당 두 메서드를 **테니스 규칙을 반영하여 오버라이딩**한다. 이렇게 구현한 ScoreCounter를 실제 경기(main함수)가 실행되는 **TennisMain**에서 객체로 생성해 사용하게끔 구조를 설정했다.      



</div>
</details>

</br>



## 6. 핵심 기능

<details>
<summary><b>핵심 기능 설명 펼치기</b></summary>
<div markdown="1">



### 6.1. 전체 흐름

![핵심기능](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/76f2e20b-0c59-4eeb-914e-828974d0aaac)

* **TennisMain** (Class) : 테니스 경기수 , 경기할 플레이어 등 경기를 세팅해 해당 정보로 계수기 객체를 생성하고 반복문으로 득점자를 도출해 생성해준 계수기 객체에 반영하는 실제 경기 실행 클래스 <br>
* **ScoreCounter** (Class): 테니스의 전반적인 규칙을 반영한 클래스. 크게 점수를 계산하는 계수기 기능과 점수를 출력하는 점수판 기능으로 이루어져 있다. <br>
* **WriteResult** (Class) : 최종적인 경기결과를 파일에 출력해주는 출력기능 클래스 <br>

</br>

### 6.2. 게임 세팅 및 진행 



![TennisMain](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/c1eac4bc-5e04-463a-b47c-f44d5680cfed)



- **게임 세팅** :pushpin: [코드 확인](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/blob/18b9b1124a69f585853726515a4a88d02aeb7b3b/tennis/src/tennis/TennisMain.java#L30-L64)

  - 실행할 경기가 남자경기, 여자경기인지 입력받는다. 남자경기는 5세트, 여자경기는 3세트로 세트수가 설정된다.   
  - 각 플레이어의 이름을 입력받은 후 세팅정보를 바탕으로 계수기 객체를 생성한다.

- **게임 진행** :pushpin: [코드 확인](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/blob/08c639b660efbea0407afeea07b35e378ce73ed1/tennis/src/tennis/TennisMain.java#L66-L75)

  - 1 또는 2로 랜덤하게 득점자를 도출하고, 생성한 계수기 객체에서 포인트를 올리는 pointWinner(), 득점 처리하는  scoreBoard(), 반영된 점수를 출력하는 dispScoreBoard()를 호출한다.
  - 해당 과정을 경기가 끝날때까지 while문으로 반복한다. 
  
</br>  

### 6.3. 계수기 기능 

![scoreBoard](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/7410cb17-8dad-4a06-8fbb-d95e875b0611)

- **득점 처리** :pushpin: [코드 확인](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/blob/2fb77b76e96d4afbde8e7204d4b52e4e98ddcbdb/tennis/src/tennis/ScoreCounter.java#L57-L82)

  - 득점자의 포인트를 올리고 이를 생성한 계수기 객체의 멤버변수(각 선수 포인트, 게임, 세트수)에 경기 규칙에 따라 반영한다. 

  - 포인트 4점 획득시 1게임을, 6게임 획득시 1 Set를 획득한 것으로 필드를 초기화며 게임, 세트 획득시 포인트 및 게임 필드를 리셋한다. 

  - 설정된 세트수의 과반수 이상 획득 시 경기를 종료하고 승자를 결정한다. 

    

- **듀스 게임** :pushpin: [코드 확인](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/blob/2fb77b76e96d4afbde8e7204d4b52e4e98ddcbdb/tennis/src/tennis/ScoreCounter.java#L85-L136)

  - 한 플레이어가 포인트 4점 획득했는데 1점차면 포인트 듀스가, 6게임 획득했는데 1 게임차면 게임 듀스가 발생한다.

  - 그 즉시 별개의 듀스 포인트 필드와 while문을 사용해 듀스게임을 실행한다. 
  
 </br>   
  

### 6.4. 점수판 기능 - dispScoreBoard() 

![dispScoreBoard](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/5f83dcb4-2c7b-4d38-894b-7446e2d8dae0)

- **경기현황 출력** :pushpin: [코드 확인](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/blob/2fb77b76e96d4afbde8e7204d4b52e4e98ddcbdb/tennis/src/tennis/ScoreCounter.java#L156-L171)

  - 현재 점수 현황, 즉 두 선수의 포인트, 게임, 세트 획득 현황을 나타내는 점수판을 함수 호출시 출력한다.
    

- **승자정보 출력** :pushpin: [코드 확인](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/blob/7f093b13a61377db0f12217858f593e3fa904756/tennis/src/tennis/ScoreCounter.java#L173-L184)

  - winner 필드가 null이 아니게 될 때 경기 종료 멘트와 함께 승자 정보를 출력한다. 

  - 파일에 출력할 최종결과 텍스트를 작성한다. 이때 formating의 편의를 위해 여러 list 변수로 텍스트를 받아둔다.
    
  - 이렇게 작성한 텍스트를 파일 입출력을 수행하는 WriteResult 객체의 생성자를 통해 넣어준다. 

  

</br>  


### 6.5. 최종결과 저장- writeTennisResult() 

![WriteResult](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/afff5816-583e-42a8-a0c0-78b6d1a3e945)

- **파일 출력** :pushpin: [코드 확인](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/blob/2fb77b76e96d4afbde8e7204d4b52e4e98ddcbdb/tennis/src/tennis/WriteResult.java#L7)

  - FileOutputStream을 통해 출력할 file을 지정한다
  - ObjectOutputStream의 writeUTF() 를 통해 tennisResult.txt에 실제로 출력한다. 

</div>
</details>

</br>

## 7. 핵심 트러블 슈팅

<details>
<summary><b>트러블 슈팅 설명 펼치기</b></summary>
<div markdown="1">


### 7.1. 인터페이스 참조변수 활용

![인터페이스 손필기](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/961a7dc0-7ab6-48f7-87ad-3e47dbc6e300)

​	

​	&nbsp;&nbsp;&nbsp;&nbsp;메서드 선언부(*Interface I*) 구현부(*Class B*)  사용부(*Class A*) 실행부(*Main*)로 클래스를 나누었다. 이 구조의 목적은 객체지향언어의 **다형성**을 활용해 부모 클래스가 완성되어야 자손 클래스가 구현가능한 상속구조의 단점을 해결해 분업의 효율성을 높이고자 함에있다.  

​	&nbsp;&nbsp;&nbsp;&nbsp;Class A에 interface 참조변수를 통해 **빈 껍데기 뿐인 메서드**를 만들어 로직을 구현하고, 다른 팀원들은 해당 interface를 상속받은 클래스B에서 **메서드의 몸체**를 구현한다. 각자 개발을 마친 후 프로그램 실행시 Class A를 객체로 생성하고 Class A 메서드의 매개변수인 interface의 참조변수, 즉 조상 참조변수에 인터페이스를 상속받은 Class B를 객체로 생성해 자손 인스턴스를 **동적으로 주입**한다. 

​	&nbsp;&nbsp;&nbsp;&nbsp;위 구조를 우리 프로젝트에 반영하면 아래와 같다. 
</br>


![초기 클래스다이어그램](https://github.com/Vida0822/TennisCounter_Java-Interface-Project/assets/132312673/1b6384a0-cc8b-4a7b-a697-1b18fb68b6bc)



​	&nbsp;&nbsp;&nbsp;&nbsp;득점시 포인트를 올리는 pointWinner(int p)와 게임현황을 출력하는 dispScoreBoard() 두 메서드를 인터페이스 I에 선언한다. 메서드를 **구현하는 ScoreCount** 클래스와, 테니스 규칙을 반영해 **득점처리**하는 계수기, **ScoreBoard** 클래스를 작성한다. **게임이 실행**되는 TennisMain에선 경기정보를 입력받아 계수기, **ScoreBoard를 객체로 생성**하면서 게임을 세팅한다. 이후 득점자를 랜덤으로 도출하고 **인터페이스 I를 매개변수**로 갖는 pointWinner(I i), dispScoreBoard(I i) 매개변수에 **ScoreCount를 넣어 호출**하며 득점처리 및 점수출력을 실행한다. 이 과정을 게임이 끝날때까지 while문으로 반복한다. 

​	&nbsp;&nbsp;&nbsp;&nbsp;게임을 세팅, 진행하는 TennisMain에 2명, 메서드 구현부에 2명, 계수기 로직 구현에 3명으로 개발 파트를 나누었다. 인터페이스에 **메서드의 기능과 리턴타입을 명확히 선언**해 놓으니 실제로 구현이 안되었더라도 **계수기 로직 개발을 동시에 진행**할 수 있었다.

<br>

*Problem*

​	 &nbsp;&nbsp;&nbsp;&nbsp;문제는 메서드의 리턴값만으로 테니스 득점로직을 계수기 클래스(ScoreBoard)에 구현해야하는데, 포인트 점수를 다루는 메서드 구현부(ScoreCounter)와 포인트 점수, 게임, 세트 모두를 처리하는 계수기(ScoreBoard)간 **멤버변수가 중복선언** 되는 등 **기능 구분이 명확하지 않았다**. 

​	&nbsp;&nbsp;&nbsp;&nbsp;또한 **객체의 주입(DI)** 에 대한 이해부족으로 **인터페이스 참조변수**를 잘 활용하지 못해, 실행부(ScoreBoard)에서 인터페이스 참조변수로 메서드를 새롭게 선언하거나 메인 함수의 게임세팅과 연결지어 줄 때 어려움이 있었다. 즉 코딩경험 부족에 의한 기술적 한계로 **클래스간의 기능 연계**가 원활이 이루어지지 못했다. 

</br>

*Solution*

​	&nbsp;&nbsp;&nbsp;&nbsp;개발 시간이 촉박했던 시점이라 **메서드 사용클래스(ScoreBoard)를 없애고**  ScoreCounter 클래스에서 테니스 규칙을 반영하며 메서드를 구현하는 방향으로 설계를 수정했다. 실제 main함수에선 구현부인 **ScoreCounter에서 직접 메서드를 호출**하도록 했다.

​	&nbsp;&nbsp;&nbsp;&nbsp;이렇게 하니 구현자체는 편해졌지만 ScoreCounter에 계수기 로직(테니스 규칙)과 득점 처리, 출력 등 여러 기능이 섞여 객체 지향의 장점인 **모듈화**가 잘 이루어지지 않고 **코드의 가독성**이 떨어졌다. 시간적 여유가 있었다면  클래스간 기능 구분을 더 명확히 하고 그 주입, 연계관계를 통해 객체지향의 장점을 최대한 살린 체계적인 프로그램을 만들 수 있었을 것 같아 팀원들과 나도 많이 아쉬웠다. 

</br>

### 7.2. 테니스 규칙에 맞는 포인트 출력

- 계수기 메서드, 즉 scoreBoard() 함수를 구현할 때 계산의 편의 및 게임, 세트수 계산과의 로직 일치를 위해 포인트 점수를 0,1,2,3 점으로 두어 득점처리 했다. 

<details>
<summary><b>기존 코드</b></summary>
<div markdown="1">

```java
	public void pointWinner(int p) { // pointWinner 오버라이딩
		if (p == 1) {
			player1Point++;
		} else
			player2Point++;
	}

	public void scoreBoard() { // 계수기 메서드
	
		if (player1Point == 4) { //player1이 4포인트를 이겼을때
			player1Game++;
			pointReset();
		}
		if (player2Point == 4) { //player2이 4포인트를 이겼을때
			player2Game++;
			pointReset();
		}
        /* 코딩 생략 */ 
    }
```

</div>
</details>

</br>



*Problem*

- 하지만 점수판 메서드, dispScoreBoard()를 구현할 때 포인트 점수를 출력할땐 테니스 경기 규칙에 따라 0,15,30,40 점으로 출력을 해야했는데, 이 점수들은 서로 불규칙하여 득점시 고정값으로 올리는 것이 불가능했다.  
</br>

*Solution*

- 1점씩 올리는 포인트 득점처리 방식은 그대로 두되,  0,1,2,3 점으로 두었던 포인트 점수를 출력할때 테니스 경기 규칙에 맞춰 변환시킨다. 
- 점수판 메서드에서 0,15, 30, 45를 포인트 점수 배열 playerPoints로 만들고, 0,1,2,3을 배열의 index로 매칭 시켜 출력형식을 바꾸어준다.
- 이 때 듀스게임까지 가게될 경우 포인트가 4를 넘을 수 있기 때문에 ( 5점,6점 => 15점. 30점 ), 단순히 값이 0,1,2,3인 것이 아닌 아닌 값의 4로 나눈 나머지를 index로 활용했다.
- 이렇게 하니 득점처리는 그대로 로직을 유지해 계산을 편하게 할 수 있고 출력하기 전에만 형식을 일치시켜 바꿔주면되어 편리했다

<details>
<summary><b>개선된 코드</b></summary>
<div markdown="1">
	
```java
int[] player1Points = { 0, 15, 30, 40 }; //포인트 점수
int[] player2Points = { 0, 15, 30, 40 };
int printplayer1Point 
		= player1Points[player1Point % 4];
int printplayer2Point 
		= player2Points[player2Point % 4];
```

</div>
</details>

</br>


</div>
</details>

</br>

## 8. 회고 / 느낀점

> '좋은 팀'에 대한 고민 : https://vida0822.github.io/memory/MR_TennisMemory/		</br> 
 
> 그래서, 그거 코딩할 수 있어? : https://vida0822.github.io/memory/MR_TennisMemory(2)/
