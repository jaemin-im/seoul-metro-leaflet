# Seoul Metro Visualization using Leaflet

![Implementation Image](/capture1.png)

## 구현 목표

서울 지하철역의 위치 데이터와 지도 라이브러리 Leaflet을 이용하여
서울 지하철역 위치를 시각화하는 것을 목표로 삼았습니다.

## 구현 방법

dm-office 프로젝트에 있던 Leaflet 구현 코드를 참고하여 기본 토대를
쌓았고, 서울 지하철역 위치가 담겨있던 엑셀 파일을 JSON으로 변환하여
프로젝트에서 그대로 쓸 수 있도록 하였습니다. 그리고, 각 역을 표시할
커스텀 아이콘을 flaticon에서 직접 편집하여 로컬에서 사용하였고,
popup을 이용하여 마커를 클릭할 시 역명이 나오게 하도록 하였습니다.'
또한, 검색기능을 구현하기 위한 검색 바를 구현하였습니다. 추후
Vuetify의 검색 바 컴포넌트로 변경할 예정입니다.

## 어려웠던 점

Leaflet을 Vue.js에 wrapper 없이 그대로 구현시킨 코드를 찾는 것이
많이 어려웠고, 중간중간에 맵이 표시되지 않거나, 마커 생성 단계에서
오류가 발생하는 등 자잘한 오류가 발생하여 흐름이 끊기기도 하였습니다.

## 추가구현희망

미처 시간이 없어 검색 기능과 클러스터를 구현하지 못하였지만, 프로젝트를
유지하여 이후에 남는 시간을 쪼개 계속 구현해보고 싶은 프로젝트이기도 합니다.

## 아이콘 출처

<div>아이콘 제작자 <a href="https://www.flaticon.com/kr/authors/roundicons" title="Roundicons">Roundicons</a> from <a href="https://www.flaticon.com/kr/" title="Flaticon">www.flaticon.com</a></div>
