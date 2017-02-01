#!/usr/bin/env python  

'''
estimator.py will estimate the value of pi given some tolerance
Author: Patrick B. Louden
Date: 02/01/2017
'''

import sys # for flushing output data
import argparse # for extracting information from the command line
import math # for the exact value of pi
import random # for random number generation (monte carlo moves)
import time # for timestamps at the start and end of the estimation

def estimatePI(tolerance):
    piApprox = 0.0
    numPntsInCircle = 0
    numAttempts = 0
    
    # While our approximation for pi is less than the specified tolerance
    while( math.fabs(piApprox - math.pi) >= tolerance):
        if( (numAttempts%1000) == 0):
            print "Still approximating pi, number of iterations so far = ", numAttempts
            # I would like to add a feature giving how close we are to convergence....

        numAttempts += 1

        # Generate a random x (0,1) and random y (0,1)
        x = random.random()
        y = random.random()
        
        if( (x**2 + y**2) <= 1):
            numPntsInCircle += 1
            piApprox = 4.0*(float(numPntsInCircle) / float(numAttempts) )
    
    return (piApprox, numAttempts)

def writeOut(piApprox, numAttempts, startTime):
    print "Finished approximating pi!"
    print "Approximate value of pi = ", str(piApprox)
    print "Number of iterations required = ", str(numAttempts)
    print "The program took ", time.time() - startTime, " seconds to run."

def usage():
    print __doc__

def main(argv, startTime):
    parser = argparse.ArgumentParser(
        description='This script will estimate the value of pi by randomly generating points in an x-y plane, and taking the ratio of the number of points that land within a unit circle to the total number of points generated.',
        formatter_class=argparse.RawDescriptionHelpFormatter,
        epilog="Example: estimator -t 0.001")
    parser.add_argument("-t","--tolerance=", action="store", type=float, dest="tol", default="0.001", help="the desired tolerance of the estimate")

    if (not parser.parse_args().tol):
        print "No tolerance specified, default value of 0.001 being used."

    
    (piApprox, numAttempts) = estimatePI(parser.parse_args().tol)
    writeOut(piApprox, numAttempts, startTime)

if __name__ == "__main__":
    startTime = time.time()
    main(sys.argv[1:], startTime)
