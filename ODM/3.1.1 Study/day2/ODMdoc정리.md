# ODM
- 본 자료에 사용된 ODM은 open EDC 사용 ODM이다.
- 본 문서에서는 ODM의 상위 태그부터 하위태그까지의 속성들을 순차적으로 설명한다.

- 각 태그의 바디내용은 명시되어 있지 않을 경우, 들여쓰기의 내용이 body 내용임을 나타낸다.
- 명시되어 있는 경우, 바디에 작성될 수 있는 타입이 명시된다.

본 문서에서 다룰 태그 영역은 다음과 같다.


```
- ODM 프리뷰 -

  Study
    📁  Globalvariables
        StudyName
        StudyDescription
        ProtocolName
    📁  BasicDefinitions
        MeasurementUnit
          Symbol
    📁  MetaDataVersion
        📌Protocol
            StudyEventRef
        📌StudyEventDef
            ✅ Description
            ✅ FormRef
        📌FormDef
            ✅ Description
		ItemGroupRef
        📌ItemGroupDef
            ✅ Description
               ItemRef
        📌ItemDef
            Question
            CodeListRef
            MeasurementUnitRef
            RangeCheck
        📌CodeList
            CodeListItem

```


## ODM 
- ODM의 이하 attribute들로는 다음과 같이 존재하는데,

  ### Description (text 형식)
  ODM의 설명으로써, 해당 문서의 이해를 정확하게 할수 있도록하는 역할을 한다.


  ### FileType ( Snapshot | Transactional )
  Snapshot or Transactional 으로 표현된다.
  snapshot 은 단순하게 현재상황의 데이터/ 메타데이터를 나타낸다면, Transactional의 경우 현재 이 데이터뿐만 아니라 이 데이터가 어떻게 존재하게 되었는지까지 나타내게 된다.


  ### Granularity ( All | Metadata | AdminData | ReferenceData | AllClinicalData | SingleSite | SingleSubject )
  해당 속성은 해당 문서의 정보의 폭을 나타낸다. 일반적으로 위의 범주에서 더 상세한 설명이 필요할 경우에는 Desc 속성에 추가하여 설명한다.


  ### Archival (Yes | No)
  해당 속성은 문서타입이 Transactional 일 경우에만 사용해야 하며, 21 CFR 11을 충족하는 경우에 Yes를 그렇지 않은 경우에는 No를 작성한다.
  * 21 CFR 11은 미국 의약품 의료기기 관리법률 중 전자 문서와 전자 서명에 관련한 규정이다. 


  ### FileOID (OID)
  유일한 이 파일의 인식자이다.
  OID 의 경우, 최소길이가 1인 문자열의 순서인데 조사한 바로는 특별한 명명규칙은 없는 것으로 보여진다.
  첨언하자면, openEDC에서 생성된 fileOID는 해당 study의 이름을 그대로 가져와 사용한다.


  ### CreationDateTime
  해당 파일의 생성 일시를 나타낸다. datetime 형식이며, 초까지 표현한다.


  ### PriorFileOID (oidref)
  이전파일이 있는 경우 해당 파일에 대한 참조이다.
  표현형식은 oidref이며, 표현형식은 oid와 동일하다.

  ### AsOfDateTime (datetime)
  문서를 만들기 위해 원본데이터베이스를 쿼리한 시간이다. 표현형식은 datetime 이다.


  ### ODMVersion ( 1.2 | 1.2.1 | 1.3 | 1.3.1 | 1.3.2 )
  사용한 ODM 표준 버전을 명시한다.
  ODM 버전은 최신버전이 2013년도 기준 릴리즈된 1.3.2 버전이며, 그 이후 업데이트는 홈페이지에 릴리즈 되어있지 않다.


  ### Originator
  해당 ODM 파일을 생성한 단체를 말한다.


  ### SourceSystem (text)
  컴퓨터 시스템이나 데이터베이스 관리시스템을 명시한다.


  ### SourceSystemVersion (text)
  SourceSystem의 버전을 명시한다.


  ### ID (ID)
  ds:Signature 에서 다시 사용할 요소. 현재로써 서명을 위한 요소로 이해된다.
  
      이하 코드는 ODM 속성 예시코드.
      <ODM xmlns="http://www.cdisc.org/ns/odm/v1.3" xmlns:ns2="http://www.w3.org/2000/09/xmldsig#" FileType="Snapshot" FileOID="CNR_ODM study" CreationDateTime="2022-06-27T08:39:40.595Z" ODMVersion="1.3.2" SourceSystem="OpenEDC">    
  
