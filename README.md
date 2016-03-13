# Md-Badiuzzaman-Khan#My solution (Function)
#cachematrix.R:

#1. makeCacheMatrix

makeCacheMatrix <- function(x = matrix()) {
        inv <- NULL
        set <- function(y) {
                x <<- y
                inv <<- NULL
        }
        get <- function() x
        setInverse <- function(inverse) inv <<- inverse
        getInverse <- function() inv
        list(set = set,
             get = get,
             setInverse = setInverse,
             getInverse = getInverse)
}


#2.cacheSolve

cacheSolve <- function(x, ...) {
        ## Return a matrix that is the inverse of 'x'
        inv <- x$getInverse()
        if (!is.null(inv)) {
                message("getting cached data")
                return(inv)
        }
        mat <- x$get()
        inv <- solve(mat, ...)
        x$setInverse(inv)
        inv
}


#TESTING MY FUNCTION



getwd()
dir()
ls()
source("C:/Users/mdbadiuzzaman/Documents/IntroStat/coursera/cachematrix.R")

my_matrix<-makeCacheMatrix(matrix(1:4,2,2))
my_matrix$get()

my_matrix$getInverse()

cacheSolve(my_matrix)

cacheSolve(my_matrix)

my_matrix$getInverse()

my_matrix$set(matrix(c(2, 2, 1, 4), 2, 2))

my_matrix$get()

my_matrix$getInverse()

cacheSolve(my_matrix)

cacheSolve(my_matrix)

my_matrix$getInverse()



