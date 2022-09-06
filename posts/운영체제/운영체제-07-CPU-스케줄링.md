# [운영체제] CPU 스케줄링

## CPU Scheduler & Dispatcher

- CPU Scheduler
    - Ready 상태의 프로세스 중에서 이번에 CPU를 쓸 프로세스를 고른다
- Dispatcher
    - CPU 제어권을 CPU Scheduler에 의해 선택된 프로세스에게 넘긴다
    - 이 과정을 Context Switch (문맥 교환)이라고 한다

- CPU 스케줄링이 필요한 경우는 프로세스에게 다음과 같은 상태 변화가 있는 경우다.
    1. Running -> Blocked (예: I/O 요청하는 시스템 콜)
    2. Running -> Ready (예: 할당시간 만료로 timer interrupt)
    3. Blocked -> Ready (예: I/O 완료 후 interrupt)
    4. Terminate

