### Semantics Basics
* Programmatically expressed semantics 
* Affordances (행동유도성) : 버튼, 슬라이드 등. 
* screen reader가 role, name, state, value를 읽기 때문에 충분한 정보를 제공하도록 한다.
* the DOM has implicit semantic meaning.
* 텍스트가 아닌 컨텐츠는 그를 대체할 텍스트를 반드시 제공해야 한다. (img alt같은)
* input tag 전후로 입력한 태그는 시각적으로는 해당 input에 대한 라벨처럼 보이지만 html에서도 그걸 알 수 있도록 label태그로 감싸거나, for를 사용하여 해당 input에 대한 라벨인지를 표시해줘야 한다. 
* img에서 alt가 없으면 screen reader는 파일 이름을 읽는다.
* image가 load되지 않았을 때도 페이지 전체의 컨텐츠를 이해할 수 있도록 alt text를 제공해야 한다.
* 이미 텍스트 제공이 되어있는 버튼이나, 링크같은 경우에는 `alt=""`로 비워둘 수 있다.

### Navigating Content
* voice over로 웹페이지의 요약을 말해줄 때, 링크, heading, form control, table, landmarks(?)가 얼마나 있는지 말해줌. 
* Heading
    * 각 헤딩으로 바로 갈 수도 있음. heading의 레벨로 페이지의 구조 및 중요도를 파악할 수 있음.
    * DOM의 순서대로 읽기 때문에, 스타일로 DOM의 위치를 바꾸는 것 보다 전체적인 DOM의 구조를 컨텐츠의 흐름으로 가져가는 것이 좋다. 
    * 컨텐츠 블록에서 heading을 유용하게 쓰면, 스크린 리더로 웹페이지를 보다 수월하게 이용할 수 있음.
* link
    * a태그로 링크가 아닌 버튼효과를 주는 것은 지양. 스크린 리더가 링크로 읽기 때문.
    * 이미지를 a태그로 감싸서 링크를 할 때도, 이미지의 alt를 반드시 넣을 것.
    * 링크 태그의 텍스트를 연결된 페이지의 타이틀로 한다. 텍스트로 링크의 정보를 충분히 제공하기 위함. 
    * Learn more...종류의 링크는 자세한 설명을 담고 있지 않기 때문에 좋은 방법은 아니다. 그 블록의 타이틀에 링크를 거는 편이 좋음.
* landmarks : semantic tag를 사용한 블록.
* meaningful heading and link texts, good structure
* 스크린리더 유저들을 위해서 스크린리더의 작동을 컨트롤 하려고 하지 말아라. 오히려 더 혼란을 줄 수 있다.

### ARIA
* Web Accessibility Initiative Accessible Rich Internet Applications
* custom 체크박스 같은 경우, `role="checkbox"` `aria-checked="true"` 추가로 native 체크박스와 같은 스크린 리더 결과를 얻을 수 있다.
* ARIA는 accessibility tree에만 영향을 준다.
* HTML에는 없는 aria accessible widget을 만들 수도 있다.
* aria-label : 버튼을 감싸고 있는 텍스트가 있어도 aria-label이 우선함.
* aria-labelledby : 참조하고 있는 요소를 가르킬 때 사용. input의 label 처럼 클릭이벤트로 해당 input요소에 이벤트가 적용된다거나 하진 않음. hidden 처리된 요소도 참조할 수 있다. 모든 요소에 오버라이드 할 수 있음. 
* 기본 시맨틱요소에 role을 재정의하지 않는다.
* 랜드마크의 경우 브라우저에 따라 시맨틱 엘리먼트에 role을 추가해야 할 수도 있다. 
* aria-owns : submenu가 있을 때 사용. 여러개의 아이디를 설정해줄 수 있다. 
* aria-describedby : 부가적인 설명을 더할때. 예를 들어, 비밀번호의 경우 조건을 설명하는 div를 참조. 
* aria-posinset, aria-setsize : 데이터의 양이 많은 리스트의 경우, 전체 사이즈를 aria-setsize에, 해당 엘리먼트의 데이터를 aria-posinset에 설정하여 화면의 맨 처음으로 해당요소가 나와도 데이터 파악이 수월함.
* `visibility: hidden`, `display: none`, html의 `hidden` 속성 모두 accessibility tree에서도 사라진다. 브라우저 밖으로 위치를 설정하거나, aria-describedby로 참조한 엘리먼트는 hidden 속성을 주어도 참조가능하다. 
* aria-hidden 속성은 시각적으로는 보이나, accessibility tree에는 사라짐. 슬라이드가 여러장인 경우, 아직 보이지 않는 슬라이드에 사용함. 
* aria-live 
    * polite : 사용자가 하던 것을 마치면 알려주는 것. 중요하지만 급하지 않음. 채팅에서 상대방에게 메세지가 도착했을 때.
    * assertive : 서버 에러 등과 같은 즉시 알려줘야 되는 사항.
* aria-live와 함께 사용하는 속성
    * aria-atomic : date input 처럼 day, month, year 각각 입력하고 전체 데이터를 사용할 때.
    * aria-relevant : additions - 엘리먼트가 추가되었을 때. 예) 채팅메시지에서 span이 추가.
