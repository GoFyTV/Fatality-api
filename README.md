# Fatality API
<a name="-1"></a>

|FATALITY|
|--------|
|[Callback](#callback)|
|[Render](#render)|
|[Input](#input)|
|[Math](#math)|
|[Config](#config)|
|[Menu](#menu)|
|[      Control](#control)|
|[            Checkbox](#checkbox)|
|[            Slider](#slider)|
|[            Combobox](#combobox)|
|[            Button](#button)|
|Datatypes|
|[      Lag_record_t](#lag_record_t)|
|[      Record_shot_info_t](#record_shot_info_t)|
|[      Shot_t](#shot_t)|
|[      Value](#value)|

|CSGO|
|--------|
|[Interface Handler](#interface_handler)|
|[      Engine_client](#engine_client)|
|[      Events](#events)|
|[      Global_vars](#global_vars)|
|[      Debug_overlay](#debug_overlay)|
|[      Entity_list](#entity_list)|
|[      Cvar](#cvar)|
|Datatypes|
|[      Color](#color)|
|[      Game_event](#game_event)|
|[      Vector3](#vector3)|
|[      Vector2](#vector2)|
|[      Angle](#angle)|
|[      Matrix3x4_t](#matrix3x4_t)|
|[      Font](#font)|
|[      Convar](#convar)|
|[      Entity](#entity)|
|[            Player](#player)|

---

## <a name="callback"></a>Callback

Index | Description

1     | What are callbacks ?

2     | Accessing the 'Callback' interface

3     | Adding a callback 

4     | Callback protatypes 

** **

1 - **What are callbacks ?**

Callbacks are functions that get called within the main cheat whenever something happens ( e.g. whenever a frame gets rendered )
** **
2 - **Accessing the 'Callback' interface**

Accessing the interface is as easy as doing this:
```java
local callbacks = fatality.callbacks;
```
** **
3 - **Adding a callback**

Adding a callback can be done via the fatality.callbacks:add function.

type     |   name           | description

string   | keyword          | defines when your function will be called

function | function_to_call | defines what function will be called

Example usage:
```java
function on_paint( )
    -- Paint code
end

local callbacks = fatality.callbacks;

callbacks:add( "paint", on_paint )
```
** **
4 - **Callback prototypes**

keyword | description | parameters

paint | call every frame ( render here! ) | ( )

events | call whenever the server sends an event to you ( e.g. player_hurt, bullet_impact etc. ) | ( event : game_event )

registered_shot | call whenever a shot from the rage-/legitbot gets registered on the server | ( shot : shot_t)

level_init | call once map and all entities have been initialized | ( )
** **
## <a name="render"></a>Render

Member | Description

rect_filled( x : float, y : float, width : float, height : float, col : [csgo.color](#color) ) : void | filled rectangle

create_font( font_family : string, size : int, weight : int, outline : boolean ) : csgo.font | creates font and returns it

text( font : csgo.font, x : float, y : float, text : string, col : csgo.color ) : void | renders text with specified font

rect_fade( x : float, y : float, width : float, height : float, col1 : csgo.color, col2 : csgo.color, horizontal : boolean ) : void | gradient filled rectangle

rect( x : float, y : float, width : float, height : float, col : csgo.color ) : void | rectangle

text_size( font : csgo.font, text : string ) : csgo.vector2 | gets size of specified text with specified font

indicator( x : float, y : float, text : string, is_active : boolean, bar_progress : float ) : void | renders indicator with a bar below ( 0 - 1 / -1 for no bar )

draw_hitgroup( player : csgo.player, matrices : csgo.matrix3x4_t, hitgroup : int, duration: float, col : csgo.color ) : void | renders specified hitgroup ( -1 for all hitboxes )

screen_size( ) : csgo.vector2 | gets screen size
** **
Example usage

```java
-- Get render instance
local render = fatality.render

-- Will be called every time a frame is rendered
function on_paint( )

    -- Create color
    local dark_blue = csgo.color( 33, 27, 70, 255 )

    -- Draw filled rectangle at position 10, 10 with size 100, 100
    render:rect_filled( 10, 10, 100, 100, dark_blue )

end

-- Register all callback functions that should be called
local callbacks = fatality.callbacks
callbacks:add( "paint", "on_paint" )
```
## <a name="input"></a>Input

Index | Description

1     | Accessing the 'Input' interface

2     | input:is_key_down( key ) : bool
** **
1 - **Accessing the 'Input' interface**
```java
local input = fatality.input;
```
** **
2 - **input:is_key_down( key ) : bool**

type|name|description
number( [key-codes](https://docs.microsoft.com/en-us/windows/win32/inputdev/virtual-key-codes) hex -> decimal )

Example usage
```java
local input = fatality.input;

-- 72 -> 0x47 -> G key
local is_down = input:is_key_down(72)
```

## <a name="math"></a>Math

Member | Description

calc_angle( point1 : [csgo.vector3](#vector3) , point2 : [csgo.vector3](#vector3) ) : [csgo.angle](#angle) | calculates the angle between two points

Example usage
```java
-- Get math insance
local math = fatality.math

-- Calculates angle between two vectors
local angle = math:calc_angle( csgo.vector3( 0, 0, 0 ), csgo.vector3( 100, 50, 300 ) )
```

[back to Contents](#-1)
