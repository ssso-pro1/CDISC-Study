# 3.1 ODM
> 3.1 ODM </br>
    - π 3.1.1Study </br>
        - π 3.1.1.1GlobalVariables </br>
        - π 3.1.1.2       BasicDefinitions </br>
        
        
`λ°λ: Study, AdminData*, ReferenceData*, ClinicalData*, Association*, ds:Signature*` </br>
`μμ±: `

|μΈλΆμ¬ν­|λ¬Έμ|μ€λͺ|
|--------|--------|------------------------|
|FileType|μ€λμ·/ νΈλμ­μ| - μ€λμ· : λ¬Έμμ ν¬ν¨λ νμ¬ λ°μ΄ν°μ μνμ λ©νλ°μ΄ν°μ νμ¬ μνλ§ ν¬ν¨λκ³ , νΈλμ­μ κΈ°λ‘μ ν¬ν¨λμ§ μμ. μ€λμ· λ¬Έμμλ λ°μ΄ν° ν¬μΈνΈ λΉ νλμ λͺλ Ήλ§ ν¬ν¨. μμ λ°μ΄ν°μ κ²½μ° μ€λμ· νμΌμ νΈλμ­μ νμμ μ‘΄μ¬νμ§ μκ±°λ μλ ₯μ΄ μμ΄μΌ ν¨.</br></br> - νΈλμ­μ: λ¬Έμκ° λ°μ΄ν° ν¬μΈνΈ λΉ λ μ΄μμ λͺλ Ήμ ν¬ν¨ν  μ μλ€λ κ²μ λ»νλ€. νΈλμ­μ λ¬Έμλ₯Ό μ¬μ©νμ¬ λ°μ΄ν°μ νμ¬ μνμ λ°μ΄ν°κ° μ΄λ»κ² κ±°κΈ°μ μκ²Όλμ§λ₯Ό λͺ¨λ μ μ‘ν΄λΌ.  |
|Granularity| All/Metadata/AdminData/</br> ReferenceData/AllClinicalData/</br> SingleSite/SingleSubject| λ°μ μΈμκ² νΉμ  μΌλ°μ μΈ μ νμ λ¬Έμμ λν΄ λ¬Έμμ μ λ³΄ λ²μλ₯Ό μ€λͺνλ κ°λ¨ν λ°©λ²μ μ κ³΅νκΈ° μν κ². |
|Archival|(Yes/No)|νμΌμ΄ 21 CFR 11μ μ μλ μ μ κΈ°λ‘μ μκ΅¬ μ¬ν­μ μΆ©μ‘±νλλ‘ μλλμμμ λνλ΄λ €λ©΄ μ΄ μμ±μ μλ‘ μ€μ .  FileTypeμ΄ νΈλμ­μμΈ κ²½μ°μλ§ μ΄ μμ±μ μ¬μ©|
|FileOID|oid|μ΄ νμΌμ κ³ μ  μλ³μ|
|CreationDateTime|datetime|λ¬Έμκ° ν¬ν¨λ νμΌμ λ§λ  μκ°|
|PriorFileOID|oidref|μλ¦¬μ¦μ μ΄μ  νμΌ(μλ κ²½μ°)μ λν μ°Έμ‘°|
|AsOfDateTime|datetime|μ΄ λ¬Έμλ₯Ό λ§λ€κΈ° μν΄ μλ³Έ λ°μ΄ν°λ² μ΄μ€λ₯Ό μΏΌλ¦¬ν λ μ§/μκ°|
|ODMVersion|( 1.2/1.2.1/1.3/1.3.1/1.3.2 )|μ¬μ©λ ODM νμ€ λ²μ |
|Originator|text|ODM νμΌμ μμ±ν μ‘°μ§|
|SourceSystem|text|μ΄ νμΌμ μλ μ λ³΄μ μμ€μΈ μ»΄ν¨ν° μμ€ν λλ λ°μ΄ν°λ² μ΄μ€ κ΄λ¦¬ μμ€ν|
|SourceSystemVersion|text|μμ "SourceSystem" λ²μ |
|ID|ID|ds:Signature μμμμ μ΄ μμλ₯Ό λ€μ μ°Έμ‘°νλ λ° μ¬μ©|

- AsOfDateTime  
    - μ λ°μ΄ν° λλ νμ¬ νμΌμ ν¬ν¨λ λ°μ΄ν° μλ°μ΄νΈμ μ΅μ  λ μ§/μκ°. 
    - μλ΅νλ©΄ AsOfDateTimeμ΄ CreationDateTimeκ³Ό λμΌν κ²μΌλ‘ κ°μ λ¨. 
    - CreationDateTimeλ³΄λ€ λ¦μ AsOfDateTimeμ μ κ³΅νλ κ²μ μ€λ₯.

