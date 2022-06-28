# ODM
- 본 자료에 사용된 ODM은 open EDC 사용 ODM이다.
- 본 문서에서는 ODM의 상위 태그부터 하위태그까지의 속성들을 순차적으로 설명한다.

- 각 태그의 바디내용은 명시되어 있지 않을 경우, 들여쓰기의 내용이 body 내용임을 나타낸다.
- 명시되어 있는 경우, 바디에 작성될 수 있는 타입이 명시된다.

본 문서에서 다룰 태그 영역은 다음과 같다.

<img src="https://user-images.githubusercontent.com/25499386/176077390-0b23aa1a-f103-4446-93a2-dec8f7f044e0.PNG" width="550" height="600">


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
