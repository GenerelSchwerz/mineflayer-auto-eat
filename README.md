<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [mineflayer-auto-eat](#mineflayer-auto-eat)
  - [Install](#install)
  - [Example](#example)
  - [API](#api)
    - [Properties](#properties)
      - [bot.autoEat.disabled](#botautoeatdisabled)
      - [bot.autoEat.isEating](#botautoeatiseating)
      - [bot.autoEat.options](#botautoeatoptions)
      - [bot.autoEat.options.priority](#botautoeatoptionspriority)
      - [bot.autoEat.options.startAt](#botautoeatoptionsstartat)
      - [bot.autoEat.options.bannedFood](#botautoeatoptionsbannedfood)
      - [bot.autoEat.options.ignoreInventoryCheck](#botautoeatoptionsignoreinventorycheck)
      - [bot.autoEat.options.checkOnItemPickup](#botautoeatoptionscheckonitempickup)
      - [bot.autoEat.options.eatingTimeout](#botautoeatoptionseatingtimeout)
      - [bot.autoEat.options.useOffhand](#botautoeatoptionsuseoffhand)
      - [bot.autoEat.options.equipOldItem](#botautoeatoptionsequipolditem)
    - [Methods](#methods)
      - [bot.autoEat.enable()](#botautoeatenable)
      - [bot.autoEat.disable()](#botautoeatdisable)
      - [bot.autoEat.eat()](#botautoeateat)
  - [Author](#author)
  - [Show your support](#show-your-support)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

<h1 align="center">mineflayer-auto-eat</h1>

![npm](https://img.shields.io/npm/v/mineflayer-auto-eat)
![npm bundle size](https://img.shields.io/bundlephobia/min/mineflayer-auto-eat)
![CI](https://github.com/link-discord/mineflayer-auto-eat/actions/workflows/ci.yml/badge.svg)
![GitHub](https://img.shields.io/github/license/link-discord/mineflayer-auto-eat)

> An auto eat plugin for mineflayer

## Install

```sh
npm install mineflayer-auto-eat
```

## Example

```js
const mineflayer = require('mineflayer')
const autoeat = require('mineflayer-auto-eat').default

const bot = mineflayer.createBot({
    host: process.argv[2],
    port: process.argv[3],
    username: process.argv[4],
    password: process.argv[5]
})

bot.loadPlugin(autoEat)

bot.on('autoeat_started', (item, offhand) => {
    console.log(`Eating ${item.name} in ${offhand ? 'offhand' : 'hand'}`)
})

bot.on('autoeat_error', (error) => {
    console.error(error)
})

bot.on('autoeat_finished', (item, offhand) => {
    console.log(`Finished eating ${item.name} in ${offhand ? 'offhand' : 'hand'}`)
})
```

## API

### Properties

#### bot.autoEat.disabled

Boolean value indicating whether auto eat is disabled or not.

#### bot.autoEat.isEating

Boolean value indicating whether the bot is currently eating or not.
This value should never be set manually.

#### bot.autoEat.options

Can be changed to change the settings for the auto eat plugin
(Should only be changed when the bot has spawned)

Example

```js
bot.once('spawn', () => {
    bot.autoEat.options = {
        priority: 'saturation',
        startAt: 16,
        bannedFood: ['golden_apple', 'enchanted_golden_apple', 'rotten_flesh']
    }
})
```

#### bot.autoEat.options.priority

Acceptable Values are "saturation" or "foodPoints"

default: "foodPoints"

#### bot.autoEat.options.startAt

If the bot has less or equal food points than this value, the bot will start eating

default: 14

#### bot.autoEat.options.bannedFood

The bot will not eat the items in the array.

default: []

#### bot.autoEat.options.ignoreInventoryCheck

Forces bot to disable inventory window click confirmation.
Related to [PrismarineJS/mineflayer#2030](https://github.com/PrismarineJS/mineflayer/issues/2030)

default: false

#### bot.autoEat.options.checkOnItemPickup

Attempts to eat food when the bot picks up an item and the bot reached the startAt threshold.

default: true

#### bot.autoEat.options.eatingTimeout

Timeout of food consumption. If eating takes too long, we're assuming that
it is finished after that time. Time in seconds, null or negative value means
"no timeout".

default: 3

#### bot.autoEat.options.useOffhand

If true, the bot will use the offhand slot to eat food.

default: false

#### bot.autoEat.options.equipOldItem

If true, the bot will equip the previous item after eating.

default: true

### Methods

#### bot.autoEat.enable()

Calling this function will enable the plugin
(its enabled by default ofc)

#### bot.autoEat.disable()

Calling this function will disable the plugin

#### bot.autoEat.eat()

If you want to call the eat function manually
you can do it like this below

```js
bot.autoEat
    // Setting to true will use offhand slot
    .eat(true)
    .then(() => {
        console.log('Finished eating')
    })
    .catch((error) => {
        console.error(error)
    })
```

## Author

👤 **Link#0069**

-   Github: [@link-discord](https://github.com/link-discord)

## Show your support

Give a ⭐️ if this plugin helped you!

---

```

```
