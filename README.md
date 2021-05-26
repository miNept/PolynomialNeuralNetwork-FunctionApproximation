# PolynomialNeuralNetwork-FunctionApproximation
Function Approximation model develop using PNN

# OverView
본 프로젝트는 Polynomial Neural Network를 통한 보편적인 수학 공식의 근사를 연구한 것으로써, 실제 Neural Net이 Function Approximation의 기능을 어느정도로 수행할 수 있을지 알아보기 위한 것이다. 

```PNN.ipynb```는 피타고라스의 정리를 근사한 것이고, ```PNN(2x^2+1).ipynb```는 ```2x^2+1```함수를 근사한 것이다. 두 파일 모두 Linear Layer만 사용했으며, 별도의 추가 Network나 Optimizing방법은 사용하지 않았다.

## PNN(2x^2+1).ipynb
본 프로젝트의 시작점이었으며, Neural Network자체의 Gradient Descent결과를 알아보기 위해 구성한 네트워크다. 데이터는 x와 x^2을 concat하였고, 타겟값은 실제 ```2x^2+1```값을 통과시켜 얻었다. 굳이 데이터에 x^2를 이용한 것은, 현재의 Neural Network는 어떠한 경우에서도 sqr, 즉 제곱을 근사할 수 없다는 판단하에서였다. 실제로 x만 사용했을시, 고정된 범위내에서만 작동할 수 있도록 함수가 근사되었고, 사실상 Function Approximation보다는 Overfitting에 가까운 결과를 얻었다. 

연구결과, 역시나 x에 곱해지는 가중치는 0에 수렴하게되었고, bias는 1에 수렴하게 되었다. 이는 Linear Layer 1층만을 사용해 나온 결과이며, Layer를 몇층으로 늘리든 결과는 같을 것으로 예상된다.

## PNN.ipynb
데이터는 x1, x2의 제곱들을 concat시켰고, 라벨링은 실제 피타고라스의 정리를 이용한 값을 사용했다. 이때 피타고라스의 정리는 sqrt가 사용되는데, 이를 직접 활성화 함수로 적용시킬 수 있었지만, 이는 Function Approximation의 기능에 맞지 않을 것으로 생각되어 ReLU를 사용했다. Linear Layer 1개의 층만으로는 제대로 함수가 근사되지 않을 것 같아 2개의 Layer를 사용했으며, Optimizer는 MSE를 사용했다. 직접 실험 결과, 실제 값과 비슷한 값이 도출되었다. 즉 본 프로젝트를 통해 Linear함수와 ReLU를 이용하여, sqrt같은 함수를 근사 가능하다 판단되며, 아직 수학적으로는 증명하지 못한 상태다. 

이후 푸리에근사를 생각해 활성함수를 ```sin```을 사용해보기도 했지만, 눈에 띄는 변화는 찾지 못했다. 개인적인 의견으로는 ```ReLU```역시 비선형성을 가지게 되면서 푸리에 근사와 비슷한 효과를 내는 것이 아닐까 생각한다. 
