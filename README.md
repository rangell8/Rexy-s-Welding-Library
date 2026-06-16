# GlueLib
A lightweight Roblox Lua library for teleporting and physics manipulation.

---

## Loading the Library

```lua
local GlueLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/rangell8/Rexy-s-Welding-Library/refs/heads/main/Lib"))()
```

---

## Functions

### `GlueLib.glueto(hrp, target, enabled)`

Teleports the HumanoidRootPart to a target part every frame using a Heartbeat loop. Also sets the `PhysicsRepRootPart` hidden property to sync the physics representation.

**Arguments**

| Argument | Type | Description |
|---|---|---|
| `hrp` | `BasePart` | The HumanoidRootPart to teleport |
| `target` | `BasePart` | The part to teleport to |
| `enabled` | `boolean` | `true` to start the loop, `false` to stop it |

**Examples**

```lua
local hrp = game.Players.LocalPlayer.Character.HumanoidRootPart

-- Start teleporting to a part every frame
GlueLib.glueto(hrp, workspace.Part, true)

-- Stop the loop and reset physics
GlueLib.glueto(hrp, workspace.Part, false)
```

**Notes**
- Calling `glueto(..., true)` while already running will cleanly restart the loop.
- Calling `glueto(..., false)` resets `PhysicsRepRootPart` back to the HRP itself.
- If either `hrp` or `target` are destroyed mid-loop, the loop safely skips that frame.

---

### `GlueLib.glue(hrp, target, enabled)`

Sets the `PhysicsRepRootPart` hidden property of the HRP to the target part directly, as a one-shot call with no loop.

**Arguments**

| Argument | Type | Description |
|---|---|---|
| `hrp` | `BasePart` | The HumanoidRootPart to modify |
| `target` | `BasePart` | The part to set as the physics rep root |
| `enabled` | `boolean` | Currently unused, reserved for future use |

**Example**

```lua
local hrp = game.Players.LocalPlayer.Character.HumanoidRootPart

GlueLib.glue(hrp, workspace.Part, true)
```

---

## Full Usage Example

```lua
-- Load the library
local GlueLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/rangell8/Rexy-s-Welding-Library/refs/heads/main/Lib"))()

local character = game.Players.LocalPlayer.Character or game.Players.LocalPlayer.CharacterAdded:Wait()
local hrp = character:WaitForChild("HumanoidRootPart")

-- Teleport to a part on loop
GlueLib.glueto(hrp, workspace.TargetPart, true)

-- After 5 seconds, stop
task.wait(5)
GlueLib.glueto(hrp, workspace.TargetPart, false)
```
