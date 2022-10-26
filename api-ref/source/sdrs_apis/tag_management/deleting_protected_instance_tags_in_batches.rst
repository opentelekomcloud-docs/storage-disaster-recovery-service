:original_name: sdrs_05_0807.html

.. _sdrs_05_0807:

Deleting Protected Instance Tags in Batches
===========================================

Function
--------

This API is used to delete protected instance tags for a specified protected instance in batches.

You can add a maximum of 20 tags to a protected instance.

This API is idempotent.

-  During tag deletion, if some tags do not exist, the operation is considered to be successful by default. The character set of the tags will not be checked. When you delete tags, the tag structure cannot be missing, and the key cannot be left blank or be an empty string.

URI
---

-  URI format

   POST /v1/{project_id}/protected-instances/{protected_instance_id}/tags/action

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

   +-----------------+-----------------+------------------+----------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                          |
   +=================+=================+==================+======================================================================+
   | action          | Yes             | String           | Identifies the operation. The value can be **create** or **delete**. |
   |                 |                 |                  |                                                                      |
   |                 |                 |                  | -  **delete**: indicates to delete a tag.                            |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------+
   | tags            | Yes             | Array of objects | Specifies the tag list.                                              |
   |                 |                 |                  |                                                                      |
   |                 |                 |                  | For details, see :ref:`Table 1 <sdrs_05_0807__table6785202564616>`.  |
   +-----------------+-----------------+------------------+----------------------------------------------------------------------+

   .. _sdrs_05_0807__table6785202564616:

   .. table:: **Table 1** **resource_tag** field description

      +-----------+-----------+--------+------------------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description                                                      |
      +===========+===========+========+==================================================================+
      | key       | Yes       | String | Specifies the tag key. The tag key of a resource must be unique. |
      +-----------+-----------+--------+------------------------------------------------------------------+
      | value     | No        | String | Specifies the tag value.                                         |
      +-----------+-----------+--------+------------------------------------------------------------------+

-  Example request

   POST https://{Endpoint}/v1/{project_id}/protected-instances/67a2cc7e-fb87-41a8-ba28-9c032abcaee1/tags/action

   .. code-block::

      {
          "action": "delete",
          "tags": [
              {
                  "key": "key1"
              },
              {
                  "key": "key2",
                  "value": "value3"
              }
          ]
      }

Response
--------

-  Parameter description

   None

Returned Values
---------------

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
