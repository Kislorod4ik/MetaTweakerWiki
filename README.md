<div align="center">

  <p>
    <img src="https://cdn-icons-png.flaticon.com/512/1844/1844987.png" alt="icon" width="128" height="128">
  </p>

  <h1>MetaTweaker</h1>

  Альфа версия мода.

  Мало функций. **ItemRightClick**, **ItemUse**, ~~the end~~.

  Мало методов в **MCWorld**, **MCPlayer**

  **MCItemStack** был переписан, методов много

</div>

<h2>Контент</h2>

+ [Кератив таб](#creative-tab)
  + [Создание](#creaite-creative-tab)
  + [Методы](#methods-creative-tab)
+ [Предмет](#item)
  + [Создание](#create-item-common)
  + [Создание инструмента](#create-item-tool)
  + [Методы](#methods-item)
+ [Материал-блок](#material-block)
  + [Создание](#create-material-block)
  + [Методы](#methods-material-block)
+ [Дроп-блок](#material-drop-block)
  + [Создание](#create-drop-block)
  + [Методы](#methods-drop-block)
+ [Звук](#sound)
  + [Создание](#create-sound)
  + [Методы](#methods-sound)
+ [Блок](#block)
  + [Создание](#create-block)
  + [Создание с звуком](#create-block-sound)
  + [Создание с дропом](#create-block-drop)
  + [Методы](#methods-block)


<h2>Функции</h2>

+ [Предметные](#functions-item)
  + [ItemRightClick](#function-item-rightclick)
  + [ItemUse](#function-item-use)

<h2>MC-API</h2>

+ [MCItemStack](#api-itemstack)
+ [MCWorld](#api-world)
+ [MCPlayer](#api-player)

<h2>Дополнительно</h2>

+ [Список mapColor](#dop-mapcolors)
+ [Список creativeTab](#dop-creativetabs)



<br><h1 id="creative-tab">Кератив таб</h1>

```zs
IZenCreativeTab createCreativeTab(String unlocalizedName, @Optional IItemStack iconIItemStack);
```

<h2 id="creaite-creative-tab">Создание</h2>

```zs
import mods.metatweaker.Factory;
var creativeTab = Factory.createCreativeTab("test_tab", <minecraft:stick>).register();
```

<h2 id="methods-creative-tab">Методы</h1>

| Тип данных      | Метод                                      |
|-----------------|--------------------------------------------|
| String          | getUnlocalizedName                         |
| IZenCreativeTab | setUnlocalizedName(String unlocalizedName) |
| IItemStack      | getIconStackItem                           |
| IZenCreativeTab | setIconStackItem(IItemStack iItemStack)    |
| IZenCreativeTab | register()                                 |

<br><h1 id="item">Предмет</h1>

```zs
IZenItem createItem(String unlocalizedName);
```

<h2 id="create-item-common">Создание</h2>

```zs
// Пример #1
import mods.metatweaker.Factory;
var test_item1 = Factory.createItem("test_item1")
  .setTextureName("test_item_texture")
  .setCreativeTab("misc")
  .addLore("Test lore1", "Test lore2")
  .register();
  
// Пример #2
import mods.metatweaker.Factory;
var test_item2 = Factory.createItem("test_item1");
test_item2.setTextureName("test_item_texture");
test_item2.setCreativeTab("misc");
test_item2.register(); 
```

<h2 id="create-item-common">Создание инструмента</h2>

```zs
import mods.metatweaker.Factory;
var pickaxe_5_1500 = Factory.createItem("test_tool")
  .setTextureName("test_item_texture")
  .setCreativeTab("tools")
  .setTool("pickaxe", 5)
  .setMaxDamage(1500)
  .register();
```

<h2 id="methods-item">Методы</h1>

| Тип данных      | Метод                                               |
|-----------------|-----------------------------------------------------|
| String          | getUnlocalizedName                                  |
| IZenItem        | setUnlocalizedName(String unlocalizedName)          |
| String          | getTextureName                                      |
| IZenItem        | setTextureName(String textureName)                  |
| String          | getCreativeTab                                      |
| IZenItem        | setCreativeTab(String creativeTab)                  |
| IZenItem        | setCreativeTab(IZenCreativeTab creativeTab)         |
| int             | getMaxStackSize                                     |
| IZenItem        | setMaxStackSize(int maxDamage)                      |
| int             | getMaxDamage                                        |
| IZenItem        | setMaxDamage(int maxDamage)                         |
| boolean         | getUnbreakable                                      |
| IZenItem        | setUnbreakable(boolean unbreakable)                 |
| boolean         | getNoRepair                                         |
| IZenItem        | setNoRepair(boolean noRepair)                       |
| String          | getToolClass                                        |
| IZenItem        | setToolClass(String toolClass)                      |
| int             | getToolLevel                                        |
| IZenItem        | setToolLevel(int toolLevel)                         |
| boolean         | getEnchantInAnvil                                   |
| IZenItem        | setEnchantInAnvil(boolean enchantInAnvil)           |
| boolean         | getEnchantInTable                                   |
| IZenItem        | setEnchantInTable(boolean enchantInTable)           |
| IZenItem        | setTool(String toolClass, @Optional int toolLevel)  |
| float           | getDigSpeed                                         |
| IZenItem        | setDigSpeed(float digSpeed)                         |
| String[]        | getLore                                             |                                  |
| IZenItem        | addLore(String... lore)                             |
| IItemRightClick | getItemRightClick()                                 |
| IZenItem        | setItemRightClick(IItemRightClick onItemRightClick) |
| IItemUse        | getItemUse()                                        |
| IZenItem        | setItemUse(IItemUse onItemUse)                      |
| IZenItem        | register()                                          |

<br><h1 id="block-drop">Дроп-блок</h1>

```zs
IZenDropBlock createDropBlock(IItemStack dropIItemStack)
```

<h2 id="create-block-material">Создание</h2>

```zs
// Пример #1
import mods.metatweaker.Factory;
var drop1_1 = Factory.createDropBlock(<minecraft:stick> * 2);
var drop1_2 = Factory.createDropBlock(<minecraft:bedrock>).setRandomChanceDrop(85).setMultiplierFromFortune(5)
var drop1_3 = Factory.createDropBlock(<minecraft:stone>).setFortuneActive(true);
block1.addDrop(drop1_1, drop1_2, drop1_3);

// Пример #2
import mods.metatweaker.Factory;
block2.addDrop(
  Factory.createDropBlock(<minecraft:stick> * 2),
  Factory.createDropBlock(<minecraft:bedrock>).setRandomChanceDrop(85).setMultiplierFromFortune(5),
  Factory.createDropBlock(<minecraft:stone>).setFortuneActive(true)
);
```

<h2 id="methods-drop-block">Методы</h2>

| Тип данных      | Метод                                               |
|-----------------|-----------------------------------------------------|
| IItemStack      | getDropIItemStack                                   |
| IZenDropBlock   | setDropIItemStack(IItemStack dropIItemStack)        |
| boolean         | getFortuneActive                                    |
| IZenDropBlock   | setFortuneActive(boolean fortuneActive)             |
| int             | getRandomChanceDrop                                 |
| IZenDropBlock   | setRandomChanceDrop(int randomChanceDrop)           |
| int             | getMultiplierFromFortune                            |
| IZenDropBlock   | setMultiplierFromFortune(int multiplierFromFortune) |
| int             | getAmount                                           |


<br><h1 id="block-material">Материал-блок</h1>

```zs
IZenMaterial createMaterial(String idMapColor, @Optional IBlock block)
```

<h2 id="create-block-material">Создание</h2>

```zs
// Пример #1
import mods.metatweaker.Factory;
var material_extends_stone = Factory.createMaterial("stone", <minecraft:stone>)
  .setBurning(true);
  
// Пример #2
import mods.metatweaker.Factory;
var custom_material_burn_replaceable = Factory.createMaterial("lime")
  .setBurning(true)
  .setReplaceable(true);
```


<h2 id="methods-block-material">Методы</h1>

| Тип данных   | Метод                                                 |
|--------------|-------------------------------------------------------|
| String       | getIdMapColor()                                       |
| IZenMaterial | setIdMapColor(String idMapColor)                      |
| boolean      | getBurning()                                          |
| IZenMaterial | setBurning(boolean isBurn)                            |
| boolean      | getAdventureModeExempt()                              |
| IZenMaterial | setAdventureModeExempt(boolean isAdventureModeExempt) |
| boolean      | getRequiresTool()                                     |
| IZenMaterial | setRequiresTool(boolean isRequiresTool)               |
| boolean      | getReplaceable()                                      |
| IZenMaterial | setReplaceable(boolean isReplaceable)                 |


<br><h1 id="sound">Звук</h1>

```zs
IZenSound createSound(@Optional float volume, @Optional float frequency, @Optional String breakSoundName, @Optional String placeSoundName, @Optional String stepSoundName);
```

<h2 id="create-sound">Создание</h2>

```
config/metatweaker/sounds/break/test_break.ogg

config/metatweaker/sounds/place/test_place.ogg

config/metatweaker/sounds/step/test_step_1.ogg
config/metatweaker/sounds/step/test_step_2.ogg
config/metatweaker/sounds/step/test_step_3.ogg

config/metatweaker/sounds.json
```

```json
{
  "break.metatweaker": {
    "category": "block",
    "sounds": [
      "break/test_break"
    ]
  },
  "place.metatweaker": {
    "category": "block",
    "sounds": [
      "place/test_place"
    ]
  },
  "random.step.metatweaker": {
    "category": "block",
    "sounds": [
      "step/test_step_1",
      "step/test_step_2",
      "step/test_step_3"
    ]
  }
}
```

```zs
// Пример #1
import mods.metatweaker.Factory;
var sound1 = Factory.createSound();
sound.setBreakSound("break.metatweaker");
sound.setPlaceSound("place.metatweaker");
sound.setStepSound("random.step.metatweaker");
block1.setCound(sound1);

// Пример #2
import mods.metatweaker.Factory;
var sound2 = Factory.createSound(1, 1, "break.metatweaker", "place.metatweaker", "random.step.metatweaker");
block2.setCound(sound2);

// Пример #3
import mods.metatweaker.Factory;
block2.setCound(Factory.createSound(1, 1, "break.metatweaker", "place.metatweaker", "random.step.metatweaker"));

// Пример #4
import mods.metatweaker.Factory;
var sound4 = Factory.createSound(0.8, 0.9).setStepSound("random.step.metatweaker");
block4.setCound(sound4);
```


<h1 id="methods-sound">Методы</h1>

| Тип данных | Метод                                |
|------------|--------------------------------------|
| IZenSound  | setBreakSound(String breakSoundName) |
| IZenSound  | getBreakSound()                      |
| IZenSound  | setPlaceSound(String placeSoundName) |
| IZenSound  | getPlaceSound()                      |
| IZenSound  | setStepSound(String stepSoundName)   |
| IZenSound  | getStepSound()                       |
| IZenSound  | setVolume(float volume)              |
| IZenSound  | getVolume()                          |
| IZenSound  | setFrequency(float frequency)        |
| IZenSound  | getFrequency()                       |

<br><h1 id="block">Блок</h1>

```zs
IZenBlock createBlock(String unlocalizedName, IZenMaterial material);
IZenBlock createBlock(String unlocalizedName, IBlock iBlock);
```

<h2 id="create-block">Создание</h2>

```zs
// Пример #1
import mods.metatweaker.Factory;
var test_block1 = Factory.createBlock("test_block1", <minecraft:stone>)
  .setTextureName("test_block_texture")
  .setCreativeTab("misc")
  .register();
  
// Пример #2
import mods.metatweaker.Factory;  
var test_block2 = Factory.createBlock("test_block2", Factory.createMaterial("lime").setReplaceable(true))
  .setTextureName("test_block_texture")
  .setCreativeTab("misc")
  .register();
```

<h2 id="create-block-sound">Создание с звуком</h2>
[Создание звуков](#create-sounds)

```zs
// Пример #1
import mods.metatweaker.Factory;
var test_block1 = Factory.createBlock("test_block1", <minecraft:stone>)
  .setTextureName("test_block_texture")
  .setCreativeTab("misc")
  .setSound(1, 1, "break.metatweaker", "place.metatweaker", "random.step.metatweaker")
  .register();
  
// Пример #2
import mods.metatweaker.Factory;  
var sound = Factory.createSound()
  .setBreakSound("break.metatweaker");
  .setPlaceSound("place.metatweaker");
  .setStepSound("random.step.metatweaker");

var test_block2 = Factory.createBlock("test_block2", <minecraft:stone>)
  .setTextureName("test_block_texture")
  .setCreativeTab("misc")
  .setSound(sound)
  .register();
```

<h2 id="create-block-sound">Создание с дропом</h2>
[Создание дропа](#create-drop-block)

```zs
// Пример #1
import mods.metatweaker.Factory;
var test_block1 = Factory.createBlock("test_block1", <minecraft:stone>)
  .setTextureName("test_block_texture")
  .setCreativeTab("misc")
  .setSound(1, 1, "break.metatweaker", "place.metatweaker", "random.step.metatweaker")
  .addDrop(
    Factory.createDropBlock(<minecraft:stick> * 2),
    Factory.createDropBlock(<minecraft:bedrock>).setRandomChanceDrop(85).setMultiplierFromFortune(5),
    Factory.createDropBlock(<minecraft:stone>).setFortuneActive(true)
  )
  .register();
  
// Пример #2
import mods.metatweaker.Factory;  
var drop1_1 = Factory.createDropBlock(<minecraft:stick> * 2);
var drop1_2 = Factory.createDropBlock(<minecraft:bedrock>)
  .setRandomChanceDrop(85)
  .setMultiplierFromFortune(5)
var drop1_3 = Factory
  .createDropBlock(<minecraft:stone>)
  .setFortuneActive(true);

var test_block2 = Factory.createBlock("test_block2", <minecraft:stone>)
  .setTextureName("test_block_texture")
  .setCreativeTab("misc")
  .setSound(sound)
  .addDrop(drop1_1, drop1_2, drop1_3);
  .register();
```

<h2 id="methods-block">Методы</h1>

| Тип данных      | Метод                                                                                                                                     |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| String          | getUnlocalizedName()                                                                                                                      |
| IZenBlock       | setUnlocalizedName(String unlocalizedName)                                                                                                |
| IZenMaterial    | getMaterial()                                                                                                                             |
| IZenBlock       | setMaterial(IZenMaterial material)                                                                                                        |
| String          | getTextureName()                                                                                                                          |
| IZenBlock       | setTextureName(String textureName)                                                                                                        |
| String          | getCreativeTab()                                                                                                                          |
| IZenBlock       | setCreativeTab(String creativeTab)                                                                                                        |
| IZenBlock       | setCreativeTab(IZenCreativeTab creativeTab)                                                                                               |
| boolean         | getUnbreakable()                                                                                                                          |
| IZenBlock       | setUnbreakable(boolean unbreakable)                                                                                                       |
| float           | getHardness()                                                                                                                             |
| IZenBlock       | setHardness(float hardness)                                                                                                               |
| float           | getResistance()                                                                                                                           |
| IZenBlock       | setResistance(float resistance)                                                                                                           |
| float           | getLightLevel()                                                                                                                           |
| IZenBlock       | setLightLevel(float lightLevel)                                                                                                           |
| int             | getLightOpacity()                                                                                                                         |
| IZenBlock       | setLightOpacity(int lightOpacity)                                                                                                         |
| int             | getRenderType()                                                                                                                           |
| IZenBlock       | setRenderType(int renderType)                                                                                                             |
| String          | getHarvest()                                                                                                                              |
| IZenBlock       | setHarvest(String tool)                                                                                                                   |
| boolean         | getDropFromExplosion()                                                                                                                    |
| IZenBlock       | setDropFromExplosion(boolean dropFromExplosion)                                                                                           |
| int             | getMobilityFlag()                                                                                                                         |
| IZenBlock       | setMobilityFlag(int mobilityFlag)                                                                                                         |
| int             | getHarvestLevel()                                                                                                                         |
| IZenBlock       | setHarvestLevel(int level)                                                                                                                |
| IZenBlock       | setHarvestAndLevel(String harvest, int harvestLevel)                                                                                      |
| IZenDropBlock[] | getDrop()                                                                                                                                 |
| IZenBlock       | addDrop(IZenDropBlock... drop)                                                                                                            |
| int[]           | getExpRange()                                                                                                                             |
| IZenBlock       | setExpRange(int min, int max)                                                                                                             |
| IZenSound       | getSound()                                                                                                                                |
| IZenBlock       | setSound(IZenSound zenSound)                                                                                                              |
| IZenBlock       | setSound(float volume, float frequency, @Optional String breakSoundName, @Optional String placeSoundName, @Optional String stepSoundName) |
| IZenBlock       | register()                                                                                                                                |   

<br><h1 id="functions-item">Предметные</h1>

<h2 id="function-item-rightclick">ItemRightClick</h1>

```zs
// Пример
import mods.metatweaker.Factory;  
Factory.createItem("test_item1")
  .setCreativeTab("misc")
  .setItemRightClick(function(mcItemStack, mcWorld, mcPlayer){
        mcPlayer.sendChat("Успешно");
        mcItemStack.setDisplayName("Йееес");
        return mcItemStack;
   })  
   .register();
```


<h2 id="function-item-use">ItemUse</h1>

```zs
// Пример
import mods.metatweaker.Factory;  
Factory.createItem("test_item1")
  .setCreativeTab("misc")
  .setItemUse(function(mcItemStack, mcPlayer, mcWorld){
        mcItemStack.setAmount(mcItemStack.getAmount() - 1);
        return true;
   })  
   .register();
```

<br><h1 id="api-itemstack">MCItemStack</h1>

| Тип данных   | Метод                               |
|--------------|-------------------------------------|
| void         | damage(int amount, MCPlayer player) |
| String       | getUnlocalizedName()                |
| String       | getDisplayName()                    |
| void         | setDisplayName(String name)         |
| void         | setMaxDamage(int damage)            |
| int          | getMaxStackSize()                   |
| void         | setMaxStackSize(int size)           |
| float        | getBlockHardness()                  |
| void         | setBlockHardness(float hardness)    |
| int          | getDamage()                         |
| IData        | getTag()                            |
| int          | getMaxDamage()                      |
| ILiquidStack | getLiquid()                         |
| void         | setDamage(int damage)               |
| void         | setAmount(int amount)               |
| void         | setTag(IData tag)                   |
| void         | removeTag()                         |
| int          | getAmount()                         |
| boolean      | matches(IItemStack item)            |
| boolean      | matchesExact(IItemStack item)       |
| IBlock       | asBlock()                           |
| MCItemStack  | copy()                              |
| boolean      | equals(Object obj)                  |
| String       | toString()                          |

<br><h1 id="api-world">MCWorld</h1>

| Тип данных | Метод                              |
|------------|------------------------------------|
| boolean    | isDay()                            |
| int        | getBrightness(int x, int y, int z) |
| IDimension | getDimension()                     |
| IBlock     | getBlock(int x, int y, int z)      |

<br><h1 id="api-player">MCPlayer</h1>

| Тип данных | Метод                              |
|------------|------------------------------------|
| String     | getId()                            |
| String     | getName()                          |
| IData      | getData()                          |
| int        | getXP()                            |
| void       | setXP(int newXp)                   |
| void       | removeXP(int amountXp)             |
| void       | update(IData data)                 |
| void       | sendChat(IChatMessage chatMessage) |
| void       | sendChat(String text)              |
| int        | getHotbarSize()                    |
| IItemStack | getHotbarStack(int indexSlot)      |
| int        | getInventorySize()                 |
| IItemStack | getInventoryStack(int indexSlot)   |
| IItemStack | getCurrentItem()                   |
| boolean    | isCreative()                       |
| boolean    | isAdventure()                      |
| void       | give(IItemStack itemStack)         |

<br><h1 id="dop-mapcolors">Список mapColor</h1>

| Индекс     | 
|------------|
| air        |
| grass      |
| sand       |
| cloth      |
| tnt        |
| ice        |
| iron       |
| foliage    |
| snow       |
| clay       |
| dirt       |
| stone      |
| water      |
| wood       |
| quartz     |
| adobe      |
| magenta    |
| light_blue |
| yellow     |
| lime       |
| pink       |
| gray       |
| silver     |
| cyan       |
| purple     |
| blue       |
| brown      |
| green      |
| red        |
| black      |
| gold       |
| diamond    |
| lapis      |
| emerald    |
| obsidian   |
| netherrack |

<br><h1 id="dop-creativetabs">Список creativeTab</h1>

| Индекс         |
|----------------|
| block          |
| decorations    |
| redstone       |
| transportation |
| misc           |
| search         |
| food           |
| tools          |
| combat         |
| brewing        |
| materials      |
| inventory      |

