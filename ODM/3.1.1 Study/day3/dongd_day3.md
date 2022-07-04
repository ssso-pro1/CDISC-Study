## 🤦‍♂️ ItemGroupDef
    
  ### 예제

  ```xml
  <ItemGroupDef OID="IG.1" Name="PersonalItems" Repeating="No">
              <Description>
                  <TranslatedText xml:lang="en">Personal questions</TranslatedText>
                  <TranslatedText xml:lang="de">Persönliche Fragen</TranslatedText>
              </Description>
              <ItemRef ItemOID="Age" Mandatory="No"/>
              <ItemRef ItemOID="Gender" Mandatory="No"/>
              <ItemRef ItemOID="Weight" Mandatory="No"/>
              <ItemRef ItemOID="Height" Mandatory="No"/>
              <ItemRef ItemOID="BMI" Mandatory="No" MethodOID="M.1"/>
              <ItemRef ItemOID="Pregnant" Mandatory="No" CollectionExceptionConditionOID="C.2"/>
              <ItemRef ItemOID="WeeksPregnant" Mandatory="No" CollectionExceptionConditionOID="C.5"/>
          </ItemGroupDef>

  ```
  - Body : Description?, ItemRef*, Alias* 를 포함할 수 있다.
  - 해당 태그는 다음과 같은 속성을 포함한다.
    ### ✔ OID
    - OID 형식으로 작성
    ### ✔ Name
    - name 형식으로 작성
    ### ✔ Repeating
    - Yes or No 형식으로 작성
    - 반복 플래그는 이러한 유형의 항목 그룹이 포함하는 양식(또는 참조 데이터) 내에서 반복적으로 발생할 수 있음을 나타냅니다.
    ### ✔ IsReferenceData
    - Yes or No 형식으로 작성
    - IsReferenceData가 Yes인 경우 이 유형의 항목 그룹은 ReferenceData 요소 내에서만 발생할 수 있습니다. Q. Refdata는 정확이 뭐를 의미하는가
    - IsReferenceData가 No이면 이러한 유형의 항목 그룹은 ClinicalData 요소 내에서만 발생할 수 있습니다
    - 속성의 기본 값은 No 이다.
    ### ✔ SASDatasetName
    - sasName 형식으로 작성 
    - 작성 형태는 다음과 같음. ( letter | _ )( letter | digit | _ )* (maxLength="8")
    ### ✔ Domain
    - text 형식으로 작성
    - Domain 이하,  Origin, Purpose 및 Comment 속성은 SDTM 메타데이터 제출 지침에 있는 CDISC 제출 메타데이터 모델에 설명된 대로 제출 정보를 전달합니다.
    ### ✔ Origin 
    - text 형식으로 작성
    ### ✔ Role (Deprecated)
    - name 형식으로 작성
    - But, 더이상 사용되지 않음. (새로운 application은 Role 대신 Purpose를 사용)
    - 역할 속성은 목적의 동의어로 간주될 수 있습니다.
    ### ✔ Purpose
    - text 형식으로 작성
    ### ✔ Comment
    - text 형식으로 작성

    ## 🤦‍♀️ItemRef
    - Body : none
    - 특정 ItemGroupDef 내에서 발생하는 ItemDef에 대한 참조입니다.
    - ItemRefs 목록은 이 유형의 항목 그룹 내에서 발생하도록 허용된 항목 유형을 식별합니다. 
    - 단일 ItemGroupDef 내의 ItemRef에는 중복된 ItemOID 또는 OrderNumber가 없어야 합니다.

    - 해당 태그는 다음과 같은속성을 포함한다.
      ### ItemOID
      - oidref 형식으로 작성 (참조는 ItemDef로 부터)

      ### OrderNumber
      - integer 형식으로 작성
      - OrderNumbers는 항목 목록이 사용자에게 표시될 때마다 사용할 항목(포함하는 항목 그룹 내)에 대한 순서를 제공합니다. 
      - 이벤트 일정, 시간 순서 또는 데이터 정확성에 대해서는 아무 것도 암시하지 않습니다.

      ### Mandatory
      - Yes or No 형식으로 작성
      - 필수 플래그는 포함하는 항목 그룹의 인스턴스에 대한 임상 데이터가 이러한 유형의 항목 인스턴스 없이는 불완전할 것임을 나타냅니다. 
      - 이러한 의미에서 불완전한 ODM 임상 데이터 파일은 연구 검토 및 분석 목적을 위해 불완전한 것으로 간주될 수 있습니다.

      ### KeySequence
      - integer 형식으로 작성
      - KeySequence(있는 경우)는 이 항목이 포함하는 항목 그룹의 키임을 나타냅니다.
      - 또한 키에 대한 순서를 제공합니다.

      ### MethodOID
      - oidref 형식으로 작성
      - MethodOID는 이 항목의 값을 파생하는 데 사용되는 MethodDef를 참조합니다.

      ### ImputationMethodOID
      - 현재는 사용되지 않음.

      ### Role
      - text 형식으로 사용. 
      - 역할 속성은 이 데이터 항목의 사용을 설명하는 단일 역할 이름을 제공합니다.
      - Role이 표준 용어로 정의되면 RoleCodeListOID를 사용하여 Role 속성 값을 가져오는 전체 역할 집합을 정의하는 CodeList를 참조할 수 있습니다.

      ### RoleCodeListOID
      - oidref 형식으로 작성
      - 이 속성은 Role 속성이 정의되어 있지 않으면 존재하지 않아야 합니다.
      - Role이 정의된 경우 RoleCodeListOID는 여전히 선택 사항입니다

      ### CollectionExceptionConditionOID
      - oidref 형식으로 작성 (conditionDef 참조)
      - 수집되지 않아도 되는 경우에 대한 것. 해당 부분은 이미 설명 된 바 있음.

  ## 🤦‍♂️ ItemDef
  ### 예제

  ```xml
  <!-- Item Definition: Variable Level (BRTHDTC) -->
  <ItemDef OID="IT.DM.BRTHDTC" Name="BRTHDTC" DataType="date" SASFieldName="BRTHDTC">
    <Description>
      <TranslatedText xml:lang="en">Date/Time of Birth</TranslatedText>
    </Description>
      <def:Origin Type="Collected" Source="Investigator">
      <def:DocumentRef leafID="LF.acrf">
      <def:PDFPageRef PageRefs="6" Type="PhysicalRef"/>
      </def:DocumentRef>
      </def:Origin>
  </ItemDef>

  ```

  - Body : (Description?, Question?, ExternalQuestion?, MeasurementUnitRef*, RangeCheck*, CodeListRef?, Role* Deprecated, Alias*)
  - ItemDef는 연구 내에서 발생할 수 있는 항목 유형을 설명합니다. 항목 속성에는 이름, 데이터 유형, 측정 단위, 범위 또는 코드 목록 제한 사항 및 기타 여러 속성이 포함됩니다.

  - 해당 태그의 속성은 다음과 같다.
    ### ✔ OID
    - oid 형식으로 작성
    ### ✔ Name
    - Name 형식으로 작성
    ### ✔ DataType
    - (text | integer | float | date | time | datetime | string | boolean | double | hexBinary | base64Binary | hexFloat | base64Float | partialDate | partialTime | partialDatetime | durationDatetime | intervalDatetime | incompleteDatetime | incompleteDate | incompleteTime | URI ) 형식으로 작성.
    - DataType 속성은 비교 및 ​​저장을 위해 해당 값 요소를 해석하는 방법을 지정한다.
    - DataType이 float인 경우 Length와 SignificantDigits가 모두 제공되거나 둘 다 없어야 한다.
    - DataType=integer인 경우 Length=N은 수신 시스템이 10의 N승 보다 작은 크기의 모든 정수 값을 처리하고 저장할 수 있어야 하는 요구 사항입니다. 더 큰 값은 거부될 수 있습니다.
    - DataType=float인 경우 Length=N 및 SignificantDigits=S는 수신 시스템이 10-S의 배수인 10의N-S승보다 작은 모든 숫자 값을 처리하고 저장할 수 있어야 하는 요구 사항입니다. 더 큰 값은 거부될 수 있습니다. 중간 값은 10의 -S승 의 가장 가까운 배수로 반올림될 수 있습니다. 

    - DataType=text인 경우 Length=N은 수신 시스템이 N보다 작거나 같은 길이의 모든 텍스트 문자열 값을 처리하고 저장할 수 있어야 한다.
    - Text 유형의 데이터는 ItemDataString 요소에서 전송되어야 합니다. (머임)
    - 예제
    ```xml
    <ClinicalData StudyOID="P2006-101" MetadataVersionOID="101.01">
    <SubjectData SubjectKey="1000" TransactionType="Insert">
    <StudyEventData StudyEventOID="Screen">
       <FormData FormOID="DEMOG">
          <ItemGroupData ItemGroupOID="DM">
              <ItemDataString ItemOID="USUBJID">101-001-001</ItemDataString>
              <ItemDataString ItemOID="SEX">F</ItemDataString>
          </ItemGroupData>
      </FormData>
      <FormData FormOID="LABDATA">
          <ItemGroupData ItemGroupOID="LB">
              <ItemDataDatetime ItemOID="LBDTC">2006-07-14T14:48</ItemDataDatetime>
              <ItemDataString ItemOID="LBTESTCD">ALT</ItemDataString>
              <ItemDataString ItemOID="LBORRES">245</ItemDataString>
          </ItemGroupData>
      </FormData>
    </StudyEventData>
    </SubjectData>
    </ClinicalData>
    ```
    ### ✔ Length
    - positiveInteger 형식으로 작성
    - +?digit+ (and representing an integer number > 0)
    - Length 속성은 DataType이 텍스트 또는 문자열일 때 필수.
    - DataType이 정수 또는 부동 소수점일 때 선택 사항이며, 다른 데이터 유형에는 제공해서는 안 됩니다.
    ### ✔ SignificantDigits
    - nonNegativeInteger 형식으로 작성
    - +?digit+ (and representing an integer number >= 0)
    - SignificantDigits 속성은 DataType이 부동일 때 선택 사항이며 다른 데이터 유형에 대해서는 제공해서는 안 됩니다.
    - Length 및 SignificantDigits는 값 요소에서 이러한 값을 나타내는 데 사용되는 문자 수가 아니라 항목의 데이터 값에 대한 설명입니다.
    ### ✔ SASFieldName
    - sasName 형식으로 작성 
    - 작성 형태는 다음과 같음. ( letter | _ )( letter | digit | _ )* (maxLength="8")
    - SAS 소프트웨어에서 식별할 수 있는 변수로 연결?
    ### ✔ SDSVarName
    - sasName 형식으로 작성 
    - 작성 형태는 다음과 같음. ( letter | _ )( letter | digit | _ )* (maxLength="8")
    - SDSVarName, Origin 및 Comment 속성은 최신 버전의 CDISC SDTM에 설명된 대로 제출 정보를 전달합니다.
    - 제출 표준에 대해 외부 소프트웨어가 환자 정보를 SDTM 변수에 맞춰 환자정보를 일치시키기 위한 변수. (환자정보를 일치시키다.)matching up patients 
    ### Origin
    ### Comment

    참고: ODM 모델에서 모든 내부 키는 변경할 수 없는 것으로 간주된다. 
    이는 감사 추적 문제가 작동하도록 하기 위해 수행되었습니다. audit trail

    모델의 SubjectKey가 환자의 실제 외부 주제 식별자(또는 무작위 ID)이고 해당 값이 하나의 ODM 파일에서 잘못 전송된 경우 수정할 방법이 없습니다. (???) Q. 잘못 전송된 경우란 어떤 경우를 시사하는가?

    이를 수행할 때 외부 주제 키(및 기타 외부에서 볼 수 있는 키 변수)가 메타데이터의 항목으로 정의되어야 합니다.따라서 정상적인 수정/감사 메커니즘을 통해 수정할 수 있습니다. 이것은 연구 키의 수정을 지원하는 문제를 해결하지만 사용자는 어떤 ItemDefs가 특별한 의미를 가지고 있는지 또는 그 의미가 무엇인지 식별할 수 있는 방법이 없습니다. 이것이 문제가 되는 가장 명백한 위치는 외부 소스에서 데이터를 로드할 때 환자를 일치시키는 것입니다. 환자 ID를 찾을 수 없으면 어떻게 일치합니까?

    정답은 ItemDef의 SDSVarName 속성을 사용하는 것입니다. SDSVarName은 비즈니스 의미로 항목에 태그를 지정하는 데 사용할 수 있는 선택적 속성입니다. ODM 모델에서 가능한 모든 의미를 열거하려고 하기보다 ODM 작업 그룹은 CDISC SDTM에 정의된 변수 이름 집합에 의존하는 것이 가장 좋다고 생각했습니다.

    이 목록은 임상 데이터 관리에 사용되는 핵심 변수를 포함하기 때문입니다. 따라서 ODM 호환 XML 인스턴스를 처리하는 소프트웨어는 SDSVarName 속성의 특정 값을 사용하여 자주 사용되는 표준 변수를 식별할 수 있습니다. 이 속성의 사용은 SDTM 모델에 정의된 변수로 제한됩니다. 변수에 태그를 지정할 때 해당 변수에 대한 SDTM 정의와 일치하는 것으로 식별합니다. 일반적으로 사용되는 값의 일부 목록은 다음과 같습니다.
    *SDS 는 제출 표준?

    - STUDYID (Study Identifier Unique within a Submission)
    - USUBJID (Study Identifier Unique within a Submission),
    - SUBJID (Subject Identifier Unique within a Study),
    - SITEID (Unique Identifier for a study Site)
    - SEX (Sex or Gender, coded value),
    - VISITNUM (Clinical encounter Number)
    - VISIT (Protocol-defined description of clinical encounter),
    - VISITDY (Planned study day of VISIT)

    이런 변수들을 쓴다더라~

    - 이하 Body에 대한 설명.
    Question 요소에는 이 항목에 대한 데이터를 제공하라는 메시지가 표시될 때 사용자에게 표시되는 텍스트가 포함됩니다. ExternalQuestion 요소는 동일한 작업을 수행하지만 외부에서 정의된 질문을 참조합니다. 둘 다 있는 경우 일관성이 있어야 합니다.

    MeasurementUnitRefs는 이 유형의 항목에 대해 허용되는 측정 단위를 나열합니다. 숫자 항목만 측정 단위를 가질 수 있습니다. MeasurementUnitRef가 하나만 있는 경우 이 유형의 모든 항목은 기본적으로 이 측정 단위를 사용합니다. ItemDef-MeasurementUnitRef.
    수치 항목의 정의에 MeasurementUnitRef가 없는 경우 항목의 값은 스칼라(즉, 순수)입니다.

    RangeChecks는 이 유형의 항목에 대해 허용되는 값을 제한합니다.

    CodeListRef(있는 경우)는 이 유형의 항목에 대해 허용되는 값을 참조된 코드 목록의 구성원으로 제한합니다.
