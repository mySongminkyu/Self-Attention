# Self-Attention
Stand-Alone Self-Attention in Vision Models

- Stand-Alone Self-Attention in Vision Models

  ![image](https://github.com/mySongminkyu/Self-Attention/assets/132251519/45faf4c4-e2de-443f-84b2-ef29801b65f3)

  CNN은 vision에서 빼놓을 수 없는 존재임은 저명하다.
  
  CNN은 강한 inductive bias와 translation equivariance같은 특성으로 이미 관련 task에서 엄청난 성능향상을 불러일으켰는데, 아쉽게도 큰 receptive fields에 대한 scaling properties가 좋지 않은 long range interactions이 어렵다는 단점이 있었다.
  
  (-> 역설적이게도 주변 pixel과의 relation이 높고 거리가 멀어질수록 그 정도가 떨어진다는 locality 특성을 잘 살린 것이 CNN이면서 long range dependency를 못 살리는 것이 단점임 즉, 먼 거리에 있는 정보에 대한 인식 능력은 제한적이다.)
  
  이런 문제 해결을 위해 나온 것이 attention.
  NLP에서 좋은 성능을 거두었는데, CNN에서도 이를 따라 attention을 함께 적용하려 성능을 끌어올리는 연구를 함.
  
  예로 Squeeze-Excite Network(SENet)과 Spatially-aware attention등이 있음.

  ![image](https://github.com/mySongminkyu/Self-Attention/assets/132251519/b847d32e-637c-42ca-bee7-91efe5698f33)

  이렇게 Attention mechanism은 convolution models의 add-on 즉, additive method로써 사용이 되어왔는데 논문의 저자의 의도는 Attention Mechanism을 주축으로 visual models을 만들면 좋은 성능이 날거라 생각한 것.
  
  즉 Attention layer로 모든 convolutional layer를 대체한 stand-alone attention network를 만들고 이러한 모델이 baseline CNN model의 성능을 뛰어 넘으면서 parameter 및 compute efficient 까지 좋다는 결과가 있다.

  논문에서는 convolution layer를 attention으로 대체하기 위해서 local attention layer를 제안한다.

  ![image](https://github.com/mySongminkyu/Self-Attention/assets/132251519/b3377959-b67b-4545-a079-4a6be6d35953)

  Convolution과 비슷하게 self-attention을 할 windown size k를 정해준다.

  본 논문에서는 이렇게 정한 block을 memory block이라고 부른다. 또한 예시에서는 보기 쉽게 2차원상에 그려 놓았지만 실제로는 3차원 tensor형태를 지닌다.  Transformer의 self- attention구조와 비슷하다. (attention is all you need논문 참고)
