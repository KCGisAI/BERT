# BERT (논문 REVIEW TBU)

BERT는 un-supervised 방식으로 pre-trained 모델을 학습하는 방식으로, 입력은 자연어이기만 하면 되며 특별한 label이 필요가 없기 때문에 위키피디아 등의 text를 그대로 긁어와서 사용가능함

### 1.1 Masked language model (MLM)

BERT는 먼저 MLM loss로 pre-training을 진행

1. **특정 token mask:** 학습 단계에서 랜덤하게 token들을 `[MASK]` 라는 special token으로 바꿈
2. **Mask한 token 예측:** 1)에서 mask한 token들을 예측하는 방향으로 모델을 학습

기본 아이디어는 문장의 일부분을 지웠을 때, 나머지 부분들을 보고 맞추는 식으로 모델을 학습하면 자연어를 더 잘 이해할 수 있음
### 1.2 Next sentence prediction (NSP)

BERT에서 두 번째로 사용하는 loss는 NSP입니다. NSP는 text가 두 문장으로 이루어져있을 때, 두 문장이 실제로 이어진 문장인지 아니면 별개의 문장인지 맞추는 식으로 학습

일반적인 자연어 분류 문제와 같이 `[CLS]` token에 대한 representation을 사용하여 예측을 진행

NSP data는 다음과 같이 준비합니다:

- **연결된 문장들의 경우:** 위키피디아 페이지 등에서 연속된 두 문장을 sampling하여 연결되었다고 labeling
- **별개의 문장들의 경우:** 위키피디아 페이지 등에서 연결되지 않은 두 문장을 sampling하여 별개의 두 문장이라고 labeling


**BERT는 MLM과 NSP loss를 사용하여 일반적인 Transformer의 pre-training을 진행합니다. BERT의 pre-training 방식은 일반적인 자연어 처리 문제들처럼 labeling된 data가 필요없고 text만 주어지면 되기 때문에 효율적

## 2. DistilBERT

DistilBERT는 knowledge distillation이라는 방식을 활용하여 BERT와 비슷한 성능을 내지만 더 빠르고 가볍게 만든 pre-trained Transformer 모델
