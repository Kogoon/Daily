## Prometheus (프로메테우스)

오픈소스 모니터링 툴 Prometheus.   

Prometheus는 SoundCloud 사에서 만든 오픈소스 시스템 모니터링 및 경고 툴 킷이다.  

지금은 독립형 오픈소스 프로젝트이며, 많은 회사들이 사용하고 있고, 또한 kubernetes에서도 Prometheus를 사용하여 매트릭 수집 및 대시보드 구축하는 방식을 장려하고 있다.  

간단한 텍스트 형식으로 메트릭을 쉽게 노출 가능하며, 데이터 모델은 key-value 형태로 레이블을 집계한 후, Grafana 같은 대시보드 시스템에서 그래프로 쉽고 간단하게 Dashboard를 만들 수 있다. 
 
  
### Prometheus의 주요 기능
 - 메트릭 이름 및 키/값 쌍으로 식별되는 시계열 데이터가 있는 다차원 데이터 모델이다.  
 - 이러한 차원을 활용하는 유연한 쿼리 언어인 PromQL을 사용한다.   
 - 분산 스토리지에 의존하지 않는다. 단일 서버 노드는 자율적이다.  
 - Time Series 수집은 HTTP를 통한 풀 모델을 통해 발생한다. 
 - Push Time Series은 중간 게이트웨이를 통해 지원된다.  
 - 서비스 검색 또는 정적 구성을 통해 대상을 검색한다.  
 - 다양한 그래프 및 대시 보드 모드 지원한다.  
 

 
 * * *
 ### 참고
 [Prometheus 공식사이트](https://prometheus.io/docs/introduction/overview/)
 [Prometheus 를 이용한 모니터링](https://medium.com/@tkdgy0801/prometheus-%EB%A5%BC-%EC%9D%B4%EC%9A%A9%ED%95%9C-%EB%AA%A8%EB%8B%88%ED%84%B0%EB%A7%81-part-1-69de3e87d427)
 [Prometheus란?](https://medium.com/finda-tech/prometheus%EB%9E%80-cf52c9a8785f)
