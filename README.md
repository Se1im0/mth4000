# MTH4000
{
 "cells": [
  {
   "cell_type": "markdown",
   "metadata": {
    "slideshow": {
     "slide_type": "-"
    }
   },
   "source": [
    "# MTH4000 Programming in Python I - Lab 9\n",
    "Dr Matthew Lewis and Prof. Thomas Prellberg\n",
    "\n",
    "## Exercises"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "In these exercises, we will look deeper into dealing with composite data and numpy."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Exercise 1.: Hypercubes"
   ]
  },
  {
   "attachments": {
    "image.png": {
     "image/png": "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"
    }
   },
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Hypercubes are generalisations of three-dimensional cubes into other dimensions.\n",
    "\n",
    "![image.png](attachment:image.png)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "We successively get point, line, square, cube, tesseract, ..."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The figure suggests that we can build up a hypercube of dimension $d+1$ by connecting two copies of a hypercube of dimension $d$ (I see recursion coming up!)."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "While it is hard to visualise in dimensions above three, there is a very easy way to describe a $d$-dimensional hypercube: the coordinates of each of the $2^d$ corners are given by a sequence of $d$ zeros and ones, in other words, we can use it to visualise binary numbers."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Exercise 1.a.: write a function `hypercube_corners()` that takes a non-negative integer and returns a list of the coordinates of all $2^d$ corners.\n",
    "\n",
    "There are many ways of doing this. One way is to take the corrdinates for a (d-1)-dimensional hypercube and append a zero or one. Another way is to use bit-wise logic: all you need to know is that `x & 2**k` is non-zero if the binary expansion of $x$ contains $2^k$."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 24,
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T12:34:51.377837Z",
     "start_time": "2023-11-18T12:34:51.369195Z"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "0 [[]]\n",
      "1 [[0], [1]]\n",
      "2 [[0, 0], [0, 1], [1, 0], [1, 1]]\n",
      "3 [[0, 0, 0], [0, 0, 1], [0, 1, 0], [0, 1, 1], [1, 0, 0], [1, 0, 1], [1, 1, 0], [1, 1, 1]]\n"
     ]
    }
   ],
   "source": [
    "# solution 1:\n",
    "# recursion\n",
    "def hypercube_corners(d):\n",
    "    if d==0:\n",
    "        return [[]]\n",
    "    else:\n",
    "        # build up d from d-1\n",
    "        l=hypercube_corners(d-1)\n",
    "        new_l=[]\n",
    "        for p in l:\n",
    "            new_l.append(p+[0])\n",
    "            new_l.append(p+[1])\n",
    "        return new_l\n",
    "    \n",
    "for d in range(4):\n",
    "    print(d,hypercube_corners(d))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 32,
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T12:44:32.928518Z",
     "start_time": "2023-11-18T12:44:32.921994Z"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "0 [[]]\n",
      "1 [[0], [1]]\n",
      "2 [[0, 0], [1, 0], [0, 1], [1, 1]]\n",
      "3 [[0, 0, 0], [1, 0, 0], [0, 1, 0], [1, 1, 0], [0, 0, 1], [1, 0, 1], [0, 1, 1], [1, 1, 1]]\n"
     ]
    }
   ],
   "source": [
    "# solution 2:\n",
    "# binary expansion\n",
    "def hypercube_corners(d):\n",
    "    bit=lambda x,k: int(x&2**k>0)\n",
    "    return [[bit(x,k) for k in range(d)] for x in range(2**d)]\n",
    "\n",
    "for d in range(4):\n",
    "    print(d,hypercube_corners(d))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Exercise 1.b.: (advanced) find a one-line solution."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 25,
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T12:35:05.758356Z",
     "start_time": "2023-11-18T12:35:05.751288Z"
    },
    "scrolled": true
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "0 [[]]\n",
      "1 [[0], [1]]\n",
      "2 [[0, 0], [0, 1], [1, 0], [1, 1]]\n",
      "3 [[0, 0, 0], [0, 0, 1], [0, 1, 0], [0, 1, 1], [1, 0, 0], [1, 0, 1], [1, 1, 0], [1, 1, 1]]\n"
     ]
    }
   ],
   "source": [
    "# solution 1:\n",
    "# taking the above idea and forcing it into one line - need two list comprehensions. Sorting is not needed but aesthetically pleasing.\n",
    "\n",
    "hypercube_corners=lambda d:[[]] if d==0 else sorted([p+[0] for p in hypercube_corners(d-1)]+[p+[1] for p in hypercube_corners(d-1)])\n",
    "\n",
    "for d in range(4):\n",
    "    print(d,hypercube_corners(d))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 33,
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T12:46:04.145787Z",
     "start_time": "2023-11-18T12:46:04.140010Z"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "0 [[]]\n",
      "1 [[0], [1]]\n",
      "2 [[0, 0], [1, 0], [0, 1], [1, 1]]\n",
      "3 [[0, 0, 0], [1, 0, 0], [0, 1, 0], [1, 1, 0], [0, 0, 1], [1, 0, 1], [0, 1, 1], [1, 1, 1]]\n"
     ]
    }
   ],
   "source": [
    "# soltion 2:\n",
    "# this is easiest to convert from above\n",
    "hypercube_corners=lambda d:[[int(x&2**k>0) for k in range(d)] for x in range(2**d)]\n",
    "\n",
    "for d in range(4):\n",
    "    print(d,hypercube_corners(d))"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 26,
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T12:35:06.612290Z",
     "start_time": "2023-11-18T12:35:06.602049Z"
    },
    "scrolled": true
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "0 [[0]]\n",
      "1 [[0], [1]]\n",
      "2 [[0, 0], [0, 1], [1, 0], [1, 1]]\n",
      "3 [[0, 0, 0], [0, 0, 1], [0, 1, 0], [0, 1, 1], [1, 0, 0], [1, 0, 1], [1, 1, 0], [1, 1, 1]]\n"
     ]
    }
   ],
   "source": [
    "# solution 3:\n",
    "# observe that we can use binary numbers and mess about with strings\n",
    "\n",
    "hypercube_corners=lambda d:[[int(c) for c in bin(i)[2:].zfill(d)] for i in range(2**d)]\n",
    "\n",
    "for d in range(4):\n",
    "    print(d,hypercube_corners(d))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Exercise 1.c: fix the following wrong code"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "A programmer has decided to code up the above problem in the following way:"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 41,
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T12:58:28.143840Z",
     "start_time": "2023-11-18T12:58:28.137440Z"
    }
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "0 [[]]\n",
      "1 [[0, 1], [0, 1]]\n",
      "2 [[0, 1, 0, 1, 0, 0, 1, 1], [0, 1, 0, 1, 0, 0, 1, 1], [0, 1, 0, 1, 0, 0, 1, 1], [0, 1, 0, 1, 0, 0, 1, 1]]\n",
      "3 [[0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1], [0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1], [0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1], [0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1], [0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1], [0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1], [0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1], [0, 1, 0, 1, 0, 1, 0, 1, 0, 0, 1, 1, 0, 0, 1, 1, 0, 0, 0, 0, 1, 1, 1, 1]]\n"
     ]
    }
   ],
   "source": [
    "bit=lambda x,k: int(x&2**k>0) # returns one if x contains 2^k\n",
    "\n",
    "def hypercube_corners(d):\n",
    "    l=[[]]*2**d # create a list with 2^d empty lists to append to individually\n",
    "    for k in range(d): # for all the coordinates\n",
    "        for x in range(2**d): # for all the points\n",
    "            l[x].append(bit(x,k)) # add zero or one\n",
    "    return l\n",
    "\n",
    "for d in range(4):\n",
    "    print(d,hypercube_corners(d))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "The idea is sound, but something is going very wrong! Find it and fix it!\n",
    "\n",
    "\n",
    "*I fell foul of this once when trying to do some lazy hacking. It took me a while to find my error.*"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 40,
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T12:58:23.772086Z",
     "start_time": "2023-11-18T12:58:23.765412Z"
    },
    "scrolled": true
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "0 [[]]\n",
      "1 [[0], [1]]\n",
      "2 [[0, 0], [1, 0], [0, 1], [1, 1]]\n",
      "3 [[0, 0, 0], [1, 0, 0], [0, 1, 0], [1, 1, 0], [0, 0, 1], [1, 0, 1], [0, 1, 1], [1, 1, 1]]\n"
     ]
    }
   ],
   "source": [
    "# the problem is that [[]]*2**d creates a list with l identical references to the same empty list []\n",
    "# to fix this, we need to initialise l differently.\n",
    "bit=lambda x,k: int(x&2**k>0) # returns one if x contains 2^k\n",
    "\n",
    "def hypercube_corners(d):\n",
    "    l=[[] for _ in range(2**d)] # fix: use list comprehension (or for loop). This creates different empty lists\n",
    "    for k in range(d):\n",
    "        for x in range(2**d):\n",
    "            l[x].append(bit(x,k))\n",
    "    return l\n",
    "\n",
    "for d in range(4):\n",
    "    print(d,hypercube_corners(d))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Exercise 1.d: Hamming distance\n",
    "\n",
    "The Hamming distance is the distance between two binary numbers as measured by the number of differing bits. It represents the minimal number of times a bit needs to changed to transform one number into the other.\n",
    "\n",
    "Geometrically, each such bit change corresponds to an edge traversal on a hypercube, so this is the same as the minimal number of edges on the hypercube that separate the two corresponding corners. \n",
    "\n",
    "Write a function `hamming()` that takes two positive integers `x` and `y` and computes their Hamming distance when interpreted as binary numbers. \n",
    "\n",
    "(If you use `bin()` before the comparison you might need to pad the strings with leading zeros.)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 60,
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T19:17:00.689789Z",
     "start_time": "2023-11-18T19:17:00.681492Z"
    },
    "scrolled": true
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "2"
      ]
     },
     "execution_count": 60,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "def hamming(x,y):\n",
    "    bin_x=bin(x)[2:]\n",
    "    bin_y=bin(y)[2:]\n",
    "    n_x=len(bin_x)\n",
    "    n_y=len(bin_y)\n",
    "    d=max(n_x,n_y)\n",
    "    bin_x=bin_x.zfill(d)\n",
    "    bin_y=bin_y.zfill(d)\n",
    "    return sum([i!=j for i,j in zip(bin_x,bin_y)])\n",
    "\n",
    "hamming(3,9)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Exercise 1.e: (advanced) find a one-line solution. "
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 63,
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T19:25:30.734852Z",
     "start_time": "2023-11-18T19:25:30.727094Z"
    }
   },
   "outputs": [
    {
     "data": {
      "text/plain": [
       "2"
      ]
     },
     "execution_count": 63,
     "metadata": {},
     "output_type": "execute_result"
    }
   ],
   "source": [
    "# count the ones in x XOR y\n",
    "hamming=lambda x,y: bin(x^y).count(\"1\")\n",
    "\n",
    "hamming(3,9)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "### Exercise 2: ChatGPT"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Exercise 2.1: Ask ChatGPT to provide feedback on the problematic code in Exercise 1.c\n",
    "\n",
    "Do not do this before you have found the error in the code yourself."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "ChatGPT easily points out the problem with the code."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Exercise 2.2: Use ChatGPT to practice coding"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "##### I asked ChatGPT to write an Exercise Sheet for Numpy avoiding Linear Algebra problems and received the following response (as you can see I asked repeatedly until I liked what I saw):"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T20:24:10.901345Z",
     "start_time": "2023-11-18T20:24:10.878372Z"
    }
   },
   "source": [
    "Certainly! Here's another set of problems focusing on NumPy without linear algebra:\n",
    "\n",
    "### Python Problem Sheet: NumPy Practice (Without Linear Algebra)\n",
    "\n",
    "**Problem 1: Array Creation and Manipulation**\n",
    "\n",
    "a. Create a 1D array with values from 5 to 15 (inclusive).\n",
    "\n",
    "b. Create a 2D array of shape (3, 4) filled with random integers.\n",
    "\n",
    "c. Replace all even numbers in the array from part (b) with the square of their value.\n",
    "\n",
    "d. Create a new array by stacking two 1D arrays vertically.\n",
    "\n",
    "**Problem 2: Element-wise Operations**\n",
    "\n",
    "a. Create a 3x3 matrix with values from 1 to 9.\n",
    "\n",
    "b. Take the square root of each element in the matrix created in part (a).\n",
    "\n",
    "c. Compute the element-wise absolute difference between two randomly generated 3x3 matrices.\n",
    "\n",
    "d. Replace all elements in the matrix from part (c) that are greater than 10 with 10.\n",
    "\n",
    "**Problem 3: Indexing and Slicing**\n",
    "\n",
    "a. Create a 2D array with shape (4, 5) and fill it with values from 0 to 19.\n",
    "\n",
    "b. Extract the subarray consisting of the first two rows and the last three columns.\n",
    "\n",
    "c. Find the mean value of each column in the array from part (a).\n",
    "\n",
    "d. Replace all values in the array from part (a) that are less than 5 with 0.\n",
    "\n",
    "**Problem 4: Broadcasting**\n",
    "\n",
    "a. Create a 2D array with shape (3, 3) filled with random integers.\n",
    "\n",
    "b. Subtract the mean of each column from the corresponding column.\n",
    "\n",
    "c. Multiply each element in the array from part (b) by 3.\n",
    "\n",
    "**Problem 5: Advanced Operations**\n",
    "\n",
    "a. Create a 1D array of 10 elements with random values.\n",
    "\n",
    "b. Find and print all values greater than the median of the array.\n",
    "\n",
    "c. Create a new array that contains only unique elements from the array in part (a).\n",
    "\n",
    "d. Sort the array from part (a) in ascending order.\n",
    "\n",
    "**Problem 6: Boolean Indexing**\n",
    "\n",
    "a. Create a 1D array with 20 random integers.\n",
    "\n",
    "b. Find and print all values less than the mean of the array.\n",
    "\n",
    "c. Replace all values in the array that are divisible by 4 with -1.\n",
    "\n",
    "d. Count the number of negative values in the modified array from part (c)."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "##### I modified these problems slightly to make sure that they were doable with what you have learned. \n",
    "\n",
    "Work through these problems. You may have to consult some help pages to find the functions you need."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 68,
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T20:31:46.197184Z",
     "start_time": "2023-11-18T20:31:46.173183Z"
    },
    "scrolled": false
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "a: [ 5  6  7  8  9 10 11 12 13 14 15]\n",
      "b:\n",
      " [[5 4 5 9]\n",
      " [1 5 8 8]\n",
      " [9 7 7 3]]\n",
      "c:\n",
      " [[ 5 16  5  9]\n",
      " [ 1  5 64 64]\n",
      " [ 9  7  7  3]]\n",
      "d:\n",
      " [[ 5  6  7  8  9 10 11 12 13 14 15]\n",
      " [ 5  6  7  8  9 10 11 12 13 14 15]]\n",
      "a:\n",
      " [[1 2 3]\n",
      " [4 5 6]\n",
      " [7 8 9]]\n",
      "b:\n",
      " [[1.         1.41421356 1.73205081]\n",
      " [2.         2.23606798 2.44948974]\n",
      " [2.64575131 2.82842712 3.        ]]\n",
      "c:\n",
      " [[6 8 4]\n",
      " [6 1 1]\n",
      " [4 2 4]]\n",
      "a:\n",
      " [[ 0  1  2  3  4]\n",
      " [ 5  6  7  8  9]\n",
      " [10 11 12 13 14]\n",
      " [15 16 17 18 19]]\n",
      "b:\n",
      " [[2 3 4]\n",
      " [7 8 9]]\n",
      "c: [ 7.5  8.5  9.5 10.5 11.5]\n",
      "d:\n",
      " [[ 0  0  0  0  0]\n",
      " [ 5  6  7  8  9]\n",
      " [10 11 12 13 14]\n",
      " [15 16 17 18 19]]\n",
      "a:\n",
      " [[9 4 3]\n",
      " [5 3 6]\n",
      " [9 2 7]]\n",
      "b:\n",
      " [[ 1.33333333  1.         -2.33333333]\n",
      " [-2.66666667  0.          0.66666667]\n",
      " [ 1.33333333 -1.          1.66666667]]\n",
      "c:\n",
      " [[ 4.  3. -7.]\n",
      " [-8.  0.  2.]\n",
      " [ 4. -3.  5.]]\n",
      "a: [0.82886759 0.59800225 0.17245274 0.67210983 0.49916129 0.33987653\n",
      " 0.8978921  0.26251661 0.23123669 0.73878465]\n",
      "b: [0.82886759 0.59800225 0.67210983 0.8978921  0.73878465]\n",
      "c: [0.17245274 0.23123669 0.26251661 0.33987653 0.49916129 0.59800225\n",
      " 0.67210983 0.73878465 0.82886759 0.8978921 ]\n",
      "d: [0.17245274 0.23123669 0.26251661 0.33987653 0.49916129 0.59800225\n",
      " 0.67210983 0.73878465 0.82886759 0.8978921 ]\n",
      "a: [44 82 67 95 19 30 72 57 37 93 89  8 53 66 63 78 98 49 89  5]\n",
      "b: [44 19 30 57 37  8 53 49  5]\n",
      "c: [-1 82 67 95 19 30 -1 57 37 93 89 -1 53 66 63 78 98 49 89  5]\n",
      "d: 3\n"
     ]
    }
   ],
   "source": [
    "# solution courtesy of ChatGPT\n",
    "import numpy as np\n",
    "\n",
    "# Problem 1\n",
    "a = np.arange(5, 16)\n",
    "b = np.random.randint(1, 10, size=(3, 4))\n",
    "c = np.where(b % 2 == 0, b**2, b)\n",
    "d = np.vstack((a, a))\n",
    "\n",
    "print(\"a:\", a)\n",
    "print(\"b:\\n\", b)\n",
    "print(\"c:\\n\", c)\n",
    "print(\"d:\\n\", d)\n",
    "\n",
    "# Problem 2\n",
    "a = np.arange(1, 10).reshape(3, 3)\n",
    "b = np.sqrt(a)\n",
    "c = np.abs(np.random.randint(1, 10, size=(3, 3)) - np.random.randint(1, 10, size=(3, 3)))\n",
    "c[c > 10] = 10\n",
    "\n",
    "print(\"a:\\n\", a)\n",
    "print(\"b:\\n\", b)\n",
    "print(\"c:\\n\", c)\n",
    "\n",
    "# Problem 3\n",
    "a = np.arange(20).reshape(4, 5)\n",
    "b = a[:2, -3:]\n",
    "c = np.mean(a, axis=0)\n",
    "d = np.where(a < 5, 0, a)\n",
    "\n",
    "print(\"a:\\n\", a)\n",
    "print(\"b:\\n\", b)\n",
    "print(\"c:\", c)\n",
    "print(\"d:\\n\", d)\n",
    "\n",
    "# Problem 4\n",
    "a = np.random.randint(1, 10, size=(3, 3))\n",
    "b = a - np.mean(a, axis=0)\n",
    "c = b * 3\n",
    "\n",
    "print(\"a:\\n\", a)\n",
    "print(\"b:\\n\", b)\n",
    "print(\"c:\\n\", c)\n",
    "\n",
    "# Problem 5\n",
    "a = np.random.rand(10)\n",
    "b = a[a > np.median(a)]\n",
    "c = np.unique(a)\n",
    "d = np.sort(a)\n",
    "\n",
    "print(\"a:\", a)\n",
    "print(\"b:\", b)\n",
    "print(\"c:\", c)\n",
    "print(\"d:\", d)\n",
    "\n",
    "# Problem 6\n",
    "a = np.random.randint(1, 100, size=20)\n",
    "b = a[a < np.mean(a)]\n",
    "c = np.where(a % 4 == 0, -1, a)\n",
    "d = np.sum(c < 0)\n",
    "\n",
    "print(\"a:\", a)\n",
    "print(\"b:\", b)\n",
    "print(\"c:\", c)\n",
    "print(\"d:\", d)"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "#### Exercise 2.3: ChatGPT can get it wrong"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "##### I had to ask several times, as the answers did not always make sense. Fix the problem with the following problem sheet (I only give the beginning)."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Certainly! Below is an exercise sheet for practicing NumPy array manipulations without involving linear algebra problems. The exercises cover a variety of basic and intermediate array operations.\n",
    "\n",
    "### NumPy Array Manipulation Exercise Sheet\n",
    "\n",
    "1. **Create Arrays:**\n",
    "    - Create a 1-dimensional array with values from 1 to 5.\n",
    "    - Create a 2-dimensional array with shape (3, 4) filled with random integers.\n",
    "    - Create a 3x3 identity matrix.\n",
    "2. **Array Indexing and Slicing:**\n",
    "    - Access the third element of the 1-dimensional array created in exercise 1.\n",
    "    - Slice the second row of the 2-dimensional array created in exercise 1.\n",
    "    - Extract a 2x2 submatrix from the identity matrix.\n",
    "3. **Array Reshaping:**\n",
    "    - Reshape the 1-dimensional array from exercise 1 into a 2x2 matrix.\n",
    "    - Flatten the 2-dimensional array from exercise 1.\n",
    "    - Transpose the 2x2 submatrix extracted in exercise 2.\n",
    "\n",
    "(the rest is cut)"
   ]
  },
  {
   "cell_type": "code",
   "execution_count": 75,
   "metadata": {
    "ExecuteTime": {
     "end_time": "2023-11-18T20:56:54.124352Z",
     "start_time": "2023-11-18T20:56:54.090340Z"
    },
    "scrolled": true
   },
   "outputs": [
    {
     "name": "stdout",
     "output_type": "stream",
     "text": [
      "[1 2 3 4 5]\n",
      "[[1]\n",
      " [2]\n",
      " [3]\n",
      " [4]\n",
      " [5]]\n"
     ]
    },
    {
     "ename": "ValueError",
     "evalue": "cannot reshape array of size 5 into shape (2,2)",
     "output_type": "error",
     "traceback": [
      "\u001b[1;31m---------------------------------------------------------------------------\u001b[0m",
      "\u001b[1;31mValueError\u001b[0m                                Traceback (most recent call last)",
      "Cell \u001b[1;32mIn[75], line 6\u001b[0m\n\u001b[0;32m      4\u001b[0m B\u001b[38;5;241m=\u001b[39mA\u001b[38;5;241m.\u001b[39mreshape((\u001b[38;5;241m5\u001b[39m,\u001b[38;5;241m1\u001b[39m))\n\u001b[0;32m      5\u001b[0m \u001b[38;5;28mprint\u001b[39m(B)\n\u001b[1;32m----> 6\u001b[0m C\u001b[38;5;241m=\u001b[39mA\u001b[38;5;241m.\u001b[39mreshape((\u001b[38;5;241m2\u001b[39m,\u001b[38;5;241m2\u001b[39m))\n",
      "\u001b[1;31mValueError\u001b[0m: cannot reshape array of size 5 into shape (2,2)"
     ]
    }
   ],
   "source": [
    "# the reshaping in Q3 does not make sense:\n",
    "A=np.arange(1,6)\n",
    "print(A)\n",
    "# this works\n",
    "B=A.reshape((5,1))\n",
    "print(B)\n",
    "# but this does not, it doesn't fit\n",
    "C=A.reshape((2,2))"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "# Regardless of these problems, ChatGPT (in this case 3.5) is a valuable source for practice problems."
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "## Submit your Jupyter Notebook to QMPLUS"
   ]
  },
  {
   "cell_type": "markdown",
   "metadata": {},
   "source": [
    "Once you are done, save the jupyter notebook and submit it to QMPLUS under Lab Report Week 10."
   ]
  },
  {
   "cell_type": "code",
   "execution_count": null,
   "metadata": {},
   "outputs": [],
   "source": []
  }
 ],
 "metadata": {
  "kernelspec": {
   "display_name": "Python 3 (ipykernel)",
   "language": "python",
   "name": "python3"
  },
  "language_info": {
   "codemirror_mode": {
    "name": "ipython",
    "version": 3
   },
   "file_extension": ".py",
   "mimetype": "text/x-python",
   "name": "python",
   "nbconvert_exporter": "python",
   "pygments_lexer": "ipython3",
   "version": "3.9.12"
  }
 },
 "nbformat": 4,
 "nbformat_minor": 2
}
