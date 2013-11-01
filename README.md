# The Rush Hour Platform

![](http://i.imgur.com/K5O3BSQ.png?1)

## What is Rush Hour?

Rush Hour is a highly realistic traffic simulation platform. It exposes facilities to describe the
rules of traffic in an all-data medium, and renders the simulation on a dynamic heatmap.

## Architecture

Over to [Tumblr](http://michaeldrogalis.tumblr.com/post/65274692089/clojure-understood-the-rush-hour-platform) for that.

## Live demo

My little EC2 micro instance couldn't take all the traffic it was getting (pun intended).
There's directions (ha, another pun) for running it locally below.

## Repositories

- [Simulation](https://github.com/MichaelDrogalis/traffic-sim)
- [Asphalt](https://github.com/MichaelDrogalis/asphalt)
- [Triangulation Service](https://github.com/MichaelDrogalis/triangulate)

## Installation

```bash
$ sudo apt-get install openjdk-7-jre
$ sudo apt-get install leiningen
$ sudo apt-get install memcached
```

```bash
$ git clone https://github.com/MichaelDrogalis/traffic-sim.git
$ cd traffic-sim
$ lein midje # sanity check
$ lein run
```

```bash
$ git clone https://github.com/MichaelDrogalis/triangulate.git
$ cd triangulate
$ lein run
```

```bash
$ git clone https://github.com/MichaelDrogalis/asphalt.git
$ cd asphalt
$ lein cljsbuild once
$ lein run
```

```bash
$ cd asphalt
$ firefox resources/index.html
```

## Customizing the Sim

```bash
$ emacs -nw resources/intersection-schema.edn # defines lanes, lights, traffic rules
$ emacs -nw resources/connections-schema.edn # connects intersection lanes together
$ emacs -nw resources/weighted-directions.edn # summative probability of driving on each lane.
```

See [the tests](https://github.com/MichaelDrogalis/traffic-sim/tree/master/test/traffic_sim/scenarios) for examples of writing rules, lights, and intersections.

## Exploring the Sim

- `init.clj` starts the app up.
- `core.clj` contains adjustable properties.
