## 9 경매 스나이퍼 개발 의뢰
### 9.1 맨 처음부터 시작하기
    경매에 자동으로 입찰하는 애플리케이션을 만들어 달라는 위뢰를 받았다. 
    애플리케이션 동작 방식과 주요 컴포넌트에 대한 윤곽은 잡은 상태이며, 
    애플리케이션 규모를 키울 때 점진적인 단계에 대한 대략적인 계획을 함께 짰다.
     
     기본적인 용어 합의
     - 품목(Item) 은 식별, 구매 가능한 것이다.
     - 입찰가(Bidder)는 품목 구매에 관심이 있는 사람이나 조직이다.
     - 현재가(Current price)는 어떤 품목에 대해 현재 가장 놉은 입챂을 말한다.
     - 매매 지시 지정 가격(Stop price)는 어떤 품목에 대해 입찰자가 지불할 의사가 있는 가장 높은 가격이다.
     - 경매(Auction)은 어떤 품목에 대한 입찰을 관리하는 프로세스다.
     - 경매장(Auction house)은 경매를 주관하는 기관이다.
     
     __관련 품목 그룹에 대해서는 입찰할 수 있다.__

### 9.2 경매와의 상호 작용
    경매 프로토콜(Command)
        Join    입찰차가 경매에 참여한다.
        Bid     입찰자가 경매에 입찰가를 보낸다.
        Price   경매에서는 현재 수락된 가격을 보고한다.(최소 기준 가격, 현재 가격을ㅈ ㅔ시한 입찰자 이름)
        Close   경매가 종료됬음을 알린다.
        
    XMPP 메시지
  
### 9.3 안전하게 진행하기
    할 일
    - 단일 품목: 경매 참여, 입찰하지 못한 상태로 낙찰 실패
    - 단일 품목: 경매 참여, 입찰, 낙찰 실패
    - 단일 품목: 경매 참여, 입찰, 낙찰
    - 가격 상세 표시
    - 여러 품목
    - 사용자 인터페이스(GUI)를 통해 품목을 추가
    - 매매 지시 지정 가격에서 입찰을 중단
      
 ### 9.4 이건 진짜가 아니야
    유의사항
    - 이것은 실제 아키텍처가 아니다.
    - 이것은 애자일 계획하기가 아니다.
    - 이것은 현실적인 사용성 설계가 아니다.

## 10. 동작하는 골격
### 10.1 골격 사용 준비: 동작하는 골격을 대상으로 테스트하라
    대략적인 시스템 구조를 제안하고 그것의 유효성을 검증할 수 있을 정도로 요구사항을 이해
    (빌드, 패키지화, 유사 운영 환경으로 배치하는 과정을 자동화)
    
### 10.2 최초 테스트
    명확하게 의도를 기술한다. > 우리가 원하는 대로 시스템을 테스트할 수 있는 기반 구조를 만든다.
    테스트의 윤곽
    1) 경매에서 품목을 판매하고
    2) 경매 스나이퍼가 해당 경매에서 입찰을 시작하면
    3) 경매에서는 경매 스나이퍼로부터 Join 요청을 받을 것이다.
    4) 경매가 Close 됐다고 선언되면
    5) 경매 스나이퍼는 경매에서 낙찰에 실패했음을 보여줄 것이다.
    
### 10.3 몇 가지 초기 선택
    전 구간 테스트: 이벤트 기반 시스템에 대한 전 구간 테스트에서는 비동기성과 관련한 문제를 해결해야 한다.
        애플리케이션을 제어해 테스트 시나리오를 단계별로 밟는다.
    시작 준비: 첫 테스트는 실제로 전 구간을 대상으로 하지 않는다.

## 11. 첫 테스트 통과하기