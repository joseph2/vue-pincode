# @j2only/pincode

 ![npm publish](https://github.com/j2only/pincode/actions/workflows/npm.yml/badge.svg) [![npm](https://img.shields.io/npm/v/@j2only/pincode.svg)](https://www.npmjs.com/package/@j2only/pincode) ![npm bundle size (scoped)](https://img.shields.io/bundlephobia/minzip/%40j2only/pincode) [![contributions welcome](https://img.shields.io/badge/contributions-welcome-brightgreen.svg?style=flat)](https://github.com/j2only/pincode/issues) [![TypeScript](https://img.shields.io/badge/%3C%2F%3E-TypeScript-%230074c1.svg)](https://www.typescriptlang.org/) ![GitHub](https://img.shields.io/github/license/j2only/pincode)

Vue.js pincode input component. :lock:
Written entirely on Vue 3 Composition API with Typescript and Vite. Compatible only with Vue.js 3.x.

- Simple pincode input field
- Minimal style
- Customizable
- Smooth animations
- Optional keyboard input (with backspace and delete keys support)

You can check a [DEMO HERE](https://j2only.github.io/pincode/)

## Installation

Install this component via package manager:

```bash
yarn add @j2only/pincode
```

or

```bash
npm install --save @j2only/pincode
```

## Usage

Import the component in your app and pass some settings:

```typescript
<template>
    <vue-pincode
        name="pincode"
        ref="pincodeInput"
        :length="4"
        :releaseSuccess="true"
        :releaseSuccessDelay="2500"
        :releaseErrorDelay="500"
        :customButton="true"
        :keyboardInput="true"
        :focusRequired="true"
        :activeElement="activeEl"
        @clickButton="buttonFn"
        @clickCustomButton="cButtonFn"
        @pincode="checkPincode"
    />
</template>

<script setup lang="ts">
import VuePincode from "@j2only/pincode";

const pincodeInput = ref()
const cButtonFn = ref(() => alert("the custom button clicked!"))
const answer = "1234"
const activeEl = ref(document.body) as Ref<HTMLElement>

function checkPincode(pincode: string) {
    setTimeout(() => {
        if (pincode === answer)
            pincodeInput.value.triggerSuccess()
        else
            pincodeInput.value.triggerMiss()
    }, 300)
}
</script>
```

## Props

As you can see, the component accepts some props:

| Prop                | Type    | Default       | Description                                                                                          |
| ------------------- | ------- | ------------- | ---------------------------------------------------------------------------------------------------- |
| name                | String  | "pincode"     | Unique ID, in case of using several components on one page                                           |
| length              | Number  | 4             | Required pincode length, minimum 2, maximum 8                                                        |
| releaseSuccess      | Boolean | true          | Reset state after delay when entered pincode is correct                                              |
| releaseSuccessDelay | Number  | 2500          | Delay to reset state after entered pincode is correct (milliseconds)                                 |
| releaseErrorDelay   | Number  | 500           | Delay to reset state after entered pincode is invalid (milliseconds)                                 |
| customButton        | Boolean | false         | Show custom button                                                                                   |
| keyboardInput       | Boolean | true          | Dynamic prop for keyboard input capability                                                           |
| focusRequired       | Boolean | false         | Enable keyboard input only if vue-pincode if focused                                                 |
| activeElement       | Object  | document.body | Default focused HTML element with vue-pincode, use if component placed on modal or something similar |

## CSS Variables

Also, you can customize some styles via CSS Variables:

| Variable                     | Default       | Description                             |
| ---------------------------- | ------------- | --------------------------------------- |
| --pc-color-button            | #010101       | Color of digits                         |
| --pc-color-button-pressed    | #474747       | Color of pressed digit                  |
| --pc-color-button-bg         | #f6f6f6       | Color of digits background              |
| --pc-color-button-bg-pressed | #eaeaea       | Color of pressed digit background       |
| --pc-color-field-normal      | #234567       | Color of fields                         |
| --pc-color-field-success     | #42b983       | Color of fields when pincode is correct |
| --pc-color-field-error       | #eb0c0c       | Color of fields when pincode is invalid |
| --pc-custom-button-icon      | base64 string | Custom button icon                      |

## Events

| Event             | Description                                                          |
| ----------------- | -------------------------------------------------------------------- |
| pincode           | Is triggered when the entered pincode length is equal to length prop |
| clickButton       | Is triggered when the some of digit buttons is pressed               |
| clickCustomButton | Is triggered when the custom button is pressed                       |

## Project development

- `yarn dev` compiles and hot-reloads demo for development
- `yarn lint` lints and fixes files
- `yarn build` compiles and minifies production files and demo

## Licensing

MIT License
Forked from [@weslinkde/vue-pincode](https://github.com/weslinkde/vue-pincode), Dominik Lenz :copyright: 2020 [Weslink GmbH](https://weslink.de), [MIT License](LICENSE)
