## Table of Contents
* [About the Project](#about-the-project)
  * [Built With](#built-with)
* [Getting Started](#getting-started)
  * [Prerequisites](#prerequisites)
  * [Installation](#installation)
* [Usage](#usage)
* [Features](#features)
* [Roadmap](#roadmap)
* [Acknowledgements](#acknowledgements)

## About the Project
![Chatty screenshot][/images/screenshot.jpg]
Chatty is a realtime, anonymous webchat application that uses a number of open source projects to work properly. You can demo it [here](https://chattty.netlify.com).

### Built With
* [Vue.js](https://vuejs.org/) - JavaScript framework for building web UI
* [Firebase](https://firebase.google.com) - cloud-hosted, NoSQL database for syncing realtime data
* [Tailwind CSS](https://tailwindcss.com) - low-level CSS framework for customized designs
* [Netlify](https://www.netlify.com/) - web project deployment

## Getting Started
To get a local copy up and running, please follow these steps.

### Prerequisites
* npm
```sh
npm install npm@latest -g
```

### Installation
1. Clone the repo
```sh
git clone https://github.com/horyan/chatty.git
```
2. Install NPM packages
```sh
npm install
```
3. Enter your Firebase Project ID in `db.js`
```JS
    .initializeApp({ projectId: 'ENTER YOUR PROJECT ID' })
```

## Usage

Compiles and hot-reloads for development
```
npm run serve
```

Compiles and minifies for production
```
npm run build
```

Lints and fixes files
```
npm run lint
```

## Features
* Every user is assigned a randomly generated name automatically
* Users can interact with each other by sending chat messages
* Messages are only sent if they are validated to be non-empty
* Messages are displayed with the associated sender and relative time

## Roadmap
In the near-future, I plan to address the following improvements.
* restrict chat screen size and add scrolling
* add ability to remove or edit own messages

## Acknowledgements
* [Vuefire](https://github.com/vuejs/vuefire)
* [faker.js](https://github.com/marak/Faker.js/)
* [Moment.js](https://github.com/moment/moment/)
* [Vectr](https://vectr.com/)
* [WebOfficeHours](https://www.webofficehours.com/)