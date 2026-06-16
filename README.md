# GlueLib
A lightweight Roblox Lua library for teleporting and physics gluing.

---

## Loading the Library

```lua
local GlueLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/rangell8/Rexy-s-Welding-Library/refs/heads/main/Lib"))()
```

---

## Functions

### `GlueLib.glueto(target, enabled)`

Teleports you to a target part every frame. Also glues your physics to the target.

**Arguments**

| Argument | Type | Description |
|---|---|---|
| `target` | `BasePart` | The part to teleport to |
| `enabled` | `boolean` | `true` to start, `false` to stop |

**Example**

```lua
local Players = game:GetService("Players")
local target = Players:WaitForChild("imaaan00bbalt").Character:WaitForChild("HumanoidRootPart")

-- Start teleporting to target every frame
GlueLib.glueto(target, true)

-- Stop
GlueLib.glueto(target, false)
```

**Notes**
- Calling `glueto(target, true)` while already running will cleanly restart the loop.
- Calling `glueto(target, false)` unglues your physics.
- If the target is destroyed mid-loop, the loop safely skips that frame.

---

### `GlueLib.glue(target, enabled)`

Glues your physics to a target part on loop with no teleporting involved.

**Arguments**

| Argument | Type | Description |
|---|---|---|
| `target` | `BasePart` | The part to glue physics to |
| `enabled` | `boolean` | `true` to start gluing, `false` to stop |

**Example**

```lua
local Players = game:GetService("Players")
local target = Players:WaitForChild("imaaan00bbalt").Character:WaitForChild("HumanoidRootPart")

-- Start gluing physics to target
GlueLib.glue(target, true)

-- Stop
GlueLib.glue(target, false)
```

**Notes**
- No teleporting, only physics are glued to the target.
- Calling `glue(target, false)` unglues your physics.

---

## Full Usage Example

```lua
-- Load the library
local GlueLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/rangell8/Rexy-s-Welding-Library/refs/heads/main/Lib"))()

local Players = game:GetService("Players")
local target = Players:WaitForChild("imaaan00bbalt").Character:WaitForChild("HumanoidRootPart")

-- Teleport and glue to target
GlueLib.glueto(target, true)

-- After 5 seconds, stop
task.wait(5)
GlueLib.glueto(target, false)
```



Glue lib made by Rexy.

Yes this readme is made by ai im not typin a whole essay.
