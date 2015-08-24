title: Setting up Eclipse CDT for SDL2 development
date: 2013-08-08 13:00:25
tags:
- c++
- eclipse
- sdl
---
This tutorial assumes you already have SDL2 installed. If your on Linux install it using your Distro's package manager. On OpenSUSE you can find SDL2 in the Games repository, details can be found here http://en.opensuse.org/Games

First you'll want a copy of Eclipse for C/C++ Developers from http://www.eclipse.org/downloads/

Once downloaded you'll want to unzip it somewhere on your harddrive. I'm on Linux so I unzipped it to /home/myuser/apps/

Launch Eclipse, it will ask you to pick a workspace. I just leave it the defaults and move on.

Create a new c++ project (File > New > C++ Project). You will need to pick a toolchain, I'm on Linux so I picked Linux GCC.

Before you can build your project there is a few things you will need to configure.

**If you want to use c++11 do the following:**

  1. Right click your Project under "Package Explorer" and select Properties.
  2. Select (C/C++ Build > Settings > GCC C++ Compiler > Miscellaneous)
  3. Under "Other flags" add: **-std=c++0x**
  4. Click Apply then OK

**Configure Eclipse to use SDL2**

  1. Right click your Project under "Package Explorer" and select Properties.
  2. Select (C/C++ General &gt; Paths and Symbols &gt; Libraries)
  3. Click "Add" and add "SDL2" and click OK
  4. Click "Add" and add "SDL2main" and click OK

Your project should be configured for SDL2 development now. Lets try creating a quick Hello World program just to make sure.

Create a main.cpp file and add the following code.

    #include "SDL2/SDL.h";

    int main(int argc, char** argv){

        // Start SDL2
        SDL_Init(SDL_INIT_EVERYTHING);

        // Create a Window in the middle of the screen
        SDL_Window *window = nullptr;
        window = SDL_CreateWindow("Hello World!",
                SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED, // x and y
                640, 480, // Width and Height
                SDL_WINDOW_SHOWN);

        // Delay so that we can see the window appear
        SDL_Delay(2000);

        // Cleanup and Quit
        SDL_DestroyWindow(window);
        SDL_Quit();

        return 0;
    }

You should now be able to build and run this code.

To build press **ctrl+b**.
To run press **ctrl+f11**.

A blank window should appear with the title "Hello World!". If you see this congratulations you've successfully configured SDL2 in Eclipse.
