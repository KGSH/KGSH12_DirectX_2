# DX 시험문제
### 객관식(17문제)
##### 1, 2. D3D초기화하기위한 헤더파일과 함수, 라이브러리파일
* 헤더 파일 : d3d9.h
* 라이브러리 파일 : d3d9.lib
* 초기화 함수 : Direct3DCreate9( [매개변수 : D3D_SDK_VERSION] );
##### 3. CreateDevice()함수의 매개변수
* Adapter : 사용할 디스플레이 어댑터 수, D3DADAPTER_DEFAULT는 기본 디스플레이 어댑터를 지정함
* DeviceType : D3DDEVTYPE 열거형 멤버의 유효 값이다.
  > D3DDEVTYPE_REF : 소프트웨어에서 Direct3D의 기능을 구현한다. 테스트 목적으로만 유용하다.
  >이 형식은 DirectX SDK가 설치된 시스템 에서만 동작하므로, 절대 릴리스 코드에 사용하면 안 된다.

  >XP의 경우에는 Windows/System32 폴더에 설치되어 있다.

  >비스타와 7의 경우, 일반적으로 DirectX SDK에 의해 설치되지 않는다.
d3dref9.dll을 프로젝트 폴더에 복사하면 잘 동작할 것이다.

  >일반적으로 설치경로에 따라 'Program File(X86)\Microsoft DirectX SDK(Month year)\Developer Runtime\X86'또는 비슷한 폴더 이름에서 파일을 발견할 수 있다.

  >D3DDVETYPE_HAL : 하드웨어 레스터 변환을 지정한다. D3DDEVTYPE_HAL을 지정한 상태에서 CreateDevice가 실패한다면, 어댑터가 하드웨어 그래픽 가속을 지원하지 않는다는 것을 의미한다.

* hFocusWindow : 포커스 윈도우는 Direct3D에게 애플리케이션이 포그라운드모드에서 백그라운드 모드로 전환했다고 알려준다. 창 화면만 사용하는 애플리케이션의 경우 이 매개변수는 NULL이다. 일반적으로 윈도우에 대한 핸들로 이 매개변수에 채워 넣는다.
* BehaviorFlags : 사용 가능한 플래그 값은 다양하지만, 실제로 적용할 수 있는 플래그는 2개 뿐이다.
  >D3DCREATE_HARDWARE_VERTEXPROCESSING : 정점 처리를 그래픽 하드웨어가 수행하도록 지정 (하드웨어가 지원할 때만)

  >D3DCREATE_SOFTWARE_VERTEXPROCESSING : 정점처리를 시스템 CPU에서 소프트웨어를 실행해 수행하도록 지정

##### 4. D3D RGB값
* 대상을 칠할 색상 값

* DirectX에 미리 정의된 매크로를 통해 RGB색상을 좀 더 쉽게 만들 수 있게 해준다.

* D3DCOLOR_XRGB(0, 255, 0)은 적색, 녹색, 청색에 대해 지정된 값을 사용해 단색의 RGB색상을 만든다.

* 각 색상의 범위는 0~255이다.

##### 5. 페이지 전환 함수
* 기본적으로 아래 매개변수들은 NULL로 설정한다(각 매개변수의 설명은 84p에 있음).
<pre><code>HRESULT Present (
const RECT \*pSourceRect,
const RECT \*pDestRect,
HWND hDestWindowOverride,
const RGNDATA \*pDirtyRegion
)
result = device3d->Present(NULL, NULL, NULL, NULL);
</code></pre>

##### 6. D3D 객체의 원형
솔직히 뭐인지 모르겠음, 대충 예상으로는
LPDIRECT3DDEVICE9,
LPDIRECT3D9,
D3DPRESENT_PARAMETERS

##### 7. Clear()함수의 매개변수 (이 역할을 하는 매개변수는 무엇인가??)
<pre><code>
HRESULT Clear(
// pRects 가 가리키고 있는 배열에 나열돼 있는 지울 사각형의 개수다.
DWORD Count,           
// 지울 사각형을 기술하는 D3DRECT 구조체 배열을 가리키는 포인터 버퍼 전체를 비우고싶다면 pRect를 NULL, Count 를 0으로설정
coonst D3DRect *pRects,
// 비율 표면의 형식을 지정하기 위해 D3DCLEAR에 정의된 하나 이상의 플래그 D3DCLEAR_TARGET = 버퍼를 비우길 원한다는 뜻
DWoRD Flags,
// 대상을 칠할 RGB값
D3DCOLOR Color,
// 깊이 버퍼 채우기 위해 0에서 1사의 부동 소수점 숫자로 Z값 지정
float Z,
// 스텐실버퍼 를 체우기 위해 0에서 2의n-1승 사이의 숫자값을 지정 하지만 책에선 안씀(개갞기)
DWORD Stencil
);
</code></pre>
##### 8. 예외처리 문장
( 150p )
##### 9. D3D FMT 색상 포맷 (예제에서 사용했던 포맷)
* D3DFMT_X8R8G8B8 : 32 비트의 RGB 픽셀 포맷으로, 각 색에 8 비트가 확보되고 있다.
* D3DFMT_UNKNOWN : 표면 포맷은 불명하다.
##### 10. 접근 제어자
* private
* protected
* public
##### 11. 테스트 코퍼레이티브 레벨 메소드 (반환값)
* HRESULT : 윈도우 표준 반환 코드
* FAILED : 실패했을 경우
* SUCCEEDED : 성공했을 경우
##### 12. 실제 경과 시간 (시간 계산)
( 142p, 175p )
* frameTime = (timeEnd - timeStart) / timerFreq
* frameTime 변수는 이전 프레임으로부터 경과된 실제 시간을 포함한다.
* MAX_FRAME_TIME 으로 frameTime 값을 제한한다.
##### 13. 제시된 함수의 형태 (이 함수는 어떤 함수인가?)
##### 14. 코드 문제: 윈도우 크기 조절
( 110p )
<pre><code>if(!FULLSCREEN)             // if window
{
    // Adjust window size so client area is GAME_WIDTH x GAME_HEIGHT
    RECT clientRect;
    GetClientRect(hwnd, &clientRect);   // get size of client area of window
    MoveWindow(hwnd,
                0,                                           // Left
                0,                                           // Top
                GAME_WIDTH+(GAME_WIDTH-clientRect.right),    // Right
                GAME_HEIGHT+(GAME_HEIGHT-clientRect.bottom), // Bottom
                TRUE);                                       // Repaint the window
}
</code></pre>

