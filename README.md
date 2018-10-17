# mvblackout
blank project of rpgmv https://katai5plate.github.io/mvblackout/

```
var [width, height] = [SceneManager._screenWidth, SceneManager._screenHeight]

var draw = () => {};

var __u = Game_Screen.prototype.update, __reference = null;
Game_Screen.prototype.update = function () {
  var drawId = "test";
  __u.apply(this);
  if (!SceneManager._scene[drawId]) {
    SceneManager._scene[drawId] = new Sprite();
    SceneManager._scene[drawId].bitmap = new Bitmap(width, height);
    SceneManager._scene.addChild(SceneManager._scene[drawId]);
  }
  const { bitmap } = SceneManager._scene[drawId], { context } = bitmap;
  bitmap.clear();
  // context.textBaseline = 'top';
  if(!__reference) __reference = context;
  draw(context);
}
```
