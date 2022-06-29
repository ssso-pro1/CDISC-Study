# ODM

> 3.1 ODM </br>
📑 3.1.1 Study </br>
     📁  MetaDataVersion </br>
          📌 3.1.1.3.3 StudyEventDef </br>
               ✅ 3.1.1.3.3.1 FormRef </br>
> 

# 3.1 ODM

# 📑 3.1.1. Study

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
            ✅ Description
            ✅ FormRef
        📌FormDef
            ✅ Description
		ItemGroupRef
        📌ItemGroupDef
            ✅ Description
               ItemRef
        📌ItemDef
            Question
            CodeListRef
            MeasurementUnitRef
            RangeCheck
        📌CodeList
            CodeListItem

```

## 📁 3.1.1.3 MetaDataVersion


```xml
<MetaDataVersion OID="MDV.1" Name="MetaDataVersion">
    <Protocol>
        <StudyEventRef StudyEventOID="SE.3" Mandatory="No"/>
    </Protocol>
		<StudyEventDef OID="SE.1" Name="Baseline (T0)" Repeating="No" Type="Common">
        <Description></Description>
        <FormRef FormOID="F.1" Mandatory="No"/>
    </StudyEventDef>		
		<FormDef OID="F.1" Name="Basis data" Repeating="No">
				<Description></Description>		
				<ItemGroupRef ItemGroupOID="IG.1" Mandatory="No"/>
		</FormDef>
		<ItemGroupDef OID="IG.1" Name="PersonalItems" Repeating="No">
		    <Description></Description>
		    <ItemRef ItemOID="Age" Mandatory="No"/>
		</ItemGroupDef>
		<ItemDef OID="Gender" Name="Gender" DataType="text">
		    <Question></Question>
		    <CodeListRef CodeListOID="CL.1"/>
		</ItemDef>
		<CodeList OID="CL.1" Name="CL.1" DataType="text">
        <CodeListItem CodedValue="Female"></CodeListItem>
    </CodeList>
</MetaDataVersion>
```

1.  `바디`:
    - Include
    - Protocol
    - 📌 StudyEventDef
    - 📌 FormDef
    - ItemGroupDef
    - ItemDef
    - CodeList
    - Imputationmethod Deprecated
    - Presentation
    - ConditionDef
    - MethodDef
2. `속성`:
    - OID oid
    - Name name
    - Description text (선택사항)
3. `포함된 곳`:
    
    📑 Study
    
- 메타데이터 버전은 연구 데이터를 구성하는 연구 이벤트, 양식, 항목 그룹 및 항목의 유형을 정의
- Include요소는 이전 메타 데이터 버전을 참조하며, 이전 버전의 모든 정의가 해당 버전에 자동으로 포함됨. 이러한 정의는 새 버전에서 동일한 OID를 사용 하여 재정의할 수 있음
</br>

## 📌 3.1.1.3.1 Include

```xml
<Study OID="S.001">
  <MetaDataVersion OID="MDV.002" Name="Second Metadata version"> 
    <Include StudyOID="S.001" MetaDataVersionOID="MDV.001"/>
    <ItemGroupDef OID="IG.001" Name="First ItemGroup (modified)"> 
      <ItemRef ItemOID="I.001" Mandatory="Yes" OrderNumber="1"/> 
      <ItemRef ItemOID="I.003" Mandatory="Yes" OrderNumber="2"/> 
      <ItemRef ItemOID="I.002" Mandatory="Yes" OrderNumber="3"/> 
      <Alias Context="Context1" Name="IG1"/> 
    </ItemGroupDef> 
  </MetaDataVersion> 
</Study>
```

1. `바디`: EMPTY
2. `속성`:  
    - StudyOID oidref
    - MetaDataVersionOID oidref
3.  `포함된 곳`:  
    
    📁 MetaDataVersion
    
- 이전 메타데이터 버전에 대한 참조
- 이 버전은 동일한 ODM파일 혹은 시리즈의 이전 파일에 존재해야 함
- ItemDef와 같은 메타 데이터 요소가 메타데이터 버전에서 재정의되면, 동일한 타입이나 OID를 갖는 모든 메타 데이터 요소는 대체됨. 새 정의에 존재하지 않는 모든 속성 및 자식 요소는 이전 버전에서 삭제됨
</br>

## 📌 3.1.1.3.2 Protocol

```xml
<Protocol>
    <StudyEventRef StudyEventOID="SE.1" Mandatory="No"/>
    <StudyEventRef StudyEventOID="SE.2" Mandatory="No"/>
    <StudyEventRef StudyEventOID="SE.3" Mandatory="No"/>
</Protocol>
```

1. `바디`: 
    
    ✅ **Description?**
    
    ✅ StudyEventRef*****
    
    ✅ **Alias*** </br>
    
2. `속성`: NONE
3. `포함된 곳`:
    
    📁 MetaDataVersion
    
- 연구의 특정 버전 내에서 발생할 수 있는 연구 이벤트의 종류를 나열
- 모든 임상 데이터는 이러한 연구 이벤트 중 하나 내에서 발생해야 함
- 참고: 메타데이터에 프로토콜 정의가 포함되지 않은 연구는 임상 데이터를 가질 수 없음. 이러한 연구는 ‘공통 메타데이터 사전’의 역할을 할 수 있어 연구 간 메타데이터를 공유할 수 있음
</br>

## 📌 3.1.1.3.3 StudyEventDef

```xml
<StudyEventDef OID="SE.1" Name="Baseline (T0)" Repeating="No" Type="Common">
    <Description>
        <TranslatedText xml:lang="en">Baseline (T0)</TranslatedText>
        <TranslatedText xml:lang="de">Vorbefragung (T0)</TranslatedText>
    </Description>
    <FormRef FormOID="F.1" Mandatory="No"/>
    <FormRef FormOID="F.2" Mandatory="No"/>
