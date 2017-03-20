# Corona SDK - Menu Slider Library

CopyRight (C) 2017 - Leonardo Soares e Silva - lsoaresesilva@gmail.com

## Sumary

Use this library to create left side menus on Corona Labs SDK. 
These menus are very popular on Business Apps, and you can find examples on all Google's apps for Android, TripAdivisor, and others.


## Instalation

Just copy menu_slider.lua to your Corona project's folder.


## Usage

This library is organized in two containers, top and left. 

Top container contains the three dashs used to open the menu and a centered text. Also, you can use an image.
Left side is the container for menu itens. Each item must be associated to a composer scene, when user clicks on it, a scene is loaded.

Example:

* Top container with text

```lua
-- in your main.lua
local menu = require("menu_slider")
local newMenu = menu:new({
    data={
        {text="Cities", scene="scene1.lua"},
        {text="States", scene="scene2.lua"},
        {text="Countries'", scene="scene3.lua"}
        }, 
    containers={
        topContainerProperties={
            bgColor={0.5,0.5,1}, -- background color
            strokeColor={1,1,0.8}, -- dashs color
            text="Menu Slider", -- text which will appear centered    
        }
    }
    })

```

![alt tag](![alt tag](http://i36.photobucket.com/albums/e43/leonardo_soares4/slider01_zps6mjsjzlj.png)

![alt tag](![alt tag](http://i36.photobucket.com/albums/e43/leonardo_soares4/slider02_zpsybnrdtwg.png)

* Top container with image

```lua
local menu = require("menu_slider")
local newMenu = menu:new({
    data={
        {text="Cities", scene="alo"},
        {text="States", scene="alo"},
        {text="Countries'", scene="alo"}
        }, 
    containers={
        topContainerProperties={
            fileName="img_container.png", -- this image is loaded inside a newImageRect, so its supports image scaling
            imageWidth=display.contentWidth, -- you must specify image width
            imageHeight=50 -- you must specify image height
        }
    }
    })
```
And it is done.

