프로젝트 이름 : O'Kitchen <br />
사용된 도구 : PWA, JavaScript, Swiper, HTML, CSS <br />
사용환경 : Mobile <br />
:point_right: [O'Kitchen](https://kkii0801.github.io/O_Kitchen/)

***

## 주요 인터렉션 설명

1. 메인 상품 페이지 Swiper 구축하기
2. Google Maps API 적용하기
3. PWA로 빌드하기

***

## 메인 상품 페이지 Swiper 구축하기

### 동작 예시
![images](https://github.com/kkii0801/Readme_files/blob/main/images_2/Okitchen_mainslider.gif?raw=true)

### 코드 설명
``` HTML

```

``` JavaScript

```


***

## Google Maps API 적용하기

### 동작 예시
![images](https://github.com/kkii0801/Readme_files/blob/main/images_2/Okitchen_map.gif?raw=true)

### 코드 설명
``` JavaScript
let map;
```
let map; 변수를 선언합니다. 이 변수는 Google Maps 객체를 저장하는 데 사용됩니다. <br />
``` JavaScript
function initMap(){
	let myLatLng={lat: 37.390141551118695, lng: 126.97151846772532};
```
initMap 함수는 지도를 초기화하는 역할을 합니다. 이 함수는 Google Maps API에서 호출됩니다. <br />
myLatLng 객체는 위도(lat)와 경도(lng)를 포함하여 지도의 중심점을 정의합니다. 여기서는 (주)오뚜기의 위치를 나타냅니다.
```
	let map=new google.maps.Map(document.getElementById("map"), {
		center: myLatLng,
		zoom: 16,
		mapTypeControl: false,
		zoomControl: false,
		fullscreenControl: false,
		rotateControl: false
	});
```
google.maps.Map 객체를 생성하여 map 변수에 저장합니다. <br />
document.getElementById("map")는 HTML에서 id가 map인 요소를 선택합니다. <br />
center는 지도의 중심을 설정하고, zoom은 확대/축소 수준을 지정합니다 (16은 상당히 가까운 확대 수준). <br />
mapTypeControl, zoomControl, fullscreenControl, rotateControl은 각각 지도 유형, 확대/축소, 전체 화면, 회전 컨트롤을 사용할지 여부를 설정하는 옵션입니다.
``` JavaScript
	let marker=new google.maps.Marker({
		position: myLatLng,
		map: map,
		title: "(주)오뚜기"
	});
}
```
google.maps.Marker 객체를 생성하여 마커를 추가합니다. <br />
position은 마커가 위치할 좌표를 설정합니다. <br /> 
map은 마커가 표시될 지도를 지정합니다. <br />
title은 마커에 마우스를 올렸을 때 표시될 텍스트입니다.
***

## PWA로 빌드하기

### PWA란?
HTML, CSS, JavaScript와 같은 웹 기술로 만드는 앱입니다. <br />
네이티브 앱을 개발하는 것은 상당히 어렵지만, PWA는 훨씬 더 빠르게 개발할 수 있습니다. <br />
또한, 푸시 알림이나 오프라인 지원과 같은 네이티브 앱의 특징들도 전부 제공할 수 있습니다.

### PWA 제작 방법
1. 기존 html source(favicon.icon 필요)를 git에 커밋을 해준 다음에, PWA를 지원해주는 사이트([PWABuilder](https://www.pwabuilder.com/))에 접속해줍니다.
2. repository 링크를 입력하고, Manifest 설정을 작성해주고 다운로드 해줍니다. (이미지 파일 변환 必)
    Name : O'Kicten <br />
    Short Name : 오‘키친 <br />
    Id : kkii0801 <br />
    Description : 쉽고 간편하게 따라할 수 있는 맛있는 요리가 한가득! 오뚜기의 레시피 앱 오'키친에 놀러오세요. <br />
    Background Color : #FFFFFF, StyleSheet가 로드되기 전의 배경색입니다. <br />
    Theme Color : #FFFFFF, 앱의 기본 테마 색상입니다. <br />
    Start URL : https://kkii0801.github.io/O_Kitchen/, 앱이 시작되어야 하는 위치를 지정합니다. <br />
    사용자들이 PWA에서 원하는 특정한 페이지에서 시작하도록 설정하는 것이 좋습니다. <br />
    Scope : /, 사용자가 볼 수 있는 앱 페이지를 제한합니다. <br />
    Language : Korean <br />
    Orientation : Portrait <br />
    Display : standalone, 보여주고 싶은 브라우저 UI의 타입을 설정할 수 있습니다. 설정할 수 있는 옵션으로는 fullscreen(전체 화면), <br />
    standalone(네트워크에 연결되지 않은 상태에서도 스스로 동작할 수 있는 것), minimal-ui(최소화된 UI), browser(브라우저 표준 인터페이스)가 있습니다.
3. Manifest.json와 image source 파일의 icon.json 내부의 이미지 경로를 현 폴더 상황에 맞게 수정, index.html에도 Manifest.json 경로를 설정해줍니다. (<link rel="manifest" href="manifest.json">) <br />
4. 올바르게 수정했으면 커밋 후 사이트가 정상 구동하는지 확인해줍니다.

### Service Worker란? 
Service Worker는 백그라운드에서 실행되는 Javascript입니다. 오프라인 환경에서도 웹이 작동할 수 있도록 네트워크 요청을 가로채서 네트워크 불량 상태 등 접속 환경이 안 좋은 상황을 대처합니다.<br /> 

### Service Worker 작성 방법
1. Generate Service Worker 버튼을 클릭하여, js 파일을 다운로드 받습니다.
2. pwabuilder-sw.js 파일을 수정해서 offline.html을 연결합니다.
   ```const offlineFallbackPage="offline.html";```
3. 오프라인일 경우 연결된 offline.html을 생성합니다.
   ```
   <!DOCTYPE html>
   <html lang="ko">
   <head>
   <title>오'키친</title>
   <meta charset="utf-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1">
   <head>
   <body>
   <p>인터넷 연결이 되지 않았습니다.</p>
   </body>
   </html>
   ```
4. pwabuilder-sw.js 파일을 추가하기 위해 index.html를 수정합니다.
   ```
   <script type="module">
   if("serviceWorker" in navigator){
   navigator.serviceWorker.register("pwabuilder-sw.js")
   .then(function(registration){
   // console.log("Service Worker Success", registration);
   })
   .catch(function(error){
   // console.error("Service Worker Fail", error);
   });
   }
   </script>
   ```
위 과정을 정상적으로 진행하고, 사이트 접속시 정상적으로 빌드 됐다면 아래와 같이 작동하는 것을 볼 수 있습니다.
![images](https://github.com/kkii0801/Readme_files/blob/main/images_2/OKitchen_PWA.PNG?raw=true)
