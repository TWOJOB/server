# [우분투](https://ubuntu.com/download/server)로 서버만들기!


**튜토리얼**

- 🌏 서버 컴퓨터에 [우분투](https://ubuntu.com/download/server) 설치
- 🎮 마크 페널[[aaPanel](https://www.aapanel.com/index.html)] 설치 및 설정
- 🌐 웹 페널[[ISPConfig](https://www.ispconfig.org/)] 설치 및 설정
- ☁ 클라우드[[nextcloud](https://nextcloud.com/)] 설치 및 설정
- 🚀 [마크](https://www.minecraft.net/ko-kr)서버 시작 하기
- 🚀 커뮤니티 설치
- 🚀 [워드프레스](https://ko.wordpress.org/download/) 다운로드 및 설치
- 🚀 [그누보드](https://sir.kr/g5_pds) 다운로드 및 설치
- 🚀 [Vditor](https://b3log.org/vditor/)

> **NOTE 1** - 👋 이 튜토리얼은 잘 모르는 사람이 기억하기 쉽게 하려고 만든 것입니다. 정확하지 않을 수도 있습니다.
>
> **NOTE 2** - 안되거나 오류가 나면 처음부터 다시 설치를 하다 보면 고쳐지기도 한다`그래서 50번 정도 다시 설치하면 서 알게 된 거...`

----


## 부팅 USB 만들기

### Step 1: [우분투](https://ubuntu.com/download/server) 설치

`[우분투](https://ubuntu.com/download/server)`사이트에 접속후

`Option 2` 클릭

`Download Ubuntu Server (최신버전) LTS` 클릭

> **NOTE** - 최신버전 도는 자신이 원하는 버전 설치

### Step 2: 부팅 가능한 USB 드라이브

[rufus](https://rufus.ie/ko/) 최신버전 설치

rufus실행후 USB선택

부트 선택옆 `선택` 버튼 클릭후 다운받은 .iso 파일 선택

`시작` 클릭

다운로드가 필요합니다.
`예` 클릭

ISO 이미지 모드로 쓰기
`OK` 클릭

USB 모든 데이터 삭제
`확인` 클릭

## Install

### Step 1: 서버 컴퓨터 시작

서버 컴퓨터에 USB연결후 전원키키

부팅화면이 나오면 `F11(또는 F12)`을 눌러 바이오스 화면으로 이동후 USB(부팅USB)로 부팅

### Step 2: [우분투](https://ubuntu.com/download/server) 설치하기

Update or create `next.config.js` with

``` javascript
const withPWA = require('next-pwa')

module.exports = withPWA({
  // other next config
})
```

After running `next build`, this will generate two files in your `distDir` (default is `.next` folder): `workbox-*.js` and `sw.js`, which you need to serve statically, either through static file hosting service or using custom `server.js`.

> If you are using Next.js 9+, you may not need a custom server to host your service worker files. Skip to next section to see the details.

### Option 1: Host Static Files

Copy files to your static file hosting server, so that they are accessible from the following paths: `https://yourdomain.com/sw.js` and `https://yourdomain.com/workbox-*.js`.

One example is using Firebase hosting service to host those files statically. You can automate the copy step using scripts in your deployment workflow.

> For security reasons, you must host these files directly from your domain. If the content is delivered using a redirect, the browser will refuse to run the service worker.

### Option 2: Use Custom Server

When an HTTP request is received, test if those files are requested, then return those static files.

Example `server.js`

```javascript
const { createServer } = require('http')
const { join } = require('path')
const { parse } = require('url')
const next = require('next')

const app = next({ dev: process.env.NODE_ENV !== 'production' })
const handle = app.getRequestHandler()

app.prepare()
  .then(() => {
    createServer((req, res) => {
      const parsedUrl = parse(req.url, true)
      const { pathname } = parsedUrl
      
      if (pathname === '/sw.js' || /^\/(workbox|worker|fallback)-\w+\.js$/.test(pathname)) {
        const filePath = join(__dirname, '.next', pathname)
        app.serveStatic(req, res, filePath)
      } else {
        handle(req, res, parsedUrl)
      }
    })
    .listen(3000, () => {
      console.log(`> Ready on http://localhost:${3000}`)
    })
  })
```

> The following setup has nothing to do with `next-pwa` plugin, and you probably have already set them up. If not, go ahead and set them up.

### Step 2: Add Manifest File (Example)

Create a `manifest.json` file in your `static` folder:

```json
{
  "name": "PWA App",
  "short_name": "App",
  "icons": [
    {
      "src": "/static/icons/android-chrome-192x192.png",
      "sizes": "192x192",
      "type": "image/png",
      "purpose": "any maskable"
    },
    {
      "src": "/static/icons/android-chrome-384x384.png",
      "sizes": "384x384",
      "type": "image/png"
    },
    {
      "src": "/static/icons/icon-512x512.png",
      "sizes": "512x512",
      "type": "image/png"
    }
  ],
  "theme_color": "#FFFFFF",
  "background_color": "#FFFFFF",
  "start_url": "/",
  "display": "standalone",
  "orientation": "portrait"
}
```

### Step 3: Add Head Meta (Example)

Add the following into `_document.jsx` or `_document.tsx`, in `<Head>`:

``` html
<meta name='application-name' content='PWA App' />
<meta name='apple-mobile-web-app-capable' content='yes' />
<meta name='apple-mobile-web-app-status-bar-style' content='default' />
<meta name='apple-mobile-web-app-title' content='PWA App' />
<meta name='description' content='Best PWA App in the world' />
<meta name='format-detection' content='telephone=no' />
<meta name='mobile-web-app-capable' content='yes' />
<meta name='msapplication-config' content='/static/icons/browserconfig.xml' />
<meta name='msapplication-TileColor' content='#2B5797' />
<meta name='msapplication-tap-highlight' content='no' />
<meta name='theme-color' content='#000000' />

<link rel='apple-touch-icon' href='/static/icons/touch-icon-iphone.png' />
<link rel='apple-touch-icon' sizes='152x152' href='/static/icons/touch-icon-ipad.png' />
<link rel='apple-touch-icon' sizes='180x180' href='/static/icons/touch-icon-iphone-retina.png' />
<link rel='apple-touch-icon' sizes='167x167' href='/static/icons/touch-icon-ipad-retina.png' />

<link rel='icon' type='image/png' sizes='32x32' href='/static/icons/favicon-32x32.png' />
<link rel='icon' type='image/png' sizes='16x16' href='/static/icons/favicon-16x16.png' />
<link rel='manifest' href='/static/manifest.json' />
<link rel='mask-icon' href='/static/icons/safari-pinned-tab.svg' color='#5bbad5' />
<link rel='shortcut icon' href='/favicon.ico' />
<link rel='stylesheet' href='https://fonts.googleapis.com/css?family=Roboto:300,400,500' />
     
<meta name='twitter:card' content='summary' />
<meta name='twitter:url' content='https://yourdomain.com' />
<meta name='twitter:title' content='PWA App' />
<meta name='twitter:description' content='Best PWA App in the world' />
<meta name='twitter:image' content='https://yourdomain.com/static/icons/android-chrome-192x192.png' />
<meta name='twitter:creator' content='@DavidWShadow' />
<meta property='og:type' content='website' />
<meta property='og:title' content='PWA App' />
<meta property='og:description' content='Best PWA App in the world' />
<meta property='og:site_name' content='PWA App' />
<meta property='og:url' content='https://yourdomain.com' />
<meta property='og:image' content='https://yourdomain.com/static/icons/apple-touch-icon.png' />

<!-- apple splash screen images -->
<!--
<link rel='apple-touch-startup-image' href='/static/images/apple_splash_2048.png' sizes='2048x2732' />
<link rel='apple-touch-startup-image' href='/static/images/apple_splash_1668.png' sizes='1668x2224' />
<link rel='apple-touch-startup-image' href='/static/images/apple_splash_1536.png' sizes='1536x2048' />
<link rel='apple-touch-startup-image' href='/static/images/apple_splash_1125.png' sizes='1125x2436' />
<link rel='apple-touch-startup-image' href='/static/images/apple_splash_1242.png' sizes='1242x2208' />
<link rel='apple-touch-startup-image' href='/static/images/apple_splash_750.png' sizes='750x1334' />
<link rel='apple-touch-startup-image' href='/static/images/apple_splash_640.png' sizes='640x1136' />
-->
```

> Tip:  Put the `viewport` head meta tag into `_app.js` rather than in `_document.js` if you need it.

``` typescript
<meta name='viewport' content='minimum-scale=1, initial-scale=1, width=device-width, shrink-to-fit=no, user-scalable=no, viewport-fit=cover' />
```

## Usage Without Custom Server (next.js 9+)

Thanks to **Next.js 9+**, we can use the `public` folder to serve static files from the root `/` URL path. It cuts the need to write custom server only to serve those files. Therefore the setup is easier and concise. We can use `next.config.js` to config `next-pwa` to generates service worker and workbox files into the `public` folder.
### withPWA

``` javascript
const withPWA = require('next-pwa')

module.exports = withPWA({
  pwa: {
    dest: 'public'
  }
})
```

**[Use this example to see it in action](https://github.com/shadowwalker/next-pwa/tree/master/examples/next-9)**

## Offline Fallbacks

Offline fallbacks are useful when the fetch failed from both cache and network, a precached resource is served instead of present an error from browser.

To get started simply add a `/_offline` page such as `pages/_offline.js` or `pages/_offline.jsx` or `pages/_offline.ts` or `pages/_offline.tsx`. Then you are all set! When the user is offline, all pages which are not cached will fallback to '/_offline'.

**[Use this example to see it in action](https://github.com/shadowwalker/next-pwa/tree/master/examples/offline-fallback-v2)**

`next-pwa` helps you precache those resources on the first load, then inject a fallback handler to `handlerDidError` plugin to all `runtimeCaching` configs, so that precached resources are served when fetch failed.

You can also setup `precacheFallback.fallbackURL` in your [runtimeCaching config entry](https://developers.google.com/web/tools/workbox/reference-docs/latest/module-workbox-build#.RuntimeCachingEntry) to implement similar functionality. The difference is that above method is based on the resource type, this method is based matched url pattern. If this config is set in the runtimeCaching config entry, resource type based fallback will be disabled automatically for this particular url pattern to avoid conflict.

## Configuration

There are options you can use to customize the behavior of this plugin by adding `pwa` object in the next config in `next.config.js`:

```javascript
const withPWA = require('next-pwa')

module.exports = withPWA({
  pwa: {
    dest: 'public',
    // disable: process.env.NODE_ENV === 'development',
    // register: true,
    // scope: '/app',
    // sw: 'service-worker.js',
    //...
  }
})
```

### Available Options

- disable: boolean - whether to disable pwa feature as a whole
  - default: `false`
  - set `disable: false`, so that it will generate service worker in both `dev` and `prod`
  - set `disable: true` to completely disable PWA
  - if you don't need to debug service worker in `dev`, you can set `disable: process.env.NODE_ENV === 'development'`
- register: boolean - whether to let this plugin register service worker for you
  - default to `true`
  - set to `false` when you want to handle register service worker yourself, this could be done in `componentDidMount` of your root app. you can consider the [register.js](https://github.com/shadowwalker/next-pwa/blob/master/register.js) as an example.
- scope: string - url scope for pwa
  - default: [`basePath`](https://nextjs.org/docs/api-reference/next.config.js/basepath) in `next.config.js` or `/`
  - set to `/app` so that path under `/app` will be PWA while others are not
- sw: string - service worker script file name
  - default: `/sw.js`
  - set to another file name if you want to customize the output file name
- runtimeCaching - caching strategies (array or callback function)
  - default: see the **Runtime Caching** section for the default configuration
  - accepts an array of cache entry objects, [please follow the structure here](https://developers.google.com/web/tools/workbox/reference-docs/latest/module-workbox-build#.RuntimeCachingEntry)
  - Note: the order of the array matters. The first rule that matches is effective. Therefore, please **ALWAYS** put rules with larger scope behind the rules with a smaller and specific scope.
- publicExcludes - an array of glob pattern strings to exclude files in the `public` folder from being precached.
  - default: `['!noprecache/**/*']` - this means that the default behavior will precache all the files inside your `public` folder but files inside `/public/noprecache` folder. You can simply put files inside that folder to not precache them without config this.
  - example: `['!img/super-large-image.jpg', '!fonts/not-used-fonts.otf']`
- buildExcludes - an array of extra pattern or function to exclude files from being precached in `.next/static` (or your custom build) folder
  - default: `[]`
  - example: `[/chunks\/images\/.*$/]` - Don't precache files under `.next/static/chunks/images` (Highly recommend this to work with  `next-optimized-images` plugin)
  - doc: Array of (string, RegExp, or function()). One or more specifiers used to exclude assets from the precache manifest. This is interpreted following the same rules as Webpack's standard exclude option.
- dynamicStartUrl - if your start url returns different HTML document under different state (such as logged in vs. not logged in), this should be set to true.
  - default: `true`
  - recommend: set to **false** if your start url always returns same HTML document, then start url will be precached, this will help to speed up first load.
- dynamicStartUrlRedirect - if your start url redirect to another route such as `/login`, it's recommended to setup this redirected url for the best user experience.
  - default: `undefined`
- fallbacks - config precached routes to fallback when both cache and network not available to serve resources.
  - **if you just need a offline fallback page, simply create a `/_offline` page such as `pages/_offline.js` and you are all set, no configuration necessary**
  - default: `object`
    - `fallbacks.document` - fallback route for document (page), default to `/_offline` if you created that page
    - `fallbacks.image` - fallback route for image, default to none
    - `fallbacks.audio` - fallback route for audio, default to none
    - `fallbacks.video` - fallback route for video, default to none
    - `fallbacks.font` - fallback route for font, default to none
- cacheOnFrontEndNav - enable additional route cache when navigate between pages with `next/link` on front end. Checkout this [example](https://github.com/shadowwalker/next-pwa/tree/master/examples/cache-on-front-end-nav) for some context about why this is implemented.
  - default: `false`
  - note: this improve user experience on special use cases but it also adds some overhead because additional network call, I suggest you consider this as a trade off.
- ~~subdomainPrefix: string - url prefix to allow hosting static files on a subdomain~~
  - ~~default: `""` - i.e. default with no prefix~~
  - ~~example: `/subdomain` if the app is hosted on `example.com/subdomain`~~
  - deprecated, use [basePath](https://nextjs.org/docs/api-reference/next.config.js/basepath) instead
- reloadOnOnline - changes the behaviour of the app when the device detects that it has gone back "online" and has a network connection. Indicate if the app should call `location.reload()` to refresh the app.
  - default: `true`

### Other Options

`next-pwa` uses `workbox-webpack-plugin`, other options which could also be put in `pwa` object can be found [**ON THE DOCUMENTATION**](https://developers.google.com/web/tools/workbox/modules/workbox-webpack-plugin) for [GenerateSW](https://developers.google.com/web/tools/workbox/reference-docs/latest/module-workbox-webpack-plugin.GenerateSW) and [InjectManifest](https://developers.google.com/web/tools/workbox/reference-docs/latest/module-workbox-webpack-plugin.InjectManifest). If you specify `swSrc`, `InjectManifest` plugin will be used, otherwise `GenerateSW` will be used to generate service worker.

### Runtime Caching

`next-pwa` uses a default runtime [cache.js](https://github.com/shadowwalker/next-pwa/blob/master/cache.js)

There is a great chance you may want to customize your own runtime caching rules. Please feel free to copy the default `cache.js` file and customize the rules as you like. Don't forget to inject the configurations into your `pwa` config in `next.config.js`.

Here is the [document on how to write runtime caching configurations](https://developers.google.com/web/tools/workbox/reference-docs/latest/module-workbox-build#.RuntimeCachingEntry), including background sync and broadcast update features and more!

## Tips

1. [Common UX pattern to ask user to reload when new service worker is installed](https://github.com/shadowwalker/next-pwa/blob/master/examples/lifecycle/pages/index.js#L26-L38)
2. Use a convention like `{command: 'doSomething', message: ''}` object when `postMessage` to service worker. So that on the listener, it could do multiple different tasks using `if...else...`.
3. When you are debugging service worker, constantly `clean application cache` to reduce some flaky errors.
4. If you are redirecting the user to another route, please note [workbox by default only cache response with 200 HTTP status](https://developers.google.com/web/tools/workbox/modules/workbox-cacheable-response#what_are_the_defaults), if you really want to cache redirected page for the route, you can specify it in `runtimeCaching` such as `options.cacheableResponse.statuses=[200,302]`.
5. When debugging issues, you may want to format your generated `sw.js` file to figure out what's really going on.
6. Force `next-pwa` to generate worker box production build by specify the option `mode: 'production'` in your `pwa` section of `next.config.js`. Though `next-pwa` automatically generate the worker box development build during development (by running `next`)  and worker box production build during production (by running `next build` and `next start`). You may still want to force it to production build even during development of your web app for following reason:
   1. Reduce logging noise due to production build doesn't include logging.
   2. Improve performance a bit due to production build is optimized and minified.
7. If you just want to disable worker box logging while keeping development build during development, [simply put `self.__WB_DISABLE_DEV_LOGS = true` in your `worker/index.js` (create one if you don't have one)](https://github.com/shadowwalker/next-pwa/blob/c48ef110360d0138ad2dacd82ab96964e3da2daf/examples/custom-worker/worker/index.js#L6).
8. It is common developers have to use `userAgent` string to determine if users are using Safari/iOS/MacOS or some other platform, [ua-parser-js](https://www.npmjs.com/package/ua-parser-js) library is a good friend for that purpose.

## Reference

1. [Google Workbox](https://developers.google.com/web/tools/workbox/guides/get-started)
2. [ServiceWorker, MessageChannel, & postMessage](https://ponyfoo.com/articles/serviceworker-messagechannel-postmessage) by [Nicolás Bevacqua](https://ponyfoo.com/contributors/ponyfoo)
3. [The Service Worker Lifecycle](https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle)
4. [6 Tips to make your iOS PWA feel like a native app](https://www.netguru.com/codestories/pwa-ios)
5. [Make Your PWA Available on Google Play Store](https://www.netguru.com/codestories/make-your-pwa-available-on-google-play-store)

## Fun PWA Projects

1. [Experience SAMSUNG on an iPhone - must open on an iPhone to start](https://itest.nz/)
2. [App Scope - like an app store for PWA](https://appsco.pe/)
3. [PWA Directory](https://pwa-directory.appspot.com/)

## License

MIT
