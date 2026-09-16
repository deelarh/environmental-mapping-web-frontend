**Read this first: what EMP is supposed to do**
EMP is a 3D copy of a factory. A user clicks a machine in the 3D model and attaches a test result to it. Later, someone searches for that test result and jumps back to the exact machine.
Five things must work perfectly:
1.	When you click a machine, EMP knows which machine it is.
2.	A test attached to Machine A stays on Machine A, forever.
3.	You can go machine → test record, and test record → machine.
4.	Search finds the right records, even with thousands of them.
5.	A broken 3D file shows a clear message, not a frozen screen.
Every task below exists to make one of those five things work.

**Words you will see in these tasks**
Word	What it means
Babylon.js	The library that draws our 3D factory in the browser.
Scene	One loaded 3D world. We create one each time a user opens a facility.
Mesh	One 3D shape. A conveyor belt is a mesh. A factory model contains hundreds.
Picking	Working out which mesh the user clicked. Babylon fires an invisible ray from the mouse and tells us the first thing it hits.
Pick predicate	A function that tells Babylon "ignore these meshes when picking".
Disc	The little coloured circle we draw on a machine to show a tag exists there.
Instance	A copy of a mesh that shares the original's shape. Used for repeated machines. It needs special handling because it is not a separate shape.
Primitive	When a 3D model splits one machine into pieces, Babylon names them _primitive0, _primitive1. They are parts of one machine, not separate machines.
Render loop	The function that redraws the screen roughly 60 times a second.
Dispose	Babylon's word for "clean up and free the memory". If we forget, memory leaks and the app slows down.
IndexedDB	A database inside the browser. We use it to cache downloaded 3D files so they load faster next time.
FPS	Frames per second. Below 30 feels laggy. This is how we measure "smooth".

**Tools you will need**
Babylon Inspector — shows draw calls, active meshes and frame time. Add it temporarily while working on any performance task:
import "@babylonjs/inspector";
scene.debugLayer.show();
Chrome DevTools → Performance tab — record while rotating the model to see where frame time goes.
Chrome DevTools → Memory tab — take a heap snapshot, open and close a model ten times, take another. If the second is much bigger, we are leaking memory.
