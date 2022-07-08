# Define-XML

## Dataset

| Dataset | Description | Calss | Structure |Keys |
| :---: |:---|:---: |:--------- |:----- |
| TA | 실험 환자군 | 실험 설계</br>(TRIAL DESIGN) | 환자군의 계획된 요소당 한 레코드(기록, raw) |STUDYID, ARMCD, TAETORD |
| TE | 실험 요소 | 실험 설계 |계획된 요소당 한 레코드 | STUDYID, ETCD |
| TI | 실험 포함/제외 기준 | 실험 설계 | 포함/제외 기준당 한 레코드 | STUDYID, IETESTCD |
| TS | 실험 요약 정보 | 실험 설계 |실험 요약 변수 값당 레코드 | STUDYID, TSPARMCD, TSSEQ |
| TV | 실험 방문 | 실험 설계 | 환자의 예약된 방문당 한 레코드 | STUDYID, VISITNUM, ARMCD |
| DM | 인적 자료 | 특수 목적</br>(SPECIAL PURPOSE) | 한 Subject당 레코드 | STUDYID, USUBJID |
| SE | 주제 요소 | 특수 목적 | 한 subject의 실제 요소당 한 레코드 | STUDYID, USUBJID, ETCD, SESTDTC |
| SV | 주제 방문 | 특수 목적 | 실제 방문별 subject당 한 레코드 | STUDYID, USUBJID, VISITNUM |
| CM | 병용/사전 의약품 | 관여</br>(INTERVENTIONS) |한 subject의 개입 발생 기록이나 일정 투여 간격당 레코드 | STUDYID, USUBJID, CMTRT, CMSTDTC|
| EC | 수집된 노출(약물 투여 간격,연구치료에 대한 노출을 나타낸다.)| 관여 | 한 subject의 프로토콜에 명시된 연구 치료법, 투여 간격당 한 레코드 | STUDYID, USUBJID, ECTRT, ECMOOD, ECSTDTC |
| EX | 투여 간격  | 관여 | 한 subejct의 프로토콜에 명시된 연구 치료법, 복용 간격당 한 레코드 | STUDYID, USUBJID, EXTRT, EXSTDTC |
| PR | 절차 | 관여 | 한 subject의 발생별 절차당 한 레코드 | STUDYID, USUBJID, PRTRT, PRSTDTC |
| AE | 부작용 | 방문</br>(EVENTS) | 한 suject의 부작용 방문당 한 레코드 | STUDYID, USUBJID, AEDECOD, AESTDTC |
| DS | 레이아웃(배치) | 방문 | 한 subject의 프로토콜의 중요 단계(사건)이나 레이아웃 상태당 한 레코드 | STUDYID, USUBJID, DSDECOD, DSSTDTC |
| DV | 프로토콜 포기(Deviation, 탈출, 일탈) | 방문 | 한 subject의 프로토콜 Deviation 당 한 레코드 |STUDYID, USUBJID, DVTERM |
| MH | 의료 기록 | 방문 | 한 subject의 방문 의료기록당 레코드 | STUDYID, USUBJID, MHDECOD |
| DA | 약물 책임 | 조사결과</br>(FINDINGS) | 한 주제당 약물 책임 조사 결과당 한 레코드 | STUDYID, USUBJID, DATESTCD, DADTC |
| EG | ECG 검사 결과 | 조사결과 | 시간별 반복 ECG실험 관찰마다 한 레코드| STUDYID, USUBJID, EGTESTCD, VISITNUM |
| IE | 충족 안되는 포함/제외 기준 | 조사결과 | 한 subject의 충족 안되는 포함/제외 기준당 한 레코드 | STUDYID, USUBJID, IETESTCD |
| LB | 실험실 시험 결과 | 조사결과 | 한 subject의 방문시간별 실험실 시험당 한 레코드 | STUDYID, USUBJID, LBTESTCD, LBSPEC, VISITNUM |
| MB | 미생물 견본 | 조사결과 | 한 subject의 방문시간별 조사한 미생물 견본당 한 레코드 | STUDYID, USUBJID, MBTESTCD, VISITNUM |
| PC | 약물의 체내에서의 (흡수, 분포, 대사, 배설)농도 | 조사결과 | 표본 특성별이나 참조 시간당 농도, 주제의 분석당 한 레코드 | STUDYID, USUBJID, PCTESTCD, VISITNUM |
| PE | 신체 검사 | 조사결과 | 한 subject의 방문별 신체나 이상(기형)당 한 기록 | STUDYID, USUBJID, PETESTCD, VISITNUM |
| RE | 호흡기(시스템) 결과 | 조사결과| 한 subject의 방문시간별 조사나 결과당 한 기록  | STUDYID, USUBJID, RETESTCD, VISITNUM |
| RP | 생식기 결과 | 조사결과 | 한 subject의 방문시간별 조사나 결과당 한 기록 | STUDYID, USUBJID, RPTESTCD, VISITNUM, RPDTC |
| RS | 질병 대응 및 임상 분류 | 조사결과 | 의사(의료 평가자)의 한 subject의 방문 시간별 대응 평가나 임상 분류 평가당 한 레코드 | STUDYID, USUBJID, RSTESTCD, RSCAT, VISITNUM |
| VS | 활력징후 | 조사결과 | 한 subject의 방문시간별 활력징후 측정당 한 레코드 | STUDYID, USUBJID, VSTESTCD, VISITNUM |
| SUPPAE | 부작용의 보충사항 | 관련성</br>(RELATIONSHIP) | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드 | STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM |
| SUPPCM | 병용/사전 의약품의 보충사항 | 관련성 | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드 | STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM |
| SUPPDA | 약물 책임의 보충 사항 | 관련성 | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드 | STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM |
| SUPPDS | 레이아웃의 보충 사항 | 관련성 | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드| STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM|
| SUPPDV | 프로토콜 Deviation의 보충 사항 | 관련성 | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드| STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM|
| SUPPEG | ECG 시험 결과의 보충 사항 | 관련성 | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드| STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM|
| SUPPLB | 실험실 시험 결과 보충 사항 | 관련성 | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드| STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM|
| SUPPMH | 의료 기록 보충 사항 | 관련성 | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드| STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM|
| SUPPPE | 신체검사 보충 사항 | 관련성 | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드| STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM |
| SUPPPR | 절차의 보충 사항| 관련성 | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드| STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM|
| SUPPRE | 호흡기 결과 보충 사항 | 관련성 | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드| STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM|
| SUPPVS | 활력징후 보충 사항 | 관련성 | 한 주제의 IDVAR, IDVARVAL, QNAM값당 한 레코드| STUDYID, RDOMAIN, USUBJID, IDVAR, IDVARVAL, QNAM|
