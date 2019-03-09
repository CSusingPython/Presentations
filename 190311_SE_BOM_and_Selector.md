# 브라우저 객체 (Browser Object Model, BOM)와 선택자 (Selector)
## 브라우저 객체 (Browser Object Model, BOM)


![BOM](./data/images/BOM.jpg)


* ```window``` 객체
* 클라이언트 측 자바스크립트 전역 객체
* 함수 안에서를 제외하고 ```this```는 ```window``` 객체 의미
* 생략하여 사용 가능 e.g. window.alert() = alert()
* BOM을 알면 자바스크립트로 자유롭게 브라우저를 조작할 수 있음

## 문서 객체 모델 (Document Object Model, DOM)


![DOM](./data/images/DOM.gif)


* HTML의 각 구성요소를 메모리상 객체로 생성하고, 객체들 간 관계를 계층 구조로 표현한 모형
* 종류
  
![DOM types](./data/images/DOM-types.png)

## 바닐라스크립트로 DOM 조작하기
```
// 엘리먼트 선택
document.getElementById('id') // 하나의 엘리멘트만 반환
document.getElementsByClassName('class') // 여러 개 엘리먼트 반환, return[index] 또는 return.item(index)로 가져올 수 있음
document.getElementsByName('name')
document.getElementsByTagName('tag')

// 엘리먼트 생성
document.createElement('tagname');

// 텍스트 노드 생성
document.createTextNode('text');

// 노드 연결
parent-element.appendChild(child-element);

// 노드 연결 해제
parent-element.removeChild(child-element);

// 속성 추가
element.setAttribute('attribute-name','value');
```

