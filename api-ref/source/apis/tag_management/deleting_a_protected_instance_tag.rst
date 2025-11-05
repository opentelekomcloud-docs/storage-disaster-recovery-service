:original_name: sdrs_05_0804.html

.. _sdrs_05_0804:

Deleting a Protected Instance Tag
=================================

Function
--------

This API is idempotent.

-  During deletion, the tag character set is not verified. The URI must be encoded before the API is invoked. Other services need to decode the URI.

   .. note::

      Select a desired tool for URI encoding.

-  The tag key cannot be left blank or be an empty string. If the key of the tag to be deleted does not exist, 404 will be returned.

URI
---

-  URI format

   DELETE /v1/{project_id}/protected-instances/{protected_instance_id}/tags/{key}

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
   | key                   | Yes             | String          | Specifies the tag key.                                               |
   +-----------------------+-----------------+-----------------+----------------------------------------------------------------------+

Request
-------

-  Request parameters

   None

-  Example request

   DELETE https://{Endpoint}/v1/{project_id}/protected-instances/67a2cc7e-fb87-41a8-ba28-9c032abcaee1/tags/DEV

Response
--------

-  Response parameter

   None

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
