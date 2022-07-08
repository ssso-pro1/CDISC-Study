  
## codelist
- 항목에 대해 허용되는 개별 값 집합을 정의합니다. </br>
- 정의는 명시적 값 목록(CodeListItem | EnumeratedItem+)이거나 외부에서 정의된 코드 목록(ExternalCodeList)에 대한 참조일 수 있습니다.

- DataType은 내부 또는 외부 여부에 관계없이 CodeList에 나타날 수 있는 값을 제한합니다.
- 해당 태그에 대한 속성은 다음과 같다.
    ### OID
    ### Name
    ### DataType
    - integer or float or text or string 형태의 입력을 지원한다.
    ### SASFormatName



## 예시
```
<CodeList OID="CL.1" Name="CL.1" DataType="text">
                <CodeListItem CodedValue="1">
                    <Decode>
                        <TranslatedText xml:lang="en">Male</TranslatedText>
                    </Decode>
                </CodeListItem>
                <CodeListItem CodedValue="2">
                    <Decode>
                        <TranslatedText xml:lang="en">Female</TranslatedText>
                    </Decode>
                </CodeListItem>
            </CodeList>

```

선택하는 것에 대해 Itemdef 에 Codelistref를 참조

```
    <ItemDef OID="I.5" Name="I.5" DataType="text">
                <Question>
                    <TranslatedText xml:lang="en">Sex</TranslatedText>
                </Question>
                <CodeListRef CodeListOID="CL.1"/>
                <Alias Context="SDTM" Name="DM.SEX"/>
            </ItemDef>

```

이 경우 openedc 상에 성별 선택에 대한 코드정의 한 다음, itemdef 에서 choice 에 대해 codelist를 참조한 것.

## CodeListItem
- 해당 태그는 CodeList의 하위 태그로써 
- 표시 형식을 포함하여 코드 목록의 개별 구성원 값을 정의합니다. 실제 값이 인쇄/표시 형식 세트와 함께 제공됩니다. 


- 단일 CodeList 내의 CodeListItems에는 중복 CodedValues가 없어야 합니다(CodeList의 DataType에 의해 해석됨).





- 단일 CodeList 내의 CodeListItems에는 중복된 Rank 또는 OrderNumbers가 없어야 합니다.
- 해당 태그의 속성은 다음과 같다.
    ### CodedValue
    - text로 작성됨
    - CodedValue는 포함하는 CodeList의 DataType에 대해 허용 가능한 값이어야 합니다. 
    ### Rank
    - Rank 속성은 열거에 해당하는 상대 값이 어휘 순서에 의해 결정될 수 없거나 결정되어서는 안 되는 경우에 사용될 수 있습니다. 
    - 예를 들어 "낮음", "중간" 및 "높음"을 포함하는 열거된 텍스트 값 목록이 있고 이러한 상대 숫자 값 1, 2 및 3을 각각 할당하려는 경우 각 CodeListItem에 대한 Rank 속성을 포함해야 합니다. 한정된. 적용된 순위 속성이 없으면 일반적인 어휘 순서는 "높음", "낮음" 및 "중간"입니다.
    ### OrderNumber
    - integer 형태로 작성합니다.
    - OrderNumbers는 CodeList 항목 목록이 사용자에게 표시될 때마다 사용할 CodeListItems(포함하는 CodeList 내)에 대한 순서를 제공합니다.
    -  이벤트 일정, 시간 순서 또는 데이터 정확성에 대해서는 아무 것도 암시하지 않습니다.

### 예시
```xml
    <CodeList OID="CL.12" Name="CL.12" DataType="text">
                <CodeListItem CodedValue="1">
                    <Decode>
                        <TranslatedText xml:lang="en"> Mild</TranslatedText>
                    </Decode>
                </CodeListItem>
                <CodeListItem CodedValue="2">
                    <Decode>
                        <TranslatedText xml:lang="en">Moderate</TranslatedText>
                    </Decode>
                </CodeListItem>
                <CodeListItem CodedValue="3">
                    <Decode>
                        <TranslatedText xml:lang="en"> Severe</TranslatedText>
                    </Decode>
                </CodeListItem>
            </CodeList>

```

# decode
- codelistitem의 하위 태그입니다.
- 단순하게 code value를 표시하는 값입니다.
- 하위 태그로는 translatedText가 있습니다.

# externalCodeList
- codelistitem의 하위태그입니다.
- 외부에서 정의된 코드 목록입니다.
- 해당 태그의 속성은 다음과 같습니다.
    - Dictionary	text	(optional)	The name of the external codelist.
    - Version	text	(optional)	The version designator of the external codelist.
    - ref	text	(optional)	Reference to a local instance of the dictionary.
    - href	text	(optional)	URL of an external instance of the dictionary.

# EnumeratedItem
- 유효한 값 목록의 개별 구성원 값을 정의합니다. 코딩된 값만 제공됩니다. 인쇄/표시 양식이 필요한 경우 CodeListItem을 사용해야 합니다. CodeListItems 및 EnumeratedItems는 단일 코드 목록 내에서 혼합될 수 없습니다. 
- CodedValue는 포함하는 CodeList의 DataType에 대해 허용 가능한 값이어야 합니다.

- 단일 CodeList 요소 내의 EnumeratedItems에는 중복 CodedValues(CodeList의 DataType에 의해 해석됨)가 없어야 합니다.

- Rank 속성은 열거에 해당하는 상대 값이 어휘 순서에 의해 결정될 수 없거나 결정되어서는 안 되는 경우에 사용될 수 있습니다. 예를 들어 "낮음", "중간" 및 "높음"을 포함한 열거된 텍스트 값 목록이 있고 이러한 상대 숫자 값 1, 2 및 3을 각각 할당하려는 경우 각 EnumeratedItem에 대한 순위 속성을 포함해야 합니다. 한정된. 적용된 순위 속성이 없으면 일반적인 어휘 순서는 "높음", "낮음" 및 "중간"입니다.

- OrderNumbers는 열거 항목 목록이 사용자에게 표시될 때마다 사용할 EnumeratedItems(포함하는 CodeList 내)에 대한 순서를 제공합니다. 이벤트 일정, 시간 순서 또는 데이터 정확성에 대해서는 아무 것도 암시하지 않습니다.

- 단일 CodeList 내의 EnumeratedItems에는 중복된 Rank 또는 OrderNumbers가 없어야 합니다.
