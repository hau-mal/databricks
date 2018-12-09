# Databricks sample content

## 1. dbstats - Compute statistics for all tables (&columns) in a schema
* [Notebook](https://raw.github.com/hau-mal/databricks/master/notebooks/dbstat.dbc)

## 2. Read data from IoT-Hub and write it back to an EventHub and Azure Data Lake
* [Notebook](https://raw.github.com/hau-mal/databricks/master/notebooks/PySimulatedDevicesfromIoTHub2EH.dbc)

## 3. Reading Azure IoT-Hub data stored at a Storage Container Endpoint
Demo-Notebooks to read data from an Azure Storage Container added as an additional custom endpoint to Azure IoT-Hub:

![iot-endpoint](https://raw.githubusercontent.com/hau-mal/articles/master/images/iot-hub-enpoint-1.png)


In this example the Blob file format is configured as:
    
    input/simdev/ingestdate={YYYY}-{MM}-{DD}/{HH}{mm}{iothub}{partition}.avro
       
Important: 
* use the extension .avro
* think how to partition the data, in this example it is daily, if you want to read data hourly define partitions with a finer granularity

Configure a route to the new custom endpoint for the Device Messages. You have to type in nothing in the route query string, it will be true by default, so all messages are routed to the endpoint.

![iot-routes](https://raw.githubusercontent.com/hau-mal/articles/master/images/iot-hub-routes-1.png)

Now all new messages will be streamed to the new endpoint. If you mount the storage container in Azure Databricks, the data can be accessed directly under the mountpoint.

Sample Notebooks can be found here:
* [Notebook1 Scala](https://raw.github.com/hau-mal/databricks/master/notebooks/Read-IoT-Data-from-a-Storage-Container(Scala).dbc)
* [Notebook2 Python](https://raw.github.com/hau-mal/databricks/master/notebooks/Read-IoT-Data-from-a-Storage-Container-Endpoint.dbc)
