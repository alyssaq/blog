Title: Installing OpenCV on Mac OSX with homebrew
Date: 2014-08-18 16:24 
Tags: mac, opencv

1. Install the package manager [Homebrew](http://brew.sh/). It beats MacPorts any day.
2. Go ahead and install [OpenCV](http://opencv.org/):

		$ brew install opencv

3. If all is well, it should be available at:
    
		/usr/local/Cellar/opencv/2.4.9
    
4. Create a symlink to the compiled OpenCV files. If you don't mind setting up your `PYTHONPATH` and messing up python2 and python3 support, you may use `brew link opencv`. Otherwise, I recommend doing the manual symlink to your Python 2.7 site-packages.

    	$ sudo ln -s /usr/local/Cellar/opencv/2.4.9/lib/python2.7/site-packages/cv.py /Library/Python/2.7/site-packages/cv.py
    	$ sudo ln -s /usr/local/Cellar/opencv/2.4.9/lib/python2.7/site-packages/cv2.so /Library/Python/2.7/site-packages/cv2.so 
    
5. Check that it works!

		$ python
		Python 2.7.9
		[GCC 4.2.1 (Apple Inc. build 5666) (dot 3)] on darwin
		Type "help", "copyright", "credits" or "license" ...
		>>>
		>>> import cv2
		>>> img = cv2.imread('path-to-image/helloworld.jpg')
		>>> cv2.imshow('Test image', img)