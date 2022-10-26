:original_name: sdrs_05_0806.html

.. _sdrs_05_0806:

Querying Tags of All Protected Instances in a Specified Project
===============================================================

Function
--------

This API is used to query all resource tags of a protected instance in a specified project.

URI
---

-  URI format

   GET /v1/{project_id}/protected-instances/tags

-  Parameter description

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   ========== ========= ====== =========================

Request
-------

-  Request parameters

   None

-  Example request

   GET https://{Endpoint}/v1/{project_id}/protected-instances/tags

Response
--------

-  Parameter description

   +-----------------+-----------------+------------------+-------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                       |
   +=================+=================+==================+===================================================================+
   | tags            | Yes             | Array of objects | Specifies the tag list.                                           |
   |                 |                 |                  |                                                                   |
   |                 |                 |                  | For details, see :ref:`Table 1 <sdrs_05_0806__table09990210488>`. |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------+

   .. _sdrs_05_0806__table09990210488:

   .. table:: **Table 1** Data structure of the **tag** field

      +-----------+-----------+------------------+------------------------------------------------------------------+
      | Parameter | Mandatory | Type             | Description                                                      |
      +===========+===========+==================+==================================================================+
      | key       | Yes       | String           | Specifies the tag key. The tag key of a resource must be unique. |
      +-----------+-----------+------------------+------------------------------------------------------------------+
      | values    | Yes       | Array of strings | Lists the tag values.                                            |
      +-----------+-----------+------------------+------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
          "tags": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              },
              {
                  "key": "key2",
                  "values": [
                      "value1",
                      "value2"
                  ]
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
