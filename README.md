# 전기차 판매 촉진 구매 요인분석 및 지역별 정책 제안

> 전국 시군구 데이터를 기반으로 전기차 구매 요인을 분석하고, 지역별 맞춤 정책 방향을 제안한 데이터 분석 프로젝트

---

## 📌 프로젝트 개요

| 항목 | 내용 |
|------|------|
| 기간 | 2025.03 ~ 2025.07 (5개월) |
| 유형 | 팀 프로젝트 (5명) |
| 역할 | 군집화 분석 담당 · 정책 제안 보고서 작성 |
| 데이터 | 전기차 판매 데이터 약 10만 건 (2015~2025) |

---

## 🛠 기술 스택

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-3F4F75?style=flat&logo=plotly&logoColor=white)

`Python` `Pandas` `NumPy` `Scikit-learn` `XGBoost` `Random Forest` `K-means` `SHAP` `Matplotlib` `Plotly`

---

## 🔍 분석 파이프라인

```
데이터 수집 → 전처리 → 예측 모델링(팀) → 군집화 분석(담당) → SHAP 분석(담당) → 정책 제안(담당)
```

---

## ✅ 내 담당 역할

### 1. K-means 군집화 분석
- 전국 시군구를 **보조금 · 충전 인프라 · 소득 · 인구** 4개 변수로 분류
- PCA로 차원 축소 후 K-means 적용
- **Elbow Method + Silhouette Score(0.514)** 기반으로 k=4 결정

**클러스터 결과**

| 클러스터 | 지역 특성 | 충전소 | 인구 | 소득 | 보조금 |
|----------|-----------|--------|------|------|--------|
| 0 🔴 | 농어촌·비수도권 (89개) | 적음 (평균 23대) | 적음 | 낮음 | 높음 (1,222만원) |
| 1 🔵 | 광역시·경기 주요도시 (14개) | 많음 (평균 293대) | 많음 | 높음 | 중간 (846만원) |
| 2 🟢 | 서울특별시 단독 (1개) | 최다 (1,468대) | 최다 | 최고 | 낮음 (640만원) |
| 3 🟡 | 수도권 외곽·강원·경상 중소도시 (56개) | 중간 (평균 54대) | 중간 | 중간 | 높음 (938만원) |

### 2. SHAP 요인분석
- **충전소 수 · 시장 성숙도 · 보조금 지급 여부** 순으로 구매에 영향
- 보조금 규모보다 **충전 인프라 접근성**이 핵심 요인으로 확인
- 아이오닉5 출시(2021년)가 전기차 판매 급증의 기점

### 3. 지역별 정책 방향 제안 보고서 작성
- 클러스터 0·3 → **충전소 인프라 우선 확충** 제안
- 클러스터 1·2 → **세제혜택·충전비 지원** 등 비용 부담 완화 정책 제안

---

## 💡 주요 인사이트

- 보조금이 높아도 충전 인프라가 부족한 농어촌 지역(클러스터 0)은 EV 보급률이 낮음
- 서울(클러스터 2)은 보조금이 가장 낮지만 충전소·소득 모두 전국 1위 → 보조금 의존도 낮음
- 지역 특성에 따른 **차별화된 정책**이 필요함을 데이터로 확인

---

## 📁 파일 구성

| 파일 | 설명 |
|------|------|
| `charging_station_count.ipynb` | 전국 충전소 데이터 전처리 |
| `ev_range.ipynb` | 전기차 주행거리 데이터 분석 |
| `train_xgb_rf_prophet.ipynb` | 예측 모델 학습 (XGBoost · RF · Prophet) |
| `clustering.ipynb` | K-means 군집화 분석 |
| `visualize_feature.ipynb` | SHAP 기반 피처 중요도 시각화 |