</StudyEventDef>
```

1. `바디`: </br>
    
    ✅ **Description?**
    
    ✅ **FormRef***
    
    ✅ **Alias*** </br>
    
2. `속성`:
    - OID oid
    - Name name
    - Repeating (Yes or No)
    - Type (Scheduled or Unscheduled or Common) 
    - Category text (선택사항)
3. `포함된 곳`:
    
    📁 MetaDataVersion
    
- 연구 단계를 나타내는 것 같음 (ex. Baseline, FollowUp) 에 해당하는 주제에서 수집되는 양식
- `Repeating` 은 해당 연구 이벤트가 반복적으로 발생할 수 있다는 것을 뜻함
- `Scheduled` 예정된 연구에서 수집되는 일련의 양식 
- `unscheduled` 예정되지 않은 연구 이벤트는 심각한 부작용으로 인한 조기 종료를 위해 작성된 일련의 양식과 같이 특정 주제에 대해 발생하거나 발생하지 않을 수 있는 데이터를 수집
- `common` 
	- 유해 사례 또는 병용 약물 로그와 같은 여러 다른 데이터 수집 이벤트에서 사용되는 양식 모음/ 
	- 방문일정 마다 각각 보는 게 아니라 공통으로 빼서 common에서 한 번에 보는 것. -> 한꺼번에 보겠다.
- `Category` 속성은 연구 이벤트에 적합한 연구 단계를 나타내는 데 사용 (ex. Screening, PreTreatment, Treatment, FollowUp)
</br>

## ✅ 3.1.1.3.3 FormRef

```xml
<StudyEventDef OID="SE.1" Name="Baseline (T0)" Repeating="No" Type="Common">
    <Description>
        <TranslatedText xml:lang="en">Baseline (T0)</TranslatedText>
        <TranslatedText xml:lang="de">Vorbefragung (T0)</TranslatedText>
    </Description>
    <FormRef FormOID="F.1" Mandatory="No"/>
    <FormRef FormOID="F.2" Mandatory="No"/>
</StudyEventDef>
```

1. `바디`: EMPTY
2. `속성`:
    - FormOID oidref
    - OrderNumber integer  (선택사항)
    - Mandatory (Yes | No)
    - CollectionExceptionConditionOID oidref
3. `포함된 곳`:
    
    📌 StudyEventDef
    
- 특정 StudyEventDef 내에서 발생하는 FormDef에 대한 참조로 양식 유형을 식별. 단일 StudyEventDef 내의 FormRef에는 중복 FormOID 또는 OrderNumber가 없어야 함
- `OrderNumbers` : 양식 목록이 사용자에게  표시될 때 사용할 양식의 순서 제공
- ConditionDef 참조 : CollectionExceptionConditionOID 속성이 제공되면 이 Form에 대한 데이터가 수집되지 않아야 함을 설명
</br>

### ✅ **Description**

```xml
<Description>
    <TranslatedText xml:lang="en">Baseline (T0)</TranslatedText>
    <TranslatedText xml:lang="de">Vorbefragung (T0)</TranslatedText>
</Description>
```

1. `바디`: TranslatedText </br>
2. `속성`: NONE </br>
3. `포함된 곳`: </br>
    - Protocol, StudyEventDef, FormDef, ItemGroupDef, ItemDef, ConditionDef, MethodDef
    </br>
- 연구 메타 데이터 구성요소에 대한 free-text 상세 설명
</br>

### ✅ **Alias**

```xml
<ItemDef OID="..." Name="Systolic blood pressure" DataType="float" ...>
    <Question>...</Question>
    <Alias Context="SDTM" Value="VSORRES where VSTESTCD=SYSBP"/>
</ItemDef>
```

1.  `바디`: EMPTY
2. `속성`:  </br> 
    - Context text
    - Name text
3.  `포함된 곳`:  </br>
    - Protocol
    - StudyEventDef
    - FormDef
    - ItemGroupDef
    - ItemDef
    - CodeList
    - CodeListItem
    - EnumeratedItem
    - ConditionDef
    - MethodDef
</br>

## 📑 속성별 데이터 타입

---

|  | 키 | 데이터 타입 | 참조 사항 |
| --- | --- | --- | --- |
| OID | oid | xs:string (아무 문자, 최소길이=1) |  |
| Name | name | xs:string (아무 문자, 최소길이=1) |  |
| Description | text |  |  |
| StudyOID  | oidref |  |  |
| MetaDataVersionOID  | oidref |  |  |
| Repeating  |  | (Yes or No) |  |
| Type  |  | (Scheduled or Unscheduled or Common) |  |
| Category  | text  | xs:string (아무 문자) |  |
| FormOID  | oidref  |  xs:string (아무 문자, 최소길이=1) | FormDef참조 |
| OrderNumber  | integer  | xs:integer (-?digit+) |  |
| Mandatory  |  | (Yes or No) |  |
| CollectionExceptionConditionOID  | oidref  | (Scheduled or Unscheduled or Common) (선택사항)  | ConditionDef참조 |
| Context | text |  |  |
| Name | text |  |  |
