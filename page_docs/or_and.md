## and, or 그리고 삼항연산자는 무엇인가
###### 부제 : if 를 대신하는 연산자들 [샘플]
###### 작성 ; Qwreey | 작성일 : 2021 1/11 
---
주요 목차 :
 - [and 은 무엇인가](#what_is_and)
 - [or 은 무엇인가](#what_is_or)
---
### and 란? <a name="what_is_and"></a>
and 는 중요한 논리 연산자중 하나로써 lua 에서는 if 만큼이나 많이 쓰이는 연산자 입니다 

and 는 앞에 값과 뒤에 값을 주었을 때, 두 값이 모두 nil,false<sup>[참조1](#footnote_1)</sup> 이 아니라면 뒤에값을 반환합니다 그렇지 않으면 nil 또는 false 을 반환합니다 

이 예제를 실행하여 테스트 해볼 수 있습니다
```lua
print(true and 5) -- 5
print(1 and true) -- true
print(0 and true) -- true (0 도 true 취급)
print(true and "Hello world") -- 'Hello world'
print({} and true) -- true 

-- false(nil,false) 을 반환하는것들
print(nil and false) -- nil (앞에꺼)
print(false and false) -- false (앞에꺼)
print(false and nil) -- false (앞에꺼)
print(false and 1) -- false
print(1 and nil) -- nil
print(1 and false) -- false
```
<!-- 접을 수 있는 라벨 -->
<details>
<summary>출력(output) > </summary>
<div markdown="1">

> Info : Lua 5.3.5<br/>
> 5<br/>
> true<br/>
> true<br/>
> Hello world<br/>
> true<br/>
> nil<br/>
> false<br/>
> false<br/>
> false<br/>
> nil<br/>
> false<br/>

</div>
</details>

and 는 이러한 특성상 if 를 합쳐지도록 만들 수 있습니다
```lua
if (조건문) and (조건문) and (조건문) ... then
```
다음과 같이 and 로 무수히 많은 조건문을 합칠 수 있습니다
이 방법은 if 를 여러번 사용하는것 보다 더 깔끔하기에 많이 사용됩니다
```lua
local Apple = {
   type = "fruit";
   from = "earth";
   cost = nil;
} 

-- and 로 합치지 않은 조건문
if Apple.type == "fruit" then
   if Apple.from == "earth" then
      print("이 사과는 지구에서 온 과일이다")
   end
end 

-- and 로 합친 조건문
if Apple.type == "fruit" and Apple.from == "earth" then
   print("이 사과는 지구에서 온 과일이다")
end
```
<!-- 접을 수 있는 라벨 -->
<details>
<summary>출력(output) > </summary>
<div markdown="1">

> Info : Lua 5.3.5<br/>
> 이 사과는 지구에서 온 과일이다<br/>
> 이 사과는 지구에서 온 과일이다<br/>

</div>
</details>

---
### or 이란? <a name="what_is_or"></a>
or 도 and 와 마찬가지로 논리 연산자중 하나로써 lua 에서 많이 사용되는 연산자 입니다 

or 은 뒤에 있는 값과는 상관 없이 앞에 있는 값이 nil,false[참조1] 이 아니라면 앞에 있는 값을 반환하고 그렇지 않다면 뒤에 있는 값을 반환합니다 

이 예제를 실행하여 테스트 해볼 수 있습니다
```lua
print(1 or true) -- 1
print(false or nil) -- nil
print(false or false) -- false
print(nil or "Hello world") -- 'Hello world'
print("Cookie" or nil) -- 'Cookie'
```
<!-- 접을 수 있는 라벨 -->
<details>
<summary>출력(output) > </summary>
<div markdown="1">

> Info : Lua 5.3.5<br/>
> 1<br/>
> nil<br/>
> false<br/>
> Hello world<br/>
> Cookie<br/>

</div>
</details>

<!-- 각주 부분 -->
 <a name="footnote_1">[참조 1]</a> : lua 에서는 nil 과 false 을 제외한 모든것(0 을 포함한 모든 숫자,문자열,테이블,유저데이터(Instance...),true, 등등) 을 true 처럼 취급합니다.