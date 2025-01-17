# three.js

### 고해상도 화면에서 canvas 화질이 떨어져보이는 이유

HD-DPI는 고해상도(high-density dot per inch)의 줄임말이다. HD-DPI와 같은 고해상도 화면에서는 CSS 픽셀과 물리적 픽셀의 비율이 `window.devicePixelRatio`에 의해 달라진다.

Three.js에서 캔버스가 기본적으로 CSS 크기를 기준으로 렌더링되면, 고해상도 화면에서 픽셀 밀도 차이로 인해 이미지가 흐릿하게 보일 수 있다.

```js
const pixelRatio = window.devicePixelRatio;
const width = Math.floor(canvas.clientWidth * pixelRatio);
const height = Math.floor(canvas.clientHeight * pixelRatio);
```

`pixelRatio`를 활용해 캔버스의 물리적 크기를 조정하면, 디스플레이의 실제 픽셀 밀도에 맞춰 더 선명한 렌더링을 제공할 수 있다.

즉, 디스플레이 해상도에 따른 렌더링 품질을 최적화하기 위해 위 코드를 추가해주는 것
