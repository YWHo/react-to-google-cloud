# react-to-google-cloud

## Setup a React App (Client side App)

The following steps are used to setup an initial React Application using Vite

```console
terminal~% npm create vite@latest
? Project name: > react-app
? Select a framework: React
? Select a variant: TypeScript
```

Go into the project directory

```console
terminal~% cd react-app
```

Install the dependencies

```console
terminal~% npm install
```

Run the App locally (in Development mode)

```
terminal~% npm run dev
```

After the above step, the local website should be available at: \
  http://localhost:5173/

![Browser View 1](./screenshots/browser1.png "Browser View 1")


## Update the React Code

Update `src/App.tsx` file to insert following code below `<button>` tag:
```html
<p>
  Ahoy, me hearties!
</p>
```

After the above step, the local website should display the changes:

![Browser View 2](./screenshots/browser2.png "Browser View 2")

## Build the React App for deployment

In the terminal where the `npm run dev` command is running, press `CTRL-C` to stop the command.

Then run following command to build the App.

```console
terminal~% npm run build
```

Please note that 4 files in a `/dist` folder will be generated. Below is the example:

```console
dist/index.html                   0.46 kB │ gzip:  0.30 kB
dist/assets/react-CHdo91hT.svg    4.13 kB │ gzip:  2.05 kB
dist/assets/index-DiwrgTda.css    1.39 kB │ gzip:  0.72 kB
dist/assets/index-B4DS1gM9.js   143.24 kB │ gzip: 46.08 kB
```


