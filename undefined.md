---
description: >-
  컴퓨터를 이용한 코퍼스를 구축시 사용할 수 있는 프로그래밍 언어는 다양하다. 여기서는 사용하기 쉬우면서 가장 대중화되고 여러 연구자들에
  의해서 코퍼스 구축에 필요한 라이브러리들을 사용할 수 있는 파이썬을 이용할 것이다. 파이썬은 귀도 반 로썸에 의해서 오픈 소스로 개발된
  언어이다. 본 장에서는 코퍼스 구축에서 알아두어야 할 파이썬 문법에 대해서 소개한다.
---

# 파이썬 기초

파이썬은 버전 2와 버전 3가 존재한다. 파이썬을 개발하고 있는 파이썬 파운데이션에서는 파이썬 2에 대한 지원을 2020년에 중단할 예정이므로, 앞으로 여기서는 파이썬 3의 문법에 대해서 다룰 것이다. 별도의 이야기가 없다면, 파이썬이라고 말했을때는 파이썬 3를 말하는 것으로 이해하면 된다. 

## 설치

파이썬을 설치하기 위해서는 여러가지 방법이 있다. 여기서는 라이브러리들의 설치를 편하게 진행하기 위해서 Anaconda라는 것을 이용하여 파이썬을 설치할 것이다. Anaconda는 파이썬 및 주로 사용하는 \(데이터 분석 또는 과학 계산용\) 라이브러리들을 관리하고, 쉽게 설치할 수 있도록 지원해주는 프로그램이다.

Anaconda는 "[https://www.anaconda.com/distribution/](https://www.anaconda.com/distribution/)"에서 받을 수 있다. 윈도우 또는 맥을 사용하는 사용자의 경우는 Python 3.7의 64-Bit Graphical Installer을 다운로드 후 설치하면 된다. Graphical Installer는 설치 방법이 간단하기 때문에 화면에 나오는 지시대로 설치하면 된다. 리눅스를 사용하는 경우 여러가지 배포판이 존재하고, 그 배포판에 따라서 GUI가 다르기 때문에 Anaconda에서는 Command Line Installer만 제공한다.

#### Anaconda Graphical Installer

&lt;Anaconda Graphical Installer 설명&gt;

#### Anaconda Command Line Installer

&lt;Anaconda Command Line Installer 설명&gt;

#### 필수 설치 라이브러리

Corpus를 구축하기 위해서는 word tokenizing및 stemming등의 전처리 작업등을 해야한다. 이를 위한 라이브러리는 nltk와 gensim이다. nltk는 Natural Language Toolkit의 약자로 python으로 자연어 처리를 하기 위해서 필요한 기능들을 제공한다. nltk는 3.4.1이 최근 버전이다. 여기서는 최근 버전으로 설치할 것이다. Anaconda에서 nltk를 설치하는 방법은 간단하다.

`$ conda install nltk`

참고\) 앞의 '$'는 Command Line의 프롬프트에 해당한다. 맥 OS와 리눅스의 경우 Command Line 프롬프트가 "$"일 경우가 많기 때문에 여기서는 '$'로 표시한다. 윈도우의 경우는 "C:"로 시작한다. 여기서는 리눅스 버전으로 가정하고 진행한다.

gensim은 문장에 대한 통계적 분석 도구들을 제공한다. gensim 역시 설치 방법은 간단하다.

`$ conda install gensim`

#### 코드 편집기

Microsoft Word를 사용한 적이 있는가? Microsoft Word와 같은 프로그램을 문서 편집기라고 부르는데, 문서의 작성부터 수정, 수정이력 관리 등의 기능들을 제공하여, 문서 작성을 편하게 해주는 프로그램이다. 여기서 문서를 코드로 바꿔서 생각하면, 이것이 코드 편집기이다. 코드 편집기는 프로그램 코드를 \(비교적\) 쉽게 작성, 편집할 수 있는 프로그램을 의미한다. 다양한 프로그램이 존재하는데, 자신에게 맞는 프로그램을 사용하면 된다.

참고\) 코드 편집기를 이용하지 않고 코딩을 할수는 있다. 하지만 아주 고통스러울 것이다.  

여기서는 크게 세가지를 소개할 것이다. 하나는 Microsoft사에 만든 Visual Studio Code와 JetBrain에서 만든 PyCharm이다. 마지막으로 Jupyter Notebook을 이용한 방법이다.

Microsoft사는 개발도구를 굉장히 잘 만드는 것으로 알려져 있다. 그것은 Microsoft Visual Studio이다. Visual Studio는 Intellisense\([코드 완성, 인자 정보, 함수 또는 맴버 변수, 함수 등의 정보, 클래스의 맴버 목록 등을 보여주는 기능들을 합쳐서 이야기한다.](https://code.visualstudio.com/docs/editor/intellisense)\) 및 디버깅 기능, UI 제작도구\(디자인 툴\) 등이 타의 추종을 불허한다고 한다. Microsoft Visual Studio\(MS VS\)는 윈도우 프로그램 개발용 도구이기 때문에 현재 윈도우만 지원한다. Microsoft에서는 최근에 Microsoft Visual Studio의 Editor기능들을 다른 OS에서도 사용할 수 있도록 하기 위해서 Microsoft Visual Studio Code\(VSCode\)를 제작하였다. VSCode는 MS VS의 Editor기능 일부만을 흉내냈기 때문에 가볍고, 언어지원 및 컴파일, 디버깅 등과 관련된 기능들은 플러그 인\(VSCode에서는 Extension이라고 부른다\)형태로 제공하여 사용자가 필요시 설치할 수 있도록 했기 때문에 확장성 등이 굉장히 좋은 것으로 알려져 있다. 파이썬 개발을 하기 위해서는 Extension에서 Python extension for Visual Studio Code를 찾아서 설치하면 된다.

PyCharm은 Python을 개발하기 위해서 JetBrain에서 만든 IDE이다. MS VS에서와 같이 파이썬을 위한 개발 기능들을 포함하고 있다. 예를 들어, IntelliSense기능은 기본이고, 실행 및 디버깅까지 편리하게 되어 있다. 

### 파이썬 문법

파이썬 문법을 설명한다. 

#### 출력

어떤 언어를 처음 소개할때 가장 유명한 코드를 소개할 것이다. 일명 "Hello, World"이다.  

