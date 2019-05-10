# AICollisionDemo
A demo featuring AI, Collision, and other features from the 2D Nickel RTS Game Engine.

## [Run Demo](http://ibrahimsardar.rf.gd/)


---

### Key Implementations:
<ul>
    <li><a href="https://www.red3d.com/cwr/steer/gdc99/">Combining multiple behaviors in autonomous agents</a></li>
    <li>Various steering behaviors (seek, flee, wander, obstacle avoidance, etc...)</li>
    <li>BOIDS steering behavior (align, separate, cohere)</li>
    <li><a href="http://idm-lab.org/bib/abstracts/papers/aaai07a.pdf">Theta * pathfinding</a></li>
    <li>A * pathfinding</li>
    <li>Dijkstra pathfinding</li>
    <li>Line-of-sight detection (used by Theta * algorithm)</li>
    <li>2D collision detection with separating axis theorem (polygon to polygon)</li>
    <li>More 2D collision detection with circles, polygons, rays, lines, & points</li>
    <li>2D collision resolution (without rotational resolution)</li>
    <li>Quadtree for collision optimization</li>
    <li>2D Particle effects (in this demo: smoke, fire, jet, falling ice)</li>
    <li><a href="http://realtimecollisiondetection.net/blog/?p=91">Buffer optimization for particles</a></li>
    <li>Custom UI</li>
    <li>Debug visualizations (some steering vectors, quadtree, collisions, etc...)</li>
    <li>Editable tilemap</li>
    <li>Advanced parameter control of most aspects of the demo</li>
</ul>

### Areas of Improvement:
<ul>
    <li>If the sight line ends up at an intersection of 2 avoid circles, agent may get stuck:
        to fix this, we would need to scan all obstacles in the scan area and create a new convex avoid surface.</li><br>
    <li>Game objects are quite loaded with functions and variables, causing major slowdowns with just a few objects:
        to fix this, we can separate static-abled properties from individual game objects into static classes.</li><br>
    <li>The UX is not as intuitive as it could be, users may get overwhelmed on first look at all the options:
        to fix this, we revamp all the options and place them next to similar options, and fit advanced options
        in dropdown menus or dialogue boxes that would pause the simulation.</li><br>
    <li>Looking underneath the hood, we see many areas of the code to be quite messy,
        this is because this demo and many parts of the Nickel library were hacked together with
        little to medium attention to software design, but with greater attention to specific algorithms.
        To fix this, we could separate game data and logic, then have an MVC style approach, except the
        controller would be split into multiple parts, where each part would handle a crucial portion of
        the game loop as well as initialization, and the model would be simple .json files filled with 
        object data. So now if we wanted to create a game using the engine, we could simply add modular 
        structures to the controller and the view, and easily setup our game data in .json files.
        Along with this high level architecture, we should also make use of some design patterns.
        For this, we should focus on using the pipeline design pattern with the different parts of the
        controller. Using abstract modules will also help to allow more extensibility. Since game objects,
        more often than not, are tangled with each other, we can allow users to inject custom scripts into
        game objects to manipulate them easily. Since this is JavaScript and not C++, it is too easy to
        inject variables and whatnot into JavaScript objects, so we would have to devise a way to discourage
        that and utilize the game objects bulit-in script injector system instead. This is a summary of what
        the architecture can look like after some improvements.
    </li>
</ul>
