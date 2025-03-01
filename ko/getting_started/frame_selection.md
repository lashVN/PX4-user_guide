# 기체 선정

PX4는 항공, 지상, 수상 및 수중 차량등에 사용할 수 있습니다. PX4와 호환되는 차량 프레임의 전체 목록은 [기체 정의서](../airframes/airframe_reference.md)를 참고하십시오.

아래를 참고하여 목적에 적합한 기체를 선택하십시오.
- **Multicopters** offer precision hovering and vertical takeoff, at the cost of shorter and generally slower flight. PX4는 드론 비행에 널리 사용되는 편리한 비행 모드들을 제공합니다.
- **Helicopters** similar to Multicopters, mechanically more complex, but more efficient.
- **Fixed-wing** airplanes offer longer and faster flight, and hence better coverage for ground surveys etc. 멀티콥터보다 이착륙이 어렵고 호버링이나 저속 비행(예 : 수직 구조물 조사 등)등 에는 적합하지 않는 단점이 있습니다.
- **VTOL**(수직 이착륙기)은 틸트로터, 테일 시터, 쿼드 플레인 등의 다양한 기체 유형들이 있습니다. 멀티콥터의 수직 이착륙 및 호버링의 장점과 고정익의 전방 고속 비행의 장점을 모두 가지고 있습니다. They are often more expensive than either multicopters and fixed-wing aircraft, and harder to build and tune.
- **비행선과 풍선**은 비행 속도와 방향 제어가 극히 제한되며, 저비용 고고도 장기 비행에 적합한 공기보다 가벼운 기체입니다.
- **로버**는 자동차와 같은 지상용 차량입니다. 제어와 사용이 용이합니다.
- **보트**는 수상 차량입니다.
- **잠수정**은 수중 차량입니다.

::: info The airframe settings used by PX4 are configured in *QGroundControl* during initital setup: [Airframe setup](../config/airframe.md).

![프레임 선택 ](../../assets/qgc/setup/airframe/airframe_px4.jpg) :::