## 선택자 (Selector)
* Jquery 사용 또는 Selenium을 이용한 웹 스크래핑 시 유용
* CSS 선택자 ([출처](https://www.w3schools.com/cssref/css_selectors.asp))
  * CSS에서 엘리먼트 선택 시 사용


CSS 선택자|설명
------|----
```.class```|클래스 선택자, 클래스는 한 문서 안에 여러 개 사용 가능
```#id```|아이디 선택자, 아이디는 한 문서 안에서 유일하게 사용 (여러 개 사용 시 ```warning```)
```element```|엘리먼트 선택자
```element1 element2```|element1의 자손 element2 (손자 엘리먼트도 선택 가능)
```element1>element2```|element1의 자식 element2 (바로 아래 자식만 선택 가능)
```element1+element2```|element1의 동생 element2
```element1~element2```|element1의 형 element2
```[attribute]```|해당 속성의 엘리먼트
```[attribute=value]```|특정 속성값의 엘리먼트
```[attribute~=value]```|특정 속성값을 포함하는 엘리먼트 (```[attribute~=ba]```일때 ```element[attribute=ba]```만 선택 가능)
```[attribute|=value]```|특정 속성값으로 시작하는 엘리먼트 (```[attribute|=foo]```일때 ```element[attribute=foo]``` 또는 ```element[attribute=foo-bar]```만 선택)
```[attribute^=value]```|특정 속성값으로 시작하는 엘리먼트 (```[attribute^=foo]```일때 ```element[attribute=foobar]``` 선택 가능)
```[attribute$=value]```|특정 속성값으로 끝나는 엘리먼트
```[attribute*=value]```|특정 속성값을 포함하는 엘리먼트 (```[attribute*=ba]```일때 ```element[attribute=bar]``` 선택 가능)
```:first-child```|첫 번째 자식 선택
```:last-child```|마지막 자식 선택
```:nth-child(n)```|n번째 자식 선택


* XPath
  * XML 경로 표현
  * 웹 페이지에서 id, class 등으로 요소 (element)를 찾지 못할 때 사용

표현|설명
----|----
```노드명```|해당 노드명의 노들를 모두 선택
```/```|루트 노드 (root node)부터 선택
```//```|선택된 노드와 그 후손 노드들 안에서 지정한 노드를 선택
```.```|현재 노드 선택
```..```|현재 노드의 부모 노드 선택
```@```|속성 (attribute) 선택
 
* CSS <> XPath ([출처](https://stackoverflow.com/questions/16347121/selenium-looking-for-examples-of-converting-xpath-locators-to-css))
```
//ul[contains(@id,'district-switcher')]//li/ul/li[4]/a
css=ul#district-switcher li > ul > li:nth(3) > a

//ul[contains(@id,'district-switcher')]//a[contains(text(),'District Management Council')]
css=ul#district-switcher a:contains('District Management Council')

//ul[contains(@id,'district-switcher')]//a[contains(text(),'${QA_run_number}')]
css=ul#district-switcher a:contains('${QA_run_number}')

//h3[contains(@id,'active-district')]
css=h3#active-district

//ul[contains(@class,'home-menu')]//a[contains(text(),'Calendar')]
css=ul.home-menu a:contains("Calendar")

//tr[1]//td[contains(@class,'starts_on')]
css=tr td.starts_on

//tr[1]//td[contains(@class,'ends_on')]
css=tr td.ends_on

//ul[contains(@class,'home-menu')]//a[contains(text(),'Schools')]
css=ul.home-menu a:contains('Schools')

//table[contains(@id, 'schools')]//tbody//tr//td/a
css=table#schools tbody tr td a

//a[contains(text(),'6DAYERS')]
css=a:contains('6DAYERS')

//ul[contains(@class,'home-menu')]//a[contains(text(),'Students')]
css=ul.home-menu a:contains(Students)

//body//td[contains(text(),'QA-001')]
css=td:contains('QA-001')

//ul[contains(@class,'home-menu')]//a[contains(text(),'Roles')]
css=ul.home-menu a:contains(Roles)

//table//tr//td[contains(text(),"Language Therapist")]
css=table tr td:contains(LanguageTherapist)

//table//tr//td[contains(text(),"Speech Therapist")]
css=table tr td:contains(Speech Therapist )

//table//tr//td[contains(text(),"DELETE_ME")]
css=table tr td:contains(DELETE_ME)

//ul[contains(@class,'home-menu')]//a[contains(text(),'Activities')]
css=ul.home-menu a:contains(activities)

xpath=(//li[contains(@id,'activity_roles_input')]//input[@type="checkbox"][1])
css=li#activity_roles_input input[@type="checkbox"]:nth(0)

//table[contains(@id,'activities')]//tr//td[contains(text(),"Activity001")]
css=table#activities tr td:contains("Activity001")

//ul[contains(@class,'home-menu')]//a[contains(text(),'Practitioners')]
css=ul.home-menu a:contains(Practitioners)

//table//tr//td[contains(text(),'mdurrant+${QA_run_number}_001@dmcouncil.org')]
css=table tr td:contains(mdurrant+${QA_run_number}_001@dmcouncil.org)

//ul[contains(@class,'home-menu')]//a[contains(text(),'Topics')]
css=ul.home-menu a:contains(Topics)

xpath=(//li[contains(@id,'topic_roles_input')]//input[@type="checkbox"])[1]
css=li#topic_roles_input input[type=checkbox]:nth(0)

//a[contains(text(),'Topic001')]
link=Topic001

//ul[contains(@class,'home-menu')]//a[contains(text(),'Settings')]
link=Settings

//ul[contains(@class,'home-menu')]//a[contains(text(),'Settings')]
css=ul.home-menu a:contains(Settings)

xpath=(//li[contains(@id,'setting_roles_input')]//input[@type="checkbox"])[1]
css=li#setting_roles_input input[type=checkbox]:nth(0)

xpath=(//table/tbody/tr//td/a[contains(@class,'delete_link')])
table > tbody > tr td > a.delete_link

//td[contains(text(),'Setting001')]
css=td:contains('setting001')
```