# the-original-movie-app

-------------------------------
## 0. 프로젝트 세팅

### 새로 알 수 있었던 점 && 진행하면서 겪었던 이슈
version catalog로 의존성 관리하는 법을 알 수 있었다.
version catalog를 처음 사용해보기 때문에 coil 라이브러리를 추가하는 과정에서 아래 코드와 같이 추가하면서 낭패를 봤다...
```
coil = {group = "io.coil-kt:coil-compose", name = "coil-compose", version.ref = "coil-compose" }
```

이렇게 구성하면 문제가 되는 이유는 implementation하게 될 때 io.coil-kt:coil-compose:coil-compose:2.5.0 이렇게 implementation 되버린다는 점.
당연히 Could not found가 뜨게된다.
group에 namespace명을 입력하고, name에 module명을 입력해야한다는 것을 새롭게 알았다.

```
coil = {group = "io.coil-kt", name = "coil-compose", version.ref = "coil-compose" }
```
위처럼 바꿔서 작성하니 잘 작동하는 것을 확인할 수 있었다!


```
// + build.gradle.kts에서는 이렇게 작성해야한다!
implementation(libs.coil)
```
