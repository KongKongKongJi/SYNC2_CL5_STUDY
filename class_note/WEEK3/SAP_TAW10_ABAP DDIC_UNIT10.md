# SELECTION SCREENS
**&nbsp;&nbsp; B4.P290**  

## 셀렉션 스크린구현
### Default SCREEN 1000 
parmeter , select-option로 제작한 스크린과
LOsical DB로 생성한 `NODES ..` 로 제작한 스크린은
SCREEN 1000 이 기본 값으로 지정됨.

variant 로 이전에 입력한 값을 저장해서 이후 프로그램 시작시 재상용이 가능함.

---

```abap
    selection-screen begin of screen 1100.
    ...
    selection-screen end of screen 1100.
```
### parameter select
**&nbsp;&nbsp; B4.P292**  
**parameter Documentation 이 작성되어있음**

|parameter의<br>additional 문법| 설명|
|:---:|:---|
| memory id <pid>| IMPUT 값을 SAP Memory에 저장하고<br>이후 프로그램 실행시 memory에서 불러옴|
| OBLIGATORY| 해당 필드 값을 필수로 요청함.|
| lowercheck| 입력값의 대소문자를 구분함.|
| value check.| selectt help|
| AS CheckBox| 마우스로 선택할 수 있는 체크박스로 생성<br> 다중 선택가능함.|
| RADIOBUTTOON GROUP <grp>| 그룹명이 꼭 있어야함 <br> 해당 그룹중 한개만 선택해야함.|
| Modif id <mod>| 나중에 보자|

#### !!셀렉션 스크린 생성 실습!!

<b>zabap_e01_032 생성</b>

- 셀렉션 텍스트를 통해 Text 설정도 가능함.

---
### Selct-options Screen
**&nbsp;&nbsp; B4.P293**  

인터널 테이블의 컴포넌트로만 선언할 수 있음

|Sign|Option|Low|High|
 |:---:|:---:|:---:|:---:|
 |포함여부|조건연산자|최소값|최대값|
 |I|EQ|||
 |Inclusive|동일함|해당값|해당값|
 |E|BT|||
 |Exclusive|비트윈|||
 |위 두개가<br>끝!|...|||
 
Selct-options는 위와 같이 테이블 구조이기 때문에 멀티플 선택이 가능함

**&nbsp;&nbsp; B4.P296**  
MEmory id <>를 사용할때에는 1개 값만 입력이 가능하다.  
- 기초적인 사항은 parameter와 동일함  

|Selct-options의<br>additional 문법| 설명|
|:---:|:---|
| NO-EXTENSION <pid>| 우측 확장입력칸이 등장하지 않음.|
| NO INTERVALS | 두번째 입력칸이 Display되지 않음.|

#### !!셀렉트 옵션 스크린 생성 실습!!

<b>zabap_e01_033 생성</b>

---

### INITIALIZATION.
**&nbsp;&nbsp; B4.P297**
- 레프트 프로그램에서만 발생 가능한 이벤트.
- 해당 이벤트 종료 후 엔드 유저에게 스크린 디스플레이함
- 값을 동적으로 할당할 수 있음.

### AT SELCTION-SCREEN
- CHeck Logic을 통해 SECT SCREEN에 입력된 값을 체크
- Dialog message E를 이용하요 체크 메시지 Display함.  
    즉, Status bar에서 확인가능하도록 함.
- 오류 체크에 문제가 있으면 다시 스크린 display
- 오류 체크 통과 이후에 메인 소스코드가 시행됨.

---
### SELECTION SCREEN BLOCKS
**&nbsp;&nbsp; B4.P299**
- 셀렉트 스크린을 블럭으로 나눠서 디스플레이 할때사용
- TITLE 구문 뒤에 TEXT SYMBOl을 이용하여 블럭 제목을 Display할 수 있다.

```abap
    SELECTION-SCREEN BEGIN OF BLOCK blk1 WITH FRAME TITLE TEXT-001.
    SELECT-OPTIONS: so_car FOR gv_carrid ,
                    so_con FOR gs_flight-connid ,
                    so_fdt FOR gs_flight-fldate .
    SELECTION-SCREEN END OF BLOCK blk1.

```
### selection-screen Lines
**&nbsp;&nbsp; B4.P300**
- 라디오버튼이나 체크버튼 같은경우 1 줄에 DIsplay할때 사용하는 기능
```abap
    SELECTION-SCREEN BEGIN OF LINE.

    SELECTION-SCREEN END OF LINE.
```
```abap
    SELECTION SCREEN COMMENT 1(20) text-001
    *SELECTION SCREEN COMMENT 위치 (글자길이) 텍스트 심벌              
```
스크린에 코멘트 작성할때 사용

[스크린 소스코드](/ABAP_source_code\Week3\zabap_e01_033.abap)

---

<h2 align =center><b>UNIT10 EX21</b></h2>

---












---
## 멀티플 스크린 구현

---
## 인풋 체크와 베리언트 생성