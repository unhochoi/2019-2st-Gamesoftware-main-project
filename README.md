# GameSoftwareD

**We'll make first-person parking game [PC]**

**Unity version - 2019.2.10f1**

**항상 작업 시작하기전에 Github에서 FETCH & PULL 하기!!!!!!**

**깃 허브 ReadMe에 업데이트 기록 꾸준히 하면 좋을 듯**

[1차 회의록](https://github.com/anheew1/GameSoftwareD/wiki/1st-Meeting-Log)
[2차 회의록](https://github.com/anheew1/GameSoftwareD/wiki/2nd-Meeting-Log)
[3차 회의록](https://github.com/anheew1/GameSoftwareD/wiki/3rd-Meeting-Log)
[4차 회의록](https://github.com/anheew1/GameSoftwareD/wiki/4th-Meeting-Log)
[5차 회의록](https://github.com/anheew1/GameSoftwareD/wiki/5th-Meeting-Log)

---

### Tags
Damage ( 파손도)

ObstacleFix ( 플레이어가 건드려도 움직이지 않는 것 ex) 주차된 자동차 )

ObstacleUnfix ( 플레이어가 건드리면 움직이는 것 ex) 꼬깔 )

PlayTime (플레이 시간)

StarRank (부가사항)

GoalSpot (도착지점)

### 화면 규격
화면 비율 16:9 (확정) 

전 씬에 통일하는 걸로 

# 맵 관련 Requirements
* 맵 디자인

    * 후진만하면 주차할수 있는 맵 (기어변경만 하면 됨)

    * 주차에 컨트롤도 하는 맵 (약간의 컨트롤이 필요)

    * T자 맵 (정교한 컨트롤이 필요)

    * 맵은 클 필요가 없음 (기본 유니티 Plain 3배정도)

    * 맵 바깥을 배경이랑 벽으로 채우기

* 필요한 프리팹 

    * 차(장애물)

    * 꼬깔

    * 주차선

    * 목적지선 

    * 기타 등등


## Next to Do

### Map and UI

* Select Map에 별이랑 시간 띄우기

* 로딩스크린   

* 최종 스테이지에서 Next하면 Home으로 돌아가게끔

* Map 벽 세우기

* 끝날때 Home으로 돌아가는데 Start로 돌아가게끔 해야함.

### Car

* 게임 내부 Stage 표기 변경이 필요함. (Stage0)에서 문제

* 사이드 미러 조정 (모델이 뚫려보이는 문제가 있음)

* Stage2에 차 적용해야함.

### 다음 일정은 2019-11-27 5:00 PM ~~수업 끝나고 정비할 시간은 필요~~

***

## 11월 4일 차량팀 개발 사항
* CarDamage(차량 손상 제어)
   * void Die() : 차량 다 파손 됐을 경우 종료
   * void  OnTriggerEnter(Collider other) : 차량 충돌 제어

* CarUIManager(차량 화면 UI)
   * Damage : 차량 손상도
   * void OnGUI() : 차량 손상도 표시

* GameManager(게임 로직 구현) 

## 11월 5일 차량팀 개발 사항
* GearManager(기어 구동 제어)
   * GearStatus(기어 상태)

* CarUIManager(차량 화면 관리)
   * Canvas, Gear, Stick 오브젝트 추가
   * 기어 상태에 따라 Stick위치 변경 구현
   * 현재 스테이지 정보 표시
   * Start UI 구현
   * End UI 구현(실패시)
   * Pass UI 구현(성공시)
   
* WheelDrive(바퀴 작동)
   * GearManager에서 GearStatus를 가져와서 토크 결정  

* CarDamage(차량 손상 제어)
   * 도착지점에 닿으면 스테이지 종료
 
* GameManager(게임 로직 구현) 
   * Scene index 생성
   * 차량 파손으로 인한 종료 이벤트 생성
   * 도착지점에 의한 종료 이벤트

## 11월 7일 차량팀 개발 사항
* GearManager(기어 구동 제어)
   * 재시작시 기어 변경 안해도 출발하는 오류 수정

* CarDamage(차량 손상 제어)
   * 도착지점에 닿으면 스테이지 종료
 
* ScoreManager(점수 제어)
   * 랭크로 점수 설정
   * Score[] - 길이가 3인 배열로 맵 별 도전과제 클리어 확인
   * 최대 점수 3점
   * getRank() - Score 배열에서 클리어 개수 리턴

* CarUIManager
   * 게임 시작 후 우측 상단 타이머 표시
   * 게임 종료 후 타이머 숨김
   * 게임 성공 후 중앙에 노란색 별로 랭크 표시

* TimeManager
   * 타이머 변수 생성
   * 게임 진행 상태에선 타이머 증가
   * 게임 준비 상태에선 타이머 초기화

## 11월 10일 차량팀 개발 사항

* CarUIManager
   * 파손도 UI 생성, 장애물에 닿을 경우에 파손도가 5씩 깎임  
   * 파손도 0 ~ 100, 0이하로 떨어지면 게임 종료

* FrontCheck
   * 차량 앞 부분이 주차 구역에 들어가 있는지 판별

* BackCheck
   * 차량 뒷 부분이 주차 구역에 들어가 있는지 판별
   * 후진 주차 여부 판별

* GearManager
   * P 누르면 게임 종료

## 11월 11일 차량 관련 개발 사항 

* CarUIManager
   * SceneChanger 스크립트를 넣어 기능을 처리함
   * Home 버튼은 SelectMap으로 전환 : ChangeToSelectMap()
   * Restart 버튼은 다시 씬을 재생하도록 :  RestartScene()
   * Next 버튼은 SampleScene에서는 Stage00으로(예외적인 경우),다른 스테이지에서는 그 다음 스테이지로 갈 수 잇도록 처리함 ( ChangeToNext() )
* SceneChanger
   * 대부분의 씬 변경은 스트링을 입력하여 변경함
   * index로 처리시 빌드 세팅에 따라 Scene변화에 문제가 생길 수 있음

혹시 몰라서 제가 CarUIManager에서 삭제한 기능은 주석으로 남겨놨습니다.

자세한건 Commit 기록이나 주석들 보시면 아실거에요

그리고 개인적으로는 GameManager의 StageLevel은 추천하지 않는 방식임. (BuildSetting의 변경으로 문제가 있을 수 있으니)

## 11 월 18일 개발 사항

* Car 프리팹을 Stage에 적용함 (성공)


## 그 외 추가로 구현하고 싶은 것
* 미니맵

* 마우스로 화면 돌리는 거

* 사용자가 시작하기전에 맵 위에서 카메라 돌면서 
맵 구조를 파악 할 수 있도록 함

## Images

![2_CarUI](https://user-images.githubusercontent.com/28583561/67908501-11f36580-fbbf-11e9-99cd-f3977bc94927.jpg)
![2_firstStage](https://user-images.githubusercontent.com/28583561/67908569-4ebf5c80-fbbf-11e9-843c-ab57edeffce5.jpg)
![2_SecondStage](https://user-images.githubusercontent.com/28583561/67908570-4f57f300-fbbf-11e9-956c-e023c8443460.jpg)
![2_ThirdStage](https://user-images.githubusercontent.com/28583561/67908572-4f57f300-fbbf-11e9-9f48-ac6f0472a941.jpg)
![2_SelectMapAndSystem](https://user-images.githubusercontent.com/28583561/67908571-4f57f300-fbbf-11e9-8745-82a47859d529.jpg)
