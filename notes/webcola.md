---
UID: '0000:2019:0813:0236'
---
grouped layout:
https://ialab.it.monash.edu/webcola/examples/smallgroups.html

gridified grouped layout:
https://ialab.it.monash.edu/webcola/examples/gridifiedSmallGroups.html
https://codepen.io/karlin/pen/qdYYmz

also check out this
http://bl.ocks.org/nitaku/7733be2b2e595cd17189

USING WITHOUT D3
https://github.com/tgdwyer/WebCola/issues/230

to break into this:
* look at their D3 example for setting up.

const nodeSize = 20, threshold = 0.01; 
let starts = 0, ticks = 0, ends = 0, 
     layout = new cola.Layout() 
     .handleDisconnected(false) // handle disconnected repacks the components which would hide any drift 
     .linkDistance(1) // minimal link distance means nodes would overlap if not for... 
     .avoidOverlaps(true) // force non-overlap 
     .links([{ source: 0, target: 1 }]) 
     .constraints([{ type: "alignment", axis: "y", 
         offsets: [ 
             { node: 0, offset: 0 }, 
             { node: 1, offset: 0 }, 
         ] 
     }]) 
     .on(cola.EventType.start, e => starts++) 
     .on(cola.EventType.tick, e => ticks++) 
     .on(cola.EventType.end, e => ends++); 
 layout.nodes().forEach(v=>v.width = v.height = nodeSize) // square nodes 
 layout.start(); // first layout 

 look at cola.Layout()

 Let's test this theory

 