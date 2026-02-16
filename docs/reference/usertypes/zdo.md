# ZDO

The bread-and-butter of Valhiem

This class represents automatically synchronized networked objects 
and states throughout Valheim gameplay. 

!!! tip "Shared lifetime"

    All ZDO's retrieved via ZDOManager or through callbacks have
    shared references, and thus are safe to persistently store 
    between calls unlike the previous project.
    

## Instance Members

### `zdo.id`
  > Returns `ZDOID` | **readonly**
  
  > The id of the zdo
  
### `zdo.pos`
  > Returns `Vec3f`
  
  > The position of the zdo
  
### `zdo.zone`
  > Returns `Vec2i` | **readonly**
  
  > The current zone the zdo is contained within
  
### `zdo.rot` 
  > Returns `Quaternion`
  
  > The rotation of the zdo
  
### `zdo.prefab`
  > Returns `Prefab` | **readonly**

### `zdo.prefab_hash`
  > Returns `number` | **readonly**
  
### `zdo.owner`
  > Returns `Int64`
  
### `zdo:is_owner(uuid)`
  > Returns `boolean`
  
  > Checks whether the specified uuid is the owner of the zdo
  
### `zdo.mine`
  > Returns `boolean`
  
  > Whether the zdo is owned by the server

  > Can set to true to locally claim ownership
  ```lua
  zdo.mine = true
  -- zdo.owner is now the server

  zdo.mine = false
  -- zdo is now unclaimed (owner set to 0)
  ```
  
### `zdo.owned`
  > Returns `boolean` | **readonly**
  
  > Returns whether this zdo has an owner
  
### `zdo:disown()`
  > Sets the zdos owner to none (0)
  
### `zdo.data_rev`
  > Returns `number` | **readonly**

  >The zdos data revision number
  
### `zdo.owner_rev`
  > Returns `number` | **readonly**

  > Returns the zdos owner revision number
  
### ~~`zdo.ticks_created`~~
  > Returns `Int64`

  > Returns the time in ticks the zdo was created

  > *Removed following Valheim version 0.x.x where ZDO's underwent 
    a rehaul for memory efficiency*
  
## Data Variables

  ZDOs have Data Variables that are automatically synchronized between server 
  and client. Data Variables are contained in key, value pairs within individual 
  types. Can be read and written from using accessors below:

### Getters
  > A zdo has several named getter and setter types
  
  > `get_float`, `get_int`, `get_long`, `get_quat`, `get_vec3f`, `get_string`, 
    `get_bool`, `get_zdoid`
  ```lua
  zdo:get_...(hash: number, default: any)
  zdo:get_...(hash: number)
  zdo:get_...(name: string, default: any)
  zdo:get_...(name: string)
  ```

  >
  ```lua
  local t = zdo.get_float("plantTime", 240)
  -- if "plantTime" does not exist, 240 is returned
  ```

### Setters  
  > `set_float`, `set_int`, `set`
  ```lua
  zdo:set_...(hash: number, value: any)
  zdo:set_...(name: string, value: any)
  ```
  
  > The overload `set(...)` accepts any of the above non-numeric types

  > Any usage of a long (64-bit integer) utilizes a `Int64` and is overloaded
    by `set(...)`

  >
  ```lua
  zdo:set("RightBackItem", "chestplate")
  zdo:set(VUtils.String.GetStableHashCode("RightBackItem"), "chestplate")

  -- the two lines above achieve the same outcome

  -- all keys are 32-bit hashes, lost but obtainable through lookup
  ```

## ZDO <-> ZDO Connection

### `zdo:set_connection(type: ConnectorType, zdoid)`
  > Sets the connection pair for this ZDO

### `zdo:get_connection(type: ConnectorType)`
  > Returns `ZDOID`

  > The conneciton pair for the ZDO