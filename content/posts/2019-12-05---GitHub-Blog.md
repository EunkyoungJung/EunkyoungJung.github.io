---
title: GitHub 블로그 만들기
date: "2019-12-05T15:40:32.169Z"
template: "post"
draft: false
slug: "/posts/GitHub-Blog"
category: "terminal"
description: "global다."
tags:
  - "terminal"
  - "linux"
---

# Gatsby로 블로그 만들기

## 마크업 vs. 마크다운
* 마크업:
* 마크다운: 일반 플레인 텍스트를 쓰면 html처럼 보여지도록 하는 것

## Gatsby 블로그 생성 STEP

### 0. 사전 준비
0-1) NPM 설치
구글에서 NPM을 검색해서 OS에 맞는 버전을 다운받아 설치하면 되어요!
NPM (Node Package Manager)

0-2) git 설치
git이 설치되었다면, 아래와 같이 버전정보가 확인가능해요!
![image.png](https://images.velog.io/post-images/muchogusto/03ee46f0-167a-11ea-8623-937c19918606/image.png)

##### 1. 블로그 관련 파일을 정리할 디렉터리 생성
![image.png](https://images.velog.io/post-images/muchogusto/8d523e60-167a-11ea-8623-937c19918606/image.png)
블로그 관련 파일을 정리할 디렉터리를 생성합니다.
이 디렉터리는 앞으로 블로그 템플릿을 복사해오고,
블로그에 포스팅할 내용도 저장할꺼에요. 그리고 깃허브 레포지토리에 연결해서 배포(deploy)할 꺼에요.

##### 2. 블로그 템플릿을 복제해 오자! (git clone)
2-1) git clone 실행
~~~
git clone "복제해 올 코드들이 있는 깃허브의 주소"
~~~
블로그 관련 파일을 정리할 디렉터리에 들어가서 아래의 명령어를 실행하여 블로그 템블릿을 복제해보겠습니다.

![image.png](https://images.velog.io/post-images/muchogusto/400fb0a0-167b-11ea-8faa-3d85bfc68934/image.png)

아래와 같이 다운이 완료되었어요.
![image.png](https://images.velog.io/post-images/muchogusto/f29e4ab0-167b-11ea-b898-651c3e685599/image.png)

2-1) 다운받은 폴더의 이름내용 기호에 맞게 변경하기
'mv'라는 리눅스 명령어를 이용해서 다운받은폴더("yeri-kim.githumb.io")를 새로운 이름("jek_blog")으로 변경을 하였어요!
![image.png](https://images.velog.io/post-images/muchogusto/d938ed00-1676-11ea-929a-9b65c9994145/image.png)

![image.png](https://images.velog.io/post-images/muchogusto/eb886d00-1676-11ea-8faa-3d85bfc68934/image.png)


2-2) 다운받은 폴더의 안 살펴보기
다운받은 폴더의 안을 살펴볼까요?
![image.png](https://images.velog.io/post-images/muchogusto/ded3a6f0-167c-11ea-8623-937c19918606/image.png)
다운받은 폴더 안에는 여러 파일들이 있는데요.
요기서 주목해야할 폴더/파일은 아래의 2개입니다!
.git
package.json
~~~
.git 파일은 깃허브의 레포지토리와 이 파일(.git)이 설치된 폴더를 연결하는 역할을 합니다.
~~~
~~~
package.json 파일은 깃허브 레포지터리에 업로드하는 파일의 양을 줄이기 위해서 해당 프로그램에서 사용되는 여러 라이브러리 중에 자주 쓰이는 유명한 라이브러리를 굳이 해당 프로그램 코드에 포함시키지 않고 라이브러리명과 버전만을 표시하도록 하는 것입니다.
~~~

2-3) 복제된 파일의 기존 '.git' 폴더 삭제하기
'.git'폴더를 삭제해서 내 환경?에 맞게 다시 생성할 것이기에 복제된 파일의 기존 '.git' 폴더는 삭제합니다.
![image.png](https://images.velog.io/post-images/muchogusto/d45b6030-167e-11ea-b898-651c3e685599/image.png)


##### 3. 'package.json' 파일의 'devDependencies'에 명시된 파일 설치 (NPM install)
복제한 파일의 'package.json' 파일을 열어보면,
"devDependencies" 오브젝트가 있어요.
이는 이 프로그램을 실행하기위에 추가적으로 설치가 필요한 유명한 라이브러리/파일의 이름과 버전을 명시하고 있어요.
![image.png](https://images.velog.io/post-images/muchogusto/d3855610-167f-11ea-8623-937c19918606/image.png)

3-1) NPM install 실행
위의 명시된 파일들을 설치하기 위해
아래의 명령어를 실행합니다.
명령어를 실행하는 위치는, 블로그 내용을 정리하기로 한 폴더입니다!
~~~
NPM install
~~~
![image.png](https://images.velog.io/post-images/muchogusto/3625e6e0-1680-11ea-b898-651c3e685599/image.png)

3-2) node_modules라는 폴더의 생성 확인
'NPM install'이라는 명령어 실행 후, 폴더의 리스트를 조회하면,
바로 앞전까지만 해도 없었던!
"node_modules"라는 폴더가 생성되었음을 알 수 있어요!
설치가 필요했던(devDependencies에 명시되었던) 함수/라이브러리가 설치된 것 같죠?
![image.png](https://images.velog.io/post-images/muchogusto/a0ec3100-1680-11ea-8623-937c19918606/image.png)


##### 3. git init 실행
~~~
git init
~~~
'git init'을 실행해서 git이라는 프로그램?이 잘 돌아갈 수 있는 세팅을 합니다.
그 세팅의 결과로 ".git" 폴더가 생성됩니다.
".git"은 로그를 관리하는 등, git의 관리용 폴더라고 보면 될 것 같아요.
![image.png](https://images.velog.io/post-images/muchogusto/0958aca0-1681-11ea-8623-937c19918606/image.png)


##### 4. "git remote add origin '현파일을 연결할 깃허브 주소'"를 실행
4-1) git remote add origin 실행
~~~
git remote add origin https://github.com/EunkyoungJung/EunkyoungJung.github.io.git
~~~
![image.png](https://images.velog.io/post-images/muchogusto/5cd003b0-1681-11ea-8623-937c19918606/image.png)

4-2) 결과 확인
![image.png](https://images.velog.io/post-images/muchogusto/85a70810-1681-11ea-922d-e34369a1c657/image.png)

##### 5. git status 실행
![image.png](https://images.velog.io/post-images/muchogusto/af280810-1681-11ea-b898-651c3e685599/image.png)
git status를 실행함으로써 git이 현재 브런치의 상태를 체크할 수 있도록 합니다.

##### 6. 'git add .' 실행
~~~
git add .
~~~
git add다음의 '.'은 현디렉터리를 기준으로 하위의 모든 디렉터리까지 'git add'를 적용시킵니다.
![image.png](https://images.velog.io/post-images/muchogusto/cd473690-1681-11ea-922d-e34369a1c657/image.png)


##### 7. 커밋메시지 작성
~~~
git commit -m "커밋메시지"
~~~
커밋메시지는 반드시 작성해야합니다. 
작성을 하지 않으면 커밋이 안되어요.
그리고 커밋메시지는 아주 중요한 역활을 합니다.
모두가 보는 메세지이며, 해당 커밋에서 무엇이 변경되었는지를 정확하게 써야합니다.
![image.png](https://images.velog.io/post-images/muchogusto/e6de1dd0-1681-11ea-922d-e34369a1c657/image.png)

##### 8. git log 실행
~~~
git log
~~~
git의 log를 확인하는 명령어입니다.
앞 전에 commit만하고 별다른 게 없어서 로그가 없네요~
![image.png](https://images.velog.io/post-images/muchogusto/779c4130-1682-11ea-8623-937c19918606/image.png)

##### 9. git branch develop
//##### 10. git push origin master //꼭 안해도 됨!
##### 10. git push origin develop
##### 11. git checkout develop
##### 12. NPM run deploy


실행이 안되는 경우, 아래의 명령어를 실행해서 해결했어요!
deploy를 실행이 안될경우! "yarn"프로그램이 있는지를 확인해보세요!
deploy는 다양한 명령어의 조합인데, 그 명령어 중에 "yarn"이 있어요.
혹시 설치가 안될때는 'sudo'를 이용해 강제적으로 실행해봐용

![image.png](https://images.velog.io/post-images/muchogusto/31408420-1683-11ea-922d-e34369a1c657/image.png)






