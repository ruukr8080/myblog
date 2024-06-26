# Spring Security와 JPA를 학습하기 위한 블로그 프로젝트

배포 url : http://1.236.96.47:9000/
(현재 배포 중지됨)


## 1. 팀원 구성
|<img src="https://avatars.githubusercontent.com/u/97038857?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/131014787?v=4" width="150" height="150"/>|
|:-:|:-:|
|hyunsu<br/>[@mypace0600](https://github.com/mypace0600)|ruukr8080<br/>[@ruukr8080](https://github.com/ruukr8080)|

©generated by (https://profile-table-md.vercel.app/)

## 2. 프로젝트 목표
- Spring Security의 동작 탐구
- OAuth2 로그인 구현 및 동작 탐구
- JPA를 통한 ORM 개념 정리
- 엔티티간 연관관계 설정 및 개념 정리
- QueryDSL을 활용한 쿼리문 작성
- redis와 batch 맛보기
- thymeleaf를 활용한 화면 개발
- summernote 를 활용한 웹 에디터 적용
- 홈서버 구축 실습

## 3. 스펙
java 17, spring-boot 3.2.4, JPA, postgreSQL, redis, thymeleaf, javascript

## 4. 데이터베이스 설계
<img width="606" alt="스크린샷 2024-05-15 오후 2 25 21" src="https://github.com/mypace0600/myBlog/assets/97038857/1b8274e9-b330-4694-ac84-0eb89bfa95e7">


## 5. 프로젝트 구조

```
📦 
├─ .gitignore
├─ build.gradle
├─ gradle
│  └─ wrapper
│     ├─ gradle-wrapper.jar
│     └─ gradle-wrapper.properties
├─ gradlew
├─ gradlew.bat
├─ information
│  ├─ memo.md
│  ├─ 블로그 DB설계.pdf
│  ├─ 블로그 erd.pdf
│  ├─ 블로그 기획서 수정.pdf
│  ├─ 스프링 시큐리티 동작 순서.JPG
│  └─ 스프링 흐름 이미지.png
├─ readme.md
├─ settings.gradle
└─ src
   ├─ main
   │  ├─ java
   │  │  └─ com
   │  │     └─ project
   │  │        └─ myBlog
   │  │           ├─ MyBlogApplication.java
   │  │           ├─ common
   │  │           │  ├─ GlobalControllerAdvice.java
   │  │           │  └─ ResponseDto.java
   │  │           ├─ config
   │  │           │  ├─ PrincipalDetail.java
   │  │           │  ├─ PrincipalDetailService.java
   │  │           │  ├─ SecurityConfig.java
   │  │           │  └─ oauth
   │  │           │     ├─ CustomOAuth2AuthenticationSuccessHandler.java
   │  │           │     ├─ CustomOAuth2UserService.java
   │  │           │     └─ OAuthAttributes.java
   │  │           ├─ controller
   │  │           │  ├─ CommentController.java
   │  │           │  ├─ ErrorController.java
   │  │           │  ├─ MainController.java
   │  │           │  ├─ PostController.java
   │  │           │  ├─ TagController.java
   │  │           │  └─ UserController.java
   │  │           ├─ dto
   │  │           │  ├─ CommentDto.java
   │  │           │  └─ PostDto.java
   │  │           ├─ entity
   │  │           │  ├─ BaseEntity.java
   │  │           │  ├─ Comment.java
   │  │           │  ├─ Image.java
   │  │           │  ├─ Post.java
   │  │           │  ├─ PostTag.java
   │  │           │  ├─ RoleType.java
   │  │           │  ├─ Tag.java
   │  │           │  └─ User.java
   │  │           ├─ repository
   │  │           │  ├─ CommentRepository.java
   │  │           │  ├─ PostRepository.java
   │  │           │  ├─ PostTagRepository.java
   │  │           │  ├─ PostTagRepositoryCustom.java
   │  │           │  ├─ PostTagRepositoryCustomImpl.java
   │  │           │  ├─ TagRepository.java
   │  │           │  ├─ TagRepositoryCustom.java
   │  │           │  ├─ TagRepositoryCustomImpl.java
   │  │           │  └─ UserRepository.java
   │  │           └─ service
   │  │              ├─ CommentService.java
   │  │              ├─ PostService.java
   │  │              ├─ PostTagService.java
   │  │              ├─ TagService.java
   │  │              └─ UserService.java
   │  └─ resources
   │     ├─ application.yml
   │     ├─ static
   │     │  ├─ css
   │     │  │  ├─ common.css
   │     │  │  ├─ index.css
   │     │  │  └─ lop.css
   │     │  └─ js
   │     │     ├─ common.js
   │     │     └─ post.js
   │     └─ templates
   │        └─ thymeleaf
   │           ├─ common
   │           │  └─ error
   │           │     ├─ error400.html
   │           │     ├─ error404.html
   │           │     ├─ error405.html
   │           │     └─ error500.html
   │           ├─ fragment
   │           │  ├─ config.html
   │           │  ├─ footer.html
   │           │  ├─ header.html
   │           │  ├─ nav.html
   │           │  ├─ rows.html
   │           │  └─ zoom.html
   │           ├─ index.html
   │           ├─ layout
   │           │  └─ default_layout.html
   │           ├─ post
   │           │  ├─ detail.html
   │           │  ├─ edit_form.html
   │           │  ├─ post.html
   │           │  ├─ post_list.html
   │           │  └─ write_form.html
   │           └─ user
   │              ├─ joinForm.html
   │              └─ loginForm.html
   └─ test
      └─ java
         └─ com
            └─ project
               └─ myBlog
                  └─ MyBlogApplicationTests.java
```
©generated by [Project Tree Generator](https://woochanleee.github.io/project-tree-generator)

## 6. 페이지 별 기능
1) 회원
- 회원가입
- 로그인
- 깃허브를 통한 로그인
- 로그아웃
- 최초 진입시 방문자 카운트

2) 포스트
- 글쓰기 (관리자)
- 글 수정 (관리자)
- 글 삭제 (관리자)
- 글 목록 조회
- 글 상세 조회
- 인기 글 보기 (추후 작업 예정)

3) 태그
- 태그 별 게시글 카운팅
- 태그 별 게시글 모아보기

