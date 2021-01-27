Multi-Validation Workflow
===============

This workflow performs multiple validations on each incoming record

* Records which pass validation are output into the first edge
* Records which fail validation are output into the seconds edge

Validations
-----------
* Ensures that field is greater than or equal to specified string value
* Ensures that field is less than or equal to specified string value
* Ensures that field matches given datePattern
* Ensures that the email is valid
* Ensures field length is greater than or equal to specified length

Workflow
--------

Below is the workflow. It does the following:

* Reads data from a CSV file.
* Performs specific validation on specific columns.

.. figure:: ../../_assets/tutorials/data-engineering/data-validation-multiple/Capture1.PNG
   :alt: Data Validation Multiple
   :align: center
   :width: 60%
   
Reading from CSV File
---------------------

``DatasetCSV`` processor reads data from a CSV file. 

Processor Configuration
^^^^^^^^^^^^^^^^^^

.. figure:: ../../_assets/tutorials/data-engineering/data-validation-multiple/Capture2.PNG
   :alt: Data Validation Multiple
   :align: center
   :width: 60%
   
   
Processor Output
^^^^^^

.. figure:: ../../_assets/tutorials/data-engineering/data-validation-multiple/Capture3.PNG
   :alt: Data Validation Multiple
   :align: center
   :width: 60%

String Functions
----------------
``StringFunctions`` processor performs specified operation on the selected column (i.e. trim function for column 'name' in this case)

Processor Configuration
^^^^^^^^^^^^^^^^^^

.. figure:: ../../_assets/tutorials/data-engineering/data-validation-multiple/Capture4.PNG
   :alt: Data Validation Multiple
   :align: center
   :width: 60%
   
Processor Output
^^^^^^

.. figure:: ../../_assets/tutorials/data-engineering/data-validation-multiple/Capture5.PNG
   :alt: Data Validation Multiple
   :align: center
   :width: 60%
   

Performing Validation
---------------------

``ValidationMultiple`` processor performs different validation on different columns.

Processor Configuration
^^^^^^^^^^^^^^^^^^

.. figure:: ../../_assets/tutorials/data-engineering/data-validation-multiple/Capture6.PNG
   :alt: Data Validation Multiple
   :align: center
   :width: 60%   

   
Processor Output
^^^^^^

.. figure:: ../../_assets/tutorials/data-engineering/data-validation-multiple/Capture7.PNG
   :alt: Data Validation Multiple
   :align: center
   :width: 60%   

Prints the Valid Records
------------------

Processor Output
^^^^^^

.. figure:: ../../_assets/tutorials/data-engineering/data-validation-multiple/Capture8.PNG
   :alt: Data Validation Multiple
   :align: center
   :width: 60%   


Prints the Invalid Records
------------------

Processor Output
^^^^^^

.. figure:: ../../_assets/tutorials/data-engineering/data-validation-multiple/Capture9.PNG
   :alt: Data Validation Multiple
   :align: center
   :width: 60%   

