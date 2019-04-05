# Overview
Spatial is a module which contains a series of spatially relevent helper
functionality and classes. 

## Bounds
A Bounding Box allows you
to calculate the overall bounds of a point cloud - but does not store
the point cloud itself, it simply expands to match the outer most limits
of the point cloud data.

There are three Bounding Box classes:

__Bounds__: This is an N-Dimensional bounding box, allowing your points to
be of any dimensional length. This is useful if working in one dimension
or in a dimensional space greater than three dimensions.

__Bounds2D__: This inherits from Bounds - so gives all the same funcitonaltiy
except it has some convenience functions with an assumption of width
and height.

__Bounds3D__: Much like Bounds2D, Bounds3D is a Bounds object which exposes
functionality with the assumption of Width, Height and Depth.

In this example we create two three dimensional bounding boxes
and test wether they intersect

```python
import spatial

# -- Test bound intersections
points_a = [
    [0, 0, 0],
    [1, 1, 1],
]

points_b = [
    [5, 5, -5],
    [3, 3, 3],
]

bounds_a = spatial.Bounds3D(points_a)
bounds_b = spatial.Bounds3D(points_b)

print('Does bounds A intersect with bounds B : %s' % ('Yes' if bounds_b.intersects(bounds_a) else 'No'))
```


In the following example we create a bounding box and test whether
the given point is inside the bounds:

```python
import spatial

bounds = spatial.Bounds2D()

# -- Create a point cloud
points = [
    [-2, -2],
    [2, 2],
]

# -- Add all our points
bounds.add_points(points)

# -- Test whether a point is inside the bounds
outside_point = [3, 5]
print('Bound contains %s : %s' % (outside_point, bounds.contains(outside_point)))

# -- Same test giving a point inside the bounds
inside_point = [1, 1]
print('Bound contains %s : %s' % (inside_point, bounds.contains(inside_point)))
```

## Credits & Collaboration


I am always open to collaboration, so if you spot bugs lets me know, or if
you would like to contribute or get involved just shout!


## Compatibility

Launchpad has been tested under Python 2.7 and Python 3.7 on Windows and Ubuntu.
