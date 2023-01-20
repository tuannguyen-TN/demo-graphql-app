# GraphQL Demo Application

## Introduction to GraphQL

GraphQL is an open-source data query and manipulation language for APIs, and a runtime for fulfilling queries with existing data.

Instead of fetching everything there is to offer like we usually do with REST APIs, now with GraphQL, only a single entry point is in use, then the data is queried and fetched through describing its schema that mirrors its return shape in JSON.

## GraphQL Pokemon Demonstration

In this application, using a powerful combination of Vue 3 + TypeScript + Vite, I am going to demonstrate how to apply GraphQL to a Vue application, as well as how to write GraphQL queries to get data.

To run GraphQL queries with Vue 3, there are some libraries that need installing beforehand. Make sure to check out first [GraphQL](https://graphql.org/) and [Vue Apollo](https://v4.apollo.vuejs.org/).

For the GraphQL endpoint, this [GraphiQL](https://graphql-pokemon2.vercel.app/) is utilized.

## How to run

Clone the repo onto local machine

```
git clone https://github.com/tuannguyen-TN/demo-graphql-app.git
```

Get into the repo folder, and install the dependencies

```
cd demo-graphql-app/
yarn install
```

When finished, run the application on localhost

```
yarn dev
```

When visited for the first time, the app shows no Pokemon, as there is no argument for the component to render any.

Therefore, you can add a number after the end of URL, behind the last /, and the page will render that number of Pokemons.
NOTE: If you enter a negative number, it will work in the opposite way. As for -1, the app displays all the Pokemon there are from the GraphQL entry point.

## Vue 3 + TypeScript + Vite

This template should help get you started developing with Vue 3 and TypeScript in Vite. The template uses Vue 3 `<script setup>` SFCs, check out the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Recommended IDE Setup

- [VS Code](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur) + [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin).

## Type Support For `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [TypeScript Vue Plugin (Volar)](https://marketplace.visualstudio.com/items?itemName=Vue.vscode-typescript-vue-plugin) to make the TypeScript language service aware of `.vue` types.

If the standalone TypeScript plugin doesn't feel fast enough to you, Volar has also implemented a [Take Over Mode](https://github.com/johnsoncodehk/volar/discussions/471#discussioncomment-1361669) that is more performant. You can enable it by the following steps:

1. Disable the built-in TypeScript Extension
   1. Run `Extensions: Show Built-in Extensions` from VSCode's command palette
   2. Find `TypeScript and JavaScript Language Features`, right click and select `Disable (Workspace)`
2. Reload the VSCode window by running `Developer: Reload Window` from the command palette.
