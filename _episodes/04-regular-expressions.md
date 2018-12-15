---
title: 정규 표현식
teaching: 20
exercises: 25
questions:
- "본인 작업에 정규 표현식을 사용한다는 사실이 상상이 가는가?"
objectives:
- 검색에 정규 표현식을 사용한다.
keypoints:
- "정규 표현식은 패턴을 매칭하는 언어다."
- "정규 표현식을 인터랙티브하게 [regex101.com](https://regex101.com/) 혹은 [RegExr.com](http://www.regexr.com/) 웹사이트에서 테스트하고, [regexper.com](https://regexper.com/) 사이트에서 시각화도 해본다."
- "[RegexCrossword.com/](https://regexcrossword.com/) 혹은 [다중선택 퀴](https://librarycarpentry.github.io/lc-data-intro/05-quiz/)를 풀어본다."
---

## 정규 표현식(Regular expressions)

정규 표현식은 많은 프로그래밍 환경에서 정교한 패턴을 매칭하는데 사용되는 개념이면서 구현체이도 하다.
믿을 수 없을 정도로 강력한 도구라서 데이터와 파일에서 무언가를 찾고 관리하고 변형시키는 능력을 획기적으로 증대시킨다.


정규 표현식(regular expression)을 줄여서 *regex*로 표기하기도 한다. 
문자 순열을 사용해서 문자열을 매칭하도록 검색을 정의하는 방법("찾아서 바꾸는(find and replace)" 유형의 연산)으로 알려져 있다.
전산(computation)에서 문자열(string)은 인접한 기호 또는 값의 순열이다.
예를 들어, 단어, 날짜, 숫자 집합(예를 들어, 전화번호), 알파벳 영숫자 값(예를 들어, 식별자)이 이에 해당된다.
도서관 검색에서 "와일드 카드 문자"로 알려진 일부 정규표현식 사용에는 누구나 친숙하다.
하지만, 완전한 정규 표현식 구문에는 훨씬 더 많은 기능이 있다. 정규 표현식을 통해서 다음 기능을 익힐 수 있다:

- 문자 유형에 따라 매칭할 수 있다 (예를 들어, '대문자', '숫자', '공백', 등 )
- 반복되는 패턴을 매칭할 수 있다.
- 본인이 정의한 패턴과 매칭되는 원본 문자열의 일부를 잡아낼 수 있다.

정규표현식은 문자 그대로의 문자(리터럴 문자, literal character)와 메타문자 사용을 기반으로 한다.
메타문자(metacharacter)는 특별한 의미를 갖는 ASCII 문자를 지칭한다.
메타문자와 리터럴 문자를 사용함으로써 특정 문자열 보다는 패턴과 매칭되는 문자열 혹은 파일을 찾아낼 수 있는 정규 표현식을 만들어 낼 수 있게 된다.
예를 들어, 지역코드를 감싼 괄호를 제거해서 웹사이트에 전화번호 표시방법을 바꾸는 경우를 가정해보자.
전화번호 전부를 찾거나 (상당히 시간이 많이 걸리고 실수하기 쉽다.) 여는 괄호 문자를 전수 조사하는 것(상당히 시간도 많이 걸리고 거짓 양성이 많을 수 있음)보다 전화번호 패턴을 찾는 것도 방법이다.

