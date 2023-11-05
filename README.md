# Studying-functions-
#A program which have the ability to calculate functions 

import math

# Define a function to display the properties of a given function
def display_properties(f):
    print("Function: f(x) =", f.__name__)
    print("Domain: all real numbers")
    
    # Check if the function is even
    if is_even(f):
        print("Even function: f(-x) = f(x) for all x in the domain")
    else:
        print("Not an even function")
    
    # Check if the function is odd
    if is_odd(f):
        print("Odd function: f(-x) = -f(x) for all x in the domain")
    else:
        print("Not an odd function")
    
    # Check if the function is periodic
    period = find_period(f)
    if period:
        print("Periodic function: f(x +", period, ") = f(x) for all x in the domain")
    else:
        print("Not a periodic function")
    
    # Check if the function is monotonic
    if is_monotonic(f):
        print("Monotonic function: f(x) is either increasing or decreasing for all x in the domain")
    else:
        print("Not a monotonic function")

# Define a function to check if a function is even
def is_even(f):
    for x in range(-10, 11):
        if f(x) != f(-x):
            return False
    return True

# Define a function to check if a function is odd
def is_odd(f):
    for x in range(-10, 11):
        if f(x) != -f(-x):
            return False
    return True

# Define a function to find the period of a function (if it exists)
def find_period(f):
    for i in range(1, 11):
        period = i
        for x in range(-10, 11):
            if f(x) != f(x + period):
                period = 0
                break
        if period:
            return period
    return 0

# Define a function to check if a function is monotonic
def is_monotonic(f):
    is_increasing = True
    is_decreasing = True
    for x in range(-10, 11):
        if f(x) > f(x+1):
            is_increasing = False
        if f(x) < f(x+1):
            is_decreasing = False
    return is_increasing or is_decreasing

# Define some sample functions to test the code
def f(x):
    return x**2

def g(x):
    return math.sin(x)

def h(x):
    return math.exp(x)

# Call the display_properties function for each sample function
display_properties(f)
print("--------------------")
display_properties(g)
print("--------------------")
display_properties(h)
