#  대용량 시계열 데이터 기반 태양광 일사량 예측 모델

## 1. 프로젝트 개요
본 프로젝트는 약 1,900만 행에 달하는 방대한 환경 센서 데이터를 분석하여 태양광 발전의 핵심 변수인 일사량(nins)을 예측하는 AI 모델링 프로젝트입니다.

전체 데이터의 **90% 이상이 결측치**로 이루어진 데이터 환경에서, 단순한 모델 튜닝을 넘어 데이터 중심의 전처리 전략과 물리적 도메인 지식을 결합하여 결측 정보를 복원하고 예측 정확도를 극대화하는 데 초점을 맞췄습니다.

* **활동 기간:** 2025.10.25 ~ 2025.11.14
* **참가 형태:** 팀 프로젝트 (우택 외 1명)
* **주요 목표:** 대용량 시계열 데이터 파이프라인 구축 및 결측치 복원 최적화


###  데이터 상세 정보 

#### 1. 기본 정보 및 타겟
| 변수명 | 설명 | 단위 |
| :--- | :--- | :---: |
| `time` | 데이터 측정 시간 | - |
| `pv_id` | 발전소 고유 ID | - |
| `type` | 데이터 구분 (train/test) | - |
| `coord1`, `coord2` | 발전소 위치 좌표 (보안상 익명화) | - |
| **`nins`** | **[Target] 태양광 일사량** | **W/m²** |
| `energy` | 발전량 (Train 데이터에만 존재) | kWh |

#### 2. 기상 관측소 A 데이터 (Weather Station A)
| 변수명 | 설명 | 단위 |
| :--- | :--- | :---: |
| `temp_a` | 대기 중의 실제 온도 | °C |
| `humidity` | 습도 (상대습도) | % |
| `wind_spd_a` | 풍속 | km/h |
| `wind_dir_a` | 풍향 | ° |
| `cloud_a` | 구름량 (운량) | % |
| `rain` | 강우량 | mm |
| `snow` | 강설량 | mm |
| `ground_press` | 지면 기압 | hPa |
| `temp_max` / `min` | 해당 시간대의 최고/최저 기온 | °C |

#### 3. 기상 관측소 B 및 파생 데이터 (Weather Station B & Derived)
| 변수명 | 설명 | 단위 |
| :--- | :--- | :---: |
| `temp_b` | 기상관측소 B의 기온 | °C |
| `rel_hum` | 상대습도 | % |
| `wind_spd_b` | 풍속 | km/h |
| `wind_dir_b` | 풍향 | ° |
| `cloud_b` | 구름량 | % |
| `pressure` | 대기압 | hPa |
| `precip_1h` | 1시간 강수량 | mm |
| `appr_temp` | 체감 온도 | °C |
| `real_feel_temp` | 날씨 조건(바람, 습도) 반영 체감 온도 | °C |
| `real_feel_temp_shade` | 그늘 체감 온도 | °C |
| `wind_chill_temp` | 풍속 냉각 온도 | °C |
| `dew_point` | 이슬점 | °C |
| `uv_idx` | 자외선 지수 | - |
| `vis` | 가시거리 | km |
| `ceiling` | 구름층 높이 (천장고) | m |
| `wind_gust_spd` | 돌풍 속도 | km/h |

---

## 2. 사용 기술 (Tech Stack)
* **언어:** Python 3.13.7
* **데이터 처리:** Pandas, Numpy (Feather 포맷 활용)
* **모델링:** LightGBM Regressor
* **군집화:** Scikit-learn (KMeans, StandardScaler)
* **환경:** VS Code, Jupyter Notebook





## 3. 프로젝트 구조 (Directory)

```bash
nins-prediction-project/
│
├── README.md                 # 프로젝트 설명서 (현재 파일)
├── main                      # 최종코드
├── requirements.txt          # 필요 라이브러리 목록
│
├── modules/                  # 최종 코드에 직접적으로 활용된 로직들
│   ├── 01.ipynb  # CSV 대용량 처리 및 Feather 변환
│   ├── 02.ipynb  # 타겟 분리 및 데이터 통합
│   └── 03.ipynb  # 결측치 보간 및 군집화 로직
│
└── archive/                  # [연구 기록] 시행착오 로직들
    ├── 01.ipynb   # 복합 보간법 시도 및 메모리 문제로 인한 chunk병합
    ├── 02.ipynb   # 초기 파생변수 생성 실험
    ├── 03.ipynb   # 맵핑 방식 접근 시도 및 군집
    └── 04.ipynb   # 모델 학습 실험
```
---    
## 4. 핵심 수행 내용 (Key Process)

### 1) 데이터 전처리 최적화


### 2) 통합 파이프라인 구축 (One-Universe)

### 3) 이중 군집화 전략 (Dual Clustering)


### 4) 물리 도메인 지식 적용 (Physics-Informed)

