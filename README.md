# mvblackout
blank project of rpgmv https://katai5plate.github.io/mvblackout/

```js
const [__sw, __sh] = [SceneManager._screenWidth, SceneManager._screenHeight]

var __draw = () => {};

let __u = Game_Screen.prototype.update, __reference = null;
Game_Screen.prototype.update = function () {
  const drawId = 'test';
  __u.apply(this);
  if (!SceneManager._scene[drawId]) {
    SceneManager._scene[drawId] = new Sprite();
    SceneManager._scene[drawId].bitmap = new Bitmap(__sw, __sh);
    SceneManager._scene.addChild(SceneManager._scene[drawId]);
  }
  const { bitmap } = SceneManager._scene[drawId], { context } = bitmap;
  bitmap.clear();
  // context.textBaseline = 'top';
  context.strokeStyle = 'white';
  context.fillStyle = 'white';
  if(!__reference) __reference = context;
  __draw(context);
}
```
