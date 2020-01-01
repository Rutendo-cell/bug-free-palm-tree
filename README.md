# bug-free-palm-tree
makeCacheMatrix function creates a special matrix object that can cache its inverse.
## the special matrix is a list containing a function to
## set the value of the matrix
## get the value of the matrix
## set the inverse of the matrix
## get the inverse of the matrix

 makeCacheMatrix <- function(x = matrix()) 
{m <- NULL
set <- function(y)
{
  x <<- y
  m <<- NULL
}
get <- function() x
setInverse <- function(i) m <<- solve(x)
getInverse <- function() m
list(set = set, get = get, setInverse = setInverse, getInverse = getInverse)
}


## cacheSolve function computes the inverse of the matrix returned by makeCacheMatrix.
##If this inverse has already been calculated cacheSolve should retrieve the inverse of the cache 

cacheSolve <- function(x, ...) {
  m <- x$getInverse()
  if(!is.null(m))
  {
    return(m)
  }
  m <- solve(x$get())
  x$setInverse(m)
  m
}
