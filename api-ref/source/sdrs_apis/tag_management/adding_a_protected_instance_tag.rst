:original_name: sdrs_05_0803.html

.. _sdrs_05_0803:

Adding a Protected Instance Tag
===============================

Function
--------

You can add a maximum of 20 tags to a protected instance.

This API is idempotent.

If a to-be-created tag has the same key as an existing tag, the tag will be created and overwrite the existing one.

URI
---

-  URI format

   POST /v1/{project_id}/protected-instances/{protected_instance_id}/tags

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

-  Parameter description

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                         |
   +=================+=================+=================+=====================================================================+
   | tag             | Yes             | Object          | Specifies the tag to be added.                                      |
   |                 |                 |                 |                                                                     |
   |                 |                 |                 | For details, see :ref:`Table 1 <sdrs_05_0803__table1569003154718>`. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------+

   .. _sdrs_05_0803__table1569003154718:

   .. table:: **Table 1** **tag** field description

      +-----------+-----------+--------+------------------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description                                                      |
      +===========+===========+========+==================================================================+
      | key       | Yes       | String | Specifies the tag key. The tag key of a resource must be unique. |
      +-----------+-----------+--------+------------------------------------------------------------------+
      | value     | Yes       | String | Specifies the tag value.                                         |
      +-----------+-----------+--------+------------------------------------------------------------------+

-  Example request

   POST https://{Endpoint}/v1/{project_id}/protected-instances/67a2cc7e-fb87-41a8-ba28-9c032abcaee1/tags

   .. code-block::

      {
          "tag": {
              "key": "DEV",
              "value": "DEV1"
          }
      }

Response
--------

-  Example response

   None

**Returned Value**
------------------

-  Normal

   ============== ===========
   Returned Value Description
   ============== ===========
   204            No Content
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
