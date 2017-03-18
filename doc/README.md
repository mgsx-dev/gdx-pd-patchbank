
# Why an API ? 

It allows to easily switch any node of same kind. eg. change an instrument to another without to have to rewire cables and adapt its interface to the context. Idea is to define pluggable node types. This API addresses common points like controllers, persistence, synchronization, ... and so on.

# Standard events

A "standard event" is a pd message with format <note> <velocity> plus optional extra data. "note" is interpreted as MIDI note by synthetizers (instruments) but can be any float. Velocity is interpreted as MIDI velocity ranging from 0 to 127 but not necessary integer. Values beyond 127 could lead to unexpected behavior and should be avoided.

# Audio standard

Audio standard is inlets/outlets orders : first outlet is first channel (mono), second is right, ... TODO 5.1 ? and is not restricted to 2 (multi channels ...)

# Matrix

					none out 		events out		audio out

none in 			  ????			device/seq		pure generator

events in 				????		midi effect		instrument

audio in 			recorder ?		analyser		audio effect


# Top to Bottom

* clocks
* sequencers
* midi effects
* instruments
* audio effects
* final mixer (see u-mix)

others are utility (u-) and doesn't have to conform to node API (no storage, not named, no controls ...) ???
some specialties : device can be at any stage ???

# Controls

convention : **abs** **name** *arg1* *arg2*

parameter can be get by **name**.**paramX** (object-like syntax)

# Storage


# Random notes

* passing stop message is cumbersome when implemnting a new midi effect or things like that, it is related to sequencers and clocks and have to be define in other way : eg. a global message ? or clock message piped manually to all nodes requiring a stop !
idea is to let implements just by who cares : instrument with sustain, midi effect / sequencer requiring reset in some way.
But with make poly, you don't really need it, only makepoly have to take care about stop and clear ?!....


