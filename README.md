```text
data/
├─ raw/                     # 크롤링 직후 또는 최소 전처리 상태의 원본 데이터
│   ├─ FINAL_DATA_CLEANED_READY.csv
│   ├─ FEAR_raw.csv / FEAR_source.csv   # (옵션) 공포지수 원본
│   └─ ... (개별 사이트별 원본 CSV들)
│
├─ interim/                 # 중간 전처리/필터링 결과
│   ├─ FINAL_DATA_FILTERED_#TRUE.csv
│   │   # is_related_topic = True 인 코로나/백신 관련 텍스트만 남긴 버전
│   ├─ FINAL_DATA_FILTERED_#FALSE.csv
│   │   # 관련성이 낮아 제거된 텍스트 (분석에는 사용 X, 검증용으로 보관)
│   ├─ FINAL_DATA_ROWS_#DELETED.csv
│   │   # 링크 공유 위주·의견/감정이 거의 없는 중립 문장 추가 삭제본
│   └─ ... (필요한 중간 버전들)
│
├─ processed/               # 분석/모델 학습에 사용되는 최종본
│   ├─ DDDD.csv
│   │   # 최종 분석용 메인 데이터셋
│   │   # (정제 완료 텍스트 + 날짜 + 사이트 정보 + 모델 예측 감성 등)
│   ├─ labeled_output#.csv
│   │   # 전체 데이터의 약 10% 샘플에 대해
│   │   # 사람이 직접 Binary/Three-Class 감성 라벨을 붙인 결과
│   ├─ 10_per#_final.csv
│   │   # 수동 라벨링 정제본 (학습/검증에 실제 사용한 버전)
│   └─ ... (토픽모델링/시계열용으로 가공된 추가 CSV가 있다면 여기에)
│
└─ external/                # 외부 지표/보조 데이터
    ├─ FEAR#.csv
    │   # 공포·탐욕 지수(Fear-Greed Index) 시계열
    │   # 날짜(date) 기준으로 DDDD.csv의 부정 비율과 merge해서 사용
    └─ ... (향후 추가할 다른 외부 지표들)
```
