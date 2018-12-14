---
title: "밑바탕 토대"
teaching: 45
exercises: 0
questions:
- 도서관과 관련된 프로그램을 성공적으로 생성하고 사용하는데 필요한 일반적인 기술과 좋은 관례는 어떤 것이 있을까요?
objectives:
- 소프트웨어와 데이터를 사용하는데 좋은 관례(best practice)를 식별한다.
- 파일을 저장하는데 좋은 관례(best practice)를 식별한다.
- 파일명을 짓는데 좋은 관례(best practice)를 식별한다.
keypoints:
- 자료구조는 일관성과 함께 예측가능해야 된다.
- 데이터 디렉토리에 데이터 식별자 혹은 의미론적 요소(semantic element)를 적극 사용하는 것을 고려한다.
- 본인 작업에 적합하도록 자료 구조를 맞추고 조정한다.
- 파일과 디렉토리를 식별하도록 작명 규칙(naming conventions)을 적용시켜 데이터 요소간에 연관관계를 생성함으로써 
  장기적으로 자료 구조에 대한 이해와 가독성을 높인다.
  
---

## 밑바탕 토대

컴퓨팅 도구를 자유자재로 사용하기 전에,
시간 일부를 투여해서 라이브러리 카펜트리(library carpentry)에서 마주할 것에 도움이 되는 밑바탕 토대를 살펴본다.
본인 작업에 컴퓨팅 접근법을 도입할 때 알아두면 유용한 몇가지 원칙과 행동을 다루게 된다.


### 컴퓨터는 멍청하다.

자명한 사실로 정말 컴퓨터는 멍청하다. 영어로 The computer is stupid.
하지만, 컴퓨터는 유용하기도 하다. 
반복 작업(repetitive task), 쭉 열거된 작업(enumerative task), 기억에 의존하는 작업이 주어졌을 때,
마지못해 억지로 작업을 수행하는 사람보다 컴퓨터는 훨씬 더 빨리, 더 정확하게 작업을 수행한다.
컴퓨터는 컴퓨터가 지시받는 바만 정확하게 수행한다.
오류가 발생하면 잘못은 바로 작업을 내린 당신이다. 즉, 당신 머리속에 버그가 있는 것이다.
대부분의 경우 컴퓨터가 의도한 바를 잘못 이해하는 경우가 있는데 이유는 컴퓨터는 원래 자신이 아는 한도내에서 동작하기 때문이다.


### Why take an automated or computational approach?

### 자동화 즉 컴퓨팅 접근법을 취하는 이유는 뭘까?

다른 말로 바꾸게 되면, "수작업으로 못 할 이유는 뭘까?"라는 질문과 같다.
문제에 대해서 수작업이 훨씬 더 쉽고, 빠르고, 가장 효율적인 접근법이 되는 경우도 무척이나 많다.
**자동화(automation)**, 즉 컴퓨팅 접근법(computational approach)을 고려해야되는 조건 두가지는 다음과 같다:

 - 본인이 작업 자동화 방법을 알고 있는 경우.
 - 본인이 알기로 본인이 반복해서 계속해야 되는 작업인 경우.

주요 수업내용:

- **빌리고, 빌리고, 또 빌려라.**. 전문직업 프로그래머부터 도서관에서 코딩하는 우리와 같은 일반인 모두에게 공통되는 프로그래밍의 중심;
- **배워야 되는 적합한 언어는 본인 작업 맥락에서 동작하는 것이다.** 진정한 최고 언어는 없고 단지 서로 다른 장점과 단점을 갖는 언어만 있을 뿐이다.
    하지만, 프로그래밍 언어 모두는 동일한 토대가 되는 원칙은 채택하고 있다;
- **전문개발 측면에서 프로그래밍의 역할을 고려하라.** 컴퓨팅 기술은 효율성과 함께 효과성도 증진시킨다. 학습하고자 하는 기술에 집중하고 함께하는 직원들이 어떤 기술을 습득하는지도 숙지한다;
- **코드를 (조금이라도) 알게되면 코드를 사용하는 프로젝트를 평가하는데 도움이 된다.** 프로그래밍이 외계인처럼 보일 수 있지만, 코드를 알게 되면 소프트웨어 개발 품질을 판단하고 소프트웨어 개발이 포함된 활동을 계획하는데 도움을 줄 수 있다;
- **다른 무언가를 할 수 있도록 시간을 벌 수 있도록 자동화하라!** 시간을 들여서라도 한 곳에 모아라. 가장 단순한 프로그래밍 기술도 더 흥미진지한 작업을 수행하는데 상당한 시간을 절약해 줄 수 있다!(더 흥미로운 작업은 더 많은 프로그래밍 기술을 학습할지라도 ...)