- ODMVersion μμ±μ ODM 1.1μμ μ μλμ§ μμμΌλ―λ‘ λλ½λ ODMVersionμ "1.1"λ‘ ν΄μλμ΄μΌ ν¨.

- μ΄ λ²μ μ μλ‘μ΄ κΈ°λ₯μ μ¬μ©νλ €λ©΄ ODM 1.3.2 κΈ°λ° λ¬Έμμ ODMVersion="1.3.2"κ° μ€μ λμ΄ μμ΄μΌ ν¨. ODM 1.2.0 κΈ°λ° λ¬Έμμλ ODMVersion="1.2"κ° μμ΄μΌ νκ³ , ODM 1.3.0 κΈ°λ° λ¬Έμμλ ODMVersion="1.3"μ΄ μμ΄μΌ νλ©°, ODM 1.3.1 κΈ°λ° λ¬Έμμλ μ΄μ  λ²μ κ³Όμ νΈνμ±μ μν΄ ODMVersion="1.3.1"μ΄ μμ΄μΌ ν¨.


## π 3.1.1 Study
`λ°λ: (GlobalVariables, BasicDefinitions, MetaDataVersion*)` </br>
`μμ±: oid` </br>
`ν¬ν¨λ κ³³: ODM` </br>
κ°λ³ μ°κ΅¬μ λν μ μ  κ΅¬μ‘° μ λ³΄λ₯Ό μμ§.
</br>

### π 3.1.1.1 GlobalVariables
`λ°λ: 	(StudyName, StudyDescription, ProtocolName)` </br>
`μμ±: NONE` </br>
`ν¬ν¨λ κ³³: Study` </br>
μ°κ΅¬μ λν μΌλ° μμ½ μ λ³΄κ° ν¬ν¨λ¨.

### StudyName
`λ°λ: 	name` </br>
`μμ±: NONE` </br> 
`ν¬ν¨λ κ³³: GlobalVariables` </br>
μ°κ΅¬μ μ§§μ μΈλΆ μ΄λ¦.

### StudyDescription
`λ°λ: 	text` </br>
`μμ±: NONE` </br>
`ν¬ν¨λ κ³³: GlobalVariables` </br>
μ°κ΅¬μ λν μμ  νμ€νΈ μ€λͺ.

### ProtocolName
`λ°λ: 	name` </br>
`μμ±: NONE` </br>
`ν¬ν¨λ κ³³: GlobalVariables` </br>
νλ‘ν μ½μ λν νμμμ λ΄λΆ μ΄λ¦.
</br>

### π 3.1.1.2 BasicDefinitions
`λ°λ: 	MeaurementUnit` </br>
`μμ±: NONE` </br>
`ν¬ν¨λ κ³³: Study` 

### MeasurementUnit
`λ°λ: 	(Symbol, Alias)` </br>
`μμ±: OID-oid, Name-text` </br> 
`ν¬ν¨λ κ³³: BasicDefinitions` </br>
λ°μ΄ν° ν­λͺ© λλ κ°μ λν λ¬Όλ¦¬μ  μΈ‘μ  λ¨μ. MeasurementUnitμ μλ―Έλ Name μμ±μ μν΄ κ²°μ λ¨. </br>
ex) ν¬λ‘κ·Έλ¨, μΌν°λ―Έν°, μ/λ°λ¦¬λ¦¬ν° λ±

μ°Έκ³ : μΈ‘μ  λ¨μμ μ΄λ¦μ νμ€ννλ κ²μ ODMμ λ²μλ₯Ό λ²μ΄λ¨

### Symbol
`λ°λ: 	(TranslatedText)` </br>
`μμ±: NONE` </br>
`ν¬ν¨λ κ³³: MeaurementUnit` </br>
μΈ‘μ  λ¨μμ μ¬λμ΄ μ½μ μ μλ μ΄λ¦.

### TranslatedText
`λ°λ: 	text` </br>
`μμ±: xml:lang-languageTag (μ΅μ)` </br>
`ν¬ν¨λ κ³³: Decode, ErrorMessage, Question, Symbol, Description` </br>
μΌλ°μ μΌλ‘ μλ¦¬μ¦λ‘ λνλλ©° λ€μν μΈμ΄μ λν λμ²΄ νμ€νΈ λ³ν μΈνΈλ₯Ό μ κ³΅.

μ°Έκ³ : xml:lang μμ±μ XML νμ€μ μΌλΆμλλ€.
