This is the code from my PyTexas 2015 lighting talk.

Currently the docker deployment is broken, will fix soon.

.. image:: https://raw.githubusercontent.com/stevemartingale/pytexas2015/master/screenshot.png

The scenario is that you run a toy factory.  Your toy making machines send a message to a data collection API (Flask) every time a toy is completed. The data collection API puts the message into a Kafka topic called "sensor_temp".    
There is a Storm Spout that consumes that Kafka topic, deserializes the message and emits the machine id and the machine's temperature to a Storm Bolt. The bolt increments the machines' production count and updates the temperature value, this is stored in MongoDB.  A very simple Meteor.js app displays a dashboard of the machine stats.

The toy machine message data is generated by simulator/simulation.py.

Parse.ly's Streamparse library was used to write the Apache Storm topology in Python.