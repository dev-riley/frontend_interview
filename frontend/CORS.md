# CORS

Cross-Origin Resource Sharing (교차 출처 리소스 공유 정책)

다른 출처를 가진 HTTP요청을 제한하는 브라우저 보안 기능이다. 여기서 출처(Origin)란,  protocol + Host + Port 까지 모두 합친 URL을 말합니다. 다른 출처에 대해서 허용을 하려면 서버측에서 클라이언트의 요청에 대한 응답헤더에 Access-Control-Allow-Origin이라는 필드를 추가하고 값으로 '이 리소스를 접근하는 것이 허용된 출처  url'을 내려보낸다.

다른 출처의 리소스 공유에 대한 허용/비허용 정책

