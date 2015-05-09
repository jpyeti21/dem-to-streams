# dem-to-streams
Generate stream network based on DEM, allowing for selection of stream density and DEM extent
1)	Select DEM
2)	Select Extent (Bounding Box)
a)	Bounding box will be converted into projection of DEM
b)	Project(data management)
3)	Clip DEM
a)	Clip(data management)
4)	Watershed Creation Steps
a)	Fill
i)	Input = clipDEM
ii)	Output = fill
b)	Flow Direction
i)	Input = fill
ii)	Output = flowdir
c)	Flow Accumulation
i)	Input = flowdir
ii)	no input weight raster
iii)	FLOAT
iv)	Output = flowaccum
v)	Takes some time to run
d)	Con (conditional evaluation)
i)	Input = flowaccum
ii)	Expression (Value > 500)
(1)	a variety of threshholds (cells), for example: 100, 250, 500, 750, 1000, 2000, 4000
iii)	Input True Raster = 1
iv)	Input False Raster (not used)
v)	Output = net
e)	Stream Link
i)	Input stream raster = net
ii)	Input flow direction raster = flowdir
iii)	Output = source
f)	Watershed
i)	Input flow dir raster = flowdir
ii)	Input raster = source
iii)	Pour point field = Value
iv)	Output = watershed
g)	Stream Order
i)	Input stream raster = source
ii)	Input flow dir raster = flowdir
iii)	Output = stream_order
iv)	Coordinate system of clip raster
h)	Stream to Feature
i)	Input stream raster = stream_order
ii)	Input flow dir raster = flowdir
iii)	Output features = new Feature Class
