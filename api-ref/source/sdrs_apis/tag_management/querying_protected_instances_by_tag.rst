:original_name: sdrs_05_0801.html

.. _sdrs_05_0801:

Querying Protected Instances by Tag
===================================

Function
--------

This API is used to query protected instances by tag.

URI
---

-  URI format

   POST /v1/{project_id}/protected-instances/resource_instances/action

-  Parameter description

   ========== ========= ====== =========================
   Parameter  Mandatory Type   Description
   ========== ========= ====== =========================
   project_id Yes       String Specifies the project ID.
   ========== ========= ====== =========================

Request
-------

-  Parameter description

   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   +=================+=================+==================+====================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | offset          | No              | String           | Specifies the index position. This parameter is unavailable when **action** is set to **count**. If **offset** is set to *N*, the resource query starts from the N+1 piece of data. If **action** is set to **filter**, the value of **offset** is **0** by default, indicating that the query starts from the first piece of data. The **offset** value must be a number and cannot be a negative number.                                                                                                                                                                                                                         |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | limit           | No              | String           | Specifies the number of limited queries. This parameter is unavailable when **action** is set to **count**. The default value is **1000** when **action** is set to **filter**. The maximum value is **1000**, and the minimum value is **1**. The value cannot be a negative number.                                                                                                                                                                                                                                                                                                                                              |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | action          | Yes             | String           | Specifies the operation to be performed. The value can be **filter** (filtering) or **count** (querying the total number).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                  | If **action** is set to **filter**, the query is performed based on the filter conditions. If **action** is set to **count**, only the total number of records is returned.                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | matches         | No              | Array of objects | Specifies the search field. The tag key is the field to be matched, for example, **resource_name**. The tag value indicates the value to be matched. The key is a fixed dictionary value and cannot contain duplicate keys or unsupported keys.                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                  | Determine whether fuzzy match is required based on the keys. For example, if **key** is **resource_name**, fuzzy search (case insensitive) is used by default. If **value** is an empty string, exact match is used. Currently, only **resource_name** for **key** is supported. Other **key** values will be available later.                                                                                                                                                                                                                                                                                                     |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                  | For details, see :ref:`Table 2 <sdrs_05_0801__table16621174514217>`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags        | No              | Array of objects | The resources to be queried do not contain tags listed in **not_tags**. Each resource to be queried contains a maximum of 20 keys. Each tag key can have a maximum of 20 tag values. The tag value corresponding to each tag key can be an empty array but the structure cannot be missing. Each tag key must be unique, and each tag value in a tag must be unique. The response returns resources containing no tags in this list. Keys in this list are in an AND relationship while values in each key-value structure are in an OR relationship. If no tag filtering condition is specified, full data is returned.           |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                  | For details, see :ref:`Table 1 <sdrs_05_0801__table9607445020>`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags            | No              | Array of objects | The resources to be queried contain tags listed in **tags**. Each resource to be queried contains a maximum of 20 keys. Each tag key can have a maximum of 20 tag values. The tag value corresponding to each tag key can be an empty array but the structure cannot be missing. Each tag key must be unique, and each tag value in a tag must be unique. The response returns resources containing all tags in this list. Keys in this list are in an AND relationship while values in each key-value structure are in an OR relationship. If no tag filtering condition is specified, full data is returned.                     |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                  | For details, see :ref:`Table 1 <sdrs_05_0801__table9607445020>`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tags_any        | No              | Array of objects | The resources to be queried contain any tags listed in **tags_any**. Each resource to be queried contains a maximum of 20 keys. Each tag key can have a maximum of 20 tag values. The tag value corresponding to each tag key can be an empty array but the structure cannot be missing. Each tag key must be unique, and each tag value in a tag must be unique. The response returns resources containing the tags in this list. Keys in this list are in an OR relationship and values in each key-value structure are also in an OR relationship. If no tag filtering condition is specified, full data is returned.           |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                  | For details, see :ref:`Table 1 <sdrs_05_0801__table9607445020>`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | not_tags_any    | No              | Array of objects | The resources to be queried do not contain any tags listed in **not_tags_any**. Each resource to be queried contains a maximum of 20 keys. Each tag key can have a maximum of 20 tag values. The tag value corresponding to each tag key can be an empty array but the structure cannot be missing. Each tag key must be unique, and each tag value in a tag must be unique. The response returns resources containing no tags in this list. Keys in this list are in an OR relationship and values in each key-value structure are also in an OR relationship. If no tag filtering condition is specified, full data is returned. |
   |                 |                 |                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
   |                 |                 |                  | For details, see :ref:`Table 1 <sdrs_05_0801__table9607445020>`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _sdrs_05_0801__table9607445020:

   .. table:: **Table 1** **tag** field description

      +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type             | Description                                                                                                                                                                                                                                          |
      +=================+=================+==================+======================================================================================================================================================================================================================================================+
      | key             | Yes             | String           | Specifies the tag key. It contains a maximum of 127 Unicode characters. It cannot be left blank. **key** cannot be empty, an empty string, or spaces. Before using **key**, delete spaces of single-byte character (SBC) before and after the value. |
      +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | values          | Yes             | Array of strings | Lists the tag values. Each value contains a maximum of 255 Unicode characters. Before using **values**, delete SBC spaces before and after the value.                                                                                                |
      |                 |                 |                  |                                                                                                                                                                                                                                                      |
      |                 |                 |                  | The asterisk (``*``) is reserved for the system. If the value starts with \*, it indicates that fuzzy match is performed based on the value following \*. The value cannot contain only asterisks (*).                                               |
      |                 |                 |                  |                                                                                                                                                                                                                                                      |
      |                 |                 |                  | If the values are null, it indicates **any_value** (querying any value). The resources containing one or more values listed in **values** will be found and displayed.                                                                               |
      +-----------------+-----------------+------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. _sdrs_05_0801__table16621174514217:

   .. table:: **Table 2** Description of the **match** field

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                               |
      +=================+=================+=================+===========================================================================================================+
      | key             | Yes             | String          | Specifies the tag key.                                                                                    |
      |                 |                 |                 |                                                                                                           |
      |                 |                 |                 | Currently, only **resource_name** for **key** is supported. Other **key** values will be available later. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+
      | value           | Yes             | String          | Specifies the tag value.                                                                                  |
      |                 |                 |                 |                                                                                                           |
      |                 |                 |                 | Each value can contain a maximum of 255 Unicode characters.                                               |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------+

