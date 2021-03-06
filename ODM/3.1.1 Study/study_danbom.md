# π Study μ€ν°λ
**Body** :<br>
π₯ `GlobalVariables` μ μ­ λ³μ<br>
π₯ `BasicDefinitions?` κΈ°λ³Έ μ μ<br>
π₯ `MetaDataVersion*` λ©νλ°μ΄ν° λ²μ 

**Attributes** :<br>
`OID(Object Identifier)` oid

**Contained in** : ODM

<br>

```
This element collects static structural information about an individual study.
```
κ° μ€ν°λμ λν μ μ  κ΅¬μ‘° μ λ³΄λ₯Ό μμ§νλ€.

<br><hr>

# π₯ GlobalVariables μ μ­ λ³μ
**Body** :<br>
1οΈβ£ `StudyName` μ€ν°λ μ΄λ¦<br>
2οΈβ£ `StudyDescription` μ€ν°λ μ€λͺ<br>
3οΈβ£ `ProtocolName` νλ‘ν μ½ μ΄λ¦

**Attributes** : NONE

**Contained in** : Study

<br>

```
GlobalVariables includes general summary information about the Study.
```
μ€ν°λμ λν μΌλ°μ μΈ μμ½ μ λ³΄κ° ν¬ν¨λλ€.

<br>

## 1οΈβ£ StudyName μ€ν°λ μ΄λ¦
**Body** : `name`

**Attributes** : NONE

**Contained in** : GlobalVariables

<br>

```
This is a short external name for the study.
```
μ€ν°λμ μ§§μ μΈλΆ μ΄λ¦μ μλ―Ένλ€.

<br>

## 2οΈβ£ StudyDescription μ€ν°λ μ€λͺ
**Body** : `text`

**Attributes** : NONE

**Contained in** : GlobalVariables

<br>

```
This is a free-text description of the study.
```
μ€ν°λμ λν μμ  νμ€νΈ μ€λͺμ μλ―Ένλ€.

<br>

## 3οΈβ£ ProtocolName νλ‘ν μ½ μ΄λ¦
**Body** : `name`

**Attributes** : NONE

**Contained in** : GlobalVariables

<br>

```
This is the sponsor's internal name for the protocol.
```
νλ‘ν μ½μ λν μ€ν°μμ λ΄λΆ μ΄λ¦μ μλ―Ένλ€.<br>
μ€μ§μ μΌλ‘λ `Protocol No.`λ‘ μ£Όλ‘ μ¬μ©λλ©° `CNR_001` λ± μ°κ΅¬ κ³ μ  λ²νΈλ₯Ό μλ―Ένλ€. μλ₯Ό λ€μ΄ μ€ν°λ μ΄λ¦μ΄ λλ¬΄ κΈ΄ κ²½μ° μ€ν°λ μ΄λ¦μ μ½μ΄λ‘ μ°κΈ°λ νλ€.

<br><hr>

# π₯ BasicDefinitions κΈ°λ³Έ μ μ
**Body** :<br>
1οΈβ£ `MeasurementUnit*` μΈ‘μ  λ¨μ

**Attributes** : NONE

**Contained in** : Study

<br>

## 1οΈβ£ MeasurementUnit μΈ‘μ  λ¨μ
**Body** :<br>
π°οΈ οΈ`Symbol` κΈ°νΈ<br>
π±οΈ `Alias*` λ³μΉ­<br>

**Attributes** :<br>
π°οΈ `OID` oid<br>
π± `Name` text

**Contained in** : BasicDefinitions

<br>

```
The physical unit of measure for a data item or value. The meaning of a MeasurementUnit is determined
by its Name attribute. Examples include kilograms, centimeters, cells/milliliter, etc.

Note: Standardizing the names of measurement units is beyond the scope of the ODM
```
λ°μ΄ν° ν­λͺ© λλ κ°μ λν λ¬Όλ¦¬μ  μΈ‘μ  λ¨μλ₯Ό μλ―Ένλ€.<br>
**μΈ‘μ  λ¨μ**μ μλ―Έλ Name μμ±μ μν΄ κ²°μ λλ€. μλ₯Ό λ€μ΄ ν¬λ‘κ·Έλ¨(kg), μΌν°λ―Έν°(cm), μ(cell)/λ°λ¦¬λ¦¬ν°(ml) λ±μ΄ μλ€.<br>

μ°Έκ³  : **μΈ‘μ  λ¨μ**μ μ΄λ¦ νμ€νλ ODMμ λ²μλ₯Ό λ²μ΄λλ€.(?)

<br>

### π°οΈ οΈSymbol(κΈ°νΈ)
**Body** : `TranslatedText+` λ²μ­ νμ€νΈ

**Attributes** : NONE

**Contained in** : MeasurementUnit

<br>

```
A human-readable name for a measurement unit.
```
μ¬λμ΄ μ½μ μ μλ μΈ‘μ  λ¨μμ μ΄λ¦μ μλ―Ένλ€.

<br>

