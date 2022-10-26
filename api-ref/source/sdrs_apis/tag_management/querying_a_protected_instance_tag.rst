:original_name: sdrs_05_0805.html

.. _sdrs_05_0805:

Querying a Protected Instance Tag
=================================

Function
--------

This API is used to query tags of a specified protected instance.

URI
---

-  URI format

   GET /v1/{project_id}/protected-instances/{protected_instance_id}/tags

-  Parameter description

   +-----------------------+-----------------+-----------------+----------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type            | Description                                                          |
   +=======================+=================+=================+======================================================================+
   | project_id            | Yes             | String          | Specifies the project ID.                                            |
   +-----------------------+-----------------+-----------------+----------------------------------------------------------------------+
   | protected_instance_id | Yes             | String          | Specifies the ID of a protected instance.                            |
   |                       |                 |                 |                                                                      |
   |                       |                 |                 | For details, see :ref:`Querying Protected Instances <sdrs_05_0503>`. |
   +-----------------------+-----------------+-----------------+----------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example request

   GET https://{Endpoint}/v1/{project_id}/protected-instances/50f5091e-9e9e-473c-a932-2a2cbcbeb1ff/tags

Response
--------

-  Parameter description

   +-----------------+-----------------+------------------+--------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                        |
   +=================+=================+==================+====================================================================+
   | tags            | Yes             | Array of objects | Specifies the tag list.                                            |
   |                 |                 |                  |                                                                    |
   |                 |                 |                  | For details, see :ref:`Table 1 <sdrs_05_0805__table684444618473>`. |
   +-----------------+-----------------+------------------+--------------------------------------------------------------------+

   .. _sdrs_05_0805__table684444618473:

   .. table:: **Table 1** **resource_tag** field description

      +-----------+-----------+--------+------------------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description                                                      |
      +===========+===========+========+==================================================================+
      | key       | Yes       | String | Specifies the tag key. The tag key of a resource must be unique. |
      +-----------+-----------+--------+------------------------------------------------------------------+
      | value     | Yes       | String | Specifies the tag value.                                         |
      +-----------+-----------+--------+------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key2",
                  "value": "value3"
              }
          ]
      }

**Returned Value**
------------------

-  Normal

   ============== ===========
   Returned Value Description
   ============== ===========
   200            OK
   ============== ===========

-  Abnormal

   ============== =====================================
   Returned Value Description
   ============== =====================================
   400            Invalid parameters.
   401            Authentication failed.
   403            Insufficient permission.
   404            The requested resource was not found.
   500            Internal service error.
   ============== =====================================
