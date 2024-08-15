# react-to-google-cloud

## Initial Setup

First, create an initial folder for everything inside. In this example, the folder is named as `react-go-google-cloud`

```console
terminal~% mkdir react-go-google-cloud
```

Go into the new folder
```console
terminal~% cd react-go-google-cloud
```

## Setup a React App (Client side App)

The following steps are used to setup an initial React Application using Vite. The React App is named as `react-app`.

```console
terminal~% npm create vite@latest
? Project name: > react-app
? Select a framework: React
? Select a variant: TypeScript
```

Go into the React App folder

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

## Setup an Express app (Server side App)

Go back to the parent folder

```console
terminal~% cd ..
```

Generate the package.json file inside `/react-go-google-cloud` folder

```console
terminal~% npm init -y
```

Install the Express package to allow receiving HTTP request from the React App.
```console
terminal~% npm install express
```

Using the VSCode editor, create a new file called `index.js` inside `/react-go-google-cloud` folder. Then, insert following code inside `index.js` file.

```js
const express = require('express');
const app = express();
app.use(express.json());
app.use(express.static('react-app/dist')); // use the built code for React-App
const port = process.env.PORT || 8080;
app.listen(port, () => {
    console.log(`Listening on port ${port}`);
});

app.get('/api/pirates/:id', (req, res) => {
    const id = req.params.id;
    const pirate = getPirate(id);
    if (!pirate) {
        res.status(404).send({ error: `Pirate ${id} not found`})
    } else {
        res.send({ data: pirate });
    }
} );


function  getPirate(id) {
  const pirates = [
    {id: 1, name: 'Klaus Störtebeker', active: '1392-1401', country: 'Germany'},
    {id: 2, name: 'Kristoffer Trondson', active: '1535-1542', country: 'Norway'},
    {id: 3, name: 'Jan de Bouff', active: '1602', country: 'Netherlands'},
    {id: 4, name: 'Jean Bart', active: '1672-1697', country: 'France'},
    {id: 5, name: 'Tuanku Abbs', active: 'to 1844', country: 'Malay Archipelago'},
    {id: 6, name: 'Ching Shih', active: '1807-1810', country: 'China'}
  ];
  return pirates.find(p => p.id == id);
}
```

Then update `scripts` object inside `package.json` file:
```js
{
    ...
    "scripts": {
        "start": "node index.js"
    }
    ...
}
```

Run the `start` command to launch the Express App:

```console
npm run start
```

After the above step, the local website should be available at: \
  http://localhost:8080/

![Browser View 3](./screenshots/browser3.png "Browser View 3")

We can now test the API by going to following URL: \
  `http://localhost:8080/api/pirates/3`


The browser will show following API response:

![Browser View 4](./screenshots/browser4.png "Browser View 4")

or

![Browser View 5](./screenshots/browser5.png "Browser View 5")

