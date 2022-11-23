#!/usr/bin/env python
# coding: utf-8

# # <center> <h1> <font color='orange'> ORANGE TEAM <font> </h1> </center>

# # <h2><font color='blue'>TEAM MEMBER NAME </font></h2>

# # <h3><center><font color='blue'> 1. GOLNOOSH TOOSI, 2. MONOWAR HOSSAIN SAIKAT, 3. PRUDHVI RAJ DASARI</font></center></h3>

# # <h3><font color='RED'>PROJECT ASSIGNMENT 3A : EXTRACTING THE DATA FROM AN IMAGE FILE USING PYTHON </font></h3>

# Source of data:
# 
# For this assignment we have downloaded our data from the followng website.

# "https://data.tnris.org/collection?c=97a6ce2e-8a4c-4570-a3ed-983ef1a4554b#4.41/31.32/-100.08"

# From this data we will try to find out the answers of the following qiestions:
# 

# 1. What is the number of total valid points?

# 2. What is the total number of total forest cells?

# 3. What is the total percentage of forest in that raster data?

# 4. What is the total percentage of wetlands in that raster data?

# 5. What is the total percentage of developed area in that rater data?

# 6. What is the total percentage of unused point in that raster data?

# Now we will write the following code to read that raster data.

# In[1]:


#Importing libraries:
import osgeo.gdal as gdal            #Importing gdal library to interpret the image file
import numpy as np                   #Importing numpy library to pick the needed data
import matplotlib.pyplot as plt      #Importing matplot library to plot the raster data


# In[3]:


filePath = "C:\\Pyexam\\nlcd19_48_lc\\nlcd_2019_land_cover_l48_20210604_TX.img"   #Defining the directory 
dataset = gdal.Open( filePath, gdal.GA_ReadOnly )                       #Decrypting the data from the image file
ncol = dataset.RasterXSize                                              #Indicating the number of columns
nrow = dataset.RasterYSize                                              #Indicating the number of Rows                                      
nband = dataset.RasterCount                                             #Indicating the number of raster bands
DataType = dataset.GetRasterBand(1).DataType                            #Specifying the nature of the data


# In[4]:


data_array = dataset.GetRasterBand(1).ReadAsArray()                   #Storing the data as an array
CountedPoints = data_array[data_array>0]                              #Counting the valid data points
forest = data_array[data_array> 41]                                   #Sorting the forest data points
forest = forest[forest<44]                                            #Trimming the forest data points
forestPer = len(forest)*100/ len(CountedPoints)                       #Calculating the forest range percentile     
DevelopedArea = data_array[data_array> 21]                            #Sorting the developed area data points
DevelopedArea = DevelopedArea[DevelopedArea<24]                       #Trimming the developed area data points
DevAreaPer = len(DevelopedArea)*100/len(CountedPoints)                #Calculating the developed area range percentile 
Wetlands = data_array[data_array> 89]                                 #Sorting the wetlands data points
Wetlands = Wetlands[Wetlands<95]                                      #Trimming the wetlands data points
WetAreaPer = len(Wetlands)*100/len(CountedPoints)                     #Calculating the wetlands range percentile 


# In[5]:


print("Columns: ", dataset.RasterXSize)                                                           
print("Rows: ", dataset.RasterYSize)                                                              
print("Band count: ", dataset.RasterCount)                                                         
print("Total Number of valid Points: ", len(CountedPoints) )                                     
print("Total Number of forest cells: " , len(forest))                                              
print("Percentile of forest: " , forestPer)
print("Percentile of wetlands: ", WetAreaPer)
print("Percentile of Developed Area: ", DevAreaPer)
print ("Percentile of unassigned points:" , ((ncol*nrow)-len(CountedPoints))*100/(ncol*nrow))


# In[6]:


data_array.shape                              #Reshaping the data into a shape
plt.figure(figsize=(10, 10))                  #Indicating the dimensions of the plot
plt.imshow(data_array)                        #Plotting the data array into the aforementioned figure
plt.colorbar()                                #Adding the color bar


# In[ ]:




