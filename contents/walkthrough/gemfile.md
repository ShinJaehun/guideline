# Gemfile의 작성

레일스 프로젝트를 생성하면 `Gemfile` 파일이 생성된다. `Gemfile`은 다양한 `젬(gem)`들을 등록하는 파일로 텍스트 파일이다. 여기서 `젬`이란 다른 언어에서 흔히 접하게 되는 일종의 루비 라이브러리라고 간단하게 생각하면 된다. 이미 많은 `젬`들이 공개([http://rubygems.org](http://rubygems.org))되어 있기 때문에, 우리는 그저 필요한 `젬`을 `Gemfile`에 등록해서 사용하면 된다.

## 사용할 젬 소개

레일스 프로젝트를 생성하면 이미 다수의 젬들이 등록되어 있다. 이 젬들은 레일스 프로젝트가 실행되기 위한 최소한의 것들이다. 모든 `젬`은 버전을 가지고 있어서 이러한 버전이 때로는 호환성 문제로 매우 중요하게 다루어진다. 프로젝트 디렉토리를 유심히 보면 `Gemfile.lock` 파일을 찾을 수 있다. 이 파일은 `bundle install`로 설치된 젬들의 버전을 기억해 두는 파일 정도로 생각하면 된다. 따라서 이 파일은 소스관리(git)에 포함해 두는 것이 좋다. 이것은 다른 개발자가 동일한 소스로 개발할 때 동일한 `젬` 버전을 사용할 수 있게 해 주어 호환성의 문제를 해결할 수 있는 방법이 되기도 한다.

이제 여러가지 기능을 구현하기 위해 필요한 `젬`들을 `Gemfile`에 추가해 보자. 추가할 `젬` 목록은 아래와 같다.

```
gem 'bootstrap-sass', '~> 3.1.1'
gem 'simple_form'
```

[참고사항]
>[`bootstrap-sass`](https://github.com/twbs/bootstrap-sass) : 반응형 모바일 웹브라우져 환경을 구축하기 위한 프론트엔드 프레임워크 중의 하나인 Twitter-Bootstrap을 레일스 프로젝트에서 사용하기 쉽게 해 주는 젬이다.

>[`simple_form`](https://github.com/plataformatec/simple_form) : bootstrap과 함께 form을 사용할 때 잘 어울리는 젬으로 simple_form을 사용할 수 있다.


## 젬 설치하기

`젬`을 `Gemfile`에 등록한 것으로 바로 사용할 수 있는 것은 아니다. `bundle install`이라는 커맨드라인 명령을 수행하여 설치하는 과정이 필요하다. 아래와 같이 명령을 실행한다.

```
$ bundle install
```

`Bootstrap`을 실제로 프로젝트에 적용하기 위해서 약간의 설정 과정이 필요한다.

우선, 모든 css 파일에서 `Bootstrap`의 모든 스타일, mixin, 변수들을 사용하기 위해서는 아래와 같이 추가한다.

## Bootstrap Asset 설정

`app/assets/stylesheets/` 디렉토리 상의 `application.css`를 삭제하고 대신에 `application.css.scss` 파일을 생성하고 아래와 같이 추가한다.

```
$light-orange: #ff8c00;
$navbar-default-color: $light-orange;
$navbar-default-bg: #312312;
$navbar-default-link-color: gray;
$navbar-default-link-active-color: $light-orange;
$navbar-default-link-hover-color: white;
$navbar-default-link-hover-bg: black;

@import 'bootstrap';

body { padding-top: 60px; }
```

`Bootstrap`의 모든 자바스크립트 헬퍼를 사용하기 위해서는 `app/assets/javascripts/application.js` 파일을 아래와 같이 수정한다. (//= require bootstrap 추가)

```
//= require jquery
//= require jquery_ujs
//= require bootstrap
//= require turbolinks
//= require_tree .
```

## Simple_form 설치

`Bootstrap`과 `Simple_form`을 연결하기 위해 아래와 같이 `Simple_form`을 `--bootstrap` 옵션과 함께 설치한다.

```
$ rails generate simple_form:install --bootstrap
```

## Git 커밋후 Github에 푸시하기

지금까지 작업한 내용을 커밋한다. (Git에 대해서 더 자세한 내용은 `Git 설치`를 참고하기 바란다.)

```
$ git add .
$ git commit -m "Gemfile에 젬추가 : bootstrap-sass & simple_form"
```

`Github`에서 `rcafe`라는 저장소를 만들고 URL 주소를 로컬저장소의 원격 저장소 `origin`으로 등록한 후, 커밋내용을 `Github`로 푸시한다.

![](http://i1373.photobucket.com/albums/ag392/rorlab/Photobucket%20Desktop%20-%20RORLAB/rcafe/2014-05-07_10-52-32_zps9ac80427.png)

이에 대한 자세한 내용은 아래를 참고하자.

[커맨드라인에서 기존 프로젝트를 Github로 추가하기](https://help.github.com/articles/adding-an-existing-project-to-github-using-the-command-line)






