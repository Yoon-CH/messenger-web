# 유저 선택형 웹메신저 제작

## 프로젝트 소개

> 유저를 선택 하면 채팅방에 입장할 수 있는 웹 메신저를 제작하였습니다. Redux로 채팅 메세지 상태 (추가, 수정, 삭제) 를 관리하고 실시간으로 firebase로 만든 데이터베이스에 전송하여 업데이트 시켰습니다.

## member

<table>
  <tr>
        </td>
      <td align="center">
      <a href="https://github.com/LEEHYUNHO2001"
        ><img
          src="https://avatars.githubusercontent.com/LEEHYUNHO2001"
          width="100px;"
          alt=""
        /><br /><sub><b>이현호</b></sub></a>
    <br />
    </td>
    <td align="center">
      <a href="https://github.com/hoonjoo-park"
        ><img
          src="https://avatars.githubusercontent.com/hoonjoo-park"
          width="100px;"
          alt=""
        /><br /><sub><b>박훈주</b></sub></a
      ><br />
    </td>
    <td align="center">
      <a href="https://github.com/Yoon-CH"
        ><img
          src="https://avatars.githubusercontent.com/Yoon-CH"
          width="100px;"
          alt=""
        /><br /><sub><b>윤창현</b></sub></a
      ><br />
    </td>
    <td align="center">
      <a href="https://github.com/devjoylee"
        ><img
          src="https://avatars.githubusercontent.com/devjoylee"
          width="100px;"
          alt=""
        /><br /><sub><b>이주영</b></sub></a
      ><br />
  </tr>
</table>

| 팀 구성 | 담당                                                |
| ------- | --------------------------------------------------- |
| 이현호  | firebase 생성 및 프로젝트 배포, 채팅 수정 기능 구현 |
| 박훈주  | Redux 추가 및 UI 제작, 채팅 답장 기능 구현          |
| 윤창현  | 메세지 데이터 연동 및 삭제 기능 구현                |
| 이주영  | 새 채팅 추가 기능 구현 및 DB 업데이트               |

<br>

## 배포 주소

### [https://messenger-web-b98e6.web.app/](https://messenger-web-b98e6.web.app/)

<br>

## 사용 기술 및 스택

- Stack
  - React + Redux
  - Typescript
  - styled-component
  - Deploy : Firebase
  - Other : Git / GitHub
  - Build Tool (Create React App)
  - Code Quality Tool (Prettier)

<br>

## 과제 구현 목록

### 메세지 수정 기능 : 이현호

- Firebase에서 사용자의 데이터 정보를 가져오는 `getUserData` 와 채팅 메세지의 데이터 정보를 가져오는 `getContentData` 함수를 utils에 생성
- 메세지의 수정 버튼을 클릭 시 해당 메세지의 값이 들어있는`textarea` 가 나타나고, 수정을 한 뒤에 `Enter` 입력 또는 ✅ 버튼을 클릭하면 수정
- db에서 수정될 수 있도록 `editContentData` 함수 생성
- db에 반영된 정보를 UI에 실시간으로 보여주기 위한 상태관리 (`action`, `reducers` , `dispatch` )
- Firebase 배포

### 메세지 답장 기능 : 박훈주

- 답장 버튼을 클릭했을 때 `replyObj`라는 `state`를 업데이트해주는 액션과 리듀서를 생성하여 답장 기능 상태관리를 구현
- `form` 컴포넌트에서 `replyObj` `state`를 받아와 `textarea`의 `value`에 입력해주는 작업을 수행
- 이후, `textarea`의 높이가 동적으로 세팅되지 않는 문제가 발생하였음. 따라서 답장내용 텍스트 내에서 `\\n` 의 개수를 찾기 위해 정규표현식과 `String.match()`를 활용하여 직접 `textarea`의 `height`값이 계산되어 부여될 수 있도록 구현

### 메세지 삭제 기능 : 윤창현

- Redux 상태 추가: `REMOVE_CONTENT` 액션 추가로 삭제 이모지 클릭 시 해당 **입력텍스트, 날짜, 유저id, 텍스트id가 filter로 인해 삭제 되도록** Redux state에 구현
- DB 삭제 : `removeContentData` 유틸함수를 만들고 삭제 이모지 클릭 시 해당 **입력텍스트, 날짜, 유저id, 텍스트id** 가 firebase DB에서 삭제 되도록 구현
- 삭제 이모지 클릭 시 alert창 활용
  - 삭제할 메시지 표현(최대10글자)후 그 이상의 글은 “...” 으로 표기
  - 확인 / 취소 버튼을 나누어 선택 역할 구분

