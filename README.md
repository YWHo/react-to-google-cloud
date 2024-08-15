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
