:original_name: sdrs_faq_win_login_restrictions.html

.. _sdrs_faq_win_login_restrictions:

Why can I not get the password for a Windows DR server before the first failover?
=================================================================================

Symptom
-------

For the Windows server with Cloudbase-Init installed and the Key pair is used for server login, if you try to get password for the DR server before the first failover, the error message “Failed to query the password” is displayed.

.. figure:: /_static/images/sdrs_faq_win_login_restriction.png
   :alt: **Figure 1** Get password error for DR server before the first failover

   **Figure 1** Get password error for DR server before the first failover

Cause
-----

Because the Windows DR server was never started before, the Cloudbase-Init agent was never executed on the DR server and the server metadata were never obtained. Hence the login password cannot be obtained  before the first failover.

Solution
--------

Perform a first planned failover after the SDRS configuration. During the planned failover the DR server is powered on and Cloudbase-Init agent obtain the server metadata and execute configurations when the ECS starts. After failover back to production site, you are be able to Get Password for DR server even it is in stopped state. Passwords are autogenerated for every server hence the production server and DR server have different login password.
