# Unit 18.7 Azure Data Factory

## Why should one use Azure Key Vault when working in the Azure environment? What are the pros and cons? What are the alternatives?

Azure Key Vault permits users the ability to keep all credentials within one service. All linked services can have access to the Azure Key Vault to input API keys, usernames, password, and etc. This service provides high levels of security which only the Azure Data Factory or Administrators can read from. If the credentials need to be rotated ADK Linked Services will not need to be modified. Lastly, when data is being migrated the ADF pipeline from Developer to Testing to Production no change is necessary.

## How do you achieve loop functionality within a Azure Data Factory pipeline? Why would you need to use this functionality in a data pipeline?

In order to create a loop functionality within a data pipeline, one must attach the success of an activity to a foreach activity. Within the foreach activity an execute pipeline activity must be created to complete the procedure. This allows the pipeline to iterate through the input dataset and complete a function for each point of data.A specific case that would require a for loop would be to filter out unwanted data and to copy the remaining data into a data warehouse.

## What are expressions in Azure Data Factory? How are they helpful when designing a data pipeline? Please explain with an example.

Expressions must be used within a data pipeline to find the specific values or items to iterate over or even filter. You can think of expressions as a way to speak to ADF and say that you would like the output of a certain activity to be the input of another activity. Expressions also allow outputs to be formatted in a certain manner to achieve visible organization and readability.
Example:

## What are the pros and cons of parametrizing a dataset’s activity in Azure Data Factory?

Parameterizing a dataset allows for specific ranges of files to be transformed or copied into your output database or data warehouse depending on the variables that the developer creates. Pipeline activities search through the dataset and find files that match the parameters. This allows for outputs of categorical files to be stored together. The framework produces a stable and scalable pipeline for changing the input data into another data file type as well as copying the file for increased availability. If parameters did not exist then the developer would not be able to access the desired categorical, timeframe, filtered, and other types of data to input into the pipeline. Also, this allows for unique pipelines to be created to work with a single type of file to promote organization and easier bug detection.
 
## What are the different supported file formats and compression codecs in Azure Data Factory? When will you use a Parquet file over an ORC file? Why would you choose
## an AVRO file format over a Parquet file format 
 
The following file types of supported in Azure Data Factory.
*Avro format
*Binary format
*Delimited text format
*Excel format
*JSON format
*ORC format
*Parquet format
*XML format

The file formats can be categorized as unstructured, semi-structured, and structured data.
Unstructured                       |                   Semi Structured                     |                       Structured

Text					                                              JSON                                                    Avro
CSV					                                                XML						                                          ORC
TCV											                                                                                            Parquet
 
A Parquet file will be used over an ORC file when multiple Hadoop tools will be utilized. ORC files are optimized for effective Hadoop read operations and support only Hive and Pig. Parquet supports many Hadoop tools such as Apache Spark. Apache Avro uses JSON for defining data types and is highly effective for write intensive operations. In the case of pulling in ad-hoc data from a sensor would require intensive amounts of writes on a non relational db or a data warehouse, thus Avro would be the recommended file type.
