## z-index

How to avoid using it.
Try to allow the DOMs heirachy to work naturally and not let z-index interfer with ordering. However if you do end up with positioned absolute elements appearing over the top of others.

##### Note
positioned absolute elements amend the DOM's heirachy to place itself on top of others.

So you can fix this by just adding position relative to the element which you need to be ontop. This will force the elements back into the DOM's heirachy.