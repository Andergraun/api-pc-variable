## lordikek 

**Table of Contents**

* [General Functions](#general-functions)
* [Classes](#classes)
   * [Ability](#ability)
   * [Block](#block)
   * [Container](#container)
   * [Effect](#effect)
   * [Entity](#entity)
   * [FriendManager](#friendmanager)
   * [Game](#game)
   * [HitResult](#hitresult)
   * [Inventory](#inventory)
   * [Item](#item)
   * [Level](#level)
   * [LocalPlayer](#localplayer)
   * [Memory](#memory)
   * [Module](#module)
   * [ModuleManager](#modulemanager)
   * [OverlayObject](#overlayobject)
   * [OverlaySystem](#overlaysystem)
   * [Renderer](#renderer)
   * [Tessellator](#tessellator)
   * [Texture](#texture)
* [Hooks](#hooks)
* [Packets](#packets)
* [Settings](#settings)
* [Tags](#tags)
* [Constants](#constants)




## General Functions

### addTextToClipboard(text)

Copies the provided text to the clipboard.

| Name | Type | Description |
|---|---|---|
| `text` | `string` | The text to be copied. |


### getTextFromClipboard()

Returns the current text stored in the clipboard.

**Returns:**

| Type | Description |
|---|---|
| `string` | The clipboard text. |


### isInGame()

Checks if the local player is currently in a level (actively playing the game).

**Returns:**

| Type | Description |
|---|---|
| `boolean` | `true` if the local player is in a level, `false` otherwise. |


### log(text)

Writes the provided text to the `logs.txt` file.

| Name | Type | Description |
|---|---|---|
| `text` | `string` | The text to be written to the log file. |


### notification(text)

Creates and displays a notification to the user.

| Name | Type | Description |
|---|---|---|
| `text` | `string` | The message to display in the notification. |


### preventDefault()

Prevents the currently executing hook from completing its default action. 
**Note:**  Only specific hooks are preventable.


### vkCodeToString(code)

Resolves a Virtual Key (VK) code to its corresponding string representation.

| Name | Type | Description |
|---|---|---|
| `code` | `VK` | The VK code to resolve. |

**Returns:**

| Type | Description |
|---|---|
| `string` | The resolved VK code as a string. |

## Classes

### Ability 

Represents a LocalPlayer's game ability (e.g., flying, noclip, building). 

**Methods:**

 * `getAddress()`: Returns the memory address of the Ability object.
    * **Returns:** 
        * Type: `number`
        * Description: Memory address.
 * `getBoolean()`: Returns the boolean value of the Ability.
    * **Returns:** 
        * Type: `boolean`
        * Description: Boolean value.
 * `getNumber()`: Returns the numeric value of the Ability.
    * **Returns:** 
        * Type: `number`
        * Description: Numeric value.
 * `setBoolean(value)`: Sets the boolean value of the Ability.
    * **Parameters:**
        * `value`: `boolean` - The new boolean value.
 * `setNumber(value)`: Sets the numeric value of the Ability.
    * **Parameters:**
        * `value`: `number` - The new numeric value.

### Block

Represents a block in the game world. Blocks can be fetched using `Level.getBlock()`.

**Methods:**

* `getAddress()`: Returns the memory address of the Block object.
    * **Returns:** 
        * Type: `number`
        * Description: Memory address.
* `getDestroyTime()`: Returns the time it takes to destroy (break) the block.
    * **Returns:** 
        * Type: `number`
        * Description: Destroy time.
* `getFriction()`: Returns the friction value of the block.
    * **Returns:** 
        * Type: `number`
        * Description: Friction value. 
* `getId()`: Returns the numeric ID of the block.
    * **Returns:** 
        * Type: `number`
        * Description: Block ID.
* `getName(data)`: Returns the name of the block.
    * **Parameters:**
        * `data`: `number` (optional) -  The auxiliary ID of the block.
     * **Returns:** 
        * Type: `string`
        * Description: Block name.
* `getStringId()`: Returns the translation key for the block.
    * **Returns:** 
        * Type: `string`
        * Description: Translation key.
* `mayPlace(pos)`: Checks if the block can be placed at the specified position.
    * **Parameters:**
        * `pos`: `number[]` - The position to check.
     * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the block can be placed, `false` otherwise.
* `setDestroyTime(destroyTime)`: Sets the time it takes to destroy the block.
    * **Parameters:**
        * `destroyTime`: `number` - The new destroy time.
* `setFriction(friction)`: Sets the friction value of the block.
    * **Parameters:**
        * `friction`: `number` - The new friction value.

### Container

Provides methods for interacting with containers (e.g., chests).

**Methods:**

* `getItem(containers, slot)`: Returns the Item object at the specified slot in the container.
    * **Parameters:**
        * `containers`: `ContainerSlots` - The container to access.
        * `slot`: `number` - The slot index within the container.
    * **Returns:** 
        * Type: `Item`
        * Description: The Item object at the slot.
* `takeFrom(containers, slot)`: Transfers the item at the specified slot from the container to the local player's inventory.
    * **Parameters:**
        * `containers`: `ContainerSlots` - The container to take from.
        * `slot`: `number` - The slot index within the container.
        * **Note:** Places the item in the first available slot in the player's inventory.

### Effect 

Represents a status effect applied to an entity.

**Constructor:**

```javascript
new Effect(id, duration, amplifier, showParticles) 
```
| Parameter | Type | Description |
|---|---|---|
| `id` | `EffectType` | The type of effect. |
| `duration` | `number` | The duration of the effect in seconds. |
| `amplifier` | `number` | The amplifier (level) of the effect. |
| `showParticles` | `boolean` | Whether to display particles for the effect. |

**Methods:**

* `getAddress()`: Returns the memory address of the Effect object.
    * **Returns:** 
        * Type: `number`
        * Description: Memory address.
* `getAmplifier()`: Returns the amplifier (level) of the effect.
    * **Returns:** 
        * Type: `number`
        * Description: The effect's amplifier (level).
* `getDisplayName()`: Returns the display name of the effect, including its duration and amplifier.
    * **Returns:** 
        * Type: `string`
        * Description: The effect's display name.
* `getDuration()`: Returns the remaining duration of the effect in seconds.
    * **Returns:** 
        * Type: `number`
        * Description: The effect's remaining duration.
* `getId()`: Returns the numeric ID of the effect.
    * **Returns:** 
        * Type: `number`
        * Description: The effect's ID.
* `getStringId()`: Returns the translation key for the effect.
    * **Returns:** 
        * Type: `string`
        * Description: The effect's translation key.
* `isParticlesShown()`: Checks if particles are being displayed for the effect.
    * **Returns:** 
        * Type: `boolean`
        * Description:  `true` if particles are shown, `false` otherwise.
* `setAmplifier(amplifier)`: Sets the amplifier (level) of the effect.
    * **Parameters:**
        * `amplifier`: `number` - The new amplifier level.
* `setDuration(duration)`: Sets the duration of the effect in seconds.
    * **Parameters:**
        * `duration`: `number` - The new duration in seconds.
* `setId(id)`: Sets the numeric ID of the effect.
    * **Parameters:**
        * `id`: `number` - The new ID.
* `setIsParticlesShown(showParticles)`:  Sets whether to display particles for the effect.
    * **Parameters:**
        * `showParticles`: `boolean` - Whether to show particles.



### Entity 

Represents an entity in the game world. You cannot directly create an Entity object; it must be fetched using methods like `Level.fetchEntity()`.

**Methods:**

* `getAddress()`: Returns the memory address of the Entity object.
    * **Returns:** 
        * Type: `number`
        * Description: Memory address.
* `getArmor(slot)`: Returns the Item object equipped in the specified armor slot of the entity.
    * **Parameters:**
        * `slot`: `ArmorSlot` - The armor slot to access (e.g., `ArmorSlot.HELMET`).
    * **Returns:** 
        * Type: `Item`
        * Description: The Item object in the armor slot.
* `getCarriedItem()`: Returns the Item object currently held in the entity's main hand.
    * **Returns:** 
        * Type: `Item`
        * Description: The Item object in the main hand.
* `getDistanceTo(target)`: Calculates the distance between this entity and another entity or a set of coordinates.
    * **Parameters:**
        * `target`: `Entity | number[]` -  The target entity or position ([x, y, z]).
    * **Returns:** 
        * Type: `number`
        * Description: The distance between the entities or the entity and the position.
* `getEntityTypeId()`: Returns the entity type ID.
* `getEyeHeight()`: Returns the eye height of the entity.
* `getFallDistance()`: Returns the current fall distance of the entity.
    * **Returns:** 
        * Type: `number`
        * Description:  The fall distance. 
* `getId(runtime)`: Returns the ID of the entity.
    * **Parameters:**
        * `runtime`: `boolean` - Whether to retrieve the runtime ID (used for receiving packets).
    * **Returns:** 
        * Type: `number`
        * Description: Entity ID.
* `getInterpolatedPos()`: Returns the interpolated position of the entity. Use this for smoother rendering.
    * **Returns:** 
        * Type: `number[]`
        * Description: Interpolated position as [x, y, z].
* `getInterpolatedRot()`: Returns the interpolated head rotation of the entity. Use this for smoother rendering.
    * **Returns:** 
        * Type: `number[]`
        * Description: Interpolated rotation as [pitch, yaw].
* `getNameTag()`: Returns the name tag displayed above the entity.
    * **Returns:** 
        * Type: `string`
        * Description: The entity's name tag.
* `getOffhandItem()`: Returns the Item object currently held in the entity's offhand.
    * **Returns:** 
        * Type: `Item`
        * Description: The Item object in the offhand.
* `getPitch()`: Returns the pitch (vertical rotation) of the entity's head.
    * **Returns:** 
        * Type: `number`
        * Description: The pitch value.
* `getPos()`: Returns the coordinates of the entity.
    * **Returns:** 
        * Type: `number[]`
        * Description: The entity's position as [x, y, z].
* `getPosX()`: Returns the X-coordinate of the entity.
    * **Returns:** 
        * Type: `number`
        * Description: The entity's X-coordinate.
* `getPosY()`: Returns the Y-coordinate of the entity.
    * **Returns:** 
        * Type: `number`
        * Description: The entity's Y-coordinate.
* `getPosZ()`: Returns the Z-coordinate of the entity.
    * **Returns:** 
        * Type: `number`
        * Description: The entity's Z-coordinate.
* `getRot()`: Returns the rotation of the entity's head.
    * **Returns:** 
        * Type: `number[]`
        * Description: The head rotation as [pitch, yaw].
* `getSize()`: Returns the size of the entity's hitbox.
    * **Returns:** 
        * Type: `number[]`
        * Description: The hitbox size as [width, height].
* `getSizeX()`: Returns the width of the entity's hitbox.
    * **Returns:** 
        * Type: `number`
        * Description: The hitbox width.
* `getSizeY()`: Returns the height of the entity's hitbox.
    * **Returns:** 
        * Type: `number`
        * Description: The hitbox height.
* `getStatusFlag(flagId)`:  Returns the status of a specific entity status flag.
    * **Parameters:**
        * `flagId`: `EntityStatusFlag` - The ID of the status flag to check.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the flag is set, `false` otherwise. 
* `getVel()`: Returns the velocity of the entity.
    * **Returns:** 
        * Type: `number[]`
        * Description:  The velocity as [x, y, z].
* `getVelX()`: Returns the X-component of the entity's velocity.
    * **Returns:** 
        * Type: `number`
        * Description: The X-velocity.
* `getVelY()`: Returns the Y-component of the entity's velocity.
    * **Returns:** 
        * Type: `number`
        * Description: The Y-velocity.
* `getVelZ()`: Returns the Z-component of the entity's velocity.
    * **Returns:** 
        * Type: `number`
        * Description: The Z-velocity. 
* `getYaw()`: Returns the yaw (horizontal rotation) of the entity's head.
    * **Returns:** 
        * Type: `number`
        * Description: The yaw value.
* `isAlive()`:  Checks if the entity is currently alive based on the game's internal state.
    * **Returns:** 
        * Type: `boolean`
        * Description:  `true` if alive, `false` otherwise.
* `isBot()`: Checks if the entity is marked as a bot (potentially by a cheat).
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if marked as a bot, `false` otherwise.
* `isFalling()`: Checks if the entity is currently falling based on the game's internal state.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if falling, `false` otherwise.
* `isFriend()`: Checks if the entity is marked as a friend.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if marked as a friend, `false` otherwise.
* `isInLava()`: Checks if the entity is currently in lava based on the game's internal state.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if in lava, `false` otherwise. 
* `isInWall()`: Checks if the entity is currently inside a wall based on the game's internal state.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if in a wall, `false` otherwise. 
* `isInWater()`: Checks if the entity is currently in water based on the game's internal state.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if in water, `false` otherwise.
* `isLocalPlayer()`: Checks if this Entity object represents the local player.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if this is the local player, `false` otherwise. 
* `isOnGround()`: Checks if the entity is currently on the ground based on the game's internal state.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if on the ground, `false` otherwise. 
* `isTeammate()`:  Checks if the entity is marked as a teammate (potentially by a cheat).
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if marked as a teammate, `false` otherwise. 
* `isValidTarget()`:  Checks if the entity is marked as a valid target.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if marked as a valid target, `false` otherwise.
* `setNameTag(nametag)`: Sets the name tag displayed above the entity (client-side only).
    * **Parameters:**
        * `nametag`: `string` - The new name tag.
* `setSize(hitboxSize)`: Sets the size of the entity's hitbox.
    * **Parameters:**
        * `hitboxSize`: `number[]` - The new hitbox size as [width, height].
* `setSizeX(sizeX)`:  Sets the width of the entity's hitbox.
    * **Parameters:**
        * `sizeX`: `number` - The new hitbox width.
* `setSizeY(sizeY)`: Sets the height of the entity's hitbox.
    * **Parameters:**
        * `sizeY`: `number` - The new hitbox height.

### FriendManager

Manages a list of "friends" for cheat-related functionality.

**Methods (all static):**

* `addFriend(name)`: Adds an entity to the friend list.
    * **Parameters:**
        * `name`: `string | Entity` - The name of the entity or the Entity object itself. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the friend was added successfully, `false` otherwise. 
* `getFriends()`: Returns an array of names from the friend list.
    * **Returns:** 
        * Type: `string[]`
        * Description: An array containing the names of all friends.
* `isFriend(name)`: Checks if an entity is in the friend list.
    * **Parameters:**
        * `name`: `string | Entity` - The name of the entity or the Entity object itself.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the entity is a friend, `false` otherwise. 
* `removeFriend(name)`: Removes an entity from the friend list.
    * **Parameters:**
        * `name`: `string | Entity` - The name of the entity or the Entity object itself. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the friend was removed successfully, `false` otherwise.

### Game 

Provides additional functions for interacting with the game and handling user input.

**Methods (all static):**

* `closeScreen()`: Closes the currently open game screen (may cause unexpected behavior).
* `disconnect(message)`: Disconnects from the current game server.
    * **Parameters:**
        * `message`: `string` (optional) - A message to display upon disconnecting. 
* `getAddress()`:  Returns the memory address of the `MinecraftGame` object.
    * **Returns:** 
        * Type: `number`
        * Description: The memory address.
* `getFPS()`:  Returns the current frames per second (FPS) value.
    * **Returns:** 
        * Type: `number`
        * Description: The current FPS.
* `getGameSpeed()`: Returns the client-side ticks per second (TPS) value. 
    * **Returns:** 
        * Type: `number`
        * Description: The client-side TPS. 
* `getMousePos()`: Returns the current mouse position relative to the game window.
    * **Returns:** 
        * Type: `number[]`
        * Description: The mouse position as [x, y].
* `getMouseX()`: Returns the current X-coordinate of the mouse.
    * **Returns:** 
        * Type: `number`
        * Description: The mouse's X-coordinate.
* `getMouseY()`: Returns the current Y-coordinate of the mouse.
    * **Returns:** 
        * Type: `number`
        * Description: The mouse's Y-coordinate.
* `isKeyDown(key)`: Checks if a specific key is currently pressed.
    * **Parameters:**
        * `key`: `VK` - The Virtual Key code of the key to check. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the key is pressed, `false` otherwise.
* `getPing()`: Returns the current ping (latency) to the connected server in milliseconds.
    * **Returns:** 
        * Type: `number`
        * Description: The ping value in milliseconds.
* `getScreenHeight()`: Returns the height of the game window.
    * **Returns:** 
        * Type: `number`
        * Description: The window height.
* `getScreenName()`: Returns the name of the currently active game screen (e.g., "hud_screen", "chat_screen"). 
    * **Returns:** 
        * Type: `string`
        * Description: The screen name.
* `getScreenSize()`: Returns the size of the game window.
    * **Returns:** 
        * Type: `number[]`
        * Description: The window size as [width, height]. 
* `getScreenWidth()`: Returns the width of the game window.
    * **Returns:** 
        * Type: `number`
        * Description: The window width.
* `getTexture()`: Returns a game texture object.
    * **Returns:** 
        * Type: `Texture`
        * Description: The Texture object.
* `setGameSpeed(tps)`: Sets the client-side ticks per second (TPS) value, potentially affecting game speed.
    * **Parameters:**
        * `tps`: `number` - The desired TPS value.


### HitResult 

Provides functions for accessing information about the local player's view direction and what they are currently pointing at.

**Static Members:**

* `HitResult.TYPE_AIR`: Represents that the player is pointing at air.
* `HitResult.TYPE_BLOCK`:  Represents that the player is pointing at a block.
* `HitResult.TYPE_ENTITY`: Represents that the player is pointing at an entity.

**Methods (all static):**

* `getAddress()`: Returns the memory address of the `HitResult` object.
    * **Returns:** 
        * Type: `number`
        * Description:  The memory address.
* `getBlockPos()`: Returns the position of the block currently being pointed at by the player.
    * **Returns:** 
        * Type: `number[] | null`
        * Description: The block position as [x, y, z], or `null` if not pointing at a block.
* `getBlockPosX()`:  Returns the X-coordinate of the block currently being pointed at.
    * **Returns:** 
        * Type: `number | null`
        * Description: The block's X-coordinate, or `null` if not pointing at a block.
* `getBlockPosY()`: Returns the Y-coordinate of the block currently being pointed at.
    * **Returns:** 
        * Type: `number | null`
        * Description: The block's Y-coordinate, or `null` if not pointing at a block.
* `getBlockPosZ()`: Returns the Z-coordinate of the block currently being pointed at. 
    * **Returns:** 
        * Type: `number | null`
        * Description: The block's Z-coordinate, or `null` if not pointing at a block.
* `getEntity()`: Returns the Entity object currently being pointed at by the player. 
    * **Returns:** 
        * Type: `Entity | null`
        * Description:  The targeted Entity object, or `null` if not pointing at an entity.
* `getSide()`: Returns the side of the block currently being pointed at.
    * **Returns:** 
        * Type: `Constants#BlockSide | null`
        * Description:  The `BlockSide` being pointed at, or `null` if not pointing at a block.
* `getType()`: Returns the type of the `HitResult` (air, block, or entity). 
    * **Returns:** 
        * Type: `number`
        * Description: The `HitResult` type code (0 - block, 1 - entity, 3 - air). 
* `getViewDir()`:  Returns the exact coordinates the player is looking at.
    * **Returns:** 
        * Type: `number`
        * Description: The view direction.
* `getViewDirX()`:  Returns the X-component of the exact coordinates the player is looking at.
    * **Returns:** 
        * Type: `number`
        * Description:  The X-coordinate of the view direction.
* `getViewDirY()`:  Returns the Y-component of the exact coordinates the player is looking at.
    * **Returns:** 
        * Type: `number`
        * Description:  The Y-coordinate of the view direction.
* `getViewDirZ()`: Returns the Z-component of the exact coordinates the player is looking at.
    * **Returns:** 
        * Type: `number`
        * Description:  The Z-coordinate of the view direction. 
* `setBlockPos(blockPos)`:  Sets the position of the block being pointed at (client-side only). 
    * **Parameters:**
        * `blockPos`: `number[]` - The new block position as [x, y, z]. 
* `setBlockPosX(blockPosX)`: Sets the X-coordinate of the block being pointed at (client-side only).
    * **Parameters:**
        * `blockPosX`: `number` - The new X-coordinate.
* `setBlockPosY(blockPosY)`: Sets the Y-coordinate of the block being pointed at (client-side only).
    * **Parameters:**
        * `blockPosY`: `number` - The new Y-coordinate.
* `setBlockPosZ(blockPosZ)`:  Sets the Z-coordinate of the block being pointed at (client-side only). 
    * **Parameters:**
        * `blockPosZ`: `number` - The new Z-coordinate. 
* `setEntity(entity)`:  Sets the entity being pointed at (client-side only).
    * **Parameters:**
        * `entity`: `Entity` - The new target entity.
* `setSide(side)`:  Sets the side of the block being pointed at (client-side only). 
    * **Parameters:**
        * `side`: `number` - The new block side.
* `setType(type)`: Sets the type of the `HitResult` (air, block, or entity) (client-side only).
    * **Parameters:**
        * `type`: `number` - The new `HitResult` type code (0 - block, 1 - entity, 3 - air). 
* `setViewDir(viewDir)`:  Sets the exact coordinates the player is looking at (client-side only). 
    * **Parameters:**
        * `viewDir`: `number[]` - The new view direction as [x, y, z]. 
* `setViewDirX(viewDirX)`:  Sets the X-component of the view direction (client-side only).
    * **Parameters:**
        * `viewDirX`: `number` - The new X-coordinate of the view direction.
* `setViewDirY(viewDirY)`: Sets the Y-component of the view direction (client-side only).
    * **Parameters:**
        * `viewDirY`: `number` - The new Y-coordinate of the view direction. 
* `setViewDirZ(viewDirZ)`: Sets the Z-component of the view direction (client-side only).
    * **Parameters:**
        * `viewDirZ`: `number` - The new Z-coordinate of the view direction. 

### Inventory 

Provides functions for managing the local player's inventory.

**Methods (all static):**

* `addItem(id, count, damage)`:  Adds an item to the inventory by its ID. 
    * **Parameters:**
        * `id`: `number` -  The numeric ID of the item. 
        * `count`: `number` - The quantity of the item to add.
        * `damage`: `number` - The damage value of the item. 
* `addItem(item)`: Adds an Item object to the inventory.
    * **Parameters:**
        * `item`: `Item` - The Item object to add. 
* `clearSlot(slot)`:  Removes all items from the specified inventory slot.
    * **Parameters:**
        * `slot`: `number` - The slot index. 
* `dropSlot(slot, dropAll)`:  Drops the item(s) from the specified inventory slot.
    * **Parameters:**
        * `slot`: `number` - The slot index. 
        * `dropAll`: `boolean` - If `true`, drops the entire stack; otherwise, drops one item.
* `getAddress()`:  Returns the memory address of the `Inventory` object. 
    * **Returns:** 
        * Type: `number`
        * Description: The memory address.
* `getArmor(slot)`: Returns the Item object equipped in the specified armor slot. 
    * **Parameters:**
        * `slot`: `ArmorSlot` - The armor slot (e.g., `ArmorSlot.HELMET`). 
    * **Returns:** 
        * Type: `Item`
        * Description: The Item object in the armor slot.
* `getFreeSlot()`:  Returns the index of the first free (empty) inventory slot.
    * **Returns:** 
        * Type: `number`
        * Description:  The index of the free slot, or -1 if the inventory is full. 
* `getItem(slot)`: Returns the Item object at the specified inventory slot. 
    * **Parameters:**
        * `slot`: `number` - The slot index. 
    * **Returns:** 
        * Type: `Item`
        * Description: The Item object in the slot. 
* `getItems()`:  Returns an array of all Item objects in the inventory. 
    * **Returns:** 
        * Type: `Item[]`
        * Description:  An array of Item objects. 
* `getOffhandItem()`:  Returns the Item object currently held in the offhand slot. 
    * **Returns:** 
        * Type: `Item`
        * Description: The Item object in the offhand slot. 
* `getSelectedItem()`: Returns the Item object currently selected in the hotbar (main hand).
    * **Returns:** 
        * Type: `Item`
        * Description:  The selected Item object.
* `getSelectedSlot()`: Returns the index of the currently selected hotbar slot.
    * **Returns:** 
        * Type: `number`
        * Description: The slot index.
* `selectSlot(slot)`:  Selects the specified hotbar slot.
    * **Parameters:**
        * `slot`: `number` - The slot index to select.
* `setArmor(slot, armorItem, freeSlot)`: Equips the provided Item object into the specified armor slot.
    * **Parameters:**
        * `slot`: `number` - The armor slot index. 
        * `armorItem`: `number` - The Item object to equip.
        * `freeSlot` (optional): `number` - If provided, specifies a free slot where the item currently in the armor slot should be moved.
* `setItem(slot, item)`:  Sets the Item object at the specified inventory slot.
    * **Parameters:**
        * `slot`: `number` - The slot index. 
        * `item`: `Item` - The Item object to place in the slot. 
* `setOffhandItem(item, freeSlot)`:  Equips the provided Item object into the offhand slot.
    * **Parameters:**
        * `item`: `Item` - The Item object to equip.
        * `freeSlot` (optional): `number` - If provided, specifies a free slot where the item currently in the offhand slot should be moved.

### Item

Represents an item in the game. 

**Methods:**

* `addEnchant(enchantment, level)`:  Adds an enchantment to the item.
    * **Parameters:**
        * `enchantment`: `EnchantmentType` - The type of enchantment to add.
        * `level`: `number` -  The level of the enchantment.
* `addLore(lore)`:  Adds a line of lore text to the item.
    * **Parameters:**
        * `lore`: `string` - The lore text to add.
* `asBlock()`:  If the item represents a block, returns a `Block` object for that block.
    * **Returns:** 
        * Type: `Block`
        * Description: The Block object. 
* `canDestroySpecial(blockId)`:  Checks if the item is capable of destroying a block with the specified ID.
    * **Parameters:**
        * `blockId`: `number` - The block ID to check.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the item can destroy the block, `false` otherwise.
* `createCompoundTag()`:  Creates a new empty `CompoundTag` associated with this item.
    * **Returns:** 
        * Type: `CompoundTag`
        * Description:  The created `CompoundTag`. 
* `getAddress()`:  Returns the memory address of the Item object. 
    * **Returns:** 
        * Type: `number`
        * Description: The memory address.
* `getArmorValue()`:  Returns the armor points provided by the item. 
    * **Returns:** 
        * Type: `number`
        * Description: The armor value.
* `getArmorValueWithEnchants()`:  Returns the armor points provided by the item, including any bonuses from enchantments. 
    * **Returns:** 
        * Type: `number`
        * Description: The armor value with enchantments.
* `getAttackDamage()`:  Returns the base attack damage of the item. 
    * **Returns:** 
        * Type: `number`
        * Description: The attack damage
* `getAttackDamageWithEnchants()`:  Returns the attack damage of the item, including any bonuses from enchantments. 
    * **Returns:** 
        * Type: `number`
        * Description: The attack damage with enchantments.
* `getAuxId()`: Returns the auxiliary value of the item, often used for damage or data variations. 
    * **Returns:** 
        * Type: `number`
        * Description: The item's auxiliary value.
* `getCompoundTag()`:  Returns the `CompoundTag` associated with this item, which stores its NBT data.
    * **Returns:** 
        * Type: `CompoundTag | null`
        * Description: The `CompoundTag` object, or `null` if none exists. 
* `getCount()`: Returns the quantity (stack size) of the item.
    * **Returns:** 
        * Type: `number`
        * Description: The item count. 
* `getDamage()`: Returns the current damage value of the item (durability). 
    * **Returns:** 
        * Type: `number`
        * Description:  The item's current damage. 
* `getEnchantLevel(enchantment)`:  Returns the level of the specified enchantment on the item.
    * **Parameters:**
        * `enchantment`: `EnchantmentType` - The type of enchantment.
    * **Returns:** 
        * Type: `number`
        * Description: The enchantment level, or 0 if the item does not have the enchantment.
* `getId()`: Returns the numeric ID of the item.
    * **Returns:** 
        * Type: `number`
        * Description: The item's ID. 
* `getLore()`: Returns an array of strings containing the item's lore text.
    * **Returns:** 
        * Type: `string[]`
        * Description: An array of lore strings.
* `getMaxDamage()`:  Returns the maximum durability of the item.
    * **Returns:** 
        * Type: `number`
        * Description: The maximum damage value. 
* `getMaxStackSize()`: Returns the maximum stack size allowed for the item.
    * **Returns:** 
        * Type: `number`
        * Description:  The maximum stack size. 
* `getName()`: Returns the custom name given to the item, if any. 
    * **Returns:** 
        * Type: `string`
        * Description: The item's custom name, or the default name if none is set. 
* `getSlotForArmor()`:  Returns the `ArmorSlot` that this item is designed to be equipped in. 
    * **Returns:** 
        * Type: `ArmorSlot`
        * Description:  The appropriate armor slot.
* `getStringId()`:  Returns the translation key for the item. 
    * **Returns:** 
        * Type: `string`
        * Description: The translation key.
* `getUseDuration()`: Returns the duration (in ticks) for which the item can be used. 
    * **Returns:** 
        * Type: `number`
        * Description: The use duration.
* `hasEnchant(enchantment)`: Checks if the item has the specified enchantment.
    * **Parameters:**
        * `enchantment`: `EnchantmentType` -  The type of enchantment to check for.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the item has the enchantment, `false` otherwise.
* `isArmor()`: Checks if the item is a piece of armor. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the item is armor, `false` otherwise. 
* `isBlock()`:  Checks if the item represents a block. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the item is a block, `false` otherwise.
* `isEnchanted()`:  Checks if the item has any enchantments. 
    * **Returns:** 
        * Type: `boolean`
        * Description:  `true` if the item is enchanted, `false` otherwise.
* `isNull()`: Checks if the item object is null (does not represent a valid item).
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the item is null, `false` otherwise. 
* `isPotion()`: Checks if the item is a potion. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the item is a potion, `false` otherwise. 
* `isStackedByData()`:  Checks if the item's stacking is determined by its data value (e.g., different damage values).
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if stacking is data-dependent, `false` otherwise.
* `isThrowable()`:  Checks if the item can be thrown.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the item is throwable, `false` otherwise.
* `removeEnchant(enchantment)`:  Removes the specified enchantment from the item, if present. 
    * **Parameters:**
        * `enchantment`: `EnchantmentType` - The type of enchantment to remove.
* `setAuxId(aux)`: Sets the auxiliary value of the item.
    * **Parameters:**
        * `aux`: `number` - The new auxiliary value. 
* `setCount(count)`: Sets the quantity (stack size) of the item. 
    * **Parameters:**
        * `count`: `number` - The new item count. 
* `setDamage(damage)`:  Sets the current damage value (durability) of the item.
    * **Parameters:**
        * `damage`: `number` - The new damage value. 
* `setLore(lores)`:  Sets the lore text for the item. 
    * **Parameters:**
        * `lores`: `string[]` - An array of lore strings.
* `setMaxStackSize(stackSize)`: Sets the maximum stack size allowed for the item.
    * **Parameters:**
        * `stackSize`: `number` -  The new maximum stack size.
* `setName(name)`:  Sets a custom name for the item. 
    * **Parameters:**
        * `name`: `string` -  The new custom name. 
* `setStackedByData(stacked)`:  Sets whether the item's stacking should be determined by its data value. 
    * **Parameters:**
        * `stacked`: `boolean` - `true` to enable data-dependent stacking, `false` for default stacking. 
* `setUseDuration(duration)`: Sets the duration (in ticks) for which the item can be used.
    * **Parameters:**
        * `duration`: `number` - The new use duration.
* `use()`:  Simulates using the item (e.g., right-clicking with it).

### Level

Provides functions for interacting with the game level (world).

**Methods (all static):**

* `addParticle(type, position, velocity, size)`: Spawns a particle effect at the specified location.
    * **Parameters:**
        * `type`: `ParticleType` - The type of particle effect. 
        * `position`: `number[]` -  The particle's starting position as [x, y, z].
        * `velocity`: `number[]` -  The particle's initial velocity as [x, y, z]. 
        * `size`: `number` -  The size of the particle. 
* `displayClientMessage(text)`:  Displays a client-side message in the chat.
    * **Parameters:**
        * `text`: `string` -  The message to display. Supports text formatting and multi-line messages.
* `fetchEntity(id, runtime)`: Retrieves an entity by its ID.
    * **Parameters:**
        * `id`: `number` -  The entity's ID.
        * `runtime`: `boolean` - Whether to use the runtime ID (used for receiving packets).
    * **Returns:** 
        * Type: `Entity | null`
        * Description: The `Entity` object if found, otherwise `null`.
* `getAddress()`:  Returns the memory address of the `Level` object.
    * **Returns:** 
        * Type: `number`
        * Description: The memory address.
* `getBlock(id)`: Fetches a `Block` object representing the block at the specified position or with the given ID.
    * **Parameters:**
        * `id`: `number[] | number | string` - The block's position as [x, y, z], the block's numeric ID, or the block's string ID.
    * **Returns:** 
        * Type: `Block`
        * Description: The `Block` object.
* `getBlockData(pos)`: Returns the data value (auxiliary value) of the block at the given position. 
    * **Parameters:**
        * `pos`: `number[]` -  The block's position as [x, y, z]. 
    * **Returns:** 
        * Type: `number`
        * Description: The block's data value.
* `getDimensionId()`:  Returns the ID of the current dimension.
    * **Returns:** 
        * Type: `number`
        * Description: The dimension ID (e.g., 0 - Overworld, 1 - Nether, 2 - The End).
* `getEntities()`: Returns an array of all loaded `Entity` objects in the level. 
    * **Returns:** 
        * Type: `Entity[]`
        * Description: An array of `Entity` objects. 
* `getPlayers()`: Returns an array of all loaded player `Entity` objects in the level. 
    * **Returns:** 
        * Type: `Entity[]`
        * Description: An array of player `Entity` objects.
* `getTime()`: Returns the current time of day in the level.
    * **Returns:** 
        * Type: `number`
        * Description: The level time. See "How Time Works" (documentation not provided).
* `setTime(time)`:  Sets the current time of day in the level.
    * **Parameters:**
        * `time`: `number` -  The desired time value. See "How Time Works" (documentation not provided).

### LocalPlayer

Provides an API for interacting with and manipulating the local player's character in the game.

**Methods (all static):**

* `addEffect(effect)`:  Applies a status effect to the local player. 
    * **Parameters:**
        * `effect`: `Effect` - The `Effect` object to apply.
* `attack(victim)`:  Makes the local player attack the specified entity (player).
    * **Parameters:**
        * `victim`: `Player` - The target player entity. 
* `breakBlock(pos, side)`:  Initiates the process of breaking the block at the specified position.
    * **Parameters:**
        * `pos`: `number[]` - The position of the block as [x, y, z]. 
        * `side`: `BlockSide` - The side of the block to break.
* `buildBlock(pos, offset, side)`:  Simulates a right-click interaction with a block, primarily used for building. 
    * **Parameters:**
        * `pos`: `number[]` -  The position of the block as [x, y, z].
        * `offset`: `number[]` -  An offset from the block's position, allowing for interactions with specific parts of a block. 
        * `side`: `BlockSide` - The side of the block to interact with.
* `click(rightClick)`: Simulates a mouse click.
    * **Parameters:**
        * `rightClick`: `boolean` - `true` for a right-click, `false` for a left-click. 
* `getAbility(id)`: Retrieves a specific player ability. 
    * **Parameters:**
        * `id`: `AbilityType` - The type of ability.
    * **Returns:** 
        * Type: `Ability`
        * Description: The `Ability` object.
* `getAddress()`:  Returns the memory address of the `LocalPlayer` object. 
    * **Returns:** 
        * Type: `number`
        * Description: The memory address. 
* `getArmor(slot)`:  Returns the `Item` object equipped in the specified armor slot. 
    * **Parameters:**
        * `slot`: `ArmorSlot` - The armor slot (e.g., `ArmorSlot.HELMET`). 
    * **Returns:** 
        * Type: `Item`
        * Description: The `Item` object in the armor slot.
* `getCarriedItem()`: Returns the `Item` object currently held in the main hand. 
    * **Returns:** 
        * Type: `Item`
        * Description: The `Item` object in the main hand.
* `getDistanceTo(target)`:  Calculates the distance between the local player and another entity or a set of coordinates.
    * **Parameters:**
        * `target`: `Entity | number[]` -  The target entity or position as [x, y, z]. 
    * **Returns:** 
        * Type: `number`
        * Description: The distance.
* `getEntityTypeId()`: Returns the entity type ID of the local player.
* `getEyeHeight()`:  Returns the eye height of the local player.
* `getFallDistance()`:  Returns the current fall distance of the local player. 
    * **Returns:** 
        * Type: `number`
        * Description:  The fall distance.
* `getGameType()`: Returns the current game mode of the local player.
    * **Returns:** 
        * Type: `number`
        * Description: The game mode code (e.g., 0 - Survival, 1 - Creative).
* `getHealth()`:  Returns the current health points (HP) of the local player. 
    * **Returns:** 
        * Type: `number`
        * Description:  The player's HP (0-20). 
* `getId(runtime)`:  Returns the ID of the local player.
    * **Parameters:**
        * `runtime`: `boolean` - Whether to use the runtime ID (used for receiving packets). 
    * **Returns:** 
        * Type: `number`
        * Description: The player's ID. 
* `getInterpolatedPos()`: Returns the interpolated position of the local player (use for smoother rendering). 
    * **Returns:** 
        * Type: `number[]`
        * Description:  The interpolated position as [x, y, z].
* `getInterpolatedRot()`: Returns the interpolated head rotation of the local player (use for smoother rendering). 
    * **Returns:** 
        * Type: `number[]`
        * Description:  The interpolated head rotation as [pitch, yaw]. 
* `getNameTag()`:  Returns the name tag displayed above the local player.
    * **Returns:** 
        * Type: `string`
        * Description: The player's name tag.
* `getOffhandItem()`: Returns the `Item` object currently held in the offhand slot.
    * **Returns:** 
        * Type: `Item`
        * Description: The `Item` object in the offhand slot. 
* `getPitch()`: Returns the current pitch (vertical rotation) of the player's head. 
    * **Returns:** 
        * Type: `number`
        * Description: The pitch value.
* `getPos()`:  Returns the current coordinates of the local player. 
    * **Returns:** 
        * Type: `number[]`
        * Description: The player's position as [x, y, z].
* `getPosX()`:  Returns the current X-coordinate of the local player.
    * **Returns:** 
        * Type: `number`
        * Description: The player's X-coordinate. 
* `getPosY()`: Returns the current Y-coordinate of the local player.
    * **Returns:** 
        * Type: `number`
        * Description: The player's Y-coordinate.
* `getPosZ()`:  Returns the current Z-coordinate of the local player. 
    * **Returns:** 
        * Type: `number`
        * Description: The player's Z-coordinate. 
* `getRot()`: Returns the current head rotation of the local player. 
    * **Returns:** 
        * Type: `number[]`
        * Description:  The head rotation as [pitch, yaw].
* `getSize()`:  Returns the size of the local player's hitbox.
    * **Returns:** 
        * Type: `number[]`
        * Description: The hitbox size as [width, height].
* `getSizeX()`:  Returns the width of the local player's hitbox.
    * **Returns:** 
        * Type: `number`
        * Description: The hitbox width. 
* `getSizeY()`:  Returns the height of the local player's hitbox.
    * **Returns:** 
        * Type: `number`
        * Description: The hitbox height. 
* `getStatusFlag(flagId)`: Returns the status of a specific entity status flag for the local player. 
    * **Parameters:**
        * `flagId`: `EntityStatusFlag` - The ID of the status flag.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the flag is set, `false` otherwise. 
* `getUsername()`:  Returns the username of the local player. 
    * **Returns:** 
        * Type: `string`
        * Description: The player's username.
* `getVel()`:  Returns the current velocity of the local player.
    * **Returns:** 
        * Type: `number[]`
        * Description:  The velocity as [x, y, z].
* `getVelX()`:  Returns the X-component of the local player's velocity.
    * **Returns:** 
        * Type: `number`
        * Description: The X-velocity. 
* `getVelY()`:  Returns the Y-component of the local player's velocity.
    * **Returns:** 
        * Type: `number`
        * Description:  The Y-velocity.
* `getVelZ()`:  Returns the Z-component of the local player's velocity. 
    * **Returns:** 
        * Type: `number`
        * Description:  The Z-velocity.
* `getViewPerspective()`: Returns the current camera perspective of the local player.
    * **Returns:** 
        * Type: `number`
        * Description:  The perspective code (0-2).
* `getYaw()`:  Returns the current yaw (horizontal rotation) of the player's head.
    * **Returns:** 
        * Type: `number`
        * Description: The yaw value. 
* `hasEffect(effectId)`: Checks if the local player is currently affected by the specified status effect.
    * **Parameters:**
        * `effectId`: `number` -  The numeric ID of the effect. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the player has the effect, `false` otherwise.
* `isAlive()`: Checks if the local player is currently alive based on the game's internal state.
    * **Returns:** 
        * Type: `boolean`
        * Description:  `true` if alive, `false` otherwise. 
* `isFalling()`:  Checks if the local player is currently falling based on the game's internal state. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if falling, `false` otherwise. 
* `isInLava()`: Checks if the local player is currently in lava based on the game's internal state. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if in lava, `false` otherwise. 
* `isInWall()`: Checks if the local player is currently inside a wall based on the game's internal state. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if in a wall, `false` otherwise.
* `isInWater()`:  Checks if the local player is currently in water based on the game's internal state.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if in water, `false` otherwise. 
* `isOnGround()`:  Checks if the local player is currently on the ground based on the game's internal state. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if on the ground, `false` otherwise.
* `jump()`:  Makes the local player jump. 
* `removeEffect(effectId)`: Removes the specified status effect from the local player.
    * **Parameters:**
        * `effectId`: `number` -  The numeric ID of the effect to remove. 
* `sendMessage(text)`:  Sends a chat message to the server. 
    * **Parameters:**
        * `text`: `string` -  The chat message to send.
* `sendPacket(packet)`: Sends a network packet to the server.
    * **Parameters:**
        * `packet`: `Packets` - The `Packet` object to send.
* `sendPosition()`:  Sends the local player's current position to the server. 
* `setGameType(gametype)`: Sets the game mode of the local player.
    * **Parameters:**
        * `gametype`: `number` -  The desired game mode code.
* `setNameTag(nametag)`:  Sets the name tag displayed above the local player (client-side only). 
    * **Parameters:**
        * `nametag`: `string` - The new name tag to display. 
* `setOffhandItem(slot, freeSlot)`:  Moves the item from the specified inventory slot to the offhand slot.
    * **Parameters:**
        * `slot`: `number` - The inventory slot containing the item to move. 
        * `freeSlot` (optional): `number` -  If provided, specifies a free slot where the item currently in the offhand slot should be moved.
* `setOnGround(onGround)`:  Sets the local player's "on ground" state (client-side only). 
    * **Parameters:**
        * `onGround`: `boolean` -  `true` to set the player as on the ground, `false` for in the air.
* `setPitch(pitch)`:  Sets the pitch (vertical rotation) of the local player's head. 
    * **Parameters:**
        * `pitch`: `number` -  The new pitch value.
* `setPos(pos)`: Teleports the local player to the specified coordinates.
    * **Parameters:**
        * `pos`: `number[]` - The new position as [x, y, z]. 
* `setPosRel(relPos)`:  Moves the local player relative to their current position. 
    * **Parameters:**
        * `relPos`: `number[]` - The relative movement vector as [x, y, z].
* `setPosX(posX)`: Sets the X-coordinate of the local player.
    * **Parameters:**
        * `posX`: `number` - The new X-coordinate.
* `setPosY(posY)`:  Sets the Y-coordinate of the local player. 
    * **Parameters:**
        * `posY`: `number` - The new Y-coordinate.
* `setPosZ(posZ)`:  Sets the Z-coordinate of the local player. 
    * **Parameters:**
        * `posZ`: `number` -  The new Z-coordinate. 
* `setRot(rot)`: Sets the head rotation of the local player.
    * **Parameters:**
        * `rot`: `number[]` -  The new head rotation as [pitch, yaw]. 
* `setSize(hitboxSize)`: Sets the size of the local player's hitbox.
    * **Parameters:**
        * `hitboxSize`: `number[]` - The new hitbox size as [width, height].
* `setSizeX(sizeX)`: Sets the width of the local player's hitbox. 
    * **Parameters:**
        * `sizeX`: `number` -  The new hitbox width. 
* `setSizeY(sizeY)`:  Sets the height of the local player's hitbox.
    * **Parameters:**
        * `sizeY`: `number` -  The new hitbox height.
* `setSprinting(sprinting)`:  Sets the sprinting state of the local player for one tick. 
    * **Parameters:**
        * `sprinting`: `boolean` -  `true` to make the player sprint, `false` to stop sprinting. 
* `setStepHeight(stepHeight)`: Sets the maximum step height of the local player. 
    * **Parameters:**
        * `stepHeight`: `number` -  The new maximum step height. 
* `setUsername(username)`: Sets the username displayed for the local player (client-side only).
    * **Parameters:**
        * `username`: `string` -  The new username to display.
* `setVel(vel)`:  Sets the velocity of the local player, potentially creating a speed boost effect. 
    * **Parameters:**
        * `vel`: `number` -  The desired velocity. 
* `setVelX(velX)`: Sets the X-component of the local player's velocity. 
    * **Parameters:**
        * `velX`: `number` - The new X-velocity.
* `setVelY(velY)`:  Sets the Y-component of the local player's velocity. 
    * **Parameters:**
        * `velY`: `number` -  The new Y-velocity. 
* `setVelZ(velZ)`:  Sets the Z-component of the local player's velocity.
    * **Parameters:**
        * `velZ`: `number` -  The new Z-velocity.
* `setViewPerspective(perspective)`: Sets the camera perspective of the local player. 
    * **Parameters:**
        * `perspective`: `number` -  The desired perspective code. 
* `setYaw(yaw)`:  Sets the yaw (horizontal rotation) of the local player's head.
    * **Parameters:**
        * `yaw`: `number` -  The new yaw value.

### Memory (Deprecated - Use with Caution)

**Warning:** This class provides direct memory manipulation functions. 
Using these functions incorrectly can lead to crashes or unexpected behavior. It is highly recommended to avoid using this class unless you have a deep understanding of memory management and the game's internals. 

**Methods (all static):**

* `delete(address)`: Frees the memory allocated at the specified address.
    * **Parameters:**
        * `address`: `number` - The memory address to free.
* `getBaseAddress()`:  Returns the base address of the game in memory. 
    * **Returns:** 
        * Type: `number`
        * Description: The game's base memory address.
* `getBoolean(address)`:  Reads a boolean value from the specified memory address. 
    * **Parameters:**
        * `address`: `number` -  The memory address. 
    * **Returns:** 
        * Type: `boolean`
        * Description: The boolean value at the address.
* `getByte(address)`: Reads a byte value from the specified memory address. 
    * **Parameters:**
        * `address`: `number` - The memory address. 
    * **Returns:** 
        * Type: `number`
        * Description:  The byte value at the address. 
* `getDouble(address)`: Reads a double-precision floating-point value from the specified memory address. 
    * **Parameters:**
        * `address`: `number` - The memory address.
    * **Returns:** 
        * Type: `number`
        * Description: The double value at the address.
* `getFloat(address)`:  Reads a single-precision floating-point value from the specified memory address.
    * **Parameters:**
        * `address`: `number` -  The memory address. 
    * **Returns:** 
        * Type: `number`
        * Description: The float value at the address.
* `getInt(address)`: Reads a 32-bit integer value from the specified memory address.
    * **Parameters:**
        * `address`: `number` - The memory address. 
    * **Returns:** 
        * Type: `number`
        * Description: The integer value at the address.
* `getInt64(address)`: Reads a 64-bit integer value from the specified memory address.
    * **Parameters:**
        * `address`: `number` - The memory address.
    * **Returns:** 
        * Type: `number`
        * Description: The 64-bit integer value at the address. 
* `getShort(address)`:  Reads a 16-bit integer value (short) from the specified memory address. 
    * **Parameters:**
        * `address`: `number` - The memory address. 
    * **Returns:** 
        * Type: `number`
        * Description: The short value at the address.
* `malloc(size)`: Allocates a block of memory of the specified size. 
    * **Parameters:**
        * `size`: `number` - The size of the memory block to allocate, in bytes. 
    * **Returns:** 
        * Type: `number`
        * Description:  The memory address of the allocated block.
* `memcpy(destination, source, length)`: Copies a block of memory from one location to another. 
    * **Parameters:**
        * `destination`: `number` - The memory address to copy to.
        * `source`: `number` -  The memory address to copy from. 
        * `length`: `number` - The number of bytes to copy.
* `read(address, length)`:  Reads a sequence of bytes from memory and returns them as a string.
    * **Parameters:**
        * `address`: `number` -  The starting memory address. 
        * `length`: `number` - The number of bytes to read. 
    * **Returns:** 
        * Type: `string`
        * Description: The read bytes as a string.
* `setBoolean(address, value)`: Writes a boolean value to the specified memory address. 
    * **Parameters:**
        * `address`: `number` -  The memory address to write to.
        * `value`: `boolean` -  The boolean value to write. 
* `setByte(address, value)`: Writes a byte value to the specified memory address. 
    * **Parameters:**
        * `address`: `number` - The memory address to write to.
        * `value`: `number` -  The byte value to write. 
* `setDouble(address, value)`: Writes a double-precision floating-point value to the specified memory address. 
    * **Parameters:**
        * `address`: `number` -  The memory address to write to. 
        * `value`: `number` -  The double value to write. 
* `setFloat(address, value)`:  Writes a single-precision floating-point value to the specified memory address. 
    * **Parameters:**
        * `address`: `number` - The memory address to write to. 
        * `value`: `number` -  The float value to write. 
* `setInt(address, value)`:  Writes a 32-bit integer value to the specified memory address.
    * **Parameters:**
        * `address`: `number` - The memory address to write to. 
        * `value`: `number` -  The integer value to write. 
* `setInt64(address, value)`: Writes a 64-bit integer value to the specified memory address.
    * **Parameters:**
        * `address`: `number` -  The memory address to write to.
        * `value`: `number` -  The 64-bit integer value to write.
* `setShort(address, value)`: Writes a 16-bit integer value (short) to the specified memory address. 
    * **Parameters:**
        * `address`: `number` -  The memory address to write to. 
        * `value`: `number` - The short value to write. 
* `tryGetBlock(address)`: Attempts to retrieve a `Block` object from the specified memory address.
    * **Parameters:**
        * `address`: `number` - The memory address. 
    * **Returns:** 
        * Type: `Block | null`
        * Description: The `Block` object if found at the address, otherwise `null`. 
* `tryGetEffect(address)`: Attempts to retrieve an `Effect` object from the specified memory address.
    * **Parameters:**
        * `address`: `number` -  The memory address.
    * **Returns:** 
        * Type: `Effect | null`
        * Description: The `Effect` object if found at the address, otherwise `null`. 
* `tryGetEntity(address)`:  Attempts to retrieve an `Entity` object from the specified memory address.
    * **Parameters:**
        * `address`: `number` - The memory address. 
    * **Returns:** 
        * Type: `Entity | null`
        * Description: The `Entity` object if found at the address, otherwise `null`. 
* `tryGetItem(address)`: Attempts to retrieve an `Item` object from the specified memory address.
    * **Parameters:**
        * `address`: `number` - The memory address.
    * **Returns:** 
        * Type: `Item | null`
        * Description: The `Item` object if found at the address, otherwise `null`. 
* `tryGetPacket(address)`: Attempts to retrieve a `Packet` object from the specified memory address. 
    * **Parameters:**
        * `address`: `number` - The memory address.
    * **Returns:** 
        * Type: `Packet | null`
        * Description: The `Packet` object if found at the address, otherwise `null`.
* `tryGetString(address)`: Attempts to retrieve a string from the specified memory address.
    * **Parameters:**
        * `address`: `number` - The memory address. 
    * **Returns:** 
        * Type: `string | null`
        * Description: The string if found at the address, otherwise `null`. 
* `tryGetTag(address)`: Attempts to retrieve a `Tag` object from the specified memory address.
    * **Parameters:**
        * `address`: `number` -  The memory address.
    * **Returns:** 
        * Type: `Tag | null`
        * Description: The `Tag` object if found at the address, otherwise `null`. 
... (continued)

* `trySetBlock(address, value)`: Attempts to write a `Block` object to the specified memory address.
    * **Parameters:**
        * `address`: `number` -  The memory address to write to.
        * `value`: `Block` -  The `Block` object to write. 
* `trySetEffect(address, value)`: Attempts to write an `Effect` object to the specified memory address.
    * **Parameters:**
        * `address`: `number` -  The memory address to write to. 
        * `value`: `Effect` - The `Effect` object to write. 
* `trySetEntity(address, value)`:  Attempts to write an `Entity` object to the specified memory address. 
    * **Parameters:**
        * `address`: `number` -  The memory address to write to. 
        * `value`: `Entity` - The `Entity` object to write. 
* `trySetItem(address, value)`:  Attempts to write an `Item` object to the specified memory address.
    * **Parameters:**
        * `address`: `number` - The memory address to write to. 
        * `value`: `Item` -  The `Item` object to write.
* `trySetPacket(address, value)`: Attempts to write a `Packet` object to the specified memory address. 
    * **Parameters:**
        * `address`: `number` - The memory address to write to.
        * `value`: `Packet` -  The `Packet` object to write. 
* `trySetString(address, value)`: Attempts to write a string to the specified memory address.
    * **Parameters:**
        * `address`: `number` -  The memory address to write to.
        * `value`: `string` -  The string to write. 
* `trySetTag(address, value)`: Attempts to write a `Tag` object to the specified memory address. 
    * **Parameters:**
        * `address`: `number` - The memory address to write to. 
        * `value`: `Tag` -  The `Tag` object to write.
* `virtualProtect(address, length, protect)`: Modifies the memory protection attributes of a region of memory.
    * **Parameters:**
        * `address`: `number` - The starting memory address of the region.
        * `length`: `number` - The size of the memory region, in bytes. 
        * `protect`: `number` -  The desired memory protection flags. See [Microsoft Documentation](https://learn.microsoft.com/ru-ru/windows/win32/api/memoryapi/nf-memoryapi-virtualprotect) for details. 
    * **Returns:** 
        * Type: `number`
        * Description: The previous memory protection value of the region. 
* `write(address, bytes)`:  Writes an array of bytes to the specified memory address.
    * **Parameters:**
        * `address`: `number` - The memory address to write to.
        * `bytes`: `number[]` -  The array of bytes to write. 
    * **Returns:** 
        * Type: `boolean`
        * Description:  `true` if the write was successful, `false` otherwise.

### Module

Represents a cheat module with configurable settings.

**Constructor:**

```javascript
new Module(name, description, toggleable, category, callbacks)
```
| Parameter | Type | Description |
|---|---|---|
| `name` | `string` | The name of the module. |
| `description` | `string` | A description of the module's functionality. |
| `toggleable` | `boolean` | Whether the module can be toggled on and off. |
| `category` | `ModuleCategory | number` |  The category the module belongs to. |
| `callbacks` | `object` | An object containing callback functions for various events related to the module. 
     |  | `onClick`: `function`  - A function to be called when the module is clicked. |

**Methods:**

* `addSetting(setting)`:  Adds a setting to the module. 
    * **Parameters:**
        * `setting`: `Setting` - The `Setting` object to add. 
* `getCategory()`: Returns the category the module belongs to.
    * **Returns:** 
        * Type: `Constants#ModuleCategory`
        * Description: The module's category.
* `getDescription()`:  Returns the description of the module. 
    * **Returns:** 
        * Type: `string`
        * Description: The module's description. 
* `getKeybind()`:  Returns the keybind (Virtual Key code) associated with toggling the module, if any. 
    * **Returns:** 
        * Type: `Constants#VK | null`
        * Description: The keybind, or `null` if no keybind is set.
* `getName()`:  Returns the name of the module. 
    * **Returns:** 
        * Type: `string`
        * Description: The module's name.
* `getSetting(index)`: Returns the `Setting` object at the specified index in the module's settings list. 
    * **Parameters:**
        * `index`: `number` -  The index of the setting to retrieve. 
    * **Returns:** 
        * Type: `Setting`
        * Description:  The `Setting` object. 
* `getSettings()`:  Returns an array of all `Setting` objects associated with the module. 
    * **Returns:** 
        * Type: `Setting[]`
        * Description: An array of `Setting` objects.
* `hasSettings()`: Checks if the module has any settings defined. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if the module has settings, `false` otherwise. 
* `isEnabled()`:  Checks if the module is currently enabled. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if enabled, `false` otherwise. 
* `isToggleable()`: Checks if the module can be toggled on and off.
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if toggleable, `false` otherwise. 
* `removeSetting(setting)`:  Removes the specified setting from the module. 
    * **Parameters:**
        * `setting`: `Setting` -  The `Setting` object to remove. 
* `setKeybind(keybind)`:  Sets the keybind (Virtual Key code) for toggling the module. 
    * **Parameters:**
        * `keybind`: `VK` - The new keybind. 
* `toggle(enabled, notify)`: Toggles the module on or off. 
    * **Parameters:**
        * `enabled` (optional): `boolean` -  If provided, sets the module to the specified enabled state. 
        * `notify` (optional): `boolean` - If `true`, displays a notification indicating the change in the module's state. 

### ModuleManager

Manages the cheat's collection of modules.

**Methods (all static):**

* `addModule(module)`:  Registers a module with the cheat, making it available for use.
    * **Parameters:**
        * `module`: `Module` -  The `Module` object to register.
* `getModule(name)`: Retrieves a module by its name.
    * **Parameters:**
        * `name`: `string` -  The name of the module to find.
    * **Returns:** 
        * Type: `Module`
        * Description: The `Module` object, or `null` if not found. 
* `getModules()`: Returns an array of all registered modules.
    * **Returns:** 
        * Type: `Module[]`
        * Description: An array of `Module` objects. 
* `removeModule(module)`:  Unregisters a module from the cheat. 
    * **Parameters:**
        * `module`: `Module` - The `Module` object to unregister. 

### OverlayObject

Represents an object within the cheat's overlay system.

**Constructor:**

```javascript
new OverlayObject(identifier, position, callbacks) 
```

| Parameter | Type | Description |
|---|---|---|
| `identifier` | `string` | A unique identifier for the overlay object. |
| `position` | `number[]` | The initial position of the object within the overlay as [x, y]. |
| `callbacks` | `object` |  An object containing callback functions for events. 
     |  | `onDraw`: `function` -  A function to be called when the object needs to be rendered. |

**Methods:**

* `focus()`:  Brings the object into focus, typically used for handling input. 
* `getHeight()`:  Returns the height of the object. 
    * **Returns:** 
        * Type: `number`
        * Description: The object's height.
* `getId()`:  Returns the unique identifier of the object.
    * **Returns:** 
        * Type: `string`
        * Description: The object's identifier.
* `getPos()`: Returns the current position of the object within the overlay.
    * **Returns:** 
        * Type: `number[]`
        * Description: The position as [x, y].
* `getPosX()`:  Returns the X-coordinate of the object's position. 
    * **Returns:** 
        * Type: `number`
        * Description:  The X-coordinate. 
* `getPosY()`:  Returns the Y-coordinate of the object's position.
    * **Returns:** 
        * Type: `number`
        * Description: The Y-coordinate. 
* `getSize()`:  Returns the size of the object. 
    * **Returns:** 
        * Type: `number[]`
        * Description:  The size as [width, height].
* `getWidth()`:  Returns the width of the object.
    * **Returns:** 
        * Type: `number`
        * Description: The object's width.
* `hide()`:  Stops the object from being rendered in the overlay. 
* `isDragging()`: Checks if the object is currently being dragged by the user. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if dragging, `false` otherwise. 
* `isFocused()`: Checks if the object is currently in focus. 
    * **Returns:** 
        * Type: `boolean`
        * Description:  `true` if focused, `false` otherwise. 
* `isHovered()`: Checks if the mouse cursor is currently hovering over the object. 
    * **Returns:** 
        * Type: `boolean`
        * Description:  `true` if hovered, `false` otherwise.
* `isShowing()`:  Checks if the object is currently being rendered (visible) in the overlay. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if visible, `false` otherwise. 
* `setHeight(height)`: Sets the height of the object. 
    * **Parameters:**
        * `height`: `number` -  The new height. 
* `setPos(pos)`: Sets the position of the object within the overlay.
    * **Parameters:**
        * `pos`: `number[]` - The new position as [x, y]. 
* `setPosX(posX)`:  Sets the X-coordinate of the object's position. 
    * **Parameters:**
        * `posX`: `number` -  The new X-coordinate.
* `setPosY(posY)`: Sets the Y-coordinate of the object's position.
    * **Parameters:**
        * `posY`: `number` -  The new Y-coordinate. 
* `setSize(size)`: Sets the size of the object. 
    * **Parameters:**
        * `size`: `number[]` -  The new size as [width, height]. 
* `setWidth(width)`:  Sets the width of the object.
    * **Parameters:**
        * `width`: `number` -  The new width. 
* `show()`:  Makes the object visible and rendered in the overlay.

### OverlaySystem

Manages the cheat's graphical overlay, which is displayed over the game screen.

**Methods (all static):**

* `getFocusedObject()`:  Returns the overlay object that currently has focus. 
    * **Returns:** 
        * Type: `OverlayObject`
        * Description:  The focused `OverlayObject`.
* `getHoveredObject()`: Returns the overlay object that the mouse cursor is currently hovering over, or `null` if none. 
    * **Returns:** 
        * Type: `OverlayObject | null`
        * Description:  The hovered `OverlayObject`.
* `getObject(identifier)`:  Retrieves an overlay object by its unique identifier.
    * **Parameters:**
        * `identifier`: `string` -  The identifier of the object. 
    * **Returns:** 
        * Type: `OverlayObject`
        * Description:  The `OverlayObject` with the matching identifier.
* `getObjects()`: Returns an array of all registered overlay objects. 
    * **Returns:** 
        * Type: `OverlayObject[]`
        * Description:  An array of `OverlayObject`s.
* `getObjectsUnderMouse()`:  Returns an array of all overlay objects that are currently under the mouse cursor, or `null` if none.
    * **Returns:** 
        * Type: `OverlayObject[] | null`
        * Description:  An array of `OverlayObject`s under the mouse.
* `registerObject(object)`: Adds an overlay object to the system.
    * **Parameters:**
        * `object`: `OverlayObject` -  The `OverlayObject` to register.
* `unregisterObject(object)`:  Removes an overlay object from the system. 
    * **Parameters:**
        * `object`: `OverlayObject` - The `OverlayObject` to unregister.

### Renderer

Provides functions for rendering graphics on the game screen, both in 2D and 3D. 

**Methods (all static):**

* `drawBlock(pos, posX, posY, size)`:  Renders a block at a specified 2D screen position. 
    * **Parameters:**
        * `pos`: `number[]` - The block's world position as [x, y, z]. 
        * `posX`: `number` - The X-coordinate on the screen where the block should be rendered. 
        * `posY`: `number` -  The Y-coordinate on the screen where the block should be rendered.
        * `size`: `number` -  The size of the rendered block.
* `drawBox3D(startPos, endPos, color, thickness)`: Draws a 3D box outline in the game world. 
    * **Parameters:**
        * `startPos`: `number[]` - The starting corner of the box as [x, y, z].
        * `endPos`: `number[]` - The ending corner of the box as [x, y, z].
        * `color`: `number[]` - The color of the box as [red, green, blue, alpha]. Values should be in the range 0-1.
        * `thickness`: `number` - The thickness of the box lines.
* `drawBox3D(startPos, endPos, color)`: Draws a filled 3D box in the game world.
    * **Parameters:**
        * `startPos`: `number[]` - The starting corner of the box as [x, y, z]. 
        * `endPos`: `number[]` - The ending corner of the box as [x, y, z].
        * `color`: `number[]` - The color of the box as [red, green, blue, alpha]. Values should be in the range 0-1.
* `drawFilledRect(startPos, endPos, color, thickness)`:  Draws a filled 2D rectangle on the screen.
    * **Parameters:**
        * `startPos`: `number[]` -  The top-left corner of the rectangle as [x, y]. 
        * `endPos`: `number[]` -  The bottom-right corner of the rectangle as [x, y].
        * `color`: `number[]` - The color of the rectangle as [red, green, blue, alpha]. Values should be in the range 0-1.
        * `thickness`: `number` - The thickness of the rectangle's border (if applicable).
* `drawItem(item, posX, posY, size, enchanted)`:  Renders an item at a specified 2D screen position.
    * **Parameters:**
        * `item`: `Item` - The `Item` object to render. 
        * `posX`: `number` - The X-coordinate on the screen where the item should be rendered. 
        * `posY`: `number` - The Y-coordinate on the screen where the item should be rendered. 
        * `size`: `number` - The size of the rendered item. 
        * `enchanted`: `boolean` -  If `true`, renders the item with an enchantment glint. 
* `drawLine(startPos, endPos, color, thickness)`: Draws a 2D line on the screen.
    * **Parameters:**
        * `startPos`: `number[]` - The starting point of the line as [x, y]. 
        * `endPos`: `number[]` - The ending point of the line as [x, y].
        * `color`: `number[]` - The color of the line as [red, green, blue, alpha]. Values should be in the range 0-1.
        * `thickness`: `number` -  The thickness of the line. 
* `drawLine3D(startPos, endPos, color, thickness)`:  Draws a 3D line in the game world. 
    * **Parameters:**
        * `startPos`: `number[]` - The starting point of the line as [x, y, z].
        * `endPos`: `number[]` - The ending point of the line as [x, y, z]. 
        * `color`: `number[]` - The color of the line as [red, green, blue, alpha]. Values should be in the range 0-1.
        * `thickness`: `number` - The thickness of the line. 
* `drawOutlineBox3D(startPos, endPos, color, thickness)`:  Draws a 3D box outline in the game world. 
    * **Parameters:**
        * `startPos`: `number[]` - The starting corner of the box as [x, y, z].
        * `endPos`: `number[]` -  The ending corner of the box as [x, y, z].
        * `color`: `number[]` - The color of the outline as [red, green, blue, alpha]. Values should be in the range 0-1.
        * `thickness`: `number` -  The thickness of the outline lines. 
* `drawRect(startPos, endPos, color, thickness)`: Draws a 2D rectangle outline on the screen. 
    * **Parameters:**
        * `startPos`: `number[]` - The top-left corner of the rectangle as [x, y].
        * `endPos`: `number[]` -  The bottom-right corner of the rectangle as [x, y].
        * `color`: `number[]` -  The color of the outline as [red, green, blue, alpha]. Values should be in the range 0-1. 
        * `thickness`: `number` - The thickness of the outline lines. 
* `drawText(text, pos, color, rotation, size)`: Draws text on the screen in Minecraft style.
    * **Parameters:**
        * `text`: `string` - The text to draw.
        * `pos`: `number[]` -  The position where the text should be drawn as [x, y].
        * `color`: `number[]` - The color of the text as [red, green, blue, alpha]. Values should be in the range 0-1. 
        * `rotation`: `number` -  The rotation of the text in degrees. 
        * `size`: `number` -  The font size of the text.
* `drawTexture(texture, pos, size, uv, uvSize)`: Draws a portion of a texture on the screen.
    * **Parameters:**
        * `texture`: `Texture` -  The `Texture` object to draw from. 
        * `pos`: `number[]` - The position where the texture should be drawn as [x, y]. 
        * `size`: `number[]` - The size of the rendered texture portion as [width, height]. 
        * `uv`: `number[]` - The coordinates within the texture to start drawing from, as [u, v]. 
        * `uvSize`: `number[]` - The size of the portion to draw from the texture as [width, height]. 
* `getTextHeight(text, size)`:  Calculates and returns the height of the provided text using the specified font size.
    * **Parameters:**
        * `text`: `string` -  The text to measure.
        * `size`: `number` -  The font size.
    * **Returns:** 
        * Type: `number`
        * Description: The text height. 
* `getTextSize(text, size)`:  Calculates and returns the size (width and height) of the provided text.
    * **Parameters:**
        * `text`: `string` -  The text to measure. 
        * `size`: `number` -  The font size.
    * **Returns:** 
        * Type: `number[]`
        * Description:  The text size as [width, height]. 
* `getTextWidth(text, size)`:  Calculates and returns the width of the provided text using the specified font size. 
    * **Parameters:**
        * `text`: `string` -  The text to measure.
        * `size`: `number` - The font size. 
    * **Returns:** 
        * Type: `number`
        * Description: The text width. 
* `setClippingRects(rect)`: Defines a rectangular clipping region, preventing rendering outside of this area. Restore the clipping region immediately after rendering to avoid unexpected behavior.
    * **Parameters:**
        * `rect`: `number[]` - The clipping rectangle as [from_x, from_y, to_x, to_y]. 
* `worldToScreen(pos, screenPos)`: Converts 3D world coordinates to 2D screen coordinates.
    * **Parameters:**
        * `pos`: `number[]` - The 3D world coordinates as [x, y, z]. 
        * `screenPos`: `number[]` - An array to store the resulting 2D screen coordinates.
    * **Returns:** 
        * Type: `boolean`
        * Description:  `true` if the conversion was successful, `false` otherwise (e.g., if the point is behind the camera). 

### Tessellator

Provides low-level access to the game's rendering system, allowing for custom geometry drawing.

**Warning:**  This class is intended for advanced users who understand rendering concepts. Using it incorrectly can lead to visual glitches or crashes.

**Methods (all static):**

* `begin(mode, vertexCount)`: Begins defining a new batch of geometry to be rendered. 
    * **Parameters:**
        * `mode`: `number` - The rendering mode (e.g., triangles, lines). 
        * `vertexCount`: `number` - The expected number of vertices in this batch.
* `color(color)`: Sets the color for subsequent vertices in the batch.
    * **Parameters:**
        * `color`: `number[]` - The color as [red, green, blue, alpha]. Values should be in the range 0-1.
* `draw(material, texture)`: Renders the defined geometry batch using the specified material and texture (optional). 
    * **Parameters:**
        * `material`: `number` - The memory address of the material to use. 
        * `texture` (optional): `Texture` -  The texture to apply to the geometry.
* `getAddress()`: Returns the memory address of the `Tessellator` object.
    * **Returns:** 
        * Type: `number`
        * Description: The memory address.
* `vertex(vertex)`: Adds a vertex to the current geometry batch. 
    * **Parameters:**
        * `vertex`: `number[]` - The vertex coordinates as [x, y, z]. 

### Texture

Represents a texture loaded into the game. 

**Methods:**

* `isLoaded()`:  Checks if the texture has been successfully loaded and is not the default "missing texture" image. 
    * **Returns:** 
        * Type: `boolean`
        * Description: `true` if loaded, `false` otherwise.


## Hooks

Hooks are functions that are automatically called by the cheat at specific points during the game's execution. 
You can define your own functions to be executed as hooks, allowing you to modify game behavior or inject your own logic.

**Note:** Some hooks are "preventable," meaning you can use the `preventDefault()` function within the hook to stop the game from performing its default action.

**Hooks:**

* `onAttack(victim)`: Called right before the local player attacks an entity. 
    * **Parameters:**
        * `victim`: `Entity` - The target entity being attacked.
    * Preventable: `true`
* `onChat(text)`: Called before a chat message is sent to the server.
    * **Parameters:**
        * `text`: `string` - The chat message.
    * Preventable: `true`
* `onConnect(ip, port)`: Called when connecting to a game server.
    * **Parameters:**
        * `ip`: `string` - The server's IP address.
        * `port`: `number` - The server's port. 
* `onContainerTick(container)`: Called every tick while a container (e.g., chest) is open. 
    * **Parameters:**
        * `container`: `Container` -  The `Container` object. 
* `onContinueDestroyBlock(posX, posY, posZ, side, block)`: Called every tick while the player is continuing to break a block.
    * **Parameters:**
        * `posX`: `number` -  The X-coordinate of the block (block position, not pointed coordinates). 
        * `posY`: `number` -  The Y-coordinate of the block. 
        * `posZ`: `number` - The Z-coordinate of the block. 
        * `side`: `BlockSide` -  The side of the block being broken. 
        * `block`: `Block` -  The `Block` object being broken.
    * Preventable: `true` 
* `onDisconnect()`:  Called when disconnecting from a game server. 
* `onEffectAdded(effect)`:  Called when a status effect is applied to an entity. 
    * **Parameters:**
        * `effect`: `Effect` - The `Effect` object representing the applied effect.
* `onEffectRemoved(effect)`:  Called when a status effect is removed from an entity.
    * **Parameters:**
        * `effect`: `Effect` - The `Effect` object representing the removed effect.
* `onEffectUpdated(effect)`:  Called when a status effect on an entity is updated (e.g., its duration or amplifier changes). 
    * **Parameters:**
        * `effect`: `Effect` - The `Effect` object representing the updated effect.
* `onKeyClick(button, pressed)`: Called when a keyboard key is pressed or released.
    * **Parameters:**
        * `button`: `VK` -  The Virtual Key code of the key.
        * `pressed`: `boolean` -  `true` if the key was pressed, `false` if released.
    * Preventable: `true`
* `onMouseClick(posX, posY, key, pressed)`: Called when a mouse button is pressed or released.
    * **Parameters:**
        * `posX`: `number` - The X-coordinate of the mouse cursor. 
        * `posY`: `number` - The Y-coordinate of the mouse cursor. 
        * `key`: `number` - The mouse button code (e.g., 1 - left button, 2 - right button). 
        * `pressed`: `boolean` - `true` if the button was pressed, `false` if released. 
    * Preventable: `true`
* `onMouseMove(posX, posY)`:  Called when the mouse cursor moves.
    * **Parameters:**
        * `posX`: `number` -  The new X-coordinate of the mouse cursor.
        * `posY`: `number` -  The new Y-coordinate of the mouse cursor.
    * Preventable: `true` 
* `onMouseWheelSpin(up)`: Called when the mouse wheel is scrolled. 
    * **Parameters:**
        * `up`: `boolean` - `true` if the wheel was scrolled up, `false` if scrolled down.
    * Preventable: `true` 
* `onPostRender()`: Called after the cheat's main menu has been rendered. Often used for drawing custom elements in the overlay.
* `onPreRender()`:  Called before the cheat's main menu is rendered.  
* `onReceivePacket(packet)`: Called before a network packet is processed by the client.
    * **Parameters:**
        * `packet`: `Packet` -  The incoming `Packet` object. 
    * Preventable: `true`
* `onRender3D()`: Called every frame to allow for 3D rendering within the game world. 
* `onScriptDisable()`:  Called when the cheat script is disabled (e.g., unloaded or reloaded).
* `onScriptEnable()`: Called when the cheat script is enabled (e.g., loaded or reloaded).
* `onSendPacket(packet)`:  Called before a network packet is sent to the server. 
    * **Parameters:**
        * `packet`: `Packet` - The outgoing `Packet` object.
    * Preventable: `true`
* `onStartDestroyBlock(posX, posY, posZ, side, block)`: Called when the player starts breaking a block. 
    * **Parameters:**
        * `posX`: `number` -  The X-coordinate of the block.
        * `posY`: `number` - The Y-coordinate of the block.
        * `posZ`: `number` -  The Z-coordinate of the block.
        * `side`: `BlockSide` - The side of the block being broken.
        * `block`: `Block` - The `Block` object being broken. 
    * Preventable: `true` 
* `onStopDestroyBlock()`: Called when the player stops breaking a block. 
    * Preventable: `true`
* `onTick()`: Called every game tick. The default tick rate is 20 ticks per second, but this can be modified by the `Timer` module or changes in game speed. 
* `onUseItem(item, posX, posY, posZ, side, offsetX, offsetY, offsetZ, block)`: Called when the player uses an item (typically by right-clicking). 
    * **Parameters:**
        * `item`: `Item` - The `Item` object being used. 
        * `posX`: `number` - The X-coordinate of the block being interacted with. 
        * `posY`: `number` - The Y-coordinate of the block. 
        * `posZ`: `number` -  The Z-coordinate of the block.
        * `side`: `BlockSide` - The side of the block.
        * `offsetX`: `number` -  The offset from `posX` to the exact point of interaction (since `posX` is an integer block position). 
        * `offsetY`: `number` -  The offset from `posY`.
        * `offsetZ`: `number` -  The offset from `posZ`.
        * `block`: `Block` - The `Block` object being interacted with.
    * Preventable: `true` 

## Packets

This section provides information about classes related to network packets.

**Classes:**

 * `AdventureSettingsPacket`
 * `AnimatePacket`
 * `AttributeData`
 * `AvailableCommandsPacket`
 * `BlockEntityDataPacket`
 * `ChangeDimensionPacket`
 * `ChunkRadiusUpdatedPacket`
 * `CommandStepPacket`
 * `ContainerClosePacket`
 * `ContainerOpenPacket`
 * `ContainerSetSlotPacket`
 * `DisconnectPacket`
 * `DropItemPacket`
 * `EntityEventPacket`
 * `EntityFallPacket`
 * `FullChunkDataPacket`
 * `HurtArmorPacket`
 * `InteractPacket`
 * `ItemFrameDropItemPacket`
 * `LevelEventPacket`
 * `LevelSoundEventPacket`
 * `MapInfoRequestPacket`
 * `MobArmorEquipmentPacket`
 * `MobEffectPacket`
 * `MobEquipmentPacket`
 * `MovePlayerPacket`
 * `Packet`: The base class for all packets. 
 * `PlayStatusPacket`
 * `PlayerActionPacket`
 * `PlayerInputPacket`
 * `PlayerListEntry`
 * `PlayerListPacket`
 * `RemoveBlockPacket`
 * `RemoveEntityPacket`
 * `RequestChunkRadiusPacket`
 * `RespawnPacket`
 * `SetDifficultyPacket`
 * `SetEntityLinkPacket`
 * `SetEntityMotionPacket`
 * `SetHealthPacket`
 * `SetPlayerGameTypePacket`
 * `SetTimePacket`
 * `SetTitlePacket`
 * `ShowCreditsPacket`
 * `TakeItemEntityPacket`
 * `TextPacket`
 * `TransferPacket`
 * `UpdateAttributesPacket`
 * `UpdateBlockPacket`
 * `UseItemPacket`


## Settings 

This section provides classes for creating and managing settings for cheat modules.

**Classes:**

* `ButtonSetting` 
* `ColorSetting`
* `ContainerSetting`
* `EnumEntry`
* `EnumSetting`
* `KeySetting`
* `Setting`: The base class for all settings. 
* `SliderSetting`
* `SwitchSetting`
* `TextSetting`

## Tags

This section describes classes for working with NBT (Named Binary Tag) data, which is used to store information about items. 

**Classes:**

* `ByteTag`
* `CompoundTag`
* `DoubleTag`
* `FloatTag`
* `Int64Tag`
* `IntTag`
* `ListTag`
* `ShortTag`
* `StringTag`

## Constants

Constants are used to represent fixed values that have specific meanings within the game or the cheat. They are organized into classes (enums) for better clarity and readability.

**Constant Classes:**

* `AbilityType`: Describes types of player abilities (e.g., `FLYING`, `NOCLIP`).
* `ArmorSlot`: Represents different armor slots (e.g., `HELMET`, `CHESTPLATE`).
* `Block`: Contains constants for all block types in the game (e.g., `STONE`, `GRASS`).
* `BlockSide`:  Describes the sides of a block (e.g., `UP`, `DOWN`).
* `ContainerSlots`: Represents different slots within containers (e.g., `INVENTORY`, `HOTBAR
