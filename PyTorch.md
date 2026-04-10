---
title: PyTorch 개요 및 주요 특징
tags:
  - AI
  - DeepLearning
  - PyTorch
  - Framework
---

## 1. 개요 (Introduction)
**PyTorch**는 Meta(구 Facebook)의 AI 연구 팀(FAIR)에서 개발한 오픈 소스 머신러닝 프레임워크입니다. Python 기반의 직관적인 인터페이스와 강력한 GPU 가속 기능을 제공하며, 현재 학계와 산업계에서 가장 선호되는 딥러닝 도구입니다.

> [!quote] **핵심 철학**
> "가독성이 높고, 유연하며, 파이썬답게(Pythonic) 코딩한다."

---

## 2. 주요 특징 (Key Features)

### 2.1 Dynamic Computational Graph (동적 계산 그래프)
PyTorch의 가장 큰 차별점은 **Define-by-Run** 방식입니다.
- **설명:** 코드를 실행하는 시점에 그래프가 생성됩니다.
- **장점:** 실행 중에 네트워크 구조를 유연하게 변경할 수 있으며, 일반적인 Python 디버거(pdb)를 사용하여 한 줄씩 실행하며 오류를 찾을 수 있습니다.



### 2.2 Tensor (텐서) 연산
- NumPy의 `ndarray`와 매우 유사한 구조를 가집니다.
- **GPU 가속:** `device='cuda'` 설정을 통해 NVIDIA GPU를 활용한 대규모 병렬 연산이 가능합니다.

### 2.3 Autograd (자동 미분)
- `torch.autograd` 패키지를 통해 모든 텐서 연산에 대한 자동 미분을 지원합니다.
- 복잡한 수식의 기울기(Gradient) 계산을 `loss.backward()` 한 줄로 처리할 수 있어 모델 학습이 간편합니다.

---

## 3. 주요 사용처 (Applications)

PyTorch는 현대 AI의 거의 모든 최첨단 분야에서 표준으로 자리 잡았습니다.

| 분야 | 주요 사례 |
| :--- | :--- |
| **자연어 처리 (NLP)** | GPT, BERT, Llama 등 거대 언어 모델(LLM) 개발 및 학습 |
| **컴퓨터 비전 (CV)** | 이미지 분류, 객체 탐지(YOLO), 자율주행 알고리즘 |
| **생성형 AI** | Stable Diffusion, GAN(생성적 적대 신경망) 등 이미지/영상 생성 |
| **강화 학습 (RL)** | 게임 AI(AlphaStar 등), 로봇 제어 시스템 |
| **의료/과학** | 단백질 구조 분석(AlphaFold), 신약 후보 물질 탐색 |

---

## 4. PyTorch 생태계 (Ecosystem)

| 라이브러리 | 용도 |
| :--- | :--- |
| **torchvision** | 이미지 처리, 데이터셋 로드, 사전 학습된 CV 모델 제공 |
| **torchaudio** | 음성 및 오디오 데이터 처리 유틸리티 |
| **torchtext** | 텍스트 데이터 전처리 및 자연어 처리 도구 |
| **PyTorch Lightning** | 모델 구조와 학습 로직을 분리하여 코드 가독성을 높여주는 프레임워크 |

---

## 5. 기초 코드 예시 (Basic Snippet)

```python
import torch
import torch.nn as nn

# 1. 간단한 신경망 모델 정의
class SimpleModel(nn.Module):
    def __init__(self):
        super(SimpleModel, self).__init__()
        self.linear = nn.Linear(1, 1)

    def forward(self, x):
        return self.linear(x)

# 2. 모델, 손실함수, 최적화 도구 설정
model = SimpleModel()
criterion = nn.MSELoss()
optimizer = torch.optim.SGD(model.parameters(), lr=0.01)

# 3. 데이터 및 학습 (1단계)
x_train = torch.tensor([[1.0], [2.0]], dtype=torch.float32)
y_train = torch.tensor([[2.0], [4.0]], dtype=torch.float32)

prediction = model(x_train)
loss = criterion(prediction, y_train)

optimizer.zero_grad()
loss.backward()
optimizer.step()

print(f"Loss after 1 step: {loss.item()}")