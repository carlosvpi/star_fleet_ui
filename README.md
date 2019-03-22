# ROUTE MAP for StarFleet
UI for a Star Fleet game

## Introduction

StarFleetUI is the UI for a space fleet simulator.

## Concept

The user is given economic and military control over a part of the Universe. The goal is to increase control area and defeat enemies. The main advantage of colonizing other stars is the ability to get more antoprotons with which to start fusion reactions.

The resources are:
* Hydrogen: measured in Gg; is used to accelerate/decelerate vessel's journeys
* Antiprotons: measured in mg: is used to create a vessel, and to obtain energy (they catalize fusion reactions)
* Population: measured in amount of people: is used to operate vessels and on advancing industry

User is able to design their own vessel types
* amount of fuel (H) (typical values for AD and ADT show the distances this amount of fuel can reach in 1 year)
* crew size
* weaponry
* payload
* tech: this includes 
  * Fusion reactor kind, that determines the reachable AD of the ship.
  * Space lift, that allows to colonize other stars

User is able to design a vessel journey
* ADT: acceleration/deceleration times (when fuel is consumed)
* AD: acceleration/deceleration (Float, during ADT)
* IT: inertial travel time (total time - ADT) (the length of a travel is determined by the distance, the AD and the ADT)

Stars represent the planets around them; there is where the user develops technology. Different stars have different technological and industrial capabilities
* space lifts: [SpaceLift];
* antimater reactors: [AntimaterReactor]: provide antimater in µg at the expense of a huge waste of H

## View

Two views are presented to the user
* The star map
* Interface

### Star map

The star map spans the whole screen, and is positioned behind the interface elements.
The star map shows
* the relative location of the stars
* a simple grid system (three concentric circles and a line pointing to the vernal point)
* the routes between stars

### Interface