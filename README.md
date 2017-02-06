mandrill_webhook
=========

This role helps you create or remove a mandrill webhook from your account.
https://mandrillapp.com/api/docs/webhooks.curl.html

Requirements
------------

None

Role Variables
--------------

The variables that can be passed to this role and a brief description about them are as follows:
````
Variables with defaults :
mandrill_api_version: 1.0
mandrill_api_webhook_url: https://mandrillapp.com/api/{{mandrill_api_version}}/webhooks
mandrill_api_output_format: .json
mandrill_webhook_operation: present # Present to create a webhook, absent to remove it
mandrill_operation: add # Internally used
mandrill_request_url: "{{mandrill_api_webhook_url}}/{{mandrill_operation}}{{mandrill_api_output_format}}"
mandrill_webhook_description: Generated via ansible


Other variables :


mandrill_webhook_id: 51 # Required for deletion
mandrill_api_key: myApiKey # Required
mandrill_webhook_url: http://example.com/mandrill_webhook

# Array of operations to configure mandrill webhook
mandrill_webhook_events:
  - click
  - open
````

Dependencies
------------

None

Example Playbook
----------------

    ---
    - hosts: local
      roles:
        - role: mandrill_webhook
          vars:
            mandrill_webhook_id: 51
            mandrill_api_key: myApiKey
            mandrill_webhook_operation: absent

    ---
    - hosts: local
      roles:
        - role: mandrill_webhook
          vars:
            mandrill_webhook_url: http://example.com/mandrill_webhook
            mandrill_webhook_description: Awesome webhook
            mandrill_api_key: myApiKey

License
-------

BSD

Author Information
------------------

https://github.com/Uelb
