General Elements
=========
# 3.1 ODM


### Body


3.1.1 Study   
3.1.2 AdminData   
3.1.3 ReferenceData   
3.1.4 ClinicalData   
3.1.5 Association   
3.1.6 ds:Signature   

### Attributes
  ##### Dsecription   
      type : text   
      보내는 사람은 설명을 작성하여 받는 사람이 문서를 올바르게 해석하는데 도움이 되는 정보를 기록
      
  ##### FileType
      type : Snapshot, Transactional
      
      - Sanpshot : 문서에 설명된 데이터 및 메타데이터의 현재 상태만 포함되고 트랜잭션 기록은 포함되지 않는다.   
                   스냅샷 문서에는 각 데이터당 하나의 명령만 포함될 수 있습니다.
                   임상 데이터의 스냅샷 파일은 트랜잭션 타입을 입력해서는 안된다.
                   
      - Transactional : 문서가 데이터 포인트당(per data point?) 두개 이상의 설명을 포함할 수 있다는 것이다.   
                        트랜잭션 문서를 사용하여 데이터의 현재 상태와 데이터가 어떻게 존재하게 되었는지를 모두 전송한다.     
  #####  Granularity
    type : All, Metadata, AdminData, ReferenceData, AllClinicalData, SingleSite, SingleSubject   
    
    발신인에게 특정 문서에 대해 문서의 정보 범위를 설명하는 간단한 방법을 제공  
    
    - All : 전체적인 연구
    - Metadata : MetaDataVersion 요소
    - AdminData, ReferenceData : 각 해당 요소
    - AllClinicalData, SingleSite, SingleSubject : 연구의 임상데이터 하위 항목으로 더 중점을 둔다.     
       
    이러한 카테고리들로 충분하지 않다면, description을 사용하여 세부정보를 제공하면된다.
    
 ##### Archival
     type : Yes, No
     
     21 CRF11의 정의된 전자적인 기록의 요구사항을 충족시키기위해 파일 대신에 속성을 YES로 설정하여 나타낸다.
     속성의 의미와 다른 ODM 속성과의 상호 작용에 대한 자세한 내용은 단일 파일 및 컬렉션을 참고     
     이 속석은 FileType이 Transactional인 경우에만 사용   
     
 ##### FileOID
     type : oid   
     파일의 고유 식별자
     
 ##### CreationDateTime
     type : datetime
     문서를 만든 날짜 및 시간
 
 ##### PriorFileOID
     type : oidref
      이전의 OID 파일에 대한 참조
 
 ##### AsOfDateTime
    type : datetime
    문서작성을 위해  DB에 insert or update한 가장 최근 시간
    
 ##### ODMVersion
    type : 1.2, 1.2.1, 1.3, 1.3.1
    사용한 ODM 표준의 version
    
 ##### Originator
    type : text
    ODM 파일을 생성한 조직(회사)
    
 ##### SourceSystem
    type : text
    ODM 파일(source)의 컴퓨터 system이나 DB management system
    
 ##### SourceSystemVersion
    type : text
    SourceSystem의 version

 ##### ID
    type : ID
    Signature(ID)가 현재 ODM을 참조하는 데 다시 사용할 수 있다.
    
AsOfDateTime은 파일에 새로운 데이터가 추가되거나 업데이트된 가장 최신의 날짜이다. 
이 속성은 암시적이고 생략할 경우 AsOfDateTime과 CreationDateTime이 같다고 가정한다.
AsOfDateTime보다 CreationDateTime이 늦으면 오류이다.

ODMVersion 속성은 ODM1.1에 정의되지 않았다. 그래서 ODMVersion이 없으면 1.1Version으로 이해할 수 있다.

이 버전의 새로운 기능을 사용하려면 ODM 1.3.1 기반 문서에 ODMVersion="1.3.1"이 설정되어 있어야한다.
ODM 1.2.0 기반 문서는 ODMVersion 1.2를 가져야 하며 ODM 1.3.0 기반 문서는 이전 Version과 호환성을 위해 ODM Version 1.3을 가져야한다.

이런 속성에 대한 자세한 설명은 Single Files and Collections에서 설명한다.

 ### 3.1.1 Study
 Study는 개별 연구의 대한 정적인 구조 정보를 모은다.
 #### Body
 1. GlobalVariables
 2. BasicDefinitions
 3. MetaDataVersion
 
 ##### Attributes
 OID : oid
 ##### Contained in
 ODM

 #### 1. GlobalVariables
 GlobalVariables은 Study의 일밙거인 요약을 담고 있다. 
 ##### Body
 1. StudyName : 연구 제목 
 2. StudyDescription : 연구 설명
 3. ProtocolName : 프로토콜의 대한 sponsor이름
 
 ##### Contained in
 Study

 #### 2. BasicDefinitions
 
 #### Body
 1. MeasurementUnit : 데이터 항목 또는 값에 대한 물리적 측정 단위. 예) Kg, cm, mm   
    a. Alias   
    b. Simbol : 측정단위 이름   
    -  TranslatedText    
    사람이 읽을 수 있는 text. TranslatedText요소는 보통 연속으로 발생하고, 다른 언어데 애한 대체체 택스트 렌더링을 제공한다. LT태크가 있는 적절한 text를 찾으러면, xml속성이 LT와 정확히 일치하는 TranslatedText를 검색해야한다. 
        
        not found
        1. LT에서 끝의 subtag를 제거하고 반복해본다. 그래도 찾지 못하면 번역된 파일을 검색한다.
        2. xml:lang 요소 없이 TranslatedText를 검색해본다.

        |TranslatedTexts|검색 요청|과정|
        |-----------------|---|---|
        |\<TranslatedText xml:lang="fr-CA">'..</br>\<TranslatedText xml:lang="en-GB">..</br>\<TranslatedText>...|fr-FR|xml:lang="fr-FR" 검색</br>못찾으면,xml:lang="fr" 검색</br>또 못찾으면, xml:lang이 TranslatedTex에 없는것이다.</br>반드시 사용해야하는 text이기 때문|
        
    모호한 것을 방지하기위해서, 특정 언어 태그가 연속적인 TranslatedText요소가 두번이상 있으면 안된다.   
    그리고, 동일한 xml:lang요소에 여러개의 TranslatedText가 허용되지 않는다.   
    Note: xml:lang 속성은 XML의 표준이다.
 
