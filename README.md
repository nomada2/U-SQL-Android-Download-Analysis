# Android download analysis using U-SQL

When a developer obtains the reports of an Android App, it comes in the form of a set of CSV files. E.g. downloads file would contain information related to the number of downloads for a Device Id and the make and model of the id would be in a different CSV file. It makes it hard for a user to know how many downloads there are by commercially available make and model.  Similarly, there are situations when a developer (or a non-developer) is presented with raw CSV data and it needs to be transformed, queried, sorted, filtered and may even need to be merged with the other data. Tools like excel provide some of the basic capabilities such as sort and filter. But it does not support merging and advanced processing of the data. Power BI can query data over different sources and display it in the desired sorted order with filters. But it is more of a visual tool rather than a tool to merge data.

In such cases, developers “had” no choice but to import the CSVs in a database and process data there and export the processed data.

U-SQL provides an elegant solution to address this. Although it is intended for use with Azure Data Lake, it can be used for processing CSVs in the local environment. It provides built-in Extractors to extract data from CSVs, TSVs and store it in a row set with developer-defined names. This data can be processed using U-SQL that has SQL like syntax. The processed data can be sorted, filtered, merged with other data set. U-SQL also provides built-in Outputters that can export this to CSV or TSV format.

If one wants to create a file that shows downloads for make and model, the steps are outlined here.

0.    Initialize
Initialize the locations of the input and output files. These will be relative to the DataRoot set in the Azure Data Lake options.
1.    Extract
Extract the data from the input files i.e. installs and supported devices files. This data is stored in the in-memory Row sets. (@Model and @Downloads)
2.    Transform 
Transforms the results to the desired shape using U-SQL. This is very similar to SQL.

3.    Output
Output the results to output CSV file using Outputter.

These steps using U-SQL provides a flexible and easy to use mechanism to extract the desired data in no time.