## Study
- ODM의 이하 먼저 나타나는 하위태그는 Study이다.
- Study의 속성으로는 OID 하나만 존재한다.
  
  ### OID
  예시는 다음과 같다.
  < Study OID="S.1">
  
  ## GlobalVariables
  - 포함하는 속성은 없으며, 연구에 대한 일반적인 요약정보를 포함한다.
  
    ## StudyName
    - body에 작성될수 있는 것은 text가 아닌 name 이다. name과 text의 차이는 최소길이가 지정되었는가, 지정되지 않았는가 이다.
    - text는 최소 작성길이가 없으나, name은 최소 작성길이가 1로 지정되어있다.
    - 포함하는 속성은 없으며, 이 문서의 Study 이름이다.
    
    ## StudyDescription
    - body에 작성될수 있는 것은 text이다.
    - 포함하는 속성은 없으며, 해당 study에 대한 설명이다.
    
    ## ProtocolName
    - body에 작성될수 있는 것은 name 이다.
    - 포함하는 속성은 없으며, 계획서의 스폰서 내부 이름을 나타낸다.
    
  ## BasicDefinitions
  - 포함되는 속성은 없다.

    
    ## MeasurementUnit
    - 해당 태그의 속성은 다음과 같다.
    - 데이터 항목 또는 값에 대한 물리적 측정 단위. 해당 의미는 name 속성에 의해 지정된다.


      ### OID
      - 해당 부분 OID의 명명 예시의 경우 MU.1 ... 넘버링 사용하는 것으로 보임.
          
      
      ### Name
      - 속성은 Name 이나, 작성 유형은 text로 되어 있음. 
      - OID 와 동일하게 작성되는 경우도 존재.

            예시:
            <MeasurementUnit OID="MU.1" Name="kg">
      
      ## symbol
      - 포함되는 속성은 없다.
      - 인간이 읽을 수 있는 측정단위 이름을 작성한다.
        
        ## TranslatedText
        - 포함되는 속성은 다음과 같다
          
          ### xml:lang
          - language tag로 작성된다.
          - 설명은 다음과 같이 되어 있으나, 	LL (-CC)* (see below)
          - 실제 사용되는 양식은 다음과 같았다. -> xml:lang="en" , xml:lang="ko" ...etc
      
      ## Alias
      - 사실 MeasurementUnit 이하에 붙는다고 되어있지만, 공식 문서상에는 해당 내용이 존재하지 않는다.
      - 문서상에서 alias 가 붙는건 Contained in:Protocol, StudyEventDef, FormDef, ItemGroupDef, ItemDef, CodeList, CodeListItem, EnumeratedItem, MethodDef, ConditionDef
      - 이곳에 우리가 옵션으로 주는 annotated CRF 변수명같은 내용들이 포함 되어야 한다.