정규표현식에는 일부 ASCII 문자를 문자 그대로 의미를 갖는 이상의 "메타문자"로 정의한다. 
따라서, 메타문자를 문자 그대로 사용하려면 메타문자에서 탈출(escape)시키는 것이 필요하다.
예를 들어 마침표(`.`)은 "모든 문자와 일치시켜라(match any character)"를 의미해서 마침표(`.`)를 매칭시키고자 하는 경우,
마침표 앞에 `\`을 사용해서 정규표현식에 다음 사실을 알려야 한다; 마침표를 메타문자가 아니라 문자 그대로 마침표로 사용함.
이러한 표기법은 특수 문자 탈출(`escape`)이라고 불린다. 특수 문자를 탈출(escape)시키는 개념은 
마크다운과 HTML을 포함한 다양한 컴퓨팅 환경에서 공유되기도 한다.

매우 단순한 정규표현식 사용례로 동일한 단어로 두가지 방식으로 철자가 적힌 곳을 찾아내는 것을 들 수 있다.
예를 들어 정규표현식 `organi[sz]e`은 "organise"와 "organize"을 동시에 매칭해서 찾아낸다.
하지만, `reorganise`, `reorganize`, `organises`, `organizes`, `organised`, `organized` 등등도 매칭시키기도 한다.

### 많이 사용되는 정규표현식 메타문자 학습

꺾쇠를 사용하면 문자 범위와 목록을 정의해서 패턴을 구성할 수 있다. 그래서:

- `[ABC]` A 혹은 B 혹은 C를 매칭시킨다.
- `[A-Z]` 임의 대문자를 매칭시킨다.
- `[A-Za-z]` 대문자 혹은 소문자를 매칭시킨다.
- `[A-Za-z0-9]` 대문자 혹은 소문자 혹은 숫자를 매칭시킨다.

다음도 있다:

- `.` 임의 문자를 매칭시킨다.
- `\d` 임의 숫자 하나를 매칭시킨다.
- `\w` 임의 단어 문자를 매칭시킨다. (`[A-Za-z0-9]`와 동일)
- `\s` 임의 공백, 탭, 개행(newline)을 매칭시킨다.
- `\` 문자을 사용해서 해당 문자가 특수 문자일 때 해당문자를 탈출(escape)시킨다. 예를 들어, `.com`을 찾는 정규표현식을 구성하는 경우 `\.com`와 같이 작성하는데 이유는 `.`이 임의 문자를 매칭시키는 특수문자이기 때문이다.
- `^` 문자는 행의 시작 위치를 표현한다. 따라서, 캐럿(caret)문자 다음에 오는 것은 행의 첫번째 문자인 경우만 매칭된다. 캐럿은 `circumflex`로도 알려져 있다.
- `$` 문자는 행의 끝 위치를 표현한다. 따라서 `$`문자 앞에 오는 것은 행의 마지막 문자인 경우만 매칭된다.
- `\b` 문자는 단어 경계를 추가한다. `\b` 문자를 단어 어는 쪽이든 위치시키면 정규표현식으로 하여금 변형된 더 긴 단어와 매칭되는 것을 중지시키게 한다. 따라서;
	- 정규표현식 `foobar` 은 `foobar` `666foobar`, `foobar777`, `8thfoobar8th` 등을 매칭시킨다.
	- 정규표현식 `\bfoobar` 은 `foobar`, `foobar777` 등을 매칭시킨다.
	- 정규표현식 `foobar\b` 은 `foobar`, `666foobar` 등을 매칭시킨다.
	- 정규표현식 `\bfoobar\b` 은 `foobar` 을 매칭시키지만, `666foobar`, `foobar777` 등은 매칭되지 않는다.

그렇다면 `^[Oo]rgani.e\b`이 매칭시키는 것은 무엇일까?

> ## 경규표현식에 특수 문자를 사용해서 매칭시키기
> 정규표현식 `^[Oo]rgani.e\b`이 매칭시키는 것은 무엇일까?
>
> > ## 해답
> > ~~~
> > organise
> > organize
> > Organise
> > Organize
> > organife
> > Organike
> > ~~~
> > 즉, `o` 혹은 대문자 `O`로 시작하는 행을 먼저 매칭시키고, `rgani`이 다음에 위치하고 7번째 위치에는 임의 어떤 문자도 상관이 없고, `e` 문자로 끝나는 문자열만 매칭시킨다.
> {: .solution}
{: .challenge}

기타 유용한 특수 문자는 다음과 같다:

- `*` 문자는 선행요소를 0번 혹은 그 이상 매칭시킨다. 예를 들어, `ab*c` 은 "ac", "abc", "abbbc", 등을 매칭시킨다..
- `+` 문자는 선행요소를 한번 이상 매칭시킨다. 예를 들어, `ab+c` 은  "abc", "abbbc"은 매칭시키지만, "ac"은 매칭시키지 않는다.
- `?` 문자는 선행문자가 0번 혹은 1번 출현될 때만 매칭시킨다.
- `{VALUE}` 정규표현식은 VALUE로 정의된 횟수만큼 선행문자를 매칭시킨다; 가령 1-6 범위를 `{VALUE,VALUE}` 구문으로 명세할 수 있다. 예를 들어, 
  `\d{1,9}` 정규표현식은 1에서 9사이 임의 숫자를 매칭시키게 된다. 
- `|` 문자는 "또는" 을 의미한다.
- `/i` 정규표현식은 대소문자 구분하지 않음을 의미한다. (`[A-Za-z]`와 동일)


그렇다면, 다음 정규표현식이 매칭하는 것은 무엇일까요?

> ## ^[Oo]rgani.e\w*
> 정규표현식 `^[Oo]rgani.e\w*` 구문이 매칭하는 것은 무엇일까요?
>
> > ## 해답
> > ~~~
> > organise
> > Organize
> > organifer
> > Organi2ed111
> > ~~~
> > 즉, `o` 혹은 대문자 `O`로 시작하는 행을 먼저 매칭시키고, `rgani`이 다음에 위치하고 7번째 위치에는 임의 어떤 문자도 상관이 없고, `e` 문자가 그 다음에 위치하고,
> > `[A-Za-z0-9]` 범위 문자가 0번 이상 출현하면 된다.
> {: .solution}
{: .challenge}

> ## [Oo]rgani.e\w+$
> 정규표현식 `[Oo]rgani.e\w+$` 구문이 매칭하는 것은 무엇일까요?
>
> > ## 해답
> > ~~~
> > organiser
> > Organized
> > organifer
> > Organi2ed111
> > ~~~
> > 즉, `o` 혹은 대문자 `O`로 시작하는 행을 먼저 매칭시키고, `rgani`이 다음에 위치하고 7번째 위치에는 임의 어떤 문자도 상관이 없고, `e` 문자가 그 다음에 위치하고,
> > `[A-Za-z0-9]` 범위 문자가 **적어도 한번 이상** 출현해야 된다.
> {: .solution}
{: .challenge}

> ## ^[Oo]rgani.e\w?\b
> 정규표현식 `^[Oo]rgani.e\w?\b` 구문이 매칭하는 것은 무엇일까요?
>
> > ## 해답
> > ~~~
> > organise
> > Organized
> > organifer
> > Organi2ek
> > ~~~
> > 즉, `o` 혹은 대문자 `O`로 시작하는 행을 먼저 매칭시키고, `rgani`이 다음에 위치하고 7번째 위치에는 임의 어떤 문자도 상관이 없고, `e` 문자가 그 다음에 위치하고,
> > `[A-Za-z0-9]` 범위 문자가 **0 혹은 1번** 문자로 끝나면 된다.
> {: .solution}
{: .challenge}

> ## ^[Oo]rgani.e\w?$
> 정규표현식 `^[Oo]rgani.e\w?$` 구문이 매칭하는 것은 무엇일까요?
>
> > ## 해답
> > ~~~
> > organise
> > Organized
> > organifer
> > Organi2ek
> > ~~~
> > 즉, `o` 혹은 대문자 `O`로 시작하는 행을 먼저 매칭시키고, `rgani`이 다음에 위치하고 7번째 위치에는 임의 어떤 문자도 상관이 없고, `e` 문자가 그 다음에 위치하고,
> > `[A-Za-z0-9]` 범위에서 나온 문자가 **0 혹은 1번** 출현되야 한다.
> {: .solution}
{: .challenge}

> ## \b[Oo]rgani.e\w{2}\b
> 정규표현식 `\b[Oo]rgani.e\w{2}\b` 구문이 매칭하는 것은 무엇일까요?
>
> > ## 해답
> > ~~~
> > organisers
> > Organizers
> > organifers
> > Organi2ek1
> > ~~~
> > 즉, 단어 경계 다음에 `o` 혹은 대문자 `O`로 시작하는 행을 먼저 매칭시키고, `rgani`이 다음에 위치하고 7번째 위치에는 임의 어떤 문자도 상관이 없고, `e` 문자가 그 다음에 위치하고,
> > `[A-Za-z0-9]` 범위에서 나온 문자가 **2번** 출현되야 한다.
> {: .solution}
{: .challenge}

> ## \b[Oo]rgani.e\b|\b[Oo]rgani.e\w{1}\b
> 정규표현식 `\b[Oo]rgani.e\b|\b[Oo]rgani.e\w{1}\b` 구문이 매칭하는 것은 무엇일까요?
>
> > ## 해답
> > ~~~
> > organise
> > Organi1e
> > Organizer
> > organifed
> > ~~~
> {: .solution}
{: .challenge}

이런 로직이 유용한 경우는 디렉토리에 파일이 아주 많을 때, 파일이 논리적인 파일명을 갖고 있는 경우, 파일 일부에 대해서 격리작업을 수행할 때가 이에 해당된다.
스프레드쉬트 셀에서 특정 값을 찾거나 새로운 칼럼을 생성할 때 스프레드쉬트 칼럼에서 데이터 일부를 추출할 때도 유용하다.
중요한 것은 많은 경우에 대단히 유용하다는 것이다.
그런데, 이런 지식을 내재화하는데 컴퓨터를 사용하지 않고 종이와 연필을 사용할 것이다.


### 연습문제

Work in teams of 4-6 on the exercises below. When you think you have the right answer, check it against the solution. 
아래 연습문제를 해결하는데 4-6명이 팀을 이뤄 진행한다. 정답을 도출했다고 판단되면 `해답`을 열어본다. 

연습문제를 모두 풀게되면 팀을 두 그룹으로 나눠서 서로에게 정규표현식 문제를 만들어 준비한다.
연습문제에는 a) 상대팀이 작성해야 되는 대상 문자열과 함께 b) 상대팀이 작성해야 되는 정규표현식이 담겨져야 한다.

그리고 나서 상대방의 정답과 확인한다. 
정규표현식 로직이 맞는 확인하려면 [regex101](https://regex101.com/), [myregexp](http://myregexp.com/), [regex pal](http://www.regexpal.com/), [regexper.com](http://regexper.com/)을 참조한다; 첫 3개 사이트는 작성한 정규표현식이 매칭하는 문자열을 확인하는데 도움이 되고, 마지막은 정규표현식 동작 흐름을 시각적으로 파악할 수 있게 도움을 줄 수도 있다.


> ## 꺾쇠 괄호 사용
> 정규표현식 `Fr[ea]nc[eh]` 구문이 매칭하는 것은 무엇일까요?
>
> > ## 해답
> > ~~~
> > French
> > France
> > Frence
> > Franch
> > ~~~
> > 해답 앞뒤로 `Francer`, `foobarFrench`, `Franch911`와 같은 단어도 매칭으로 찾아낸다.
> {: .solution}
{: .challenge}

> ## 달러 기호 사용하기
> 정규표현식 `Fr[ea]nc[eh]$` 구문이 매칭하는 것은 무엇일까요?
>
> > ## 해답
> > ~~~
> > French
> > France
> > Frence
> > Franch
> > ~~~
> > 행 끝에 위치한 문자열을 찾아낸다. `foobarFrench`와 같이 앞에 문자가 붙은 단어도 검출해 낸다.
> {: .solution}
{: .challenge}

> ## 선택옵션 도입
> 행 시작지점에 `French`, `France` 문자열과 매칭되는 정규표현식을 작성하시오?
>
> > ## 해답
> > ~~~
> > ^France|^French
> > ~~~
> > `Frenchness`처럼 `French` 다음에 오는 문자도 매칭에 포함된다.
> {: .solution}
{: .challenge}

> ## 대소문자 구분하지 않음
> `colour` , `color` 같이 (대소문자 구분하지 않음) 전체 단어 전체를 매칭하는 정규표현식을 어떻게 작성하는가?
>
> > ## 해답
> > ~~~
> > \b[Cc]olou?r\b|\bCOLOU?R\b
> > /colou?r/i
> > ~~~
> > 실무에서, 대소문자를 구분하지 않는 변형 `colour`, `color`, `Colour`, `Color`, `COLOUR`, `COLOR`이 떠오르지만, `coLour` 유형은 해당되지 않는다.
> > 따라서 지금까지 학습한 것에 기초하여, 나름 합리적인 정규표현식은 `\b[Cc]olou?r\b|\bCOLOU?R\b`와 같이 작성할 수 있다.
> > 지금까지 논의하지 않은 좀더 우아한 선택 옵션은 `/` 구분자를 사용해서 대소문자 구분을 무시하는 플래그를 추가하는 방법이 있다:
> > `/colou?r/i` 정규표현식은 `colour`,  `color` 단어 대해서 대소문자 구분하지 않고 모두 매칭시킨다.
> {: .solution}
{: .challenge}

> ## 단어 경계 
> 전체 단어 `headrest`, `head rest`는 매칭시키지만 `head  rest` 처럼 `head`와 `rest` 공백이 두개 들어간 것은 제외시키는 정규표현식은 어떻게 작성하는가?
>
> > ## 해답
> > ~~~
> > \bhead ?rest\b
> > \bheadrest\b|\bhead\srest\b
> > ~~~
> > `\bhead\s?rest\b` 정규표현식을 통해 매칭이 잘 구현되었지만, `head`와 `rest` 사이 0번 혹은 1회 탭/개행문자를 매칭시킬 수 있다.
> > 그래서, 실무에서 사용해도 괜찮지만, 엄밀하게 따면 옳은 정규표현식은 아니다.
> {: .solution}
{: .challenge}

> ## 비언어적(non-linguistic) 패턴 매칭 
> 0 다음에 문자 4개로 끝나는 문자열을 찾아내는 패턴을 정규표현식으로 나타내시오?
>
> > ## 해답
> > ~~~
> > 0+[A-Za-z]{4}\b
> > ~~~
> {: .solution}
{: .challenge}

> ## 숫자 매칭
> 아무 곳에서나 숫자 4개로 구성된 문자열을 매칭시키는 정규표현식을 작성하시오?
>
> > ## 해답
> > ~~~
> > \d{4}
> > ~~~
> > 주의: 숫자와 문자로 좀더 길게 구성된 문자열 내부 숫자 4개 문자열도 매칭시킨다.
> {: .solution}
{: .challenge}

> ## 날짜 매칭
> 날짜 포맷 `dd-MM-yyyy`을 매칭시키는 정규표현식을 작성하시오?
>
> > ## 해답
> > ~~~
> > \b\d{2}-\d{2}-\d{4}\b
> > ~~~
> > 작업하는 데이터 유형에 따라 단어경계(`\b`)는 제거시킬 수도 있다.
> {: .solution}
{: .challenge}

> ## 다양한 날짜 형식 매칭
> 행 마지막에 위치한 `dd-MM-yyyy`, `dd-MM-yy` 날자 형식을 매칭시키는 정규표현식을 작성하시오?
>
> > ## 해답
> > ~~~
> > \d{2}-\d{2}-\d{2,4}$
> > ~~~
> > 행 말미에 위치한 `31-01-198` 같은 문자열도 매칭시킨다. 따라서 데이터를 확인하고 이와 같은 거짓 양성(false positive)을 제거하도록 정규 표현식을 수정한다.
> > 작업하는 데이터에 따라 정규표현식 시작부에 단어 경계(`\b`)를 추가하는 것도 가능하다.
> {: .solution}
{: .challenge}

> ## 출판 형식 매칭
> `British Library : London, 2015`, `Manchester University Press: Manchester, 1999` 와 같은 출판 형식(publication format)을 매칭시키는 정규표현식을 작성하시오.
>
> > ## 해답
> > ~~~
> > .* ?: .*, \d{4}
> > ~~~
> > 단어 경계 없이 `British` 혹은 `Manchester` 단어 앞에 임의 텍스트를 매칭하는 출판물을 검색할 수 있다. 
> > 그럼에도 불구하고, 정규표현식이 첫번째 매칭에서 나름 좋은 성과를 내고 있지만, 데이터 형태에 따라서 다시 한번 정규표현식을 정교하게 할 필요도 있다.
> {: .solution}
{: .challenge}


### `Regex101.com`, `https://regexr.com/`을 사용한 연습문제

