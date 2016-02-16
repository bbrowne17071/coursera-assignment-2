# coursera-assignment-2
R filed for coursera R programming assignment 2

## This pair of functions allows calculation and storage of a matrix
## as defined by the user

## Creates a list of subfunctions that allows the user to
## input and view the matrix of choice. Additionally if the inverse
## of a matrix has been calculated (using another function) then this
## allows that inverse matrix to be viewed.

makeCacheMatrix <- function(x = matrix()) {
    m <- NULL
    set <- function(y) {
        x <<- y
        m <<- NULL
    }
    get <- function() x 
    setinv <- function(solve) m <<- solve
    getinv <- function() m
    list(set = set, get = get, setinv = setinv, getinv = getinv)
}


## This function will calculate the inverse of a matrix input into the above
## function. If an inverse has already been calculated and stored in the 
## cache of the above function, the following function will access that stored
## variable and display it without repeating the calculation.

cacheSolve <- function(x, ...) {
        ## Return a matrix that is the inverse of 'x'
    m <- x$getinv()
    if(!is.null(m)) {
        message("getting cached data")
        return(m)
    }
    data <- x$get()
    m <- solve(data, ...)
    x$setinv(m)
    m
}
