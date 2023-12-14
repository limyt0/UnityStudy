# Center와 Pivot

|Center|Pivot|
|------|-----|
| ![image](https://github.com/limyt0/UnityStudy/assets/80087763/3a3ecf19-cdff-40fb-98fd-8645fe9f5620)|![image](https://github.com/limyt0/UnityStudy/assets/80087763/a3ccaa95-b1e5-43d0-9947-77bb91f1cf8d)|
| 자식객체까지 합쳐서 중앙 위치 | 부모의 위치를 기준으로 잡음|

그냥 Pivot쓰는 게 나은 듯.


|Local|Global|
|------|-----|
| ![image](https://github.com/limyt0/UnityStudy/assets/80087763/ca53c6bd-2987-48ad-b60c-28fdef6ac00e) | ![image](https://github.com/limyt0/UnityStudy/assets/80087763/4dd1cc55-bb07-4733-ad0e-2b8c98b93990) |

상황마다 다르겠지만 Global이 더 편한 듯.

# UndoHistory

![image](https://github.com/limyt0/UnityStudy/assets/80087763/c00b865e-2624-4ebb-b8cf-856ad1c92bc7)

말그대로 Ctrl z y 할수 있는 거

# Grid snapping

![image](https://github.com/limyt0/UnityStudy/assets/80087763/51e778f9-1743-4b47-9984-9d1b20c445f4)

- Grid Visual 
  - Grid Plane: 어느축 기준 gird인지. y가 바닥 grid임
  - Opacity: 불투명도( 투명<-> 불투명 ) 오른쪽으로 당길수록 불투명
  - Move to
    - To Handle: 선택 객체 기준으로 grid 위치를 옮김.
    - To Origin: grid를 default 위치(0,0,0 기준인 듯)로 옮김.
- Snapping
  - Grid Size: gird 네모 사이즈 조절
  - Snap to Grid: 
  - Rotate: n 간격으로 회전함.
  - Scale: n 간격으로 scale값을 조정함.
  - Align Selected: gird 간격만큼? 축방향에 위치값을 반올림(?) 함. gird크기가 소수점 1.1 이면 y위치가 1.2면 1.1로 만듦.
 
Ctrl 키 누른 상태로 객체 움직이면 Snapping됨.
    
