# 😊 오늘 공부한 내용


---
### 데몬 스레드 (daemon thread)
- 일반 스레드의 작업을 돕는 보조 스레드
- 일반 스레드가 모두 종료되면 자동 종료됨

```java
boolean isDaemon() // 스레드가 데몬 스레드인지 확인
void setDaemon(boolean on) // 스레드를 데몬 스레드 or 사용자 스레드로 변경 (on이 true면 데몬 스레드가 됨)
```
- **setDaemon(boolean on)은 반드시 start()를 호출하기 전에 실행되어야 한다.**

---
### 스레드의 실행제어
- 스레드의 실행을 제어(스케줄링)할 수 있는 메서드가 제공된다


- sleep() - 지정된 시간동안 스레드를 일시정지 시킨다
- join() - 다른 스레드를 기다린다
- interrupt() - 정지상태인 다른 스레드를 깨운다
- stop() - 스레드를 즉시 종료시킨다
- suspend() - 스레드를 일시정지 시킨다
- resume() - suspend()에 의해 일시정지 상태인 스레드를 실행대기상태로 만든다
- yield() - 다른 스레드에게 자신의 실행시간을 양보하고 자신은 실행대기상태가 된다


💡 **sleep()과 yield()는 static 메서드! 자신에게만 적용된다.**

---
### 스레드의 상태


1. 생성, start() 호출
2. 실행대기, 실행 (줄을 서다 자신의 차례가 되면 실행)
3. 자신의 차례가 끝나면 다시 뒤로 가서 줄을 선다
4. 해야하는 작업이 끝나거나 stop() 호출 시 소멸된다

소멸되기 전에 일시정지 상태(쉼터)가 될 수 있고, 다시 줄을 설 수 있다.

---
### 스레드의 실행제어 메서드 - sleep()
- 현재 스레드를 지정된 시간동안 멈추게 한다.


```java
static void sleep(long millis)
static vodi sleep(long millis, int nanos)
```

💡 예외처리를 해야한다! (InterruptedException 발생 시 깨어남)

```java
    try{
        thread.sleep(1,5000)
        }catch(InterruptedException e){}
```

- `sleep()` 호출 시 항상 해야하는 예외처리가 귀찮다?
  - **메서드를 따로 만들자!**
  - ```java
    void delay(long millis){
        try{
            Thread.sleep(millis);    
        }catch (InterruptedException e) {}
    }
    ```
  - **`delay(15)` -> `sleep()`대신에 이런식으로만 써주면 된다!** 

---

### 참고
- [자바의 정석 - 기초편] ch13-18~21 데몬쓰레드, 쓰레드의 상태 https://www.youtube.com/watch?v=W0v3Gwx92hc
- [자바의 정석 - 기초편] ch13-22~25 sleep(), interrupt() https://www.youtube.com/watch?v=cDUcF1QD4Gw&t=939s
  
