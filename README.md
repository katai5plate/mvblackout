# mvblackout
blank project of rpgmv

# Usage
1. Access this page:
https://katai5plate.github.io/mvblackout/

2. Open the Console on DevTools.

3. Paste this code:
```js
var __draw = () => {}; // Coding the drawing process here

const [__sw, __sh] = [SceneManager._screenWidth, SceneManager._screenHeight]
let __u = Game_Screen.prototype.update, __reference = null;
Game_Screen.prototype.update = function () {
  __u.apply(this); const ly = 'test', sm = SceneManager; if (!sm._scene[ly]) {
    sm._scene[ly] = new Sprite(), sm._scene[ly].bitmap = new Bitmap(__sw, __sh);
    sm._scene.addChild(sm._scene[ly]);
  } const { bitmap } = sm._scene[ly], { context } = bitmap, ctx = context;
  __reference || (()=>{__reference = ctx})();
  bitmap.clear(); ctx.textBaseline = 'top', ctx.strokeStyle = 'white', ctx.fillStyle = 'white';
  __draw(ctx);
}
```

4. Play. example:
```js
__draw = ctx => {
  ctx.beginPath();
  ctx.moveTo(10, 10);
  ctx.lineTo(90, 90);
  ctx.stroke();
}
```
