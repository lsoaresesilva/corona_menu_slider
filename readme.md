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

![alt tag](http://i36.photobucket.com/albums/e43/leonardo_soares4/screenshot_xmllayout_zpshkhn0ix0.png)

* Inserting components programmatically 

```lua
-- in your main.lua
local widget = require("widget")

local viewLoader = require("view")
local view = viewLoader:setView("layout.xml")
local layout = view:findLayoutById("layoutLinear")
local recoverButton = widget.newButton({label="Recover"})
layout:insert(recoverButton)
```

* Updating components programmatically 

```lua
-- in your main.lua
local widget = require("widget")

local viewLoader = require("view")
local view = viewLoader:setView("layout.xml")
local textUsername = view:findLayoutById("txtUsername")
textUsername.text = "New Text!"
```

* Use with composer

```lua
-- in your scene.lua

local composer = require("composer")
local viewLoader = require("view")
local view = viewLoader:setView("layout.xml")

local scene = composer.newScene()

function scene:create( event )
 
    local sceneGroup = self.view
    -- Code here runs when the scene is first created but has not yet appeared on screen
    sceneGroup:insert(view)
end

return scene

```

* Inner layouts, BlankSpace, Image example and touch listener example:

```xml

<!-- An calculator example -->

<LinearLayout id="layoutLinear"  orientation="vertical" align="center">
    <TextField id="txtField"/>
    <BlankSpace width="10" height="20"/>
    <LinearLayout id="layoutFirstRow"  orientation="horizontal" align="center">
        <Image filename="btn_1.png" width="50" height="50" touch="pressButton"/>
        <Image filename="btn_2.png" width="50" height="50" />
        <Image filename="btn_3.png" width="50" height="50" />
        <Image filename="btn_sum.png" width="50" height="50" />
    </LinearLayout>
    <BlankSpace width="10" height="20"/>
    <LinearLayout id="layoutSecondRow"  orientation="horizontal" align="center">
        
        <Image filename="btn_4.png" width="50" height="50" />
        <Image filename="btn_5.png" width="50" height="50" />
        <Image filename="btn_6.png" width="50" height="50" />
        <Image filename="btn_minus.png" width="50" height="50" />
    </LinearLayout>
    
</LinearLayout>
```

## Changelog

* 0.2 - 15/03/2017

** Added support for nested/inner layouts;
** Added support for a css-like style (experimental);
** Added support for listeners definition through XML (works for tap, touch and userinput events);
** Added a two new components: Image and BlankSpace (inserts a blank space in yout layout);
** Refactored the function to position components on screen, its much better now :)