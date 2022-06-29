# 3.1 ODM
> 3.1 ODM </br>
    - 📑 3.1.1Study </br>
        - 📌 3.1.1.1GlobalVariables </br>
        - 📌 3.1.1.2       BasicDefinitions </br>
        
        
`바디: Study, AdminData*, ReferenceData*, ClinicalData*, Association*, ds:Signature*` </br>
`속성: `

|세부사항|문자|설명|
|--------|--------|------------------------|
|FileType|스냅샷/ 트랜잭션| - 스냅샷 : 문서에 포함된 현재 데이터의 상태와 메타데이터의 현재 상태만 포함되고, 트랜잭션 기록은 포함되지 않음. 스냅샷 문서에는 데이터 포인트 당 하나의 명령만 포함. 임상 데이터의 경우 스냅샷 파일의 트랜잭션 타입은 존재하지 않거나 입력이 없어야 함.</br></br> - 트랜잭션: 문서가 데이터 포인트 당 둘 이상의 명령을 포함할 수 있다는 것을 뜻한다. 트랜잭션 문서를 사용하여 데이터의 현재 상태와 데이터가 어떻게 거기에 생겼는지를 모두 전송해라.  |
|Granularity| All/Metadata/AdminData/</br> ReferenceData/AllClinicalData/</br> SingleSite/SingleSubject| 발신인에게 특정 일반적인 유형의 문서에 대해 문서의 정보 범위를 설명하는 간단한 방법을 제공하기 위한 것. |
|Archival|(Yes/No)|파일이 21 CFR 11에 정의된 전자 기록의 요구 사항을 충족하도록 의도되었음을 나타내려면 이 속성을 예로 설정.  FileType이 트랜잭션인 경우에만 이 속성을 사용|
|FileOID|oid|이 파일의 고유 식별자|
|CreationDateTime|datetime|문서가 포함된 파일을 만든 시간|
|PriorFileOID|oidref|시리즈의 이전 파일(있는 경우)에 대한 참조|
|AsOfDateTime|datetime|이 문서를 만들기 위해 원본 데이터베이스를 쿼리한 날짜/시간|
|ODMVersion|( 1.2/1.2.1/1.3/1.3.1/1.3.2 )|사용된 ODM 표준 버전|
|Originator|text|ODM 파일을 생성한 조직|
|SourceSystem|text|이 파일에 있는 정보의 소스인 컴퓨터 시스템 또는 데이터베이스 관리 시스템|
|SourceSystemVersion|text|위의 "SourceSystem" 버전|
|ID|ID|ds:Signature 요소에서 이 요소를 다시 참조하는 데 사용|

- AsOfDateTime  
    - 새 데이터 또는 현재 파일에 포함된 데이터 업데이트의 최신 날짜/시간. 
    - 생략하면 AsOfDateTime이 CreationDateTime과 동일한 것으로 가정됨. 
    - CreationDateTime보다 늦은 AsOfDateTime을 제공하는 것은 오류.

- ODMVersion 속성은 ODM 1.1에서 정의되지 않았으므로 누락된 ODMVersion은 "1.1"로 해석되어야 함.

- 이 버전의 새로운 기능을 사용하려면 ODM 1.3.2 기반 문서에 ODMVersion="1.3.2"가 설정되어 있어야 함. ODM 1.2.0 기반 문서에는 ODMVersion="1.2"가 있어야 하고, ODM 1.3.0 기반 문서에는 ODMVersion="1.3"이 있어야 하며, ODM 1.3.1 기반 문서에는 이전 버전과의 호환성을 위해 ODMVersion="1.3.1"이 있어야 함.


## 📑 3.1.1 Study
`바디: (GlobalVariables, BasicDefinitions, MetaDataVersion*)` </br>
`속성: oid` </br>
`포함된 곳: ODM` </br>
개별 연구에 대한 정적 구조 정보를 수집.
</br>

### 📌 3.1.1.1 GlobalVariables
`바디: 	(StudyName, StudyDescription, ProtocolName)` </br>
`속성: NONE` </br>
`포함된 곳: Study` </br>
연구에 대한 일반 요약 정보가 포함됨.

### StudyName
`바디: 	name` </br>
`속성: NONE` </br> 
`포함된 곳: GlobalVariables` </br>
연구의 짧은 외부 이름.

### StudyDescription
`바디: 	text` </br>
`속성: NONE` </br>
`포함된 곳: GlobalVariables` </br>
연구에 대한 자유 텍스트 설명.

### ProtocolName
`바디: 	name` </br>
`속성: NONE` </br>
`포함된 곳: GlobalVariables` </br>
프로토콜에 대한 후원자의 내부 이름.
</br>

### 📌 3.1.1.2 BasicDefinitions
`바디: 	MeaurementUnit` </br>
`속성: NONE` </br>
`포함된 곳: Study` 

### MeasurementUnit
`바디: 	(Symbol, Alias)` </br>
`속성: OID-oid, Name-text` </br> 
`포함된 곳: BasicDefinitions` </br>
데이터 항목 또는 값에 대한 물리적 측정 단위. MeasurementUnit의 의미는 Name 속성에 의해 결정됨. </br>
ex) 킬로그램, 센티미터, 셀/밀리리터 등

참고: 측정 단위의 이름을 표준화하는 것은 ODM의 범위를 벗어남

### Symbol
`바디: 	(TranslatedText)` </br>
`속성: NONE` </br>
`포함된 곳: MeaurementUnit` </br>
측정 단위의 사람이 읽을 수 있는 이름.

### TranslatedText
`바디: 	text` </br>
`속성: xml:lang-languageTag (옵션)` </br>
`포함된 곳: Decode, ErrorMessage, Question, Symbol, Description` </br>
일반적으로 시리즈로 나타나며 다양한 언어에 대한 대체 텍스트 변환 세트를 제공.

참고: xml:lang 속성은 XML 표준의 일부입니다.
