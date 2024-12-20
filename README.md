# **반려동물 안구 질환 분류 프로젝트**
1. feature_embedding
2. Model_save_point
3. test dataset
4. train dataset
은 해당 링크에서 다운로드 받을 수 있습니다.
https://www.dropbox.com/scl/fi/phnmfxios5z3lqxhuvudm/feature_embedding-Model_save_point-test-train.zip?rlkey=25xz9gsg7l6p6klalb3l0klf1&st=ff9u9o6b&dl=0
---

## **1. 문제 정의**

### **1.1 문제의 맥락**  
반려동물의 **안구 질환**은 조기에 발견하지 않으면 악화될 위험이 큽니다. 하지만 반려동물 주인이 스스로 증상을 판단하기 어려워 병원 방문이 지연되기도 합니다. 이는 **시간적·경제적 부담**을 초래하며 질환 악화 가능성을 높입니다.

### **1.2 문제 진술**  
본 프로젝트의 목표는 **반려동물의 안구 이미지를 분석**하여 **질환의 유무와 종류를 분류**하는 모델을 개발하는 것입니다. 또한, 질병 가능성을 감지하면 **경고**를 제공해 반려동물 주인이 조기에 대응할 수 있도록 지원하고자 합니다.

### **1.3 목표, 과정 및 성공 기준**  

**목표**  
- 반려동물의 안구 이미지로 **질환 유무**를 정확히 분류  
- 주요 질환(결막염, 각막염 등)을 정확하게 구분하는 시스템 구축  
- 질병 가능성을 감지해 **경고를 제공**하는 사용자 친화적 시스템 설계  

**과정**  
1. 반려동물 안구 질환 데이터셋 수집 및 전처리  
2. **5개 모델**의 성능 비교: ViT, ResNet, Random Forest, Stacking, Boosting  
3. 최적 모델 선정 및 **성능 최적화** 기법 적용  
4. 최종 모델 배포 및 **웹 애플리케이션** 구현  

**성공 기준**  
- 모델 테스트 정확도 **70% 이상** 달성  
- 제한된 리소스 내에서 최적화된 모델 훈련  
- 사용자에게 **예측 결과를 시각화**하고 직관적으로 제공  

---

## **2. 프로젝트 진행 과정**

### **2.1 데이터 전처리 및 증강**  
- **이미지 크기 조정**: ResNet 및 ViT 입력 크기(224x224)로 변환  
- **데이터 증강**:  
   - **Random Horizontal Flip**  
   - **Random Rotation**  
   - **Color Jitter** (밝기, 대비, 채도 조절)  

### **2.2 모델 후보군**  
다섯 가지 모델을 실험 및 비교하였습니다:  
1. **Vision Transformer (ViT)**  
2. **ResNet (Residual Network)**  
3. **Random Forest**  
4. **Stacking Ensemble**  
5. **Boosting Algorithm (XGBoost)**  

---

## **3. 모델 성능 비교 및 결과**

### **3.1 최적 모델 선정**  
- 성능 비교 결과 **ResNet**이 가장 높은 정확도를 기록하여 최적의 모델로 선정되었습니다.  

### **3.2 주요 성능 결과**  
| **모델**            | **테스트 정확도** |  
|---------------------|-----------------|  
| Vision Transformer  | 51.8%            |  
| **ResNet** (최종 선정) | **53.4%**        |  
| Random Forest       | 35.2%            |  
| Stacking Ensemble   | 47.0%            |  
| XGBoost             | 40.2%            |  

---

## **4. 결론**  
본 프로젝트는 반려동물의 안구 이미지를 분석하여 **질환의 유무와 종류를 분류**하는 모델을 개발했습니다. 다양한 모델을 실험한 결과 **ResNet**이 가장 우수한 성능을 보였으며, 성능 최적화를 통해 **53.4%의 테스트 정확도**를 달성했습니다.  

최종적으로 웹 애플리케이션을 구현하여 사용자가 이미지를 업로드하면 **질병 예측 결과와 경고**를 제공하는 시스템을 설계했습니다. 이를 통해 반려동물 주인이 질병을 조기에 인지하고 적절히 대응할 수 있도록 지원하고자 했습니다.

---

## **5. 한계점 및 개선 방향**

### **5.1 한계점**  
1. **질환 간 유사성**: 비궤양성 각막질환과 색소침착성 각막염과 같은 특정 질환은 이미지 간 차이가 미세해 모델이 구분하기 어려웠습니다.  
2. **평가지표 한정**: 정확도(Accuracy)만 사용하여 F1 Score와 같은 균형 잡힌 평가가 부족했습니다.  
3. **데이터셋 샘플링 문제**: 질병 중증도(상·중·하)를 고려하지 않은 랜덤 샘플링으로 클래스 간 유사성이 모델 성능 저하에 영향을 주었습니다.  
4. **Epoch 수 부족**: 학습 Epoch 수가 부족해 딥러닝 모델이 충분히 수렴하지 못했습니다.  

### **5.2 개선 방향**  
1. 클래스 불균형 해소 및 **데이터셋 확장**  
2. F1 Score와 같은 지표를 도입해 모델 성능 평가 강화  
3. Epoch 수를 늘려 모델 학습을 충분히 진행  
4. **Self-Supervised Learning**과 같은 최신 기법 도입  