**왜 자동화하는가?**

![그럴만한 가치가 있나?](../assets/img/is_it_worth_the_time.png)

Randall Munroe가 저작한 '그럴만한 가치가 있나(Is it worth the time)?', CC-BY-NC 2.5 라이선스 [https://xkcd.com/1205/](https://xkcd.com/1205/).

### 키보드 단축키가 여러분의 친구입니다.

프로그래밍 과정을 통해 더 많은 컴퓨팅 기술을 얻게 되지만, 매우 단순한 키보드 단축키부터 차분히 시작한다.
여러분 모두 호불호를 명확한 단축키 사용법을 익혀서 노동력을 절약하기도 하지만 멍청한 컴퓨터를 가장 최선의 방식으로 활용하게도 하는 역할을 한다.
키보드 단축키 없이도 도서관 카펜트리 모든 학습을 수행할 수 있지만 단축키는 참 많이 활용될 것이 분명하다.


동작 | 윈도우 | 맥 | + 키보드 누름(Keystroke)
--- | --- | --- | --- |
저장(Save) | <kbd>Ctrl</kbd> | <kbd>Command</kbd> | + <kbd>S</kbd>
복사(Copy) | <kbd>Ctrl</kbd> | <kbd>Command</kbd> | + <kbd>C</kbd>
잘라내기(Cut) | <kbd>Ctrl</kbd> | <kbd>Command</kbd> | + <kbd>X</kbd>
붙여넣기(Paste) | <kbd>Ctrl</kbd> | <kbd>Command</kbd> | + <kbd>V</kbd>
응용프로그램 바꿈(Switch Applications) | <kbd>Alt</kbd> | <kbd>Command</kbd> | <kbd>Tab</kbd> | 

### 일반 텍스트 파일형식도 여러분 친구입니다.

왜냐구요? 컴퓨터가 텍스트를 처리할 수 있기 때문입니다!

컴퓨터로 본인 작업을 처리하게 하려면, 
일반 평문 텍스트의 경우 `.txt`, 콤마 구분자 `.csv`, 탭 구분자 `.tsv` 표형식 데이터의 경우처럼 플랫폼에 구애받지 않는 것을 사용하도록 습관을 들여라.
TSV와 CSV 파일 모두 스프레드쉬트 형식이다. 이러한 일반 평문 텍스트 형식이 상용형식(예를 들면 마이크로소프트 워트)보다 선호되는 이유는 
대다수 소프트웨어 팩키지에서 열어 볼 수 있고, 향후 계속해서 열어 볼수도 있고 편집도 가능하기 때문이다.
대부분의 표준 오피스 제품에는 `.txt`, `.csv`, `.tsv` 파일형식으로 파일을 저장할 수 있는 선택옵션을 포함하고 있습니다.
이것이 의미하는 바는 친숙한 소프트웨어로 계속해서 작업할 수 있음을 의미한다.
`.doc` 혹은 `.xls`와 비교하여 기계판독 가능한 요소만 포함하고 있다는 부가적인 좋은 점도 있다.

자동화 즉, 컴퓨팅 목적으로 파일작업을 수행할 때, 멋짓 외양보다는 유의미한 데이터 전송에 집중하는 것이 더 중요하다.
굵은 글씨, 이탤릭, 색상을 주어 제목을 돋보이게 하거나 데이터 요소간에 시각적 연결을 만들 수 있지만, 이러한 표시지향 표식은 쉽게
기계판독이 되지 않아서 쿼리하거나 검색이 되지 않아서 대량의 정보로는 부적절하다.
한가지 경험 법칙은 <kbd>F</kbd>/<kbd>Command</kbd>+<kbd>F</kbd>으로 찾을 수 없으면 기계판독은 되지 않는 것으로 간주된다.
별표(`*`) 두개 혹은 해쉬(`#`) 3개를 사용해서 데이터 기능을 표현하는 단순한 표기법이 더 선호된다;
예를 들어, 의문부호 3개를 사용해서 추적할 무언가를 나타내는 경우가 있다. 왜 `???`을 골랐나면 <kbd>Ctrl</kbd>+<kbd>F</kbd>/<kbd>Command</kbd>+<kbd>F</kbd>으로 쉽게 검색할 수 있기 때문이다.

### Use machine readable plain text notation for formatting
There are some simple notation schemes that are also plain text and machine readable, but can be used to render simple formatting. One such scheme is called Markdown, a lightweight markup language. A markup language is a a metadata language that uses notation to distinguish between the content and the formatting of the content. Markdown files, which use the file extension `.md`, are machine readable, human readable, and used in many contexts - for example, GitHub renders text via Markdown. An excellent [Markdown cheat sheet is available on GitHub](https://github.com/adam-p/markdown-here) for those who wish to follow – or adapt – this existing schema. 

### Applications for writing, reading and outputting plain text files
For Windows users, Notepad++ http://notepad-plus-plus.org/ is recommended. Mac or Unix users may find Komodo Edit, Text Wrangler, Kate, or Atom helpful. Combined with [pandoc](http://pandoc.org/), a Markdown file can be exported to PDF, HTML, a formatted Word document, LaTeX or other formats, so it is a great way to create machine-readable, easily searchable documents that can be repurposed in many ways. This [Programming Historian](https://programminghistorian.org/) [tutorial](https://programminghistorian.org/en/lessons/sustainable-authorship-in-plain-text-using-pandoc-and-markdown) spells out what to do. 

### Naming files sensible things is good for you and for your computers

Working with data is made easier by structuring your files in a consistent and predictable manner. Without structured information, our lives would be much poorer. As library and archive people, we know this. But let's linger on this a little longer because for working with data it is especially important.

Examining URLs is a good way of thinking about why structuring data in a consistent and predictable manner might be useful in your work. Good URLs represent with clarity the content of the page they identify, either by containing semantic elements or by using a single data element found across a set or majority of pages.

A typical example of the former are the URLs used by news websites or blogging services. WordPress URLs follow the format:

-   `ROOT/YYYY/MM/DD/words-of-title-separated-by-hyphens`
-   <http://cradledincaricature.com/2015/07/24/code-control-and-making-the-argument-in-the-humanities/>

A similar style is used by news agencies such as a *The Guardian* newspaper:

-   `ROOT/SUB_ROOT/YYYY/MMM/DD/words-describing-content-separated-by-hyphens`
-   <http://www.theguardian.com/uk-news/2014/feb/20/rebekah-brooks-rupert-murdoch-phone-hacking-trial>

In data repositories, URLs structured by a single data element are often used. The National Library of Australia's TROVE uses this format:

-   `ROOT/record-type/REF`
-   <http://trove.nla.gov.au/work/6315568>

The Old Bailey Online uses the format:

-   `ROOT/browse.jsp?ref=REF`
-   <http://www.oldbaileyonline.org/browse.jsp?ref=OA16780417>

What we learn from these examples is that a combination of semantic description and data elements make for consistent and predictable data structures that are readable both by humans and machines. Transferring this kind of pattern to your own files makes it easier to browse, to search, and to query using both the standard tools provided by operating systems and by the more advanced tools Library Carpentry will cover.

In practice, the structure of a good archive might look something like this:

- A base or root directory, perhaps called 'work'.
- A series of sub-directories such as 'events', 'data', ' projects' et cetera
- Within these directories are series of directories for each event, dataset or project. Introducing a naming convention here that includes a date element keeps the information organised without the need for subdirectories by, say, year or month.

All this should help you remember something you were working on when you come back to it later (call it real world preservation).

The crucial bit for our purposes, however, is the file naming convention you choose. The name of a file is important to ensuring it and its contents are easy to identify. 'Data.xslx' doesn't fulfil this purpose. A title that describes the data does. And adding dating convention to the file name, associating derived data with base data through file names, and using directory structures to aid comprehension strengthens those connections.

## For further reading

Andromeda Yelton, a US-based librarian, closely involved in the Code4Lib movement, put together an excellent American Library Association Library Technology Report called ["Coding for Librarians: Learning by Example."](https://thatandromeda.github.io/ltr/). In it, Yelton describes scenarios in which library professionals developed and shared code that made a difference to their work, to the work of their colleagues, and to the work of their library.