이번 학습에서, 브라우저를 열고, [https://regex101.com](https://regex101.com) 혹은 
[https://regexr.com/](https://regexr.com/) 웹사이트로 이동한다.

[swcCoC.md file](https://github.com/LibraryCarpentry/lc-data-intro/tree/gh-pages/data/swcCoC.md) 파일을 열어서 복사해서 
`Text` 혹은 `TEST STRING` 박스에 붙여넣는다.

정상적으로 동작하는지 파악하기 위해서, 정규표현식 박스에 `community` 문자열을 타이핑해서 입력시킨다.

화면을 살펴보면 `community` 문자열이 6번 매칭된 것이 하이라이트 강조되어 표시되어 있다.


> ## 공백도 고려해보자.
> `community ` 타이핑을 한다. 매칭된 것이 3개 나온다. 왜 6개가 아닐까?
> > ## 해답
> >
> > 'community-led'는 첫 검색에서는 매칭이 되지만, 공백이 반영된 두번째 매칭에서 `-` 문자로 인해 매칭되지 않는다.
> >
> {: .solution}
{: .challenge}

> ## 임의 문자도 고려해 보자
> `community` 표현식에 'community-led'도 매칭되도록 또다른 정규표현식 문자를 추가한다면, 무엇이 될까?
> > ## 해답
> >
> > 아마도 `.`, 따라서 `community.`
> >
> {: .solution}
{: .challenge}

> ## Exploring effect of expressions matching different words
> Change the expression to `communi` you get 13 full matches of several words. Why?
> > ## Solution
> >
> > Because the string 'communi' is present in all of those words, including `communi`cation and `communi`ty. Because the expression does not have a word boundary, this expression would also match in`communi`cado, were it present in this text. If you want to test this, type `incommunicado` into the text somewhere and see if it is found.
> >
> {: .solution}
{: .challenge}

> ## Taking capitalization into consideration
> Type the expression `[Cc]ommuni`. You get 14 matches. Why?
> > ## Solution
> >
> > The word Community is present in the text with a capital `C` and with a lowercase `c` 14 times.
> >
> {: .solution}
{: .challenge}

> ## Regex characters that indicate location
> Type the expression ^[Cc]ommuni. You get no matches. Why?
> > ## Solution
> >
> > There is no matching string present at the start of a line. Look at the text and replace the string after the `^` with something that matches a word at the start of a line. Does it find a match?
> >
> {: .solution}
{: .challenge}

> ## Finding plurals
> Find all of the words starting with Comm or comm that are plural.
> > ## Solution
> > ~~~
> > [Cc]omm\w+s\b
> > ~~~
> > `[Cc]` finds capital and lowercase `c`
> >
> > `omm` is straightforward character matches
> >
> > `\w+` matches the preceding element (a word character) one or more times
> >
> > `s` is a straightforward character match
> >
> > `\b` ensures the 's' is located at the end of the word.
> >
> {: .solution}
{: .challenge}

### Exercise finding Email addresses, Using regex101.com

For this exercise, open a browser and go to [https://regex101.com](https://regex101.com). 

Open the [swcCoC.md file](https://github.com/LibraryCarpentry/lc-data-intro/tree/gh-pages/data/swcCoC.md), copy it, and paste it into the test string box.

> ## Start with what you know
> What character do you know is held in common with all email addresses?
> > ## Solution
> >
> > The '@' character.
> >
> {: .solution}
{: .challenge}

> ## Add to what you know
> The string before the "@" could contain any kind of word character, special character or digit in any combination and length. How would you express this in regex? Hint: often addresses will have a dash (`-`) in them, and the dash is not included in the word character expression (`\w`). How do you capture this in the expression?
> > ## Solution
> > ~~~
> > [\w.-]+@
> > ~~~
> > `\w` matches any word character (including digits and underscore)
> >
> > `\.` matches any character
> >
> > `-` straightforward match, since it is not captured with `\.`
> >
> > `[]` the brackets enclose the boolean string that 'OR' the digits, word characters, characters and dash.
> >
> > `+` matches any word character OR digit OR character OR `-` repeated 1 or more times
> >
> {: .solution}
{: .challenge}

> ## Finish the expression
> The string after the "@" could contain any kind of word character, special character or digit in any combination and length as well as the dash. In addition, we know that it will end with two or three characters after a period (`.`) What expression would capture this. Hint: the `.` is also a regex expression, so you'll have to use the escape `\` to express a literal period. Note: for the string after the period, I did not try to match a character, since those rarely appear in the .xx or .xxx at the end of an email address.
> > ## Solution
> > ~~~
> > [\w.-]+\.[\w]{2,3}
> > ~~~
> > See the previous exercise for the explanation of the expression up to the `+`
> >
> > `\.` matches the literal periond ('.') not the regex expression `.`
> >
> > `\w` matches any word (including digits and underscore)
> >
> > `{2,4}` limits the number of word characters and/or digits to a two or three-character string.
> >
> > `[]` the brackets enclose the boolean string that 'OR' the digits, word characters, characters and dash.
> >
> > `+` matches any word character OR digit OR character OR `-` repeated 1 or more times
> >
> {: .solution}
{: .challenge}

### Exercise finding phone numbers, Using regex101.com

Does this Code of Conduct contain a phone number?

What to consider:
1. It may or may not have a country code, perhaps starting with a "+"
2. It will have an area code, potentially enclosed in parens
3. It may have the sections all separated with a "-"

> ## Start with what you know: find strings of digits
> Start with what we know, which is the most basic format of a phone number: three digits, a dash, and four digits. How would we write a regex expression that matches this?
> > ## Solution
> > ~~~
> > \d{3}-\d{4}
> > ~~~
> > `\d` matches digits
> >
> > `{3}` matches 3 digits
> > 
> > `-` matches the character '-'
> >
> > `\d` matches any digit
> >
> > `{4}` matches 4 digits.
> > 
> >This expression should find three matches in the document.
> {: .solution}
{: .challenge}

> ## Match a string that includes an area code with a dash
> Start with what we know, which is the most basic format of a phone number: three digits, a dash, and four digits. How would we expand the expression to include an area code (three digits and a dash)?
> > ## Solution
> > ~~~
> > \d{3}-\d{3}-\d{4}
> > ~~~
> > `\d` matches digits
> >
> > `{3}` matches 3 digits
> > 
> > `-` matches the character '-'
> >
> > `\d` matches any digit
> >
> > `{4}` matches 4 digits.
> >
> >This expression should find one match in the document
> {: .solution}
{: .challenge}

> ## Match a string that includes an area code within parenthesis separated from the rest of the phone number with a space or without a space
> Start with what we know, which is the most basic format of a phone number: three digits, a dash, and four digits. How would we expand the expression to include a phone number with an area code in parenthesis, separated from the phone number, with or without a space.
> > ## Solution
> > ~~~
> >\(\d{3}\) ?\d{3}-\d{4}
> > ~~~
> > `\(` escape character with the parenthesis as straightforward character match
> >
> > `\d` matches digits
> >
> > `{3}` matches 3 digits
> > 
> > `\)` escape character with the parenthesis as a straightforward character match
> >
> > ` ?` matches zero or one spaces
> > 
> > See the previous exercise for the explanation of the rest of the expression.
> > 
> > This expression should find two matches in the document.
> {: .solution}
{: .challenge}

> ## Match a phone number containing a country code.
> Country codes are preceded by a "+" and can have up to three digits. We also have to consider that there may or may not be a space between the country code and anything appearing next.
> > ## Solution
> > ~~~
> >\+\d{1,3} ?\(\d{3}\)\s?\d{3}-\d{4}
> > ~~~
> > `\+` escape character with the plus sign as straightforward character match
> >
> > `\d` matches digits
> >
> > `{1,3}` matches 1 to 3 digits
> >
> > ` ?` matches zero or one spaces
> > 
> > See the previous exercise for the explanation of the rest of the expression.
> > 
> > This expression should find one match in the document.
> {: .solution}
{: .challenge}

One of the reasons we stress the value of consistent and predictable directory and filenaming conventions is that working in this way enables you to use the computer to select files based on the characteristics of their file names. For example, if you have a bunch of files where the first four digits are the year and you only want to do something with files from '2017', then you can. Or if you have 'journal' somewhere in a filename when you have data about journals, you can use the computer to select just those files. Equally, using plain text formats means that you can go further and select files or elements of files based on characteristics of the data *within* those files.

> ## Extracting a substring in Google Sheets using regex
> 1. Export the the [2014 Public Library Survey](https://data.imls.gov/Public-Libraries-Survey/Main-Libraries-Branches-and-Bookmobiles-FY-2014-Pu/ucdn-7aur/data) from the IMLS data site as a CSV file.
> 2. Upload to Google Sheets and open as a Google Sheet if it doesn't do this by default.
> 3. Look in the `LOCATION` column and notice that the values contain the latitude and longitude in parenthesis after the library address.
> 4. Construct a regular expression to match and extract the latitude and longitude into a new column named 'latlong'. HINT: Look up the function `REGEXEXTRACT` in Google Sheets. That function expects the first argument to be a string (a cell in `LOCATION` column) and a quoted regular expression in the second.
>
>> ## Solution
> > This is one way to solve this challenge. You might have found others. Inside the cell you can use the below to extract the Latitude and Longitude into a single cell. You can then copy the formula down to the end of the column.
>>~~~
> > =REGEXEXTRACT(G2,"\d+\.\d+, -?\d+\.\d+")
> >~~~
> >{: .source}
> > Here we are using `\d+` for a one or more digit match followed by a period `\.`. Note we had to escape the period using `\`. After the period we look for one or more digits  `\d+` again followed by a literal comma `,`. We then have a literal space match followed by an optional dash `-` (there are few `0.0` Latitude/Longitudes that are probably errors, but we'd want to retain so we can deal with them). We then repeat our `\d+\.\d+` we used for the Latitude match.
> {: .solution}
{: .challenge}
