# Weather prediction with RNN

In this section, I will review three advanced techniques for improving the performance and generalization power of recurrent neural networks. 
I will demonstrate all three concepts on a weather forecasting problem, where there is access to a timeseries of data points coming from sensors installed on the roof of a building, 
such as temperature, air pressure, and humidity, which we use to predict what the temperature will be 24 hours after the last data point collected. 
This is a fairly challenging problem that exemplifies many common difficulties encountered when working with timeseries.

### Techniques covered:
-Recurrent dropout, a specific, built-in way to use dropout to fight overfitting in recurrent layers.
-Stacking recurrent layers, to increase the representational power of the network (at the cost of higher computational loads).
-Bidirectional recurrent layers, which presents the same information to a recurrent network in different ways, increasing accuracy and mitigating forgetting issues.

In all of the examples in this section, I will be playing with a weather timeseries dataset recorded at the Weather Station at the Max-Planck-Institute for Biogeochemistry in Jena, Germany: http://www.bgc-jena.mpg.de/wetter/.

### Dataset
In this dataset, fourteen different quantities (such as air temperature, atmospheric pressure, humidity, wind direction, etc.) are recorded every ten minutes, over several years. The original data goes back to 2003, but I limit it to data from 2009-2016. This dataset is perfect for learning to work with numerical timeseries. I will use it to build a model that takes as input some data from the recent past (a few days worth of data points) and predicts the air temperature 24 hours in the future.
