## 碰撞架構
### `interface Collider`

### `class CircleCollider implements Collider`

.field
- `private int radius`

.method
- `CircleCollider(int radius)`
- `public int getRadius()`

### `class RectangleCollider implements Collider`

.field
- `private int leftTopX`
- `private int leftTopY`
- `private int rightBottomX`
- `private int rightBottomY`
	- 一個方形包含兩個點，左上與右下，紀錄的值為與中心點的差值

.method
- `RectangleCollider(int leftTopX, int leftTopY, rightBottomX, rightBottomY)`
- `public int getleftTopX()`
- `public int getleftTopY()`
- `public int getrightBottomX()`
- `public int getrightBottomY()`

### `class Utils`


.method
- `public static void calculateCollide(CollideObject[] CollideObjects)`
	- require CollideObject.getPosition()
	- require CollideObject.onCollide()
	- require EntriesManager.getCollideObjects()

#### Usage
Define a Collider in CollideObject's field and initial it in `CollideObject()`using `new CircleCollider(int radius)`or `new RectangleCollider(int leftTopX, int leftTopY, rightBottomX, rightBottomY)`.

To calculate collide using `Utils.calculateCollide(EntriesManager.getCollideObjects())`
