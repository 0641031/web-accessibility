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