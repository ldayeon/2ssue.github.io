---
title:  "jekyll 블로그 커스터마이징하기(1)"
date:   2019-03-30 02:10:24 +0900
categories: Blog
tags: jekyll web
classes: wide
---

감격.. 드디어 원하던 스타일의 일부를 변경하는 데 성공했다!  
카테고리와 태그 메뉴에서 메뉴들이 우측에 떴으면 좋겠다고 생각했는데, 1시간의 사투 끝에 바꿀 수 있었다.  
  
> ### 개발자모드로 학습하기
  
개발자 모드로 뒤적거리다가 html을 변경해줘야 한다는 걸 알게됐다.  
html 초짜라서 태그도 못알아보지만 일단 배껴보기로 결심..  
오랜만에 jekyll server를 가동시켰다.  

사투 끝에 layout 폴더에서 categories.html파일과 tags.html 파일을 변경해봤다.  
개발자 모드로 toc이 위치한 곳을 확인했더니 aside sidebar__right스타일로 감싸져있는 것을 볼 수 있었다.  

> ### 우측으로 옮기기 성공!
  
그래서 여기서도 같은 스타일로 감싸봤는데, archive 타입에선 이렇게 해도 패딩값 때문에 보이질 않았다.  
후.. 또 한숨을 쉬었다가 html 상단의 layout을 single로 바꿔보았다.  
  
그런데 single 타입으로 바꾸니까 딱! 드디어 우측으로 메뉴가 변경된 것이다 ㅠ_ㅠ!!!  
  
모바일에서 가독성은 조금 떨어질 지 모르겠지만 대만족 XD!

> ### 내가 원하는건 grid 스타일이 아니야!
  
그런데 taxonomy display옵션이 grid라서 우측에 떠도 내가 원하던 일자 모양이 아니었다.  
또 개발자 모드를 켜서 확인에 들어갔다. 그저 빛.. 개발자 모드는 짱이다..  
Style-display옵션이 grid인 것을 풀어봤더니 드디어 일자 모양이 되었다.  
  
그런데 문제는 그게 어디서 정의되었는지를 모른다는 것...  
또 입술을 괴롭히면서 폴더를 뒤적거리기 시작했다. 어딘가엔 있을거야!!!  
  
여기저기 뒤적거리다가 _sass 폴더에서 _page.scss 파일을 뒤적거린 결과 taxonomy__index 스타일을 정의한 곳을 발견했다.  
  
display옵션을 지우고.. 드디어 원하던 스타일로 변경 성공 ㅠㅠㅠㅠ 감격의 순간이다.  

![변경된 카테고리 메뉴](/assets/images/category_style.PNG)

___
다음엔 이제 post style에서 제목과 본문을 좀 떨어트려놓는 시도를 해볼 예정이다.  
  
신난다!  