### 메세지 전송/추가 기능 : 이주영

- Redux 상태 추가 : `UPDATE_CONTENT` 액션을 추가하여 input 창에 새 메세지 입력 후 전송(버튼 클릭 or Enter키 입력)하면 **입력텍스트, 날짜, 유저id, 텍스트id** 가 Redux state에 추가되도록 구현
- firebase DB 업데이트 : `updateContentData` 유틸함수를 만들고 새 메세지 입력 후 전송(버튼 클릭 or Enter키 입력)하면 **입력텍스트, 날짜, 유저id, 텍스트id** 가 firebase DB로 전송되도록 구현
- 현재 접속한 유저가 보낸 메시지는 이름 옆에 \* 문자가 출력
- 멀티라인 기능 추가 : `textAreaRef` 를 만들어 height가 scrollHeight 값으로 바뀌도록 설정.
- 메세지 추가 시 **전송 날짜 순** 정렬 : `content.sort((a:Content, b:Content)=>a.date-b.date)`
- 렌더링 및 메세지 추가 시 `scrollIntoView` 를 사용해서 가장 아래로 **scroll down** 되도록 구현.

<br>

## CRA 구조

```markdown
├─components
│ ├─auth
│ └─chat
├─constants
├─pages
├─redux
│ ├─actions
│ └─reducers
├─server
├─styles
├─types
└─utils
```

<br>

## 커밋 컨벤션

깃모지를 사용하여 직관성을 높이고, 기능이나 UI 설계에 따른 메세지를 커밋 메세지에 담는것을 컨벤션으로 결정했습니다. 깃모지로 인해 상대방이 어떤 작업을 수행했는지 한 눈에 확인할 수 있고, 메세지를 보며 조금 더 상세한 상황을 파악할 수 있습니다.
| 깃모지 | 사용 예시 |
| --- | --- |
| 🎉 | init |
| 🚚 | 디렉토리 또는 파일 이동 |
| ✨ | 기능 구현 |
| 💄 | CSS 스타일링 |
| ♻️ | 리팩토링 |
| 📝 | Readme 수정 |
| ➕ | 모듈 추가 |
| 🐛 | 버그 해결 |
| 🚑️ | 치명적인 오류 해결 |

<br>

## 과제 후기

### **이현호** 😎

Firebase를 이용한 CRUD를 구현하고 배포를 진행했습니다. 상태를 Redux로 관리하며 db에 변동된 내용에 따른 UI를 바로 적용할 수 있도록 구현했습니다. 기능을 구현할 때, Redux의 액션을 생성하여 리듀서에 넣은 후 작업할 공간에 알맞는 액션을 넣어 디스패치하는 사이클을 팀원들과 소통하며 확실하게 이해하고 넘어갈 수 있었습니다.

### 윤창현 ✨

Redux와 firebase를 처음 접하면서 조금은 느린 속도로 진행했으나, 동기분들과의 소통과 협업으로 잘 마무리 할 수 있었던 프로젝트였습니다. 이를 통해 상태관리의 흐름을 이해할 수 있게 되었으며, 부족한 부분과 새로 배워야 할 부분을 정리해서 더욱 성장 해야겠다고 느꼈던 좋은 기회였습니다

### **박훈주** 🎅

Redux를 통해 CRA+Typescript를 활용한 프로젝트에서 상태관리를 할 수 있는 방법에 대해 배울 수 있었습니다. 또한, view → dispatch → action → reducer의 리덕스 상태관리 기본 로직에 대해 확실히 이해하게 됐습니다. 그리고 실시간 채팅창 업데이트가 구현되도록 DOM에서의 state변화와 DB 데이터 CRUD를 각각 구현하는 과정이 굉장히 흥미로웠습니다.

### **이주영 👧🏻**

이번 프로젝트를 통해 Redux를 사용한 상태관리, firebase 데이터베이스 활용법을 알게되었습니다. 처음 접한 Redux는 조금 어려웠지만 팀원들과 소통하며 많은 것을 배울 수 있었고 상태를 한 곳에서 관리하는 Redux 특성 상 변화가 많은 큰 프로젝트에서는 Redux를 사용하면 편리하겠다고 생각했습니다.
