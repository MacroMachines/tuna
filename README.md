tuna
====

An audio effects library for the Web Audio API.

Effect list<br />
====
Overdrive (6 different algorithms)<br />
Filter<br />
Cabinet<br />
Chorus<br />
Delay<br />
PingPongDelay<br />
Convolver (Reverb)<br />
Compressor<br />
Equalizer (variable number of bands)<br />
Tremolo<br />
Phaser<br />
WahWah<br />

www.dinahmoe.com

Usage:
====

You create a new tuna node as such:

var chorus = new TUNA.Chorus({
                 rate: 0.5,
                 depth: 0.5,
                 feedback: 0.5,
                 delay: 0.5
             });

You can then connect the tuna node to native Web Audio nodes by doing:

nativeNode.connect(chorus.input);
chorus.connect(gainNode);

or to other tuna nodes by doing:




Each tuna node (or effect) inherits from the same prototype. This gives the nodes some common methods:
<ul>
    <li>connect(targetNode) - simulates the connect method of the native AudioNode in Web Audio. targetNode is a native audioNode, or the input property of a tuna node</li>
    <li>bypass(true/false) - bypasses the tuna node, without having to remove it from the effect chain</li>
    <li>activate(true/false) - performs the bypass</li>
    <li>connectInOrder(array) - connects nodes in the order they're defined in the array that is passed to connectInOrder as an argument</li>
    <li>setAutomatableProperty(property, value, duration, actionTime) - allows smooth value changes (automatiation, or tweening). property is a string with the name of the property to automate, value is the value to automate to, duration is how long the automation is in milliseconds, actionTime is the time when the automation should start based on the audioContext time</li>
    <li>verify - makes sure the property that is being set is valid</li>
</ul>