### `TranslatedText` λ²μ­ νμ€νΈ
**Body** : `text`

**Attributes** :<br>
**xml:lang** `languageTag` (optional)

**Contained in** :<br>
Decode, ErrorMessage, Question, Symbol, Description

<br>

```
Human-readable text that is appropriate for a particular language. TranslatedText elements typically occur
in a series, presenting a set of alternative textual renditions for different languages.

To find the text appropriate for a target language with tag LT, search for a TranslatedText element whose
xml:lang attribute matches LT exactly (ignoring case). If that fails, remove the ending subtag from LT and
repeat. If that fails, search for a TranslatedText without an xml:lang attribute and use that. If none is found,
there is no suitable text available.
```
νΉμ  μΈμ΄μ μ ν©ν μ¬λμ΄ μ½μ μ μλ νμ€νΈλ₯Ό μλ―Ένλ€. **λ²μ­ νμ€νΈ** μμλ μΌλ°μ μΌλ‘ μ°μμ μΌλ‘ λ°μνλ©°, λ€λ₯Έ μΈμ΄μ λν μΌλ ¨μ λμ²΄ νμ€νΈ λ λλ§μ μ κ³΅νλ€.

βοΈ `LT` νκ·Έκ° μλ λμ μΈμ΄μ μ ν©ν νμ€νΈλ₯Ό μ°ΎμΌλ €λ©΄ `xml:lang` νΉμ±μ΄ `LT`μ μ νν μΌμΉ(λμλ¬Έμ λ¬΄μ)νλ **λ²μ­ νμ€νΈ**λ₯Ό κ²μνλ€. `e.g. "fr-FR"`<br>
βοΈ μ€ν¨ν κ²½μ°, `LT`μμ μ’λ£ νμ νκ·Έλ₯Ό μ κ±°νκ³  λ°λ³΅νλ€. `e.g. "fr"`<br>
π λ μ€ν¨ν κ²½μ°, `xml:lang` μμ±μ΄ μλ **λ²μ­ νμ€νΈ**λ₯Ό κ²μν΄ μ¬μ©νλ€. λ§μ½ μ°Ύμ μ μλ κ²½μ°, μ¬μ© κ°λ₯ν μ μ ν νμ€νΈκ° μλ κ²μ΄λ€.

<br>

E.g.
 
|TranslatedTexts Present|Requested|Process|
|------|---|---|
|\<TranslatedText xml:lang="fr-CA">...<br> \<TranslatedText xml:lang="en-GB">...<br> \<TranslatedText>...|fr-FR|Look for xml:lang="fr-FR".<br>This is not found, so look for xml:lang="fr".<br>This is not found, so look for a TranslatedText with no `xml:lang`.<br>This is the text that should be used.|

<br>

```
To avoid ambiguity, a particular language tag must not occur more than once in a series of TranslatedText
elements. Also, it is not permitted to have more than one TranslatedText element without an xml:lang
attribute within the same parent.

Note: The xml:lang attribute is part of the XML standard.
```
λͺ¨νΈμ±μ λ°©μ§νλ €λ©΄ νΉμ  μΈμ΄ νκ·Έκ° μΌλ ¨μ **λ²μ­ νμ€νΈ**μμ λ λ² μ΄μ λ°μνλ©΄ μλλ€.<br>
λν, κ°μ λΆλͺ¨μμ `xml:lang` μμ±μ΄ μλ **λ²μ­ νμ€νΈ**κ° νλ μ΄μ μμΌλ©΄ μλλ€.

μ°Έκ³ : `xml:lang` μμ±μ XML νμ€μ μΌλΆμ΄λ€.

<br><hr><br>

### π λ©νλ¬Έμ
`*` : λ°λ³΅μ μλ―Ένλ λ©ν λ¬Έμ. `*` λ°λ‘ μμ μλ κ²μ΄ 0λΆν° λ¬΄νλλ‘ λ°λ³΅λ  μ μλ€λ μλ―Έ.<br>
`+` : λ°λ³΅μ μλ―Ένλ λ©ν λ¬Έμ. λ¨, μ΅μ 1λ² μ΄μ λ°λ³΅λ  λ μ¬μ©.<br>
`?` : μμ κ²μ΄ μμ΄λ λκ³  μμ΄λ λλ€λ μλ―Έ.

<br>

### π λ°μ΄ν° νμ
|Format Name|Schema Datatype|Allowed String Pattern|
|------|---|---|
|`text`|xs:string|any sequence of characters|
|`oid`|xs:string|any sequence of characters<br>(minLength="1")|
|`name`|xs:string|any sequence of characters<br>(minLength="1")|
|`languageTag`|xs:language|LL (-CC)* e.g. `fr-FR` |

> μ°Έκ³  : `xs`λ `XSD` μ€ν€λ§ μ μΈμ μ λμ¬

<br><hr>

### π Reference
- https://wikidocs.net/4308#_3
- http://www.tcpschool.com/xml/xml_xsd_simpleType