-  Sample request when **action** is set to **filter**

   POST https://{Endpoint}/v1/{project_id}/protected-instances/resource_instances/action

   .. code-block::

      {
          "offset": "100",
          "limit": "100",
          "action": "filter",
          "matches": [
              {
                  "key": "resource_name",
                  "value": "resource1"
              }
          ],
          "not_tags": [
              {
                  "key": "key1",
                  "values": [
                      "*value1",
                      "value2"
                  ]
              }
          ],
          "tags": [
              {
                  "key": "key1",
                  "values": [
                      "*value1",
                      "value2"
                  ]
              }
          ],
          "tags_any": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "not_tags_any": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ]
      }

-  Sample request when **action** is set to **count**

   POST https://{Endpoint}/v1/{project_id}/protected-instances/resource_instances/action

   .. code-block::

      {
          "action": "count",
          "not_tags": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "*value2"
                  ]
              }
          ],
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
          ],
          "tags_any": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "not_tags_any": [
              {
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "matches": [
              {
                  "key": "resource_name",
                  "value": "resource1"
              }
          ]
      }

Response
--------

-  Parameter description

   +-----------------+-----------------+------------------+-------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                       |
   +=================+=================+==================+===================================================================+
   | resources       | Yes             | Array of objects | Specifies the returned protected instances.                       |
   |                 |                 |                  |                                                                   |
   |                 |                 |                  | For details, see :ref:`Table 3 <sdrs_05_0801__table16443451223>`. |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------+
   | total_count     | Yes             | Integer          | Specifies the total number of resources.                          |
   |                 |                 |                  |                                                                   |
   |                 |                 |                  | The value is not affected by the filtering criteria.              |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------+

   .. _sdrs_05_0801__table16443451223:

   .. table:: **Table 3** Description of field **resource**

      +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type             | Description                                                                                         |
      +=================+=================+==================+=====================================================================================================+
      | resource_id     | Yes             | String           | Specifies the ID of a protected instance.                                                           |
      +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------+
      | resource_name   | Yes             | String           | Specifies the protected instance name. This parameter is left blank by default if there is no name. |
      +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------+
      | resource_detail | Yes             | Object           | Specifies the details of a protected instance.                                                      |
      |                 |                 |                  |                                                                                                     |
      |                 |                 |                  | For details, see :ref:`Table 4 <sdrs_05_0801__table503353570>`.                                     |
      +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------+
      | tags            | Yes             | Array of objects | Specifies the tag list. If there is no tag in the list, **tags** is taken as an empty array.        |
      |                 |                 |                  |                                                                                                     |
      |                 |                 |                  | For details, see :ref:`Table 8 <sdrs_05_0801__table7656144514216>`.                                 |
      +-----------------+-----------------+------------------+-----------------------------------------------------------------------------------------------------+

   .. _sdrs_05_0801__table503353570:

   .. table:: **Table 4** **protected_instances** field description

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                             |
      +=======================+=======================+=========================================================================================================+
      | id                    | String                | Specifies the ID of a protected instance.                                                               |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | name                  | String                | Specifies the name of a protected instance.                                                             |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | description           | String                | Specifies the description of a protected instance.                                                      |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | server_group_id       | String                | Specifies the ID of a protection group.                                                                 |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | status                | String                | Specifies the status of a protected instance.                                                           |
      |                       |                       |                                                                                                         |
      |                       |                       | For details, see :ref:`Protected Instance Status <en-us_topic_0126152931>`.                             |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | progress              | Integer               | Specifies the synchronization progress of a protected instance.                                         |
      |                       |                       |                                                                                                         |
      |                       |                       | Unit: %                                                                                                 |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | source_server         | String                | Specifies the production site server ID.                                                                |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | target_server         | String                | Specifies the DR site server ID.                                                                        |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | created_at            | String                | Specifies the time when a protected instance was created.                                               |
      |                       |                       |                                                                                                         |
      |                       |                       | The default format is as follows: "yyyy-MM-dd HH:mm:ss.SSS", for example, **2019-04-01 12:00:00.000**.  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | updated_at            | String                | Specifies the time when a protected instance was updated.                                               |
      |                       |                       |                                                                                                         |
      |                       |                       | The default format is as follows: "yyyy-MM-dd HH:mm:ss.SSS", for example, **2019-04-01 12:00:00.000**.  |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | priority_station      | String                | Specifies the current production site AZ of the protection group containing the protected instance.     |
      |                       |                       |                                                                                                         |
      |                       |                       | -  **source**: indicates that the current production site AZ is the **source_availability_zone** value. |
      |                       |                       | -  **target**: indicates that the current production site AZ is the **target_availability_zone** value. |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | attachment            | Array of objects      | Specifies the attached replication pairs.                                                               |
      |                       |                       |                                                                                                         |
      |                       |                       | For details, see :ref:`Table 2 <sdrs_05_0503__table1575342962014>`.                                     |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | tags                  | Array of objects      | Specifies the tag list.                                                                                 |
      |                       |                       |                                                                                                         |
      |                       |                       | For details, see :ref:`Table 3 <sdrs_05_0503__table12339146338>`.                                       |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+
      | metadata              | Object                | Specifies the metadata of a protected instance.                                                         |
      |                       |                       |                                                                                                         |
      |                       |                       | For details, see :ref:`Table 4 <sdrs_05_0503__table8582730112710>`.                                     |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------+

   .. table:: **Table 5** **attachment** field description

      =========== ====== =======================================
      Parameter   Type   Description
      =========== ====== =======================================
      replication String Specifies the ID of a replication pair.
      device      String Specifies the device name.
      =========== ====== =======================================

   .. table:: **Table 6** **tags** field description

      ========= ====== ========================
      Parameter Type   Description
      ========= ====== ========================
      key       String Specifies the tag key.
      value     String Specifies the tag value.
      ========= ====== ========================

   .. table:: **Table 7** Field **metadata** description

      +-----------------------+-----------------------+------------------------------------------------------+
      | Parameter             | Type                  | Description                                          |
      +=======================+=======================+======================================================+
      | \__system__frozen     | String                | Specifies whether the resource is frozen.            |
      |                       |                       |                                                      |
      |                       |                       | -  **true**: indicates that the resource is frozen.  |
      |                       |                       | -  Empty: indicates that the resource is not frozen. |
      +-----------------------+-----------------------+------------------------------------------------------+

   .. _sdrs_05_0801__table7656144514216:

   .. table:: **Table 8** **resource_tag** field description

      +-----------+-----------+--------+------------------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description                                                      |
      +===========+===========+========+==================================================================+
      | key       | Yes       | String | Specifies the tag key. The tag key of a resource must be unique. |
      +-----------+-----------+--------+------------------------------------------------------------------+
      | value     | Yes       | String | Specifies the value.                                             |
      +-----------+-----------+--------+------------------------------------------------------------------+

-  Example response

   Example response when **action** is set to **filter**

   .. code-block::

      {
          "resources": [
              {
                  "resource_id": "d5a00c87-6b82-414a-a09e-59c37fff44d0",
                  "resource_name": "Protected-Instance-c801",
                  "resource_detail": {
                      "id": "d5a00c87-6b82-414a-a09e-59c37fff44d0",
                      "name": "Protected-Instance-c801",
                      "description": null,
                      "server_group_id": "525fbd01-d4d1-44fc-b341-6d734bcce245",
                      "status": "protected",
                      "progress": 100,
                      "source_server": "73aff1d7-48d2-494e-a9f1-a7d3ffad31ff",
                      "target_server": "0f6bc56b-a3bb-4707-a4fb-ccd4db5fac59",
                      "created_at": "2019-05-28 08:17:50.066",
                      "updated_at": "2019-05-30 01:40:00.74",
                      "priority_station": "source",
                      "attachment": [
                          {
                              "replication": "42e2016e-b96e-4f75-aa57-1377a9cb45e4",
                              "device": "/dev/vda"
                          }
                      ],
                      "tags": [
                          {
                              "key": "GH1111113fffffKdddddd",
                              "value": "aaappppppppddddddd"
                          }
                      ],
                      "metadata": {}
                  },
                  "tags": [
                      {
                          "key": "GH1111113fffffKdddddd",
                          "value": "aaappppppppddddddd"
                      }
                  ]
              }
          ],
          "total_count": 1
      }

-  Example response when **action** is set to **count**

   .. code-block::

      {
          "total_count": 1000
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
