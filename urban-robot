from math import radians, cos, sin, asin, sqrt

import urllib.request
import json

print("Simple tool to find the distance between two postcodes.")

one = input("Postcode 1: ") # enter the first postcode
two = input("Postcode 2: ") # enter the second postcode
one = one.lower() # convert to lowercase
two = two.lower() 
one = one.replace(" ", "") # remove spaces
two = two.replace(" ", "")

# first postcode
res1 = urllib.request.urlopen(f"http://api.postcodes.io/postcodes/{one}").read() # opening api.postcodes.io with f string literal for postcode one in URL
data1 = json.loads(res1) # saving dict as variable
lon1 = data1["result"]["longitude"] # getting longitutde from dict
lat1 = data1["result"]["latitude"] # getting latitude from dict

# second postcode
res2 = urllib.request.urlopen(f"http://api.postcodes.io/postcodes/{two}").read() # pening api.postcodes.io with f string literal for postcode two in URL
data2 = json.loads(res2) # saving dict as variable
lon2 = data2["result"]["longitude"] # getting longitutde from dict
lat2 = data2["result"]["latitude"] # getting latitude from dict

lon1, lat1, lon2, lat2 = map(radians, [lon1, lat1, lon2, lat2])

'''
Math time! To calculate the distance I had to look online, the below website was used.
https://byjus.com/jee/distance-formula/

'''

dlon = lon2 - lon1 
dlat = lat2 - lat1 
a = sin(dlat/2)**2 + cos(lat1) * cos(lat2) * sin(dlon/2)**2
c = 2 * asin(sqrt(a)) 
r = 3956 # converted r to miles, as this is the UK.
res = c*r
res = round(res, 2)

print(f"There are {res} miles between the two postcodes.") # display results.
