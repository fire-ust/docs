DateTimeFieldExtract
=========== 

It creates a new DataFrame by extracting Date and Time fields.

Input
--------------
It takes in a DataFrame as Input

Output
--------------
Node to extract year/month/dayofmonth/hour/minute/seconad values from TimeStamp

Type
--------- 

transform

Class
--------- 

fire.nodes.etl.NodeDateTimeFieldExtract

Fields
--------- 

.. list-table::
      :widths: 10 5 10
      :header-rows: 1

      * - Name
        - Title
        - Description
      * - inputCol
        - Column
        - The input column name
      * - extractYear
        - Extract Year
        - Extract Year
      * - extractMonth
        - Extract Month
        - Extract Month
      * - extractDayOfMonth
        - Extract Day of Month
        - Extract Day of Month
      * - extractHour
        - Extract Hour
        - Extract Hour
      * - extractMinute
        - Extract Minute
        - Extract Minute
      * - extractSecond
        - Extract Second
        - Extract Second
      * - extractWeekOfYear
        - Extract WeekOfYear
        - Extract WeekOfYear


Details
-------


Extracts year, month, day of month, hour, minute, second and week of year in different columns.


