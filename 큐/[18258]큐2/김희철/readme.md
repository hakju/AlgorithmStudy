## 풀이

대표적인 자료구조중 하나인 큐(Queue) 의 특징은 선입선출(First-In First-Out) 구조를 가지고 있습니다.  

컴퓨터의 일부에서도 큐 자료구조가 이용된 걸 CPU(중앙처리장치)에서 찾아볼 수 있는데 들어온 작업들에 대해 순서대로 처리합니다. 이를 CPU 스케줄링 기법이라하는데 스케줄링 기법에 따라 세세한 구현은 다르지만 근본적인 큐 자료구조는 같습니다.

Javascript 엔진 구동방식에서도 Task Queue 라는 공간이 있는데 이 또한 큐 자료구조를 이용합니다. 

### 선형 큐

선형 큐(Linear Queue) 는 파이프모양으로 일직선의 모양을 갖추고 있습니다. 뒤를 가리키는 rear 와 앞을 가리키는 front 값을 0으로 초기화 시킨 후 구현합니다.

#### push (=enQueue)

큐에 데이터를 삽입하는 연산자입니다. 데이터를 넣은 후 rear 값을 증가시킵니다.

#### pop (=deQueue)

큐에 데이터를 빼내어 반환하는 연산자입니다. 데이터를 빼낸 후 front 값을 증가시켜줍니다.

#### front

큐의 가장 앞쪽에 존재하는 데이터를 반환합니다. (단, pop 연산자처럼 데이터를 제거하지는 않습니다.)

#### back(=rear)

rear 또는 back 이라고합니다. front 와 반대로 가장 마지막에 들어온 데이터를 반환합니다. (단, pop 연산자처럼 데이터를 제거하지는 않습니다.)

#### empty

rear 와 front 값이 동일하다면 비어있는 상태입니다.

### 원형 큐 연산자

원형 큐(Circular Queue) 는 선형큐에서 양끝이 이어져있는 형태로 front 와 rear 가 연결되어있는 형태입니다. 원형 큐가 나오게 된 이유는 효율적인 메모리 관리를 위해서입니다. 선형 큐에서 데이터 연산을 끝까지 다 마친 후에는 front 와 rear 값이 마지막을 가리키고있어 이후에 재활용 되기 힘든 점이 있습니다.

원형 큐는 이런점을 개선한 방법입니다. 

원형 큐 연산자도 선형 큐 연산자와 동일하지만 원형큐의 특징중 하나인 양끝이 연결되어있다는 부분을 적용해야합니다. 가득차 있다는 full 연산자가 조금 특이합니다. 

#### full

큐가 가득 차있는지 판별하는 연산입니다. `front == (rear + 1)% size` 라면 가득 차있는 상태입니다.