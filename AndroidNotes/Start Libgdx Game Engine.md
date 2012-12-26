[Libgdx](http://libgdx.badlogicgames.com) is a popular crossplatform game engine.

Project Setup:

1. Downland files from <http://code.google.com/p/libgdx/downloads/list>
2. Go to the project folder on the file system and create a subfolder named libs. From the nightly zip, place gdx-backend-android.jar and the armeabi and armeabi-v7a folders in the libs folder.
In Eclipse, right click the project -> Refresh. Right click again -> Properties -> Java Build Path -> Libraries -> Add JARs, select gdx-backend-android.jar and click OK.
3. Create a Game

	Creating a game
In your main project, create a new class: right click the project -> New -> Class. Name it "Game" and specify a package (eg, "com.gamename"). Next to Interfaces, click Add, choose ApplicationListener, and click OK. It will look like this:

		import com.badlogic.gdx.ApplicationListener;
		
		public class Game implements ApplicationListener {
		        public void create () {
		        }
		
		        public void render () {
		        }
		
		        public void resize (int width, int height){
		        }
		
		        public void pause () {
		        }
		
		        public void resume () {
		        }
		
		        public void dispose () {
		        }
			}
			
4. Running the game 

Open the Activity class in the Android project that was automatically created and make it look like this:

		import com.badlogic.gdx.backends.android.AndroidApplication;
		
		public class AndroidGame extends AndroidApplication {
		        public void onCreate (android.os.Bundle savedInstanceState) {
		                super.onCreate(savedInstanceState);
		                initialize(new Game(), false);
		        }
		}
					
And just  Run it!

More details see <http://code.google.com/p/libgdx/wiki/ProjectSetup>




