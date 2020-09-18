# Fatality API

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

---

## <a name="callback"></a>Callback
```java
Index | Description

1     | What are callbacks ?

2     | Accessing the 'Callback' interface

3     | Adding a callback 

4     | Callback protatypes 
```
** **

1 - What are callbacks ?

Callbacks are functions that get called within the main cheat whenever something happens ( e.g. whenever a frame gets rendered )
** **
2 - Accessing the 'Callback' interface

Accessing the interface is as easy as doing this:
```java
local callbacks = fatality.callbacks;
```
** **
3 - Adding a callback

Adding a callback can be done via the fatality.callbacks:add function.
```java
type     |   name           | description

string   | keyword          | defines when your function will be called

function | function_to_call | defines what function will be called
```
Example usage:
```java
function on_paint( )
    -- Paint code
end

local callbacks = fatality.callbacks;

callbacks:add( "paint", on_paint )
```

4 - Callback prototypes

```java
keyword | description | parameters

paint | call every frame ( render here! ) | ( )

events | call whenever the server sends an event to you ( e.g. player_hurt, bullet_impact etc. ) | ( event : game_event )

registered_shot | call whenever a shot from the rage-/legitbot gets registered on the server | ( shot : shot_t)

level_init | call once map and all entities have been initialized | ( )
```

## <a name="render"></a>Render



[back to Contents](#-1)
