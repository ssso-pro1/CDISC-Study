## ๐คฆโโ๏ธ ItemGroupDef
    
  ### ์์ 

  ```xml
  <ItemGroupDef OID="IG.1" Name="PersonalItems" Repeating="No">
              <Description>
                  <TranslatedText xml:lang="en">Personal questions</TranslatedText>
                  <TranslatedText xml:lang="de">Persรถnliche Fragen</TranslatedText>
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
  - Body : Description?, ItemRef*, Alias* ๋ฅผ ํฌํจํ  ์ ์๋ค.
  - ํด๋น ํ๊ทธ๋ ๋ค์๊ณผ ๊ฐ์ ์์ฑ์ ํฌํจํ๋ค.
    ### โ OID
    - OID ํ์์ผ๋ก ์์ฑ
    ### โ Name
    - name ํ์์ผ๋ก ์์ฑ
    ### โ Repeating
    - Yes or No ํ์์ผ๋ก ์์ฑ
    - ๋ฐ๋ณต ํ๋๊ทธ๋ ์ด๋ฌํ ์ ํ์ ํญ๋ชฉ ๊ทธ๋ฃน์ด ํฌํจํ๋ ์์(๋๋ ์ฐธ์กฐ ๋ฐ์ดํฐ) ๋ด์์ ๋ฐ๋ณต์ ์ผ๋ก ๋ฐ์ํ  ์ ์์์ ๋ํ๋๋๋ค.
    ### โ IsReferenceData
    - Yes or No ํ์์ผ๋ก ์์ฑ
    - IsReferenceData๊ฐ Yes์ธ ๊ฒฝ์ฐ ์ด ์ ํ์ ํญ๋ชฉ ๊ทธ๋ฃน์ ReferenceData ์์ ๋ด์์๋ง ๋ฐ์ํ  ์ ์์ต๋๋ค. Q. Refdata๋ ์ ํ์ด ๋ญ๋ฅผ ์๋ฏธํ๋๊ฐ
    - IsReferenceData๊ฐ No์ด๋ฉด ์ด๋ฌํ ์ ํ์ ํญ๋ชฉ ๊ทธ๋ฃน์ ClinicalData ์์ ๋ด์์๋ง ๋ฐ์ํ  ์ ์์ต๋๋ค
    - ์์ฑ์ ๊ธฐ๋ณธ ๊ฐ์ No ์ด๋ค.
    ### โ SASDatasetName
    - sasName ํ์์ผ๋ก ์์ฑ 
    - ์์ฑ ํํ๋ ๋ค์๊ณผ ๊ฐ์. ( letter | _ )( letter | digit | _ )* (maxLength="8")
    ### โ Domain
    - text ํ์์ผ๋ก ์์ฑ
    - Domain ์ดํ,  Origin, Purpose ๋ฐ Comment ์์ฑ์ SDTM ๋ฉํ๋ฐ์ดํฐ ์ ์ถ ์ง์นจ์ ์๋ CDISC ์ ์ถ ๋ฉํ๋ฐ์ดํฐ ๋ชจ๋ธ์ ์ค๋ช๋ ๋๋ก ์ ์ถ ์ ๋ณด๋ฅผ ์ ๋ฌํฉ๋๋ค.
    ### โ Origin 
    - text ํ์์ผ๋ก ์์ฑ
    ### โ Role (Deprecated)
    - name ํ์์ผ๋ก ์์ฑ
    - But, ๋์ด์ ์ฌ์ฉ๋์ง ์์. (์๋ก์ด application์ Role ๋์  Purpose๋ฅผ ์ฌ์ฉ)
    - ์ญํ  ์์ฑ์ ๋ชฉ์ ์ ๋์์ด๋ก ๊ฐ์ฃผ๋  ์ ์์ต๋๋ค.
    ### โ Purpose
    - text ํ์์ผ๋ก ์์ฑ
    ### โ Comment
    - text ํ์์ผ๋ก ์์ฑ

    ## ๐คฆโโ๏ธItemRef
    - Body : none
    - ํน์  ItemGroupDef ๋ด์์ ๋ฐ์ํ๋ ItemDef์ ๋ํ ์ฐธ์กฐ์๋๋ค.
    - ItemRefs ๋ชฉ๋ก์ ์ด ์ ํ์ ํญ๋ชฉ ๊ทธ๋ฃน ๋ด์์ ๋ฐ์ํ๋๋ก ํ์ฉ๋ ํญ๋ชฉ ์ ํ์ ์๋ณํฉ๋๋ค. 
    - ๋จ์ผ ItemGroupDef ๋ด์ ItemRef์๋ ์ค๋ณต๋ ItemOID ๋๋ OrderNumber๊ฐ ์์ด์ผ ํฉ๋๋ค.

    - ํด๋น ํ๊ทธ๋ ๋ค์๊ณผ ๊ฐ์์์ฑ์ ํฌํจํ๋ค.
      ### ItemOID
      - oidref ํ์์ผ๋ก ์์ฑ (์ฐธ์กฐ๋ ItemDef๋ก ๋ถํฐ)

      ### OrderNumber
      - integer ํ์์ผ๋ก ์์ฑ
      - OrderNumbers๋ ํญ๋ชฉ ๋ชฉ๋ก์ด ์ฌ์ฉ์์๊ฒ ํ์๋  ๋๋ง๋ค ์ฌ์ฉํ  ํญ๋ชฉ(ํฌํจํ๋ ํญ๋ชฉ ๊ทธ๋ฃน ๋ด)์ ๋ํ ์์๋ฅผ ์ ๊ณตํฉ๋๋ค. 
      - ์ด๋ฒคํธ ์ผ์ , ์๊ฐ ์์ ๋๋ ๋ฐ์ดํฐ ์ ํ์ฑ์ ๋ํด์๋ ์๋ฌด ๊ฒ๋ ์์ํ์ง ์์ต๋๋ค.

      ### Mandatory
      - Yes or No ํ์์ผ๋ก ์์ฑ
      - ํ์ ํ๋๊ทธ๋ ํฌํจํ๋ ํญ๋ชฉ ๊ทธ๋ฃน์ ์ธ์คํด์ค์ ๋ํ ์์ ๋ฐ์ดํฐ๊ฐ ์ด๋ฌํ ์ ํ์ ํญ๋ชฉ ์ธ์คํด์ค ์์ด๋ ๋ถ์์ ํ  ๊ฒ์์ ๋ํ๋๋๋ค. 
      - ์ด๋ฌํ ์๋ฏธ์์ ๋ถ์์ ํ ODM ์์ ๋ฐ์ดํฐ ํ์ผ์ ์ฐ๊ตฌ ๊ฒํ  ๋ฐ ๋ถ์ ๋ชฉ์ ์ ์ํด ๋ถ์์ ํ ๊ฒ์ผ๋ก ๊ฐ์ฃผ๋  ์ ์์ต๋๋ค.

      ### KeySequence
      - integer ํ์์ผ๋ก ์์ฑ
      - KeySequence(์๋ ๊ฒฝ์ฐ)๋ ์ด ํญ๋ชฉ์ด ํฌํจํ๋ ํญ๋ชฉ ๊ทธ๋ฃน์ ํค์์ ๋ํ๋๋๋ค.
      - ๋ํ ํค์ ๋ํ ์์๋ฅผ ์ ๊ณตํฉ๋๋ค.

      ### MethodOID
      - oidref ํ์์ผ๋ก ์์ฑ
      - MethodOID๋ ์ด ํญ๋ชฉ์ ๊ฐ์ ํ์ํ๋ ๋ฐ ์ฌ์ฉ๋๋ MethodDef๋ฅผ ์ฐธ์กฐํฉ๋๋ค.

      ### ImputationMethodOID
      - ํ์ฌ๋ ์ฌ์ฉ๋์ง ์์.

      ### Role
      - text ํ์์ผ๋ก ์ฌ์ฉ. 
      - ์ญํ  ์์ฑ์ ์ด ๋ฐ์ดํฐ ํญ๋ชฉ์ ์ฌ์ฉ์ ์ค๋ชํ๋ ๋จ์ผ ์ญํ  ์ด๋ฆ์ ์ ๊ณตํฉ๋๋ค.
      - Role์ด ํ์ค ์ฉ์ด๋ก ์ ์๋๋ฉด RoleCodeListOID๋ฅผ ์ฌ์ฉํ์ฌ Role ์์ฑ ๊ฐ์ ๊ฐ์ ธ์ค๋ ์ ์ฒด ์ญํ  ์งํฉ์ ์ ์ํ๋ CodeList๋ฅผ ์ฐธ์กฐํ  ์ ์์ต๋๋ค.

      ### RoleCodeListOID
      - oidref ํ์์ผ๋ก ์์ฑ
      - ์ด ์์ฑ์ Role ์์ฑ์ด ์ ์๋์ด ์์ง ์์ผ๋ฉด ์กด์ฌํ์ง ์์์ผ ํฉ๋๋ค.
      - Role์ด ์ ์๋ ๊ฒฝ์ฐ RoleCodeListOID๋ ์ฌ์ ํ ์ ํ ์ฌํญ์๋๋ค

      ### CollectionExceptionConditionOID
      - oidref ํ์์ผ๋ก ์์ฑ (conditionDef ์ฐธ์กฐ)
      - ์์ง๋์ง ์์๋ ๋๋ ๊ฒฝ์ฐ์ ๋ํ ๊ฒ. ํด๋น ๋ถ๋ถ์ ์ด๋ฏธ ์ค๋ช ๋ ๋ฐ ์์.

  ## ๐คฆโโ๏ธ ItemDef
  ### ์์ 

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

  - Body : Description?, Question?, ExternalQuestion?, MeasurementUnitRef*, RangeCheck*, CodeListRef?, Role* Deprecated, Alias*
  - Question ์์์๋ ์ด ํญ๋ชฉ์ ๋ํ ๋ฐ์ดํฐ๋ฅผ ์ ๊ณตํ๋ผ๋ ๋ฉ์์ง๊ฐ ํ์๋  ๋ ์ฌ์ฉ์์๊ฒ ํ์๋๋ ํ์คํธ๊ฐ ํฌํจ๋ฉ๋๋ค. 
  - ExternalQuestion ์์๋ ๋์ผํ ์์์ ์ํํ์ง๋ง ์ธ๋ถ์์ ์ ์๋ ์ง๋ฌธ์ ์ฐธ์กฐํฉ๋๋ค. ๋ ๋ค ์๋ ๊ฒฝ์ฐ ์ผ๊ด์ฑ์ด ์์ด์ผ ํฉ๋๋ค.
  - MeasurementUnitRefs๋ ์ด ์ ํ์ ํญ๋ชฉ์ ๋ํด ํ์ฉ๋๋ ์ธก์  ๋จ์๋ฅผ ๋์ดํฉ๋๋ค. ์ซ์ ํญ๋ชฉ๋ง ์ธก์  ๋จ์๋ฅผ ๊ฐ์ง ์ ์์ต๋๋ค.
  - MeasurementUnitRef๊ฐ ํ๋๋ง ์๋ ๊ฒฝ์ฐ ์ด ์ ํ์ ๋ชจ๋  ํญ๋ชฉ์ ๊ธฐ๋ณธ์ ์ผ๋ก ์ด ์ธก์  ๋จ์๋ฅผ ์ฌ์ฉํฉ๋๋ค. ItemDef-MeasurementUnitRef.
  - ์์น ํญ๋ชฉ์ ์ ์์ MeasurementUnitRef๊ฐ ์๋ ๊ฒฝ์ฐ ํญ๋ชฉ์ ๊ฐ์ ์ค์นผ๋ผ(์ฆ, ์์)์๋๋ค.
  - RangeChecks๋ ์ด ์ ํ์ ํญ๋ชฉ์ ๋ํด ํ์ฉ๋๋ ๊ฐ์ ์ ํํฉ๋๋ค.
  - CodeListRef(์๋ ๊ฒฝ์ฐ)๋ ์ด ์ ํ์ ํญ๋ชฉ์ ๋ํด ํ์ฉ๋๋ ๊ฐ์ ์ฐธ์กฐ๋ ์ฝ๋ ๋ชฉ๋ก์ ๊ตฌ์ฑ์์ผ๋ก ์ ํํฉ๋๋ค.
  
  - ItemDef๋ ์ฐ๊ตฌ ๋ด์์ ๋ฐ์ํ  ์ ์๋ ํญ๋ชฉ ์ ํ์ ์ค๋ชํฉ๋๋ค. ํญ๋ชฉ ์์ฑ์๋ ์ด๋ฆ, ๋ฐ์ดํฐ ์ ํ, ์ธก์  ๋จ์, ๋ฒ์ ๋๋ ์ฝ๋ ๋ชฉ๋ก ์ ํ ์ฌํญ ๋ฐ ๊ธฐํ ์ฌ๋ฌ ์์ฑ์ด ํฌํจ๋ฉ๋๋ค.

  - ํด๋น ํ๊ทธ์ ์์ฑ์ ๋ค์๊ณผ ๊ฐ๋ค.
    ### โ OID
    - oid ํ์์ผ๋ก ์์ฑ
    ### โ Name
    - Name ํ์์ผ๋ก ์์ฑ
    ### โ DataType
    - (text | integer | float | date | time | datetime | string | boolean | double | hexBinary | base64Binary | hexFloat | base64Float | partialDate | partialTime | partialDatetime | durationDatetime | intervalDatetime | incompleteDatetime | incompleteDate | incompleteTime | URI ) ํ์์ผ๋ก ์์ฑ.
    - DataType ์์ฑ์ ๋น๊ต ๋ฐ โโ์ ์ฅ์ ์ํด ํด๋น ๊ฐ ์์๋ฅผ ํด์ํ๋ ๋ฐฉ๋ฒ์ ์ง์ ํ๋ค.
    - DataType์ด float์ธ ๊ฒฝ์ฐ Length์ SignificantDigits๊ฐ ๋ชจ๋ ์ ๊ณต๋๊ฑฐ๋ ๋ ๋ค ์์ด์ผ ํ๋ค.
    - DataType=integer์ธ ๊ฒฝ์ฐ Length=N์ ์์  ์์คํ์ด 10์ N์น ๋ณด๋ค ์์ ํฌ๊ธฐ์ ๋ชจ๋  ์ ์ ๊ฐ์ ์ฒ๋ฆฌํ๊ณ  ์ ์ฅํ  ์ ์์ด์ผ ํ๋ ์๊ตฌ ์ฌํญ์๋๋ค. ๋ ํฐ ๊ฐ์ ๊ฑฐ๋ถ๋  ์ ์์ต๋๋ค.
    - DataType=float์ธ ๊ฒฝ์ฐ Length=N ๋ฐ SignificantDigits=S๋ ์์  ์์คํ์ด 10-S์ ๋ฐฐ์์ธ 10์N-S์น๋ณด๋ค ์์ ๋ชจ๋  ์ซ์ ๊ฐ์ ์ฒ๋ฆฌํ๊ณ  ์ ์ฅํ  ์ ์์ด์ผ ํ๋ ์๊ตฌ ์ฌํญ์๋๋ค. ๋ ํฐ ๊ฐ์ ๊ฑฐ๋ถ๋  ์ ์์ต๋๋ค. ์ค๊ฐ ๊ฐ์ 10์ -S์น ์ ๊ฐ์ฅ ๊ฐ๊น์ด ๋ฐฐ์๋ก ๋ฐ์ฌ๋ฆผ๋  ์ ์์ต๋๋ค. 

    - DataType=text์ธ ๊ฒฝ์ฐ Length=N์ ์์  ์์คํ์ด N๋ณด๋ค ์๊ฑฐ๋ ๊ฐ์ ๊ธธ์ด์ ๋ชจ๋  ํ์คํธ ๋ฌธ์์ด ๊ฐ์ ์ฒ๋ฆฌํ๊ณ  ์ ์ฅํ  ์ ์์ด์ผ ํ๋ค.
    - Text ์ ํ์ ๋ฐ์ดํฐ๋ ItemDataString ์์์์ ์ ์ก๋์ด์ผ ํฉ๋๋ค. (๋จธ์)
    - ์์ 
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
    ### โ Length
    - positiveInteger ํ์์ผ๋ก ์์ฑ
    - +?digit+ (and representing an integer number > 0)
    - Length ์์ฑ์ DataType์ด ํ์คํธ ๋๋ ๋ฌธ์์ด์ผ ๋ ํ์.
    - DataType์ด ์ ์ ๋๋ ๋ถ๋ ์์์ ์ผ ๋ ์ ํ ์ฌํญ์ด๋ฉฐ, ๋ค๋ฅธ ๋ฐ์ดํฐ ์ ํ์๋ ์ ๊ณตํด์๋ ์ ๋ฉ๋๋ค.
    ### โ SignificantDigits
    - nonNegativeInteger ํ์์ผ๋ก ์์ฑ
    - +?digit+ (and representing an integer number >= 0)
    - SignificantDigits ์์ฑ์ DataType์ด ๋ถ๋์ผ ๋ ์ ํ ์ฌํญ์ด๋ฉฐ ๋ค๋ฅธ ๋ฐ์ดํฐ ์ ํ์ ๋ํด์๋ ์ ๊ณตํด์๋ ์ ๋ฉ๋๋ค.
    - Length ๋ฐ SignificantDigits๋ ๊ฐ ์์์์ ์ด๋ฌํ ๊ฐ์ ๋ํ๋ด๋ ๋ฐ ์ฌ์ฉ๋๋ ๋ฌธ์ ์๊ฐ ์๋๋ผ ํญ๋ชฉ์ ๋ฐ์ดํฐ ๊ฐ์ ๋ํ ์ค๋ช์๋๋ค.
    ### โ SASFieldName
    - sasName ํ์์ผ๋ก ์์ฑ 
    - ์์ฑ ํํ๋ ๋ค์๊ณผ ๊ฐ์. ( letter | _ )( letter | digit | _ )* (maxLength="8")
    - SAS ์ํํธ์จ์ด์์ ์๋ณํ  ์ ์๋ ๋ณ์๋ก ์ฐ๊ฒฐ?
    ### โ SDSVarName
    - sasName ํ์์ผ๋ก ์์ฑ 
    - ์์ฑ ํํ๋ ๋ค์๊ณผ ๊ฐ์. ( letter | _ )( letter | digit | _ )* (maxLength="8")
    - SDSVarName, Origin ๋ฐ Comment ์์ฑ์ ์ต์  ๋ฒ์ ์ CDISC SDTM์ ์ค๋ช๋ ๋๋ก ์ ์ถ ์ ๋ณด๋ฅผ ์ ๋ฌํฉ๋๋ค.
    - ์ ์ถ ํ์ค์ ๋ํด ์ธ๋ถ ์ํํธ์จ์ด๊ฐ ํ์ ์ ๋ณด๋ฅผ SDTM ๋ณ์์ ๋ง์ถฐ ํ์์ ๋ณด๋ฅผ ์ผ์น์ํค๊ธฐ ์ํ ๋ณ์. (ํ์์ ๋ณด๋ฅผ ์ผ์น์ํค๋ค.)matching up patients
    - ![image](https://user-images.githubusercontent.com/25499386/177081789-2af4ec7f-918a-4a62-8407-ec5d40b3331d.png)
 
    ### Origin
    - text ํ์์ผ๋ก ์์ฑ
    ### Comment
    - text ํ์์ผ๋ก ์์ฑ

    ์ฐธ๊ณ : ODM ๋ชจ๋ธ์์ ๋ชจ๋  ๋ด๋ถ ํค๋ ๋ณ๊ฒฝํ  ์ ์๋ ๊ฒ์ผ๋ก ๊ฐ์ฃผ๋๋ค. 
    ์ด๋ ๊ฐ์ฌ ์ถ์  ๋ฌธ์ ๊ฐ ์๋ํ๋๋ก ํ๊ธฐ ์ํด ์ํ๋์์ต๋๋ค. 
    audit trail ๊ด๋ จ

    ๋ชจ๋ธ์ SubjectKey๊ฐ ํ์์ ์ค์  ์ธ๋ถ ์ฃผ์  ์๋ณ์(๋๋ ๋ฌด์์ ID)์ด๊ณ  ํด๋น ๊ฐ์ด ํ๋์ ODM ํ์ผ์์ ์๋ชป ์ ์ก๋ ๊ฒฝ์ฐ ์์ ํ  ๋ฐฉ๋ฒ์ด ์์ต๋๋ค. (???) 
    Q. ์๋ชป ์ ์ก๋ ๊ฒฝ์ฐ๋ ์ด๋ค ๊ฒฝ์ฐ๋ฅผ ์์ฌํ๋๊ฐ?

    ์ด๋ฅผ ์ํํ  ๋ ์ธ๋ถ ์ฃผ์  ํค(๋ฐ ๊ธฐํ ์ธ๋ถ์์ ๋ณผ ์ ์๋ ํค ๋ณ์)๊ฐ ๋ฉํ๋ฐ์ดํฐ์ ํญ๋ชฉ์ผ๋ก ์ ์๋์ด์ผ ํฉ๋๋ค.
    ๋ฐ๋ผ์ ์ ์์ ์ธ ์์ /๊ฐ์ฌ ๋ฉ์ปค๋์ฆ์ ํตํด ์์ ํ  ์ ์์ต๋๋ค. ์ด๊ฒ์ ์ฐ๊ตฌ ํค์ ์์ ์ ์ง์ํ๋ ๋ฌธ์ ๋ฅผ ํด๊ฒฐํ์ง๋ง ์ฌ์ฉ์๋ ์ด๋ค ItemDefs๊ฐ ํน๋ณํ ์๋ฏธ๋ฅผ ๊ฐ์ง๊ณ  ์๋์ง ๋๋ ๊ทธ ์๋ฏธ๊ฐ ๋ฌด์์ธ์ง ์๋ณํ  ์ ์๋ ๋ฐฉ๋ฒ์ด ์์ต๋๋ค. 
    ์ด๊ฒ์ด ๋ฌธ์ ๊ฐ ๋๋ ๊ฐ์ฅ ๋ช๋ฐฑํ ์์น๋ ์ธ๋ถ ์์ค์์ ๋ฐ์ดํฐ๋ฅผ ๋ก๋ํ  ๋ ํ์๋ฅผ ์ผ์น์ํค๋ ๊ฒ์๋๋ค. ํ์ ID๋ฅผ ์ฐพ์ ์ ์์ผ๋ฉด ์ด๋ป๊ฒ ์ผ์นํฉ๋๊น?

    ์ ๋ต์ ItemDef์ SDSVarName ์์ฑ์ ์ฌ์ฉํ๋ ๊ฒ์๋๋ค. SDSVarName์ ๋น์ฆ๋์ค ์๋ฏธ๋ก ํญ๋ชฉ์ ํ๊ทธ๋ฅผ ์ง์ ํ๋ ๋ฐ ์ฌ์ฉํ  ์ ์๋ ์ ํ์  ์์ฑ์๋๋ค. 
    ODM ๋ชจ๋ธ์์ ๊ฐ๋ฅํ ๋ชจ๋  ์๋ฏธ๋ฅผ ์ด๊ฑฐํ๋ ค๊ณ  ํ๊ธฐ๋ณด๋ค ODM ์์ ๊ทธ๋ฃน์ CDISC SDTM์ ์ ์๋ ๋ณ์ ์ด๋ฆ ์งํฉ์ ์์กดํ๋ ๊ฒ์ด ๊ฐ์ฅ ์ข๋ค๊ณ  ์๊ฐํ์ต๋๋ค.

    ์ด ๋ชฉ๋ก์ ์์ ๋ฐ์ดํฐ ๊ด๋ฆฌ์ ์ฌ์ฉ๋๋ ํต์ฌ ๋ณ์๋ฅผ ํฌํจํ๊ธฐ ๋๋ฌธ์๋๋ค. ๋ฐ๋ผ์ ODM ํธํ XML ์ธ์คํด์ค๋ฅผ ์ฒ๋ฆฌํ๋ ์ํํธ์จ์ด๋ SDSVarName ์์ฑ์ ํน์  ๊ฐ์ ์ฌ์ฉํ์ฌ ์์ฃผ ์ฌ์ฉ๋๋ ํ์ค ๋ณ์๋ฅผ ์๋ณํ  ์ ์์ต๋๋ค. 
    ์ด ์์ฑ์ ์ฌ์ฉ์ SDTM ๋ชจ๋ธ์ ์ ์๋ ๋ณ์๋ก ์ ํ๋ฉ๋๋ค. ๋ณ์์ ํ๊ทธ๋ฅผ ์ง์ ํ  ๋ ํด๋น ๋ณ์์ ๋ํ SDTM ์ ์์ ์ผ์นํ๋ ๊ฒ์ผ๋ก ์๋ณํฉ๋๋ค. ์ผ๋ฐ์ ์ผ๋ก ์ฌ์ฉ๋๋ ๊ฐ์ ์ผ๋ถ ๋ชฉ๋ก์ ๋ค์๊ณผ ๊ฐ์ต๋๋ค.
    *SDS ๋ ์ ์ถ ํ์ค?
    * SDSVarName ๊ด๋ จ ๋งํฌ http://xml4pharmaserver.com/XML4PharmaWiki/doku.php?id=annotating_odm_with_sdtm_and_cdash_information
    * 

    - STUDYID (Study Identifier Unique within a Submission)
    - USUBJID (Study Identifier Unique within a Submission),
    - SUBJID (Subject Identifier Unique within a Study),
    - SITEID (Unique Identifier for a study Site)
    - SEX (Sex or Gender, coded value),
    - VISITNUM (Clinical encounter Number)
    - VISIT (Protocol-defined description of clinical encounter),
    - VISITDY (Planned study day of VISIT)

    ์ด๋ฐ ๋ณ์๋ค์ ์ด๋ค๋๋ผ~
    
    See the SDTM Specification and Implementation Guide for more information about SDTM variables.

