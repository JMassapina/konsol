# Konsol

The DevOps Console

## Development Prerequisites

Before you start following the example, please grab the following dependencies:

  1. Dependency management for tools are managed via Node.js [NPM](https://www.npmjs.com/), Install [Node.js](https://nodejs.org/en/download/) version >= 0.12

  2. Components dependency management using [Bower](http://bower.io/) by running

     ```
     npm install -g bower
     ```

  3. Install Electron

     ```
     npm install -g electron-prebuilt
     ```

  4. Grab npm Tooling dependencies

     ```
     npm install
     ```

  5. Grab bower Library dependencies

     ```
     bower install
     ```

  6. Run the project

     ```
     electron .
     ```

## Caveats Of Server-less Architecture

 - No caching, potentially firing a lot of requests

 - No auth, policies, IP based


## Advantages of Server-less Archtecture

 - Reduced complexity

 - Flexibility through composition

## konsol-task-sequence

`<konsol-task-sequence>` by default is used to wrap your editor, so task elements will be executed in sequential order.

This Example will execute pings in sequence:

```
<konsol-task-sequence>
	<konsol-exec cmd="ls -l"></konsol-exec>
	<konsol-exec cmd="ifconfig -a"></konsol-exec>
</konsol-task-sequence>
```

## konsol-task-concurrent

`<konsol-task-concurrent>` element can be used to wrap task elements that you would like to execute concurrently (asynchronously).

This Example will execute pings concurrently:

```
<konsol-task-concurrent>
	<konsol-exec cmd="ping www.bing.com"></konsol-exec>
	<konsol-exec cmd="ping www.soccernet.com"></konsol-exec>
</konsol-task-concurrent>
```
