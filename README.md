# Visual Studio 템플릿

Maven ArcheType 템플릿으로 초기 프로젝트 구조를 만드는 것 처럼 Visual Studio 에도 비슷한 기능이 있었다.

Visual Studio에서 템플릿을 만드는 방식은 어느정도 구조를 만들어둔 다음, `프로젝트`메뉴의 `템플릿 내보내기` 기능으로 압축 파일로 내보내어 기본적으로 사용할 수 있고, 세부 설정 필요시에는 내보낸 파일이 압축을 풀어, 설정 값들을 조정해주면 되었다.

지금 템플릿을 만들어본 프로젝트는 단순 C 학습용 템플릿이여서, 설정값을 반드시 조정해야할 부분이 많은 것은 아니였지만, Icon이나 Tag, 그리고 신규 소스 추가시 주석에 해당 파일명이 포함되도록 하는 정도로만 바꾸었다.

그리고 향후 버전에 따라 스키마가 달라질 수 있으니, 버전으로 구분을 미리 해두자!

템플릿은 두가지 유형이 있는데, 단순 C 파일에 대해서의 템플릿은 Item 템플릿이고, 어떤 프로젝트 단위의 템플릿은 Project 템플릿이다.

여기 있는 템플릿을 바로 사용하려면, 

`내문서\Visual Studio 2022\Templates\` 이하의 아래 경로에 잘 맞춰서 넣어주면 된다.

* ItemTemplates
* ProjectTemplates



## 템플릿

### [2022 버전](2022)





## 세부 설정 변경한 내용

### ItemTemplates  >  C-Study-Source  : 학습용 C 소스 파일

* 소스 파일 주석에 파일 명 작성 부분 

  ```c
  /**
   *  $fileinputname$.c
   */
  #define _CRT_SECURE_NO_WARNINGS 
  
  #include <stdio.h>
  
  int main(void) {
  
    return 0;
  }
  ```

  기본으로 제공되는 `$fileinputname$` 파라미터를 사용해주면, VS에서 파일 이름 지정해서 소스 추가시 해당 부분이 파일명으로 지정되서 추가된다.

* 템플릿 아이콘 (__TemplateIcon.ico)

  템플릿을 만들면 기본으로 공통적인 아이콘이 들어가는데, 이부분은 C 소스에 대한 아이콘으로 나타나는 것이 나아보여, `VCProject.dll` 에 들어있는 C 아이콘으로 변경했다.

  이 아이콘은 git에 올리지 않았다. `${VS2022 설치경로}\Common7\IDE\VC\vcpackages\VCProject.dll` 를 7zip 같은 압축 프로그램으로 풀어보면 아이콘을 추출할 수 있으니 추출해서 사용하면 되겠다.

* 기타 설명들 변경

### ProjectTemplates > C-Study-Project : 학습용 C 프로젝트

* 소스파일 주석에 프로젝트 명 작성 부분

  ```c
  /**
   *  $projectname$ 프로젝트 - main.c
   */
  #define _CRT_SECURE_NO_WARNINGS 
  
  #include <stdio.h>
  
  int main(void) {
    
    return 0;
  }
  ```

  프로젝트 템플릿에서는 최초 기본으로 생성되는 소스파일명을 고정했다. main.c 자체도 ${ProjectName}Main.c 같은 식으로 기준으로 바꿀 수도 있겠지만, 프로젝트 명은 일관적이지 않을 수도 있어서 그냥 `main.c`로 두었다.<br><br>

* 템플릿 아이콘

  ```xml
  <Icon Package="{976cf7d5-2a72-47a3-9e46-5b7c3db95f17}" ID="500" />
  ```

  이 부분도 기본 값을 공통적인 `__TemplateIcon.ico` 을 사용하게 되는데,  윈도우 콘솔 응용 프로그램이 사용하는 값으로 바꿔주었다. 

  먼저 C 소스의 아이콘도 이런식으로 코드로 접근하면 좋을 것 같은데... 가능한 부분일지 잘 모르겠다.<br><br>

* 태그 추가

  ```xml
      <PlatformTag>Windows</PlatformTag>
      <LanguageTag>C</LanguageTag>
      <ProjectTypeTag>Console</ProjectTypeTag>
  ```

  VC에서 프로젝트 템플릿 선택시 운영체제, 언어, 프로젝트 유형을  나타내기위해서 추가했다.





## 참조

* Project 템플릿 만들기
  * https://docs.microsoft.com/ko-kr/visualstudio/ide/creating-project-and-item-templates?view=vs-2022
* Item 템플릿 만들기
  * https://docs.microsoft.com/ko-kr/visualstudio/ide/how-to-create-item-templates?view=vs-2022
