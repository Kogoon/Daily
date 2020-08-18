# 외부패키지 이용하기

`english_word` : 영어 단어 수천 개와 몇 가지 유틸리티 기능이 포함되어 있는 오픈소스 패키지  

### pubspec.yaml
** `Flutter`에서 의존성 및 asset 관리는 `pubspec.yaml` 파일이 담당. **  
~~~
  dependencies:
    flutter:
      sdk: flutter
    english_words: ^3.1.0
~~~
dependencies: 부분에 `english_words`와 버전 추가.   

### 외부 패키지 설치
`pubspec.yaml`이 있는 위치(디렉토리)에서 아래와 같이 명령어 실행.   
~~~
flutter pub get
~~~
  
또한, Package get을 수행하면 pubspec.lock 프로젝트로 가져온 모든 패키지 목록과 버전 번호를 포함하고 있는 pubspec.lock  파일도 자동 생성. 
  

### Code
`main.dart`
~~~
import 'package:flutter/material.dart';
import 'package:english_words/english_words.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    final wordPair = WordPair.random();
    return MaterialApp(
      title: "Welcome to Flutter",
      home: Scaffold(
        appBar: AppBar(
          title: Text('Welcome to Flutter'),
        ),
        body: Center(
          child: Text(wordPair.asPascalCase),
        )
      ),
    );
  }
}
~~~
`import 'package:english_words/english_words.dart';`  추가  
`child: Text(wordPair.asPascalCase),` 수정  

### 결과
`Hot Reload` 할때마다, 단어가 계속 변경됨.  
