One more thing about CARP:
There's a need that the parent interface 'carpdev' needs to be in the same rdomain(4) as the carp(4) interface is.
While that's true you can add a "layer" in between to seperate the physical (e.g. em(4)) interface from that.

Basic idea:
rdomain 0: em0
bridge0 members: em0, vether51, vether52
rdomain 51: vether51, carp51
rdomain 52: vether52, carp52

So far this works in my vagrant-setup, stay tuned for more details.
