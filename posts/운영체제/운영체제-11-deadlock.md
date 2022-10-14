# [운영체제] Deadlock

## The Deadlock Problem

- Deadlock
    - 일련의 프로세스들이 서로가 가진 자원들 기다리며 block된 상태
- Resource
    - 하드웨어, 소프트웨어 등을 포함하는 개념
    - 예) I/O, CPU cycle, memory space, semaphore 등
    - 프로세스가 자원을 사용하는 절차
        - Request, Allocate, Use, Release
    - Deadlock Example
        - 시스템에 2개의 tape drive가 있다.
        - 프로세스 P1과 P2 각각 하나의 tape drive를 보유한 채 다른 하나를 기다리고 있다

## Deadlock 발생 조건 4가지

- Mutual exclusion
    - 매 순간 하나의 프로세스만이 자원을 사용할 수 있음
- No Preemption
    - 프로세스는 자원을 스스로 내어놓을 뿐 강제로 빼앗기지 않음
- Hold and wait
    - 자원을 가진 프로세스가 다른 자원을 기다릴 때, 보유 자원을 놓지 않고 계속 가지고 있음
- Cicular wait
    - 자원을 기다리는 프로세스간에 사이클이 형성되어야 함
        - P0는 P1이 가진 자원을 기다림
        - P1는 P2가 가진 자원을 기다림
        - P2는 p0가 가진 자원을 기다림

## Resource-Allocation Graph

- Vertex
    - Process P = {P1, P2, ..., Pn}
    - Resource R = {R1, R2, ..., Rn}

- Edge
    - request edge Pi -> Ri
    - assignment edge Ri -> Pi

- 그래프에 cycle이 없으면 deadlock이 아니다
- 그래프에 cycle이 있으면
    - 만약 자원 당 인스턴스가 하나 밖에 없으면 deadlock이 있다
    - 만약 자원 당 인스턴스가 여러 개 있으면 deadlock일 수도, 아닐 수도 있다.

- deadlock이 아닌 경우

![](../../assets/img/posts/운영체제/11-01.png)

- deadlock인 경우

![](../../assets/img/posts/운영체제/11-02.png)

- 그래프에 cycle이 있지만 deadlock이 아닌 경우

![](../../assets/img/posts/운영체제/11-03.png)

- R1 중 하나는 P2, R2 중 하나는 P4에 할당되어 있지만 반납을 하면 available한 상태로 바뀌고 그 때 P1, P3에게 할당하면 되므로 deadlock이 아니다

