Chronus
============

Synopsis
---------
> Chronus is a lightweight yet fully featured Message/Jobs Server for Node.js applications. It accepts both scheduled jobs (akin to crons) and queued jobs meant for immediate execution. The server then has its "workers" proceeds to run them in the proper order.

> Chronus is built with scalability and accuracy in mind. It's asyncronous nature does not impede the ACID integrity of the jobs. Unlike other queuing software on the market, Chronus can be run in different modes to customize the solution to your needs. Even with all these functionalities, it is easy to use and leaves a small footprint.

> Storing the queues is extremely simple as Chronos comes with built in database support for Redis, MySQL & plain old files. MongoDB support is planned to give access to as many databases as possible.

Installation
------------
`npm install chronus`

Usage
------------
> Chronus can run in 3 modes: **Live Mode**,  **Server Mode**  &  **Worker Mode** . In Live Mode, the queues and the workers that process the queues run in the same Node.js application instance. In Server Mode, you create the hub that stores all the jobs. The Workers then connect to this hub to retrieve and process the jobs in queue. These workers, as you've guessed, are running in Worker Mode.


**Live Mode** 
  > Both, the Jobs Server and the Worker, run in the same Node.js instance. This is the recommended setup for small to large size applications.
```sh
//Server: 
var chronusServer = new chronus.createServer();
//Worker:
var chronusWorker = new chronus.createWorker();
```

**Server Mode**
  > In this mode, you can run one Message Server that holds all the data. The Workers then connect to this Server and run the jobs. 
  > This is the recommended setup for enterprise level applications. Upgrading from Live Mode requires next to no changes
  > in your code. 
```sh
//Server acting as the Hub instance: 
var chronusServer = new chronus.createServer();
```

**Worker Mode**
  > The Workers connect to either a Chronus Server (Hub) or directly to a database to retrieve and process the job.
```sh
//Worker(s) on other Node.js instances:
var chronusWorker = new chronus.createWorker();
```

Version
-------
*Currently under construction.*

License
-------
MIT.

Copyright
---------
Copyright(C) 2014 Niroshan "GeekMode" Sugirtharatnam. All Rights Reserved.
