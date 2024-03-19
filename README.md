# Andy's Portfolio

This will be a semi-technical overview of my larger projects.

Generally, I close the source of anything that makes it past prototype phase and has the potential for revenue. 
My other repositories represent prototypes or Proof of Concepts. They _should_ be up to date on documentation as well.


## Skillset

All of these projects are Full Stack in nature. 

# Base Wars

I acted as the sole developer (2017 - 2020) to a desktop video game written in Java Swing.

The game released on Steam [here](https://store.steampowered.com/app/1747110/Base_Wars/), to critical success (~500 copies sold and counting).

The game represents a mature codebase (~80,000 LoC) with a variety of features:

- Netcode
    - Client & Server model, where the Server validates & propogates Events generated by Clients.
    - Remote matchmaking server adds clients to Redis queue and pairs FIFO
- Multithreading
    - Render thread, input thread, and model update thread to separate concerns and keep a consistent framerate
    - Asset loading thread used on startup
    - Event structure and immutable model state designed with race conditions and synchronicity in mind
- UX design
    - Responsive frontend UI changes wireframe according to screen size
    - Intuitive & unique menu system

## Specs

Frontend- Java Swing

Backend- Java Awt

Deployment Environment- Steamworks

# Iperf Professional Edition

Iperf PE is a remote scheduling tool for [Iperf 2](https://sourceforge.net/projects/iperf2/).
It is hosted on [iperf-pe.net](https://iperf-pe.net/) for production and [stg.iperf-pe.net](http://stg.iperf-pe.net/) for staging.

The app is designed with a minimalist UI, presenting essential information efficiently and clearly to the user.
The concepts of Nodes and Test scheduling are succinctly explained and designed to be as streamlined as possible.

The architecture is as follows:

- Frontend (React)
    - Stores session token & handles auth appropriately
    - Makes async API calls and renders relevant data into custom table components
- Backend (Node Express)
    - Uses Sequelize ORM to model & represent Database tables
    - Provides API to frontend for User management and CRUD operations on Nodes and Tests
    - Scheduler thread picks up 
- Database (MySQL)
- Nodes (Golang)
    - A Node is a remote server which the backend can call upon to start / stop Iperf Tests
    - Provided to the user as a GitHub release, currently
    - Uses U/P auth to validate endpoint calls
    - Runs inside a Docker image for environmental flexibility
    - Reports status, uptime, and test results to Backend

## Next Steps

As Iperf PE is still in early prototype phase, there are still fundamental improvements to be done.

- Provide the Node's Docker image directly from a container registry
- Reimplement auth on Nodes as server-provided JWT
- Add a Garbage Collector thread for any bad state Tests

## Specs

Frontend- React

Backend- Node Express

Database- MySQL

Deployment Environment- Heroku

# Idle Elemental

Idle Elemental is an unfolding mobile game still under active development.
It is scheduled for release on the Android App Store in March of 2024 and on-browser in April of 2024.

It utilizes Dart's Flutter framework for efficient separation of Model and View.
The UI layout dynamically changes with a heavy dependence on game state, only showing features as they are unlocked.

This project was initially intended as an excercise in frontend design and optimizing for UX.
It also includes calculus-level math implementation for calculating the fluctuation of resource values for any given delta-time within a highly interconnected system.

## Specs

Frontend- Flutter

Backend- Flutter Riverpod

Deployment Environment- Google App Store, Heroku



# Portfolio TODO

- Add images & gifs to individual directories
- Update Idle Elemental once published