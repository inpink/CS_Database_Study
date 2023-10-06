# Thread 구조

## Foreground Thread(Client Thread)
 - Foreground Thread의 수는 최소 MySQL Server에 접속한 Client 수만큼 존재하며, 각 Client 사용자가 요청한 Query를 처리
 - 사용자가 작업을 마치고 Session이 종료되면 해당 Thread는 Thread Cache로 반환됩니다. 이때 Thread Cache에 일정 개수 이상의 대기 중인 Thread가 있다면 해당 Thread를 종료시켜 일정 개수의 Thread만 Thread Cache에 유지
 - Thread Cache에 유지할 수 있는 최대 Thread 개수는 thread_cache_size라는 System Variable로 설정
 - 일반적인 Foreground Thread는 사용자 요청(Query)을 받아 필요한 Data를 가져오는 역할을 수행하는데, 사용 중인 스토리지 엔진에 따라 역할 및 수행 범위가 달라질 수 있음
   예를 들어, MyISAM 테이블의 경우 디스크 I/O관련 작업은 모두 Foreground Thread가 담당하지만, InnoDB 테이블은 메모리에 대한 Read/Write 작업만을 Foreground Thread가 담당
   (이외의 작업은 Background Thread가 담당)

## Background Thread
 - 다양한 MySQL의 스토리지 엔진 중 InnoDB의 경우 많은 작업을 Background Thread가 수행
 - Data 읽기 작업의 경우, 주로 Foreground Thread가 처리하기 때문에 Read Thread를 많이 설정할 필요는 없지만, 쓰기 작업의 경우 대부분의 작업을 Background Thread가 담당하므로 충분한 수의 Write Thread를 설정하는 것이 좋음
 - 과거 버전에서는 Master Thread가 여러 가지 역할을 수행했기 때문에 동시성이 떨어졌지만, 지금은 각각의 작업들이 역할별로 분리되어 각기 다른 Thread들이 담당. 
   예를 들어, Buffer Pool에 있는 Dirty Page를 Flush 하는 일은 Page Cleaner Thread가 수행하며 있으며, Delete Query에 의해서 삭제 처리된 Row를 물리적으로 삭제하는 일은 Purge Thread가 수행.

- InnoDB 엔진의 주요 Background Thread
1. Master Thread	- Background Thread의 관리 및 다양한 작업들의 스케줄링을 담당,
                   Data 일관성을 보장하기 위해 Buffer Pool의 Data를 디스크로 비동기식으로 Flush
2. Insert Buffer -	Insert Buffer(Change Buffer)를 Merge
3. Log Thread	-	트랜잭션 로그(Redo Log)를 작성
4. Read Thread	-	다양한 유형의 Read 요청 처리
5. Write Thread	-	다양한 유형의 Write 요청 처리
6. Page Cleaner - Pool의 Dirty Page를 디스크로 Flush
7. Purge Thread	-	Rollback에 더이상 필요하지 않은 Row를 제거하는 작업을 담당
