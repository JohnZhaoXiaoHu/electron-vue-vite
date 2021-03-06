# electron-vue-vite

![awesome-vite](https://camo.githubusercontent.com/abb97269de2982c379cbc128bba93ba724d8822bfbe082737772bd4feb59cb54/68747470733a2f2f63646e2e7261776769742e636f6d2f73696e647265736f726875732f617765736f6d652f643733303566333864323966656437386661383536353265336136336531353464643865383832392f6d656469612f62616467652e737667)
![GitHub license](https://img.shields.io/github/license/caoxiemeihao/electron-vue-vite?style=flat)
![GitHub stars](https://img.shields.io/github/stars/caoxiemeihao/electron-vue-vite?color=fa6470&style=flat)
![GitHub forks](https://img.shields.io/github/forks/caoxiemeihao/electron-vue-vite?style=flat)


**English | [įŽäŊä¸­æ](README.zh-CN.md)**

đĨŗ Very simple `Electron` + `Vue3` + `Vite2` boilerplate.

## Run Setup

  ```bash
  # clone the project
  git clone git@github.com:caoxiemeihao/electron-vue-vite.git

  # enter the project directory
  cd electron-vue-vite

  # install dependency(Recommend use yarn)
  yarn

  # develop
  yarn dev
  ```

## Directory

```tree
â
âââ configs
â   âââ vite-main.config.ts          Main-process config file, for -> src/main
â   âââ vite-preload.config.ts       Preload-script config file, for -> src/preload
â   âââ vite-renderer.config.ts      Renderer-script config file, for -> src/renderer
â
âââ scripts
â   âââ build.mjs                    Build script, for -> npm run build
â   âââ electron-builder.config.mjs
â   âââ watch.mjs                    Develop script, for -> npm run dev
â
âââ src
â   âââ main                         Main-process source code
â   âââ preload                      Preload-script source code
â   âââ renderer                     Renderer-process source code
â
```

#### `dist` and `src`

- Once `npm run dev` or `npm run build` is executed. Will be generated `dist`, it is the same as the `src` structure.

- This ensures the accuracy of path calculation.

```tree
âââ dist
â   âââ main
â   âââ preload
â   âââ renderer
âââ src
â   âââ main
â   âââ preload
â   âââ renderer
â
```

## Communication

**All NodeJsãElectron API invoke passed `Preload-script`**

* **src/preload/index.ts**

  ```typescript
  // --------- Expose some API to Renderer process. ---------
  contextBridge.exposeInMainWorld('fs', fs)
  contextBridge.exposeInMainWorld('ipcRenderer', ipcRenderer)
  ```

* **src/renderer/src/main.ts**

  ```typescript
  console.log('fs', window.fs)
  console.log('ipcRenderer', window.ipcRenderer)
  ```

## Mian window
<img width="400px" src="https://raw.githubusercontent.com/caoxiemeihao/blog/main/electron-vue-vite/screenshot/electron-15.png" />

## Wechat

<img width="244px" src="https://raw.githubusercontent.com/caoxiemeihao/blog/main/assets/wechat/group/qrcode.jpg" />
