# ROUTE MAP for StarFleet

## Introduction

StarFleet is an interaction of two subsystems: the StarMap and the StarController

## Abbreviations

**Measures**
* `ly`: Light year
* `px`: pixel

**Other**
* `Ctx`: html's canvas' 2D concetx

## Star Map

The star map represents a 3D cut of the Universe. Objects in the star map provide only one method:
* `draw`: (ctx: Ctx) => (); where the object is drawn in the canvas' context ctx.

### Object's ontology

This is the classification of starMap objects according to the semantics related to them:
* SMO
  * Point: has `x`, `y` and `z`: Float ly; relative to the center of the Universe. May have `vx`, `vy` and `vz`: Float ly/year
    * Location
  	  * Star: include `spectType`, `subspectType` and `spectSize`, apart from other data (like `name`)
  * Edge: has `from`, `to`: Point; represent a path betwen points `from` and `to`. It has `style` too.

### Star Map UI

The star map is controled by the starMapUI object, that contains these attributes
* `decl`: Float in [-PI/2, PI/2]; declination of the view
* `rA`: Float; right ascension of the view
* `cx`: Float ly; x position, relative to the center of the universe, of the center of the map.
* `cy`: Float ly; y position, relative to the center of the universe, of the center of the map.
* `cz`: Float ly; z position, relative to the center of the universe, of the center of the map.
* `screenCX`: Float px; horizontal position in the screen of Map's [0, 0, 0]
* `screenCZ`: Float px; vertical position in the screen of Map's [0, 0, 0]
* `objects`: [SMO]; objects that inhabit the Universe

and presents these methods
* ~`getDecl`: () => Float; user view declination~
* ~`getRA`: () => Float; user right ascension~
* `setDecl`: (decl) => starMap; decl has been set
* `setRA`: (ra) => starMap; rA has been set
* `setC`: (cx: Float ly, cy: Float ly, cz: Float ly) => starMap; cx, cy, cz have been set
* `setScreenC`: (screenCX: Float, screenCZ: Float) => starMap; screenCX and screenCZ have been set
* `draw`: () => starMap; the objects have been drawn
* `pushObject`: (object: SMO) => starMap; object has been pushed to the `objects` list.

## Interface

The interface allows the user to control the system. It is a collection of controls:
* _space controller_: provides control of the view
* _time controller_: provides control of the pass of time (pause, n * year/s)
* _master star controller_: provides controls over the stars visited by the user
* _stars controller_: provides controls over the stars visited by the user
* _master route controller_: provides controls over the routes created by the user
* _route controller_: provides controls over the routes created by the user
* _master ship type controller_: provides controls over the routes created by the user
* _ship type controller_: provides controls over the routes created by the user
* _master ship controller_: provides controls over the routes created by the user
* _ship controller_: provides controls over the routes created by the user

The interface includes an extra controller:
* _console_: provides information about what is happening in the Universe.

### _Space controller_

Located in the top bar, offers:
* Change the screen position of the map's [0, 0, 0]

It configures these events:
* mouse drag: change map's rA and decl
* mouse hover (a SMO Point): provide info (in console) of the SMO point
* mouse right click: open the controller of the clicked SMO (if any)
* mouse dbl click: sets the SMO point as the new map's [0, 0, 0]

### _Time controller_

Located at the top bar, offers:
* set the speed of the game

### _Master stars controller_

On the left, offers:
* a list of the colonized and visited stars, (that can be sorted by timeAdded, population, fleet, name), where
  * right click on the list item equals right click on the star in the map (opens the controller of the SMO)
  * dbl click on the list item equals dbl click on the star in the map (sets it as [0, 0, 0])

#### _Star controller_

Contextual. Offers control over:
* Name of the star
* Infrastructure of the star, a list of infrastructure the star has, and infrastructure available to purchase.

Shows info about:
* Star position, spectral type, population, resources inputs and outputs.

### _Master Route controller_

On the left, offers:
* a list of the routes defined by the user (sortable by timeAdded, traffic, fleet, color and name), where
  * right click on the list item opens the controller of the route
  * dbl click on the list item equals dbl click on the `from` object of the route (sets it as [0, 0, 0])
* Controls to add or remove routes that open the _Route controller_.

#### _Route controller_

Contextual. Offers control over:
* Name of the route
* Style of the route
* Stops of the route 
*

### _Master ship type controller_

On the left. Controls:
* a list of the ship blueprints, sortable by timeAdded, size, amount of ships and name), where
  * right click on the list item opens the controller of the ship type
* a "Add" button that opens the _ship type controller_.

#### _Ship type controller_

Contextual.
* Name of the ship type
* Infrastructure of the ship type, the list of tech that it has, and tech available to purchase (which would create an upgraded version of this type and add it to the _Master ship type controller_'s list)

### _Master ship controller_

On the left; shows:
* a list of the ships, sortable by date, type, name, etc.
  * right click on a list item opens the _ship controller_ of that ship.
  * dbl click on a list item sets the star where the ship is (or to which it goes) as the map's [0, 0, 0]

#### _ship controller_

Contextual.
* Name of the ship
* weaponry and crew
* Infrastructure of the ship (this is read only, as it depends on the )
