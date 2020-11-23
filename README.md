# WK3
WK three homework solution
#Write the following functions:
#makeCacheMatrix: This function creates a special "matrix" object that can cache its inverse.
#cacheSolve: This function computes the inverse of the special "matrix" returned by makeCacheMatrix above.
#If the inverse has already been calculated (and the matrix has not changed), then the cachesolve should
#retrieve the inverse from the cache.Computing the inverse of a square matrix can be done with 
#the solve function in R. For example, if X is a square invertible matrix, then solve(X) returns its inverse.

code:

MakeCache <- function(x=matrix()){
    inv = NULL
    set <- function(y){
        x <<- y
        inv <<-NULL 
    }
    get <- function(){x}
    setinverse <- function(invesrse) {inv <<-invesrse} 
    getinverse <- function(i) {inv}
    list(set = set, get=get, setinverse=setinverse, getinverse=getinverse)
}
cachesolve <- function(x,...){
    inv <- x$getinverse()
    if(!is.null(inv)){
        message("getting chache data")
        return(inv)
    }
    mat <- x$get()
    inv <- solve(mat,...)
    x$setinverse(inv)
    inv
}
source("HW-3.R")
ymatrix <- MakeCache(matrix(1:4, nrow = 2, ncol = 2))
ymatrix$get()

ymatrix$getinverse()
cachesolve(ymatrix)
cachesolve(ymatrix)
ymatrix$getinverse()
