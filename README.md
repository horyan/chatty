## Table of Contents
* [About Chatty](#about-chatty)
  * [Built With](#built-with)
* [Getting Started](#getting-started)
  * [Prerequisites](#prerequisites)
  * [Installation](#installation)
  * [Usage](#usage)
* [Features](#features)
* [Roadmap](#roadmap)
* [Acknowledgements](#acknowledgements)

## About Chatty
[![Chatty screenshot](/images/screenshot.png)](https://chattty.netlify.com)
Chatty is a realtime, anonymous webchat application that uses a number of open source projects to work properly. Demo available [here](https://chattty.netlify.com).

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

### Usage
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
* Every user is automatically assigned a randomly generated name
	* Names are automatically re-assigned on page reload
* Users can interact with each other by receiving and optionally sending chat messages
* Users have the option to type and preview their input before sending message
	* Messages can be sent by using either "Enter" key or on-screen send button
	* Messages are only sent if they are validated to be non-empty
* Chat messages are displayed along with the sender's name and the relative time it was sent ago
	* The active user's name is rendered with an orange property to differentiate from other users

## Roadmap
The following improvements will be addressed in the near-future:
* add fixed-size and scrolling for chat screen
* add ability to remove or edit own messages

## Acknowledgements
* [Vuefire](https://github.com/vuejs/vuefire)
* [faker.js](https://github.com/marak/Faker.js/)
* [Moment.js](https://github.com/moment/moment/)
* [Vectr](https://vectr.com/)
* [WebOfficeHours](https://www.webofficehours.com/)