##### 15. 메세지 핸들러의 소스 코드 일부분 괄호넣기
( 133p )
<pre><code>//=============================================================================
// Window message handler
//=============================================================================
LRESULT Game::messageHandler( HWND hwnd, UINT msg, WPARAM wParam, LPARAM lParam )
{
    if(initialized)     // do not process messages if not initialized
    {
        switch( msg )
        {
            case WM_DESTROY:
                PostQuitMessage(0);        //tell Windows to kill this program
                return 0;
            case WM_KEYDOWN: case WM_SYSKEYDOWN:    // key down
                input->keyDown(wParam);
                return 0;
            case WM_KEYUP: case WM_SYSKEYUP:        // key up
                input->keyUp(wParam);
                return 0;
            case WM_CHAR:                           // character entered
                input->keyIn(wParam);
                return 0;
            case WM_MOUSEMOVE:                      // mouse moved
                input->mouseIn(lParam);
                return 0;
            case WM_INPUT:                          // raw mouse data in
                input->mouseRawIn(lParam);
                return 0;
            case WM_LBUTTONDOWN:                    // left mouse button down
                input->setMouseLButton(true);
                input->mouseIn(lParam);             // mouse position
                return 0;
            case WM_LBUTTONUP:                      // left mouse button up
                input->setMouseLButton(false);
                input->mouseIn(lParam);             // mouse position
                return 0;
            case WM_MBUTTONDOWN:                    // middle mouse button down
                input->setMouseMButton(true);
                input->mouseIn(lParam);             // mouse position
                return 0;
            case WM_MBUTTONUP:                      // middle mouse button up
                input->setMouseMButton(false);
                input->mouseIn(lParam);             // mouse position
                return 0;
            case WM_RBUTTONDOWN:                    // right mouse button down
                input->setMouseRButton(true);
                input->mouseIn(lParam);             // mouse position
                return 0;
            case WM_RBUTTONUP:                      // right mouse button up
                input->setMouseRButton(false);
                input->mouseIn(lParam);             // mouse position
                return 0;
            case WM_XBUTTONDOWN: case WM_XBUTTONUP: // mouse X button down/up
                input->setMouseXButton(wParam);
                input->mouseIn(lParam);             // mouse position
                return 0;
            case WM_MOUSEWHEEL:                     // mouse wheel move
                input->mouseWheelIn(wParam);
                return 0;
            case WM_DEVICECHANGE:                   // check for controller insert
                input->checkControllers();
                return 0;
        }
    }
    return DefWindowProc( hwnd, msg, wParam, lParam );    // let Windows handle it
}</code></pre>

##### 16. ***보너스문제***
##### 17. 메모리 누수 탐지 헤더 파일
* crtdbg.h
### 주관식(8문제)
##### ?. D3D초기화하기위한 헤더파일과 함수, 라이브러리파일
* 헤더 파일 : d3d9.h
* 라이브러리 파일 : d3d9.lib
* 초기화 함수 : Direct3DCreate9( [매개변수 : D3D_SDK_VERSION] );
##### 1. 픽셀로 변환하는 과정 중 하나
* 래스터화 (Rasterization)
##### 2. 3D공간의 점
* 버텍스 (Vertex)
##### 3. ***보너스문제***
##### 4. GetDeviceCaps 함수로 설정(할 수 있는것)
* 지정된 Device Context의 여러 정보를 구하는 함수
* 첫번째 인수에서 정보를 구하고자할 Device Context 를 지정하며 두번째 인수에서 어떠한 종류의 정보를 가져올지에 대한 flag 지정
##### 5. (4장의 핵심 코드) 렌더링할 때 그래픽스 헤더 파일에 추가한 2개의 함수
( 140p )
* HRESULT beginScene();
* HRESULT endScene();
##### 6. CPU를 쉬게하는 함수 (코드문제)
* Sleep();
>CPU를 쉬게하기 위해서 써줘야 하는 것 이걸쓰면 정확히 1초에 가깝게 쉬게할 수 있다
(원래는 안됨)

##### 7. CPU를 쉬게하기 위해 꼭 써줘야 하는 헤더파일
* <windows.h>
