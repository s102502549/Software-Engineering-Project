# 碰撞架構

Package: Collide  

	interface Collidable
		void onCollide(CollidableObject source)

	class Collider
		Vertex center	{get, set}
		float radius		{get, set}
		Vertex[] vertices		{get, set}
		
		Collider(Vertex center, float radius)
		Collider(Vertex center , Vertex[] vertices)
		

	abstract class CollidableObject implements Collidable
		Collider collider		{get}

		CollidableObject(Collider collider)
		abstract void onCollide(CollidableObject source)
	
	class Utils
		boolean checkCollide(CollidableObject a, CollidableObject b)
		void calculateCollide(CollidableObject myself, CollidableObject[] others)


### 說明  
class Collider  
Collider定義一個碰撞物件的形狀，目前支援圓形，及凸多邊形，需要注意的是vertices是相對於center的座標，例如一個三角形，頂點為(0,1), (-1,0), (1,0)，center假設是(0.5,0.5) 則vertices應為(-0.5,0.5),(-1.5,-0.5),(0.5,-0.5)，圓形的center必須是圓心，多邊形的center則像是一個參考點，可以任意定  

class CollidableObject  
CollidableObject是個抽象類別，所有需要碰撞的物件都要繼承此類別，並且實作碰撞發生時會呼叫的onCollide方法  
目前限制每個CollidableObject只會有一個Collider

class Utils  
Utils是個算法類別calculateCollide會逐一地將others裡的object與myself檢查碰撞，若有碰撞，會呼叫各自的onCollide方法

