## Framework

### MainLoop

### State Manager

The Game state manager is a state machine.It will track the game state and manage the game information. The simplest state mathine is a switch statement:

	swtich (mystate)
	{
		case STATE_01:
		case STATE_02:
	}　
	
	
To manage the complex　game state, wee will use OOP
	
	Class GameState
	{
		...
	}
	
	class StateManager {
		void mainloop(){
			...
		}
		void change(){
			...
		}
	}
	
### Graphical Engine

向屏幕绘制的基本度量单位是像素，包含红蓝绿以及Alpha

纹理是一组像素的数据集合

图片只是一个抽象的高层概念，或许一些像素组合在一起就是一张有规律的图片了。

旋转：２D实现的话计算比较大

动画：为了保证帧的连续，二维动画每一帧要放在一个相同的纹理里面，那个纹理就是精灵。２D动画是每次重绘，每一帧都需要美工做好，而３D是通过几何计算生成，存储关键帧坐标即可。


	