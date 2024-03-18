# Swin Transformer-PyTorch

개인적으로 학습하기 위해 작성한 Swin Transformer이다.
해당 코드의 출처는 https://www.kaggle.com/code/pdochannel/swin-transformer-in-pytorch에 있으며 이를 활용하며 공부했습니다.

# Swin Transformer
![image](https://github.com/ycbkr123/Swin-Transformer-PyTotch/assets/73626645/14ecd778-e2b0-45ad-8eb8-ba2673f3c7ac)

Swin Transformer는 2021년 3월 마이크로소프트(Microsoft Research Asia)에서 발표하였다

![image](https://github.com/ycbkr123/Swin-Transformer-PyTotch/assets/73626645/7266b531-3668-476a-9dbd-691a939c73fc)

**Distinct features**
* Swin transformer은 그보다 더 작은 단위의 patch로부터 시작해서 점점 patch들을 merge해나가는 방식을 취한다(patch->proportion of image->image).
* patch들을 합치며 계층적인 구조로 각 단계마다 representation을 갖기 때문에 다양한 크기의 entity를 다루어야 하는 비전 분야에서 좋은 성능을 낼 수 있는 것이다.
* shifted window partitioning는 이전 레이어의 window와 현재의 window 사이를 이어주며 모델의 성능을 효과적으로 향상시킨다.
* window란 M개의 인접한 patch들로 구성되어 있는 patch set이다. Swin transformer는 위에서 제시한 computational complexity의 한계를 극복하기 위해 window들 내부에서만 patch끼리의 self-attention을 계산하는 것으로 제안한다.
* 단순히 window 기준으로 나누면 각 window의 경계 근처 patch(정확히는 픽셀)들은 인접해 있음에도 self-attention 계산이 수행되지 않는데, 레이어의 분할이 발생한 patch에서 ([M/2,M/2])칸 떨어진 patch에서 레이어 L+1의 window 분할함으로써 window 간의 연결성을 반영한다.
* self-attention 계산이 M개의 patch들로만 제한되기 때문에 연산의 효율성도 획득할 수 있게 된다.
