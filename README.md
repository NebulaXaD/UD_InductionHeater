# UD_InductionHeater
Repurposing the poplar universal tesla coil driver for induction heating purposes

------------

REALLY IMPORTANT: if you can, try not to run this (or any powerful induction heater) circuit without anything in the workcoil, because the voltage and current can ring up really high (well over a kV, which some resonant capacitors wont be able to handle) without a load! 

------------

Pretty much any universal tesla coil driver will work for these (even premade ud1.3 copies on ali/ebay you can get for cheap), only reason I used ud2.7 is because I had spares on hand.

For the gate drive transformer don't just use any old toroids you find, but there are quite a few materials that will work out: N30, N87, 75, 77... It's important that its properly wound and polarity of the secondaries is crucial to get right otherwise your bridge will be constantly shorted (read as VERY BAD). [A good tutorial on how to properly wind them can be found here](https://www.youtube.com/watch?v=ahb5woa-AW8)

For the current transformers you can use the same cores as for gdts, and I suggest winding more turns on the first stage because theres quite a lot of current in the lc tank, so you want to minimise the current that will go through these, in my case its 40:10:1. Polarity of the feedback transformer matters or your driver will try to drive the tank at a weird harmonic causing the circuit to behave oddly. [Tutorial](https://www.easternvoltageresearch.com/tesla-coil-workshop/how-to-build-cascaded-current-transformers-for-tesla-coils/)

The role of the coupling transformer is to lower the voltage supplied to the LC tank, and the winding ratio determines how much power it will draw (and also isolates the tank from mains as a bonus). I suggest around 20 or 10 turns on the primary side to begin with and then reduce them if you want more power. The recommended materials are N87, N97, 3C90, 3C94 and other similar ones made for power transformers. Both toroidal and E cores are great choices but in my opinion, toroidal are easier to assemble and leak less fields that can interfere with the driving circuitry. I used two B64290L699X87 cores, but feel free to pick ones that suit your need the best. Don't forget that to increase the power handling capability, you can just stack more cores without any issues where their inductance factors just add up together.

I strongly recommend winding your work coil from copper pipe and passing just a tiny bit of water through it (I'm using a tiny 2L/min fountain pump), because it dissipates quite a low of heat in use.

The tank capacitor can be made up of a bunch of smaller caps, but make sure these can handle at least 1-2kVAC, and are able to withstand your desired operating current. Dawncaps are a decent choice but they can get pricy if you use a lot of them. The resonant frequency of your tank should be below 100kHz in order not to cause additional heating issue with the driver and bridge (monitor the temperatures of the output fets of your UD because in some cases they can get warm, and additionally add a small heatsink to them in case its needed).

![TANK](https://github.com/NebulaXaD/UD_InductionHeater/blob/main/pics/LC%20tank.jpg)

Both full and halfbridges are completely valid here, but in case of a fullbridge, add a DC blocking capacitor in series with the primary of the coupling transformer (same value as halfbridge caps, as long as you dont make it and the primary of the coupling trafo resonate closely to the main LC tank frequency you are fine). Halfbridge is beneficial is you plan on using less power (<3-4kW) since it already halves the voltage so you need less turns on the coupling trafo and the bridge construction is generally cheaper.

For the igbts, make sure they are 650V or higher rated (in reallity you won't really find lower ones), and can handle at least twice or three times your planned input current continously.

35 or 50A full bridge rectifiers can be 

![SCHEM](https://github.com/NebulaXaD/UD_InductionHeater/blob/main/pics/schematic.png)