4) 댓글
- 댓글 작성
- 댓글 삭제 (작성자)
- 댓글 수정 (작성자)
- 댓글 목록 조회

5) 이미지
- 글 이미지 등록시 DB 저장
- 썸네일 지정
- 이미지 수정 삭제시 기존 등록된 이미지 삭제 (추후 작업 예정)

## 7. 신경쓴 부분
- [Security 설정](https://github.com/mypace0600/myBlog/wiki/Spring-Security)
- [OAuth2 로그인 설정](https://github.com/mypace0600/myBlog/wiki/Github-OAuth2-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EA%B5%AC%ED%98%84)
- [Authentication 통합 관리](https://github.com/mypace0600/myBlog/wiki/OAuth2Login-%EB%98%90%EB%8A%94-FormLogin-%EC%9D%84-%ED%86%B5%ED%95%9C-%EB%A1%9C%EA%B7%B8%EC%9D%B8-%EC%8B%9C--Authentication-%ED%86%B5%ED%95%A9-%EA%B4%80%EB%A6%AC)

## 8. 트러블 슈팅
- [무한참조 해결](https://github.com/mypace0600/myBlog/wiki/%EB%AC%B4%ED%95%9C%EC%B0%B8%EC%A1%B0-%ED%95%B4%EA%B2%B0)

## 9. 개선 목표
- 추후 작업 예정인 내용을 차례로 작업해보기
- test 코드를 따로 작성하지 않았는데 작성해보고 리펙토링 하기
- 홈서버 DB 백업 스크립트 작성
- 젠킨스를 통한 CICD 구축

## 10. 프로젝트 후기
- 심현수<br>
  Spring Security에 대해 공식 문서를 읽으면서 인증과 인가의 기본 개념을 파악했습니다. 특히 OAuth2 로그인을 구현하면서 관련 기능을 배우는 과정이 매우 흥미로웠습니다. JPA를 사용해 데이터베이스를 설계하면서 여러 가지 연관관계를 이해할 수 있었고, 무한참조 이슈를 해결하면서 JPA 적용 시 고려해야 할 중요한 점들도 알게 되었습니다.<br>
  프로젝트를 기획하고 디자인하며 개발과 서버 배포까지 함께 진행하는 과정에서 팀원들과 함께 토론하고 의견을 나누는 시간이 정말 좋았습니다. 무엇보다, 끝까지 포기하지 않고 함께 달려준 동료들이 있어 이 프로젝트를 완수할 수 있었습니다. 정말 고맙고, 앞으로도 함께 성장해 나가고 싶습니다.

- 신한<br>
