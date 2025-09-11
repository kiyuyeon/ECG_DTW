# ECG R-peak/DTW 비교 스크립트 — READM

## 목적

* 두 ECG 신호(단일 리드 `.npy`와 12리드 결합 `.npy`)를 정제(clean), R-peak 검출, RR 세그먼트 추출 후, 리드 II 기준으로 DTW 거리로 유사도 비교.

---

## 요구사항

```bash
python >=3.9
pip install numpy matplotlib neurokit2 dtaidistance scipy
```

---

## 입력 가정

* `npy_data`: 1D(또는 (1, N)) 단일 리드 ECG, 예시 샘플링레이트 250 Hz.
* `combined_data`: 2D (12, N) 12-lead ECG, `combined_data[1, :]` 가 Lead II, 예시 샘플링레이트 500 Hz.
* 경로는 직접 지정해야 함.

---

## 사용법

1. 경로/샘플링레이트/리드 인덱스 수정
2. 공통 샘플링레이트로 리샘플(예: 250 Hz)
3. 실행하여 R-peak, RR 세그먼트, DTW 거리 및(옵션) 플롯 확인

---

## 출력

* 콘솔: `DTW distance: <float>` (작을수록 유사).
* 선택: 정규화 후 두 파형 비교 플롯.

