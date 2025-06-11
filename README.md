# 🗑️ Clean-Boogie 

**서울 마포구 가로 쓰레기통 최적 배치 분석 프로젝트**

---

## 📌 프로젝트 소개

Clean-Boogie는 마포구 내 쓰레기통 설치 위치를 다양한 데이터를 기반으로 분석하여, 보다 효율적인 쓰레기통 재배치를 제안하는 프로젝트입니다.  
유동인구, 상권 매출, 공원, 무단투기 다발 지역 등 다양한 공간 데이터를 융합하여 시각화 및 인사이트를 도출합니다.

- 개발 환경: Python 3.10 (Conda 가상환경)
- 주요 라이브러리: pandas, geopandas, folium, matplotlib 

---

## ⚠️ 프로젝트 실행 전 주의사항 ⚠️
- **행정동별 공간 경계 데이터는 용량 문제로 업로드가 안되어 직접 다운 받아 프로젝트 폴더에 위치시켜야 정상 실행됩니다.**
- **파일명**: 1. BND_ADM_DONG_PG.zip  2. 센서스_공간정보_지역_코드.xlsx
- **출처**: 디지털트윈 국토 ( https://www.vworld.kr/dtmk/dtmk_ntads_s002.do?dsId=30017 )


## 📂 프로젝트 구성
- .inpyub파일, 전처리 완료된 csv파일 +  xlsx파일 
- 해당 파일들의 더욱 자세한 설명은 .ipynb 파일 내부에 작성되어 있습니다.
  
| 파일명 | 설명 |
|--------|------|
| `Clean-Boogie.ipynb` | 데이터 통합, 분석, 시각화 전체 작업이 진행된 Jupyter Notebook |
| `BND_ADM_DONG_PG.zip` | ✅ (별도 다운로드 필요) 행정동 공간 경계 데이터 |
| `센서스_공간정보_지역_코드.xlsx` | ✅ (별도 다운로드 필요) 행정동 코드 매칭용 데이터 |
| `seoul_street_bin_count_by_year_2013_2024.xlsx` | 서울시 자치구별 연도별 쓰레기통 설치 현황 |
| `mapo_street_bins_with_coords.csv` | 마포구 쓰레기통 위치 좌표 데이터 |
| `mapo_sales_trash_score_2020_2024.csv` | 상권 매출 기반 쓰레기 유발 가중치 데이터 |
| `mapo_park_locations.csv` | 마포구 도시공원 위치 및 면적 정보 |
| `mapo_illegal_dumping_hotspots.csv` | 무단투기 다발 지역 위치 좌표 |
| `mapo_population_by_hour_2020_2024.csv` | 시간대별 유동인구 밀도 데이터 |
| `mapo_trash_collection_by_dong_2012_2021.csv` | 행정동별 연간 쓰레기 수거량 |

---

## 📊 전처리된 데이터셋 원본 출처

### 1️⃣ 서울시 가로 쓰레기통 연도별 설치 현황
- `seoul_street_bin_count_by_year_2013_2024.xlsx`  
- 서울시 열린데이터 광장 → [바로가기](https://data.seoul.go.kr/dataList/OA-15069/F/1/datasetView.do)  
- 2013~2024년 자치구별 설치 수량 변화 추이 분석을 위해 활용

### 2️⃣ 마포구 가로 쓰레기통 위치 및 좌표
- `mapo_street_bins_with_coords.csv`  
- 마포구청 오픈데이터 → [바로가기](https://www.mapo.go.kr/site/main/openData/view?dataId=150)  
- 정확한 설치 위치 및 공간 불균형 분석에 활용

### 3️⃣ 서울시 상권 기반 매출 데이터 (2020~2024)
- `mapo_sales_trash_score_2020_2024.csv`  
- 서울 열린데이터 광장 → [바로가기](https://data.seoul.go.kr/dataList/OA-15572/S/1/datasetView.do)  
- 업종별 쓰레기 배출 수요 및 공간 융합 분석을 위해 활용

### 4️⃣ 마포구 도시공원 정보
- `mapo_park_locations.csv`  
- 마포구 공공데이터 → [바로가기](https://www.mapo.go.kr/site/main/openData/view?dataId=79)  
- 도시공원 쓰레기 발생율을 분석하고자 활용

### 5️⃣ 무단투기 다발 장소
- `mapo_illegal_dumping_hotspots.csv`  
- 마포구청 무단투기 집중 순찰지역 데이터 활용  

### 6️⃣ 서울 유동 인구 데이터 (2020~2024)
- `mapo_population_by_hour_2020_2024.csv`  
- 서울 열린데이터 광장 → [바로가기](https://data.seoul.go.kr/dataList/OA-14991/S/1/datasetView.do)  
- 마포구 생활 인구 분석을 위해 활용

### 7️⃣ 마포구 행정동별 연간 쓰레기 배출량
- `mapo_trash_collection_by_dong_2012_2021.csv`  
- 마포구 공공데이터 → [바로가기](https://www.mapo.go.kr/site/main/openData/view?dataId=226)  
- 행정동별 수거량 데이터 (2012~2021년)

---

## 🗺️ 주요 분석 내용 (`Clean-Boogie.ipynb`)

- 서울시 및 마포구 쓰레기통 설치 추세 분석
- 상권 매출 가중치 기반 쓰레기 발생 잠재 수요 파악
- 공원, 유동인구, 무단투기, 상권 데이터 융합
- **Folium 기반 지도 시각화**
- 잠재 과소·과잉 설치 지역 도출 및 개선 방향 제시
---
