# ⌨ Vim이랑 친해지기 🥰
- 목표 : Vi/Vim 이해, 사용법 습득
- 2020.05.11 ~ 2020.05.15 

## 리눅스에서 코드를 편집하려면...?
- 컴퓨터의 역사 초기엔 텍스트를 편집하려면 ed라는 굉장히 복잡하고 귀찮은 에디터를 사용해야 했습니다.
- 결국 BSD유닉스를 만들던 빌 조이라는 프로그래머가 ed에 비주얼 모드를 넣어서 vi를 만들게 되었고 텍스트 편집이 매우 편해지게 되었다네요!
- 그러나 이 vi는 ed에서 파생되었기 때문에 AT&T의 라이센스하에 있었습니다. 즉, 수정이 불가능했고 이를 복제한 복제판들이 등장하게 되었습니다.
- 그 중 하나가 vim입니다! 오늘날엔 대부분 환경에서 vi를 입력해도 alias로 vim으로 연결됩니다.

## Vim! 너로 정했다!
- 리눅스에서 사용할만한 기본적인 코드 편집기는 VIM말고도 <b>Emacs</b>와 <b>NANO</b>가 존재합니다.  
- Emacs는 기능과 확장성이 매우 뛰어나지만, 그만큼 복잡하고 익히기가 어렵습니다. 단축키만 대략 1000개...!
- NANO는 처음 CUI를 접할땐 굉장히 편하지만, 코딩용 에디터로는 효율적이지가 않습니다.
<p align = 'center'>
   <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp3/fp3_1.png">
   (찰진 비유...)
</p>

## Vim mode
- vim은 3가지의 모드가 존재합니다
  <p align = 'center'>
     <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp3/fp3_2.png" width = "1000px">
     (window vim에선 붙혀넣기(ctrl+v)와 비주얼 블록(ctrl+v)가 겹치므로 해당 기능은 ctrl+q를 쓰도록 하자! )
  </p>
- Command mode : 기본적인 모드로써 이동 및 다른 모드로 진입할 수 있습니다.
- Edit mode : 텍스트의 편집이 가능해지는 상태입니다.
- Command line : 시스템과 관련된 부분을 담당합니다.
- Visual mode : 커서로 드래그하듯이 코드를 선택해서 복사하는 등의 편집을 할 수 있습니다.

## 기본적인 사용법
- 파일 여는법 & 생성법 : ```$ vim [파일이름.파일]```
- 저장하고 종료 : ```:wq```
- 강제 종료 : ```:q!```

## 단축키
 <p align = 'center'>
     <img src = "https://github.com/KGJsGit/my_Cloud-studio/blob/master/pics/fp3/fp3_3.jpg">
 </p>

## 느낀점
- 다양한 플러그인으로 개조해서 가볍게 쓸 수 있는게 매력인 것 같다. jupyter notebook에도 연결해봐야곘다.
- chrome에 vim의 키매핑을 적용해서 쓸 수 있다니! 편안한 웹서핑이 가능해질 것 같다.
