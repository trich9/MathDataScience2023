#resize image

'''
'''python
!apt-get install poppler-utils
!pip install pdf2image
from pdf2image import convert_from_path
import requests
import matplotlib.pyplot as plt
import numpy as np
from skimage.io import imread
from skimage.transform import resize

