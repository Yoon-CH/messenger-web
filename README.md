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

### 메세지 삭제 기능 : 윤창현

- Redux 상태 추가: `REMOVE_CONTENT` 액션 추가로 삭제 이모지 클릭 시 해당 **입력텍스트, 날짜, 유저id, 텍스트id가 filter로 인해 삭제 되도록** Redux state에 구현
- DB 삭제 : `removeContentData` 유틸함수를 만들고 삭제 이모지 클릭 시 해당 **입력텍스트, 날짜, 유저id, 텍스트id** 가 firebase DB에서 삭제 되도록 구현
- 삭제 이모지 클릭 시 alert창 활용
  - 삭제할 메시지 표현(최대10글자)후 그 이상의 글은 “...” 으로 표기
  - 확인 / 취소 버튼을 나누어 선택 역할 구분

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

### 윤창현 ✨

Redux와 firebase를 처음 접하면서 조금은 느린 속도로 진행했으나, 동기분들과의 소통과 협업으로 잘 마무리 할 수 있었던 프로젝트였습니다. 이를 통해 상태관리의 흐름을 이해할 수 있게 되었으며, 부족한 부분과 새로 배워야 할 부분을 정리해서 더욱 성장 해야겠다고 느꼈던 좋은 기회였습니다