&nbsp;


  ## MetaDataVersion 관련 내용 기술 예정
  - meta 내용 어쩌구 저쩌구
    ## include
    - sdsd
    
    ## protocol
    - 프로토콜 설명 어쩌구
      ## description
      - 설명
      ## studyeventref
      - 연구의 특정 버전 내에서 발생하는 StudyEventRef에 대한 참조
      - StudyEventRefs list : 연구 내에서 발생할 수 있는 연구 StudyEvent유형을 식별. 프로토콜 내의 StudyEventRefs에는 중복된 OrderNumbers나 StudyEventOIDs가 없어야 합니다.
    
        Contained in : Protocol
        
        ## Attributes
        
        | Attributes | type | description |
        | ----- | --- | -------- |
        | StudyEventOID | oidref | StudyEventDef의 OID를 참조한다. |
        | OrderNumber | integer | StudyEventDefs의 목록이 사용자에게 표시될 때마다 사용할 수 있도록 StudyEventDefs에 대한 순서를 제공합니다. event 일정, 작업시간, 데이터 정확성을 의미하는 것은 아니다. |
        | Mandatory | Yes \ No |  Yes일때, MetaDataVersion을 포함하는 임상 데이터가 Study event 인스턴스가 없으면 불완전하다는 것을 나타낸다. 불완전한 ODM 임상 데이터 파일은 연구 검토 및 분석하기에 불완전한 것으로 볼 수 있다.  |
        | CollectionExceptionConditionOID | oidref | Study event에 대한 데이터를 수집하면 안되는 상황을 설명한다. ConditionDef를 참조한다. |
        
        ### 💚예제
        
        ```xml
        <Protocol>
        	<StudyEventRef StudyEventOID="SE.1" Mandatory="No"/>
        	<StudyEventRef StudyEventOID="SE.2" Mandatory="No"/>
        	<StudyEventRef StudyEventOID="SE.3" Mandatory="No"/>
        </Protocol>
        <StudyEventDef OID="SE.1" Name="Baseline (T0)" Repeating="No" Type="Common">
        	<Description>
        		<TranslatedText xml:lang="en">Baseline (T0)</TranslatedText>
                    <TranslatedText xml:lang="de">Vorbefragung (T0)</TranslatedText>
           </Description>
           		<FormRef FormOID="F.1" Mandatory="No"/>
                    <FormRef FormOID="F.2" Mandatory="No"/>
        </StudyEventDef>
        ```
    
    ## 🤦‍♂️StudyEventDef 

    ![화면 캡처 2022-06-28 164439](https://user-images.githubusercontent.com/25499386/176123580-d7ba92f2-1e5c-40a1-b3f0-2f7820aa4de0.png)

    - Body : Description?, FormRef*, Alias* 을 포함 할 수 있다.

    - event관련해서 openEDC의 내용을 보면 대표적으로 작성되어 있는게 Baseline , follow-up 두 부분을 봤을때, 이는 방문순서의 일부분을 말하는 것으로 보임.
    - 이하 다시 기술하겠지만 방문 타입이 3가지가 존재함. Scheduled 의 경우 예약된 것으로 각 주제에 대해 수집될 것으로 예상하는 일련의 양식.
    - unscheduled 의 경우 심각한 부작용으로 인한 조기종료를 위해 일련의 양식처럼 발생되거나 발생되지 않을 수 있는 데이터를 수집한다.
    - 마지막으로 common의 경우, 유해사례나 병용약물 로그와 같은 여러 다른 데이터 수집 이벤트에서 사용되는 양식이다.

    - 해당 태그는 다음과 같은 속성을 포함한다.
  
      ### ✔OID
      - oid 형식으로 작성. 명명 규칙은 RDF 관련하여 존재하는 것으로 파악.
      
      ### ✔Name
      - name 형식으로 작성
      
      ### ✔Repeating
      - Yes or No 형식으로 작성.
      - 이러한 연구 이벤트가 주어진 주제 내에서 반복적으로 발생하고 있는지 여부
      
      ### ✔Type
      - Scheduled or Unscheduled or Common 세가지 중 하나를 선택	
      - 해당 타입에 따라서 양식이 달라질 수 있음. 각각의 목적이 다름.
      - Scheduled 의 경우, 예약된 것으로 각 주제에 대해 수집될 것으로 예상하는 일련의 양식.
      - unscheduled 의 경우, 심각한 부작용으로 인한 조기종료를 위해 일련의 양식처럼 발생되거나 발생되지 않을 수 있는 데이터를 수집한다.
      - common의 경우, 유해사례나 병용약물 로그와 같은 여러 다른 데이터 수집 이벤트에서 사용되는 양식이다.
      
      ### ✔Category
      - text 형식으로 작성. 작성 여부는 선택적임.
      - 연구 이벤트에 적합한 연구단계를 나타내는데 사용됨. ex) 선별, 사전 치료, 치료 및 후속조치
  

      ## 🤦‍♀️Description (문서에는 없으나, StudyEventDef 의 Body에 있는 태그)
      - Body : TranslatedText+
      - 연구 메타데이터 구성요소에 대한 설명. 여기에서는 StudyEventDef 에 대한 설명.
      ![화면 캡처 2022-06-29 092226](https://user-images.githubusercontent.com/25499386/176325633-02eaed32-efe1-4f55-9de5-1e20992c7a25.png)
      
      - 해당하는 속성은 없다.
      
        ## 🤷‍♀️TranslatedText
        - 특정 언어에 적합한 사람이 읽을 수 있는 텍스트. 
        - TranslatedText 요소는 일반적으로 시리즈로 나타나며 다양한 언어에 대한 대체 텍스트 변환 세트를 제공한다.
        - 해당 태그는 다음과 같은 속성을 사용한다.
          
          ### xml:lang (optional)
          - 작성 형식은 LanguageTag 이며, LL (-CC)* 형태를 가진다. (language code)-(contury code) ko-kr
            -  *ref https://www.loc.gov/standards/iso639-2/php/code_list.php , https://www.nationsonline.org/oneworld/country_code_list.htm
          - 사용방식은 다음과 같다.
          - ☝️ LT 태그가 있는 대상 언어에 적합한 텍스트를 찾으려면 xml:lang 특성이 LT와 정확히 일치(대소문자 무시)하는 번역 텍스트를 검색한다. e.g. "fr-FR"
          - ✌️ 실패한 경우, LT에서 종료 하위 태그를 제거하고 반복한다. e.g. "fr"
          - 👉 또 실패한 경우, xml:lang 속성이 없는 번역 텍스트를 검색해 사용한다. 만약 찾을 수 없는 경우, 사용 가능한 적절한 텍스트가 없는 것이다.
          

      
      ## 🤦‍♀️FormRef
      ![image](https://user-images.githubusercontent.com/25499386/176326698-63246664-cd9a-47e4-a728-52d219065048.png)
      ![image](https://user-images.githubusercontent.com/25499386/176327262-3fe7db2b-11a5-46cb-8148-c62cf81fba37.png)


      - 특정 StudyEventDef 내에서 발생하는 FormDef에 대한 참조.
      - FormRef 목록은 이러한 유형의 연구 이벤트 내에서 발생하도록 허용된 양식 유형을 식별한다.
      - 단일 StudyEventDef 내의 FormRef에는 중복 FormOID 또는 OrderNumber가 없어야 한다.

          ### ✔FormOID
          - oidref 형식으로 참조는 FormDef의 oid 를 참조한다.

          ### ✔OrderNumber (optional)
          - integer 형식으로 작성.
          - OrderNumbers는 양식 목록이 사용자에게 표시될 때마다 사용할 양식(포함하는 연구 이벤트 내)에 대한 순서를 제공한다.
          - 다만, 이 순서는 이벤트 일정, 시간 순서 또는 데이터 정확성에 대해서는 아무 것도 암시하지 않음.
          
          ### ✔Mandatory
          - yes or no 형식으로 답변.
          - 필수 플래그는 포함하는 연구 이벤트의 인스턴스에 대한 임상 데이터가 이러한 유형의 인스턴스 없이는 불완전할 것임을 나타낸다.
          - 불완전한 ODM 임상 데이터 파일은 연구 검토 및 분석 목적을 위해 불완전한 것으로 간주될 수 있음.
          
          ### ✔CollectionExceptionConditionOID (optional)
          - oidref 형식으로, 참조는 ConditionDef 의 oid 를 참조한다.
          - CollectionExceptionConditionOID 속성이 제공되면 이 Form에 대한 데이터가 수집되지 않아야 하는 상황을 설명하는 ConditionDef를 참조한다.
          - form 데이터가 수집되지 않아야 될 상황에 대한 레퍼런스.
          - 참조를 conditionDef에 대해서 진행함을 기억하자
          ![image](https://user-images.githubusercontent.com/25499386/176353717-0a3c9c12-6550-4450-838e-12a3ce5cbf8b.png)
          - conditionDef 의 body에 조건에 해당하는 내용이 적혀있고, 이하 formal 태그내용에 이에대한 조건식이 작성되어 있음.
          
          - 이 값이 참인 경우에 해당값을 수집하지 않는 방식.
          ![image](https://user-images.githubusercontent.com/25499386/176354276-31564961-abd2-4503-9f9b-765fcbee7e19.png)
          - c.2는 여자가 아닌 경우 
          ![image](https://user-images.githubusercontent.com/25499386/176354353-07442040-491d-4c82-bec9-f900ad1770c5.png)
          - 임신 관련질문에 대한 exception으로 c.2를 걸었음.  




