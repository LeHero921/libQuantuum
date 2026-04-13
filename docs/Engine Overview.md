[[LibQuantuum]] is build on the raylib framework.
It provides compact and extended wrappers for existing functions and adds a scalable unity like structure to the game workflow.
So its object oriented, but the engine and the core game application should work in a non object approach to keep a flexible and robust workflow.

The core engine / application has a main file that initializes the game per usual and constructs the window and some core classes (e.g. audio, physics, etc.).
Though the main game loop inside this file should not be used to do gameplay stuff,
rather to act as a gateway for other managing classes to load.

So for example:
	> The main file initializes the window and the application and core services
	> then, loads the object / entity system:
		> Object Management (controls all objects (comparable to unity monobehaviour))
		> the Object Management initializes the object workflow for Start and Update functionality
		> as well as object memory management
	> game state management, saves and scenes should be manages and dealt with  	
	> the main game loop inside the main file should handle input polling or at least input module updates and either control the rendering or initialize and update the rendering pipeline

View the roadmap:
[[Engine Roadmap (by gemini)]]