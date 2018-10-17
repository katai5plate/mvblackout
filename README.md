# mvblackout
blank project of rpgmv

# Usage
1. Access this page:
https://katai5plate.github.io/mvblackout/

2. Open the Console on DevTools.

3. Paste this code:
```js
var __draw = () => {}; // Coding the drawing process here
var __debug = ctx => ["hi"]; // Coding the process to send log when pressing control/alt key here (for debugging)

const [__sw, __sh] = [SceneManager._screenWidth, SceneManager._screenHeight];
let __u = Game_Screen.prototype.update, __reference = null; Game_Screen.prototype.update = function () {
  const ly = 'mvblackout', sm = SceneManager; __u.apply(this);
  sm._scene[ly] || sm._scene.addChild(sm._scene[ly] = new Sprite(new Bitmap(__sw, __sh)));
  const { bitmap } = sm._scene[ly], { context } = bitmap, ctx = context;
  __reference || (()=>{__reference = ctx})();
  bitmap.clear(); ctx.textBaseline = 'top', ctx.strokeStyle = 'white', ctx.fillStyle = 'white';
  __draw(ctx), Input.isPressed('control') && console.log(...__debug(ctx));
}, $gameSystem._menuEnabled = false, Scene_Map.prototype.processMapTouch = () => {},
document.body.style.backgroundColor = "gray";
```

4. Play. example:
```js
__draw = ctx => {
  ctx.beginPath();
  ctx.moveTo(10, 10);
  ctx.lineTo(90, 90);
  ctx.stroke();
}
__debug = () => [TouchInput.x, TouchInput.y];
```
```js
console.log({__reference});
```

# default preference
## game
- menuEnabled: false
- processMapTouch: disable
- documentBodyColor: gray
## context
- textBaseline: top
- strokeStyle: white
- fillStyle: white
