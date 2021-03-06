# 코로나 19 확진자 수에 따른 교통량 변화 분석

#### <div align = "right" > 데.멘.토(데이터 멘토링) 활동 [2021_09_23 ~ ]</div>

## Contents
### 1. [The purpose of the project](#The-purpose-of-the-project)
### 2. [Data Description](#Data-Description)  
#### 　[Data Sources](#Data-Sources)  
#### 　[Raw Data](#Raw-Data)  
#### 　[Data Columns](#Data-Columns)  
#### 　[Dataframe Shape](#Dataframe-Shape)
### 3. [Code Description](#Code-Description)
### 4. [Fail Log](#Fail-Log)  
----
### The purpose of the project
> 코로나19 발병 이후 2020~2021년, 2년간 총 4차례의 대 유행이 일어났다. 현재 코로나19 4차 대 유행 이후 거리 두기 단계를 4단계로 올렸음에도 불구하고 확진자 수가 줄어들 기미가 보이지 않고, 주변 지인 중에는 휴가를 떠난다는 사람들 또한 늘어나고 있다. 이러한 이유로 우리 '삼현텍'은 고속도로와 톨게이트 통행량 데이터와 코로나19 확진자 수에 따른 이동량 변화의 상관관계를 `matplotlib` , `seaborn` , `pandas` 를 활용해 분석하려 한다. 
>
>  코로나19 유행 전인 2018년, 2019년, 코로나 유행의 시작 연도인 2020년, 그리고 올해 2021년까지의 대유행 시기 중 이동량 변화와 확진자 수의 이동량 변화를 분석해 전국적인 차량 이동량과 코로나19 확진자 수의 상관관계를 알아보고, 이를 시각화하는 활동을 통해 코로나19의 위험성을 알리고 경각심을 불러올 수 있는 계기가 되었으면 좋겠다.

## DATA Description
### Data Sources
> 코로나 19 확진자 데이터 출처 : [공공데이터포털](https://www.data.go.kr/index.do)  
> 교통량 데이터 출처 : [한국 도로공사_고속도로 공공데이터 포털](http://data.ex.co.kr/)

### Raw Data
#### Data Columns
* 코로나 19 확진자 데이터 
##### 　　Covid_case.csv
 > |항목설명|항목명(영문)|샘플데이터|
 > |-----|-----|-----|
 > |결과코드|	resultCode|00|
 > |결과메시지|	resultMsg|OK|
 > |한 페이지 결과 수|	numOfRows|10|
 > |페이지 번호|	pageNo|1|
 > |전체 결과 수|	totalCount|3|
 > |게시글번호(감염현황 고유값)|SEQ|74|
 > |기준일|STATE_DT|20200315|
 > |기준시간|STATE_TIME|00 : 99|
 > |확진자 수|DECIDE_CNT|8162|
 > |격리해제 수|CLEAR_CNT|834|
 > |검사진행 수|EXAM_CNT|16272|
 > |사망자 수|DEATH_CNT|75|
 > |치료중 환자 수|CARE_CNT|7253|
 > |결과 음성 수|RESUTL_NEG_CNT|243778|
 > |누적 검사 수|ACC_EXAM_CNT|268212|
 > |누적 검사 완료 수|ACC_EXAM_COMP_CNT|251940|
 > |누적 확진률|ACC_DEF_RATE|3.2396602365|
 > |등록일시분초|CREATE_DT|2020-03-15 10:01:22.000|
 > |수정일시분초|UPDATE_DT|null|  
* 교통량 데이터 
##### 　　2018_01분기.csv ,2018_02분기.csv ,2018_03분기.csv ,2018_04분기.csv ,2019_01분기.csv ,2019_02분기.csv ,2019_03분기.csv ,2019_04분기.csv ,
##### 　　2020_01분기.csv , 2020_02분기.csv ,2020_03분기.csv ,2020_04분기.csv ,2021_01분기.csv ,2021_02분기.csv
> total : (1789045, 11)
 > |항목명 및 설명|샘플데이터|  
 > |----|----|  
 > |집계일자|20180101|  
 > |영업소코드|246|  
 > |영업소명|가락|  
 > |입출구구분코드|0|
 > |입출구명|입구|
 > |TCS하이패스구분코드|1|
 > |TCS하이패스명|TCS|
 > |고속도로운영기관구분코드|0|
 > |고속도로운영기관명|한국도로공사|
 > |영업형태구분코드|0|
 > |영업형태명|폐쇄식|
 > |1종교통량|211|
 > |2종교통량|6|
 > |3종교통량|6|
 > |4종교통량|21|
 > |5종교통량|27|
 > |6종교통량|4|
 > |총교통량	|275|

#### Dataframe Shape
##### covid_data_analysis
- covid_data (998, 17)
- covid_data_new (998, 5)
- covid_data_1st_pandemic (60, 5)
- covid_data_2nd_pandemic (61, 5)
- covid_data_3rd-pandemic (119, 5)
- covid_data_4th_pandemic (117, 5)
##### traffic_data_analysis
- traffic_data (1789045, 11)
- traffic_data_total (1276,10)
- day_traffic_data_1st (7, )
- day_traffic_data_remain (7, 5)
- day_traffic_data_total (7, )
- seoul_traffic_data (1276, 10)
- daegu_traffic_data (1276, 10)

## Code Description
### breif description
* Categorize corona probability_LHJ.ipynb : unit단위로 나눈 코로나 확진자에 따른 교통량 변화 분석 
* Jan,Feb,May_covid_traffic_data_Woo.ipynb : 명절과 연휴기간 코로나 확진자 수와 교통량 데이터에 대한 분석
* covid_data_analysis.ipynb : 코로나 데이터 정리
* covid_traffic_7_8.ipynb : 휴가철 코로나 확진자 수와 교통량 데이터에 대한 분석 
* covid_traffic_analysis.ipynb : 총 코로나 데이터와 확진자 수에 대한 분석
* predict_traffic_cmp_colab.ipynb : 2020년 2021년 교통량 데이터 예측
* traffic_data_analysis.ipynb : 교통량 데이터 정리
* SamhyeonTech_Covid19_Traffic_Project.ipynb : 분석 총 정리.


## Fail Log
* 교통량 데이터 예측 : 해당 데이터는 시계열 데이터로 시간에 흐름을 반영하는 LSTM 으로 모델 구성을 진행했으나 모델 이해도가 높지 않아 그리 좋은 결과를 내지 못함
