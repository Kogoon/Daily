# Hugo를 이용해 Github 블로그 만들기  


#### Hugo 설치 

#### hugo 프로젝트 시작
~~~
> hugo new site <프로젝트 명>
~~~
##### 기본구조
 * archetypes/ : front matter 설정하는 곳 `default.md`가 있는데, 게시글 만들때마다 (**아래-글쓰기**) 서식 같은 것 설정하는 곳이라 보면 된다.   
 ~~~
  - title : 글의 제목을 설정한다. 
  - tags : 글의 태그를 설정할 수 있다.
  - date : date는 {{.Date }} 로 설정, 현재시간으로 저장된다. 
  - authors : 글의 저자를 적어준다. 
  - categories : 태그와는 다른 카테고리 설정.. (나중에 다시 확인)
  - draft : ?
  등 여러가지가 있다.
 ~~~
 * `content/` : 블로그 게시글들이 저장되는 곳. 한 파일들이 한 게시글로 설정된다.   
 * `data/` : 이런저런 데이터를 저장할 수 있다. json.. csv 파일들... (어떻게 쓰이는지는 잘 모름)  
 * `layout/` : (html 등을 코딩하는 곳)  
 * `public/` : (기본아님) ( 배포시. - 아래)  
 * `theme/` : 테마를 저장하는 곳. (블로그 테마)  
 * `static/` : css나 이미지를 저장하는 곳.   
 * `config.toml` : 블로그 설정하는 곳이다. 제목.. 등  
 
#### Theme 다운로드
> [hugo theme](https://themes.gohugo.io/)  
위에 들어가서 맘에드는 테마를 다운받아서 /theme/에 압축을 풀어준다 (또는 git clone)  
  
그리고 테마마다 Demo 로 미리 사이트를 확인할 수 있고, github을 통해서 보면 README.md에 사용법을 설명해 놓았다.

#### 블로그 설정
`/config.toml` 파일에 기본적인 내용을 설정하면 된다.   
잘 모르겠으면, 해당 테마 github repository의 README.md를 참고하거나, 다운로드 받은 테마 폴더 안에 /theme/<테마명>/config.toml 보고 설정하면된다.  

##### Taxonomies
Go Template에서는 기본적으로 `Category`와 `Tag`, 두 Taxonomies를 제공한다. 
`<baseURL>/categories` 와 `<baseURL>/tags`의 경로에서 확인할 수 있다. 
추가하고 싶으면 `config.toml`에서 설정해주면된다. 
~~~
[taxonomies]
category = "categories"
tag = "tags"
~~~
추가할 경우 category와 tag를 써줘야한다. 기본적으로 제공하지만 써서 변경하는 경우는 안쓰는 경우 사라진다.

#### 글쓰기(ex. post.md)
~~~
> hugo new <게시글 명>
(예시)> hugo new post/post.md
~~~

#### 배포하기 전에 로컬에서 확인하는 법. 
~~~
> hugo server -D
~~~
브라우저 창에서 'localhost:1313'으로 지금까지 만든 블로그를 미리 확인해 볼 수 있다. 

#### 빌드
~~~
> 
~~~

#### 배포

#### 오류

* * *
##### 참고
[IALY님 블로그 구축기](https://ialy1595.github.io/post/blog-construct-2/)

> frontend는 어렵다 (응?)
