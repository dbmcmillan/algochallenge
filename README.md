# Python Algorithmic Challenge

This is a problem I found from a prior year's coding competition, and decided to write an algorithm in python to solve it. The problem is quite simple: we're given a number of point pairs that define line segments, and the task is to count the number of geometric figures and the number of polygons formed by these line segments. For example, the first line segment is (84,84), (78,84). This defines a segment that connects these two endpoints. If another segment shares one of these endpoints, then those two line segments would form a geometric shape consisting of two line segments, with 1 shared endpoint and two unshared endpoints. 

## Solution

### Part 1: Counting number of geometric shapes
To count the number of geometric shapes, I first defined a list "lines" an empty list "geo". The elements of the lines list were themselves lists of two tuples: one tuple for each endpoint. Therefore each line segment is defined as a list consisting of two tuples, and the "lines" list is a list of all the given line segments. 

The strategy to count the number of geometric shapes will be to place the first element in list "lines" in list "geo", erase that element from list "lines", and then iterate through the list "lines" to find a line segment with an endpoint matching the endpoint of the element already in "geo". "Geo" is then appended with that line segment, and it is deleted from "lines". 

We then continue iterating through list "lines" looking for line segments with endpoints that match an endpoint of one of the line segments in list "geo". When we can no longer find such an element, we know that we have a complete geometric shape, so we will add one to the count variable representing the number of geometric shapes, print list "geo" (which shows all the line segments of the geometric shape, empty the list "geo", and start the process over. 

We continue this iteration until the "lines" list is empty, at which point we know that we've counted all the geometric shapes formed by the line segments. 

### Part 2: Counting the number of polygons

Every polygon is a geometric shape, but every geometric shape is not a polygon. To determine the number of polygons, we would need a testable rule to distinguish between polygons and non-polygons based on the properties of the line segments that create each geometric shape. I realized that since polygons are closed figures, that each vertex of the polygon would have to occur in exactly two line segments - no more and no less. Therefore, if each geometric shape has exactly two instances of every endpoint, that shape would be a polygon. I coded this test into the same iterative loop used to determine the number of geometric shapes. Like with geometric shapes, I instantiated a counter that would increase by one each time a polygon was found, prior to deleting the elements of the list "geo" and starting again.  

### Conclusion
The final answer based on the given line segment inputs is that there are 10 geometric shapes and 4 polygons, which was the correct answer. To make the algorithm more universalizable, I could alter the code to allow the user to input the various line segments as pairs of tuples, and then use the same code on the inputted values to count the number of geometric shapes and polygons. 
