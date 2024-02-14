# JSON to HTML toolkit 🥳

[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![npm version](https://badge.fury.io/js/json2html-toolkit.svg)](https://badge.fury.io/js/json2html-toolkit)
[![GitHub forks](https://img.shields.io/github/forks/robinjac/json2html-toolkit)](https://github.com/robinjac/json2html-toolkit/network)
[![GitHub stars](https://img.shields.io/github/stars/robinjac/json2html-toolkit)](https://github.com/robinjac/json2html-toolkit/stargazers)

## Description

Tiny library/tool to print out or insert a json object into the dom 🤘

## Features

- No dependencies 🥹
- Flexible and customizable 💪

## Installation

To install `json2html-toolkit`, you can use npm:

```bash
npm install json2html-toolkit
```

Or copy the source. It's tiny, just one file! 🤫 (But please give it some ⭐️ if you do 🥹)

## Usage

To print out as an html string, use `toHTMLString`. Here's an example:

```ts
import { toHTMLString } from "json2html-toolkit";

const jsonData = {
  /* Your JSON data */
};

const result = toHTMLString(jsonData);

console.log(result);
```

The output is customizable. For example, you can pass a styling object with the configuration:

```ts
import { toHTMLString } from "json2html-toolkit";

// Style like how chat gpt prints out json 🤘
const styling = {
  properties: "#df3079",
  number: "#df3079",
  string: "#00a67d",
  null: "#2e95d3",
  boolean: "#2e95d3",
  braces: "#d9d9e3",
  brackets: "#d9d9e3",
  comma: "#d9d9e3",
  semi: "#d9d9e3",
};

const result = toHTMLString(jsonData, { styling });
```

Change spacing:

```ts
const result = toHTMLString(jsonData, { styling, spacing: 4 }); // Default is 2
```

You can also use CSS variables. By default, the variables are named `--json2dom-<styling-property>`. For example, to change the color of number types, you would target `--json2dom-number` variable. If you want a different prefix, you can change it using `prefixCssVariables`:

```ts
const result = toHTMLString(jsonData, {
  styling,
  spacing: 4,
  prefixCssVariables: "my-custom-prefix",
});
```

To insert directly into the DOM, you can use `insertAt`. Here's an example:

```ts
import { insertAt } from "json2html-toolkit";

const jsonData = {
  /* Your JSON data */
};

insertAt("some-target-selector", jsonData);
```

`insertAt` uses `document.querySelector` under the hood, so you can use `#some-id` or `.some-class`, any selector you want.

`json2html-toolkit` is fully written in typescript and exports the following:

```ts
export type JSONValue =
  | string
  | number
  | boolean
  | null
  | JSONObject
  | JSONArray;

// Do we need any more here? 🤔
export type Styling = {
  properties?: string;
  number?: string;
  string?: string;
  null?: string;
  boolean?: string;
  braces?: string;
  brackets?: string;
  semi?: string;
  comma?: string;
};

export type Config = {
  space?: number;
  styling?: Styling;
  prefixCssVariables?: string;
};

export function toHtmlString(json: JSONValue, config?: Config): string;

export function insertAt(
  selector: string,
  json: JSONValue,
  config?: Config
): void;
```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgements

This project was inspired by the great work done at [highlightjs](https://github.com/highlightjs/highlight.js), [prismjs](https://github.com/PrismJS/prism) and other similar libraries! 🍻

## Support

If you have any questions or issues, please open an [issue](https://github.com/robinjac/json2html-toolkit/issues) on GitHub.
