# day2

## StudyEventDef 

![화면 캡처 2022-06-28 164439](https://user-images.githubusercontent.com/25499386/176123580-d7ba92f2-1e5c-40a1-b3f0-2f7820aa4de0.png)

- Body : Description?, FormRef*, Alias* 을 포함 할 수 있다.


- event관련해서 openEDC의 내용을 보면 대표적으로 작성되어 있는게 Baseline , follow-up 두 부분을 봤을때, 이는 방문순서의 일부분을 말하는 것으로 보임??
- 이하 다시 기술하겠지만 방문 타입이 3가지가 존재함. Scheduled 의 경우 예약된 것으로 각 주제에 대해 수집될 것으로 예상하는 일련의 양식.
- unscheduled 의 경우 심각한 부작용으로 인한 조기종료를 위해 일련의 양식처럼 발생되거나 발생되지 않을 수 있는 데이터를 수집한다.
- 마지막으로 common의 경우, 유해사례나 병용약물 로그와 같은 여러 다른 데이터 수집 이벤트에서 사용되는 양식이다.


반복 플래그는 이러한 유형의 연구 이벤트가 주어진 주제 내에서 반복적으로 발생할 수 있음을 나타냅니다.

범주 속성은 일반적으로 이러한 유형의 연구 이벤트에 적합한 연구 단계를 나타내는 데 사용됩니다. 예에는 선별, 사전 치료, 치료 및 후속 조치가 포함될 수 있습니다.

- 해당 태그는 다음과 같은 속성을 포함한다.
  
  ### OID
  - oid 형식으로 작성. 명명 규칙은 RDF 관련하여 존재하는 것으로 파악.
  
  ### Name
  - name 형식으로 작성
  
  ### Repeating
  - Yes or No 형식으로 작성.
  - 이러한 연구 이벤트가 주어진 주제 내에서 반복적으로 발생하고 있는지 여부
  
  ### Type
  - Scheduled or Unscheduled or Common 세가지 중 하나를 선택	
  - 해당 타입에 따라서 양식이 달라질 수 있음. 각각의 목적이 다름.
  
  ### Category
  - text 형식으로 작성. 작성 여부는 선택적임.
  
  ## Description (문서에는 없으나, StudyEventDef 의 Body에 있는 태그)
  - 연구 메타데이터 구성요소에 대한 설명. 여기에서는 StudyEventDef 에 대한 설명.
  - 
  
  
  ## FormRef
  - 
