## HTTP 상태 코드란?

클라이언트가 보낸 HTTP 요청에 대한 서버의 응답 코드

상태 코드에 따라 요청의 성공/실패 여부를 세 자릿수로 구분한다.

</br>

### HTTP 상태 코드 분류

| 분류                           | 내용                                                                                                                       |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| 1xx Informational(조건부 응답) | 클라이언트가 서버에 정보를 요청했지만 해당 요청이 여전히 처리 중임을 나타낸다. (해당 상태 코드는 접할 일이 많지는 않다.)   |
| 2xx Successful (성공)          | 서버가 브라우저의 요청을 성공적으로 받고, 처리했음을 나타낸다.                                                             |
| 3xx Redirection (리디렉션)     | 서버가 요청된 페이지가 일시적으로 또는 영구적으로 이동되었음을 클라이언트에 알릴 때 나타낸다.                              |
| 4xx Client Error (요청 오류)   | 클라이언트의 잘못된 요청으로 서버가 이해를 못해 요청을 수행할 수 없음을 나타낸다.                                          |
| 5xx Server Error (서버 오류)   | 클라이언트가 특정 리소스에 대한 액세스를 요청하고 성공했지만 서버 오류로 인해 서버가 요청을 정상 처리하지 못함을 나타낸다. |

</br>

### SEO에서 흔하게 접하는 HTTP 상태코드 6가지

- 200 OK
- 301 (Moved Permanently)
- 302 (Found / Moved Temporarily)
- 404 (Not Found)
- 500 (Server Error)
- 503 (Service Unavailable)

### 200 OK

의미 - 클라이언트의 요청이 성공적으로 수신되었음을 클라이언트에 알리고 요청된 내용으로 응답

즉, 모든 것이 정상적으로 작동되었음

SEO 측면의 의미 - 페이지가 완벽하게 로딩되었음. SEO에서 추가적인 작업이 필요하지 않음

### 301 (Moved Permanently)

의미 - URL이 영구적으로 다른 위치로 이동했음을 뜻한다. 해당 요청 및 이후의 모든 요청은 다른 URL로 리디렉션 되어야한다.

SEO 측면의 의미 - 검색 엔진이 이전 페이지의 페이지 순위 및 링크에 대한 점수가 새 페이지로 전달한다. 위치 변경이 일시적일 때는 이전 URL 위치로 회귀하는 경우 더 이상 페이지 순위나 링크에 대한 점수가 매겨지지 않기 때문에 301코드를 사용하면 안된다.

### 302 (Found / Moved Temporarily)

의미 - URL이 일시적으로 다른 위치로 이동했음을 뜻한다.

많은 시간이 지나면 검색 엔진에서 302 리다이렉트를 301 리다이렉트로 처리할 수 있다.

SEO 측면의 의미 - 일시적인 특성상 리디렉션된 URL의 페이지 순위나 링크에 대한 점수는 대상 URL로 전달되지 않으며 리디렉션된 URL은 통합되지 않은채로 순위가 매겨진다.

### 404 (Not Found)

의미 - 요청된 리소스를 찾을 수 없음을 나타냄.

즉, 클라이언트는 서버와 통신할 수 있지만 서버 측에선 클라이언트가 요청한 바를 찾을 수 없다는 뜻.

### 500 (Server Error)

의미 - 서버가 사용자의 리소스 요청을 처리할 수 없을 때 나타냄. 서버 구성 에러로 인해 발생하는 일반적인 에러

SEO 측면의 의미 - 내부 서버 오류는 특히 상황이 한동안 감지되지 않을 경우 SEO에 매우 강력하고 부정적인 영향을 미친다.

### 503 (Service Unavailable)

의미 - 서버를 현재 사용할 수 없으며 그 결과 클라이언트의 요청을 처리할 수 없음을 나타냄.

404에러는 한개의 페이지에서 일어나고, 503에러는 웹사이트 전체에 영향을 준다.

SEO 측면의 의미 - 503상태가 지속되면 검색 엔진의 인덱스에서 URL이 제거되어 SEO에 심각한 영향을 미침

</br>
</br>
</br>

모든 HTTP 상태코드

https://www.whatap.io/ko/blog/40/

</br>

참고 사이트

https://seo.tbwakorea.com/blog/what-is-http-status-code/