---
date: 2019-04-18T17:21:39Z
title: Customizing Documentation
linktitle: API Documentation
menu:
  main:
    parent: "Customise"
weight: 6
---

## Portal Documentation API
### Attach Documentation to Portal Catalogue

1. First Create Documentation

`POST http://www.tyk-test.com:3000/api/portal/documentation`

#### Request:
```
{
  "api_id":"",
  "doc_type":"swagger",
  "documentation":"eyJzd2FnZ2VyIj..."
}
```

The value of `documentation` is the Base64 encoded OpenAPI spec.  

#### Response:
```
{
  "Message": "5d55b277f56e1a0e09c9126d",
  "Meta": null,
  "Status": "OK"
}
```

The value of "Message" is the documentation ID which we will use to attach to an API catalogue

2. Attach documentation to an API catalogue

`PUT http://www.tyk-test.com:3000/api/portal/catalogue`

#### Request:
```
{
    "id": "5d39d4b7f56e1a815a3a27c0",
    "org_id": "5d39d4b6f56e1a815a3a27bf",
    "apis": [
        {
            "api_id": "",
            "config": {
                "signup_fields": [],
                "key_request_fields": [],
                "override": false,
                "disable_signup": false,
                "disable_auto_login": false,
                "redirect_on_key_request": false,
                "disable_login": false,
                "oauth_usage_limit": -1,
                "mail_options": {
                    "mail_from_name": "",
                    "mail_from_email": "",
                    "email_copy": {
                        "welcome_email": {
                            "enabled": false,
                            "subject": "",
                            "body": "",
                            "sign_off": "",
                            "hide_token_data": false
                        },
                        "key_email": {
                            "enabled": false,
                            "subject": "",
                            "body": "",
                            "sign_off": "",
                            "hide_token_data": false
                        },
                        "reset_password_email": {
                            "enabled": false,
                            "subject": "",
                            "body": "",
                            "sign_off": "",
                            "hide_token_data": false
                        }
                    }
                },
                "org_id": "",
                "catalogue_login_only": false,
                "id": "",
                "email": "",
                "require_key_approval": false,
                "redirect_to": ""
            },
            "is_keyless": false,
            "policy_id": "5d4c2cc3f56e1a062adac369",
            "name": "httpbin",
            "version": "v2",
            "short_description": "",
            "long_description": "",
            "fields": {},
            "documentation": "5d542181f56e1a0e09c9126b",
            "show": true
        }
    ],
    "email": ""
}
```

#### Response:
```
{
  "Message": "Data updated",
  "Meta": null,
  "Status": "OK"
}
```

### Delete Documentation
`DELETE http://www.tyk-test.com:3000/api/portal/documentation/5d55b277f56e1a0e09c9126d`

Request:

Response:
Message: "Data deleted"
Meta: null
Status: "OK"

## Swap out Swagger UI for ReDoc

This short guide will show you how easy it is to swap out out the default https://swagger.io/tools/swagger-ui/ library for Portal Catalogue API documentation for another tool like http://rebilly.github.io/ReDoc/

* Open up the default `/opt/tyk-dashboard/portal/templates/swagger.html`

```
  {{ define "swaggerPage" }}
  {{ template "header" .}}
  <link href='/portal-assets/css/swagger.min.css' media='screen' rel='stylesheet' type='text/css'/>
  <!-- <link href='/portal-assets/css/swagger-ui.css' media='screen' rel='stylesheet' type='text/css'/> -->
  <body>
    {{ template "navigation" . }}
    <div>
      <div class="container" style="margin-top: 80px;">
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" style="position:absolute;width:0;height:0">
...
        </svg>
        <div id="swagger-ui"></div>
      </div>
    </div>
    {{ template "footer" .}}
    {{ template "scripts" .}}
    <script src="/portal-assets/js/vendors.min.js"> </script>
    <script src="/portal-assets/js/swagger.min.js"> </script>
    <script type="text/javascript">
...
    </script>
  </body>
</html>
{{ end }}
```

* Replace the content of `swagger.html` with the following:

```
  {{ define "swaggerPage" }}
  {{ template "header" .}}
  <body>
    {{ template "navigation" . }}
    <div>
      <div class="container" style="margin-top: 80px;">
        <redoc spec-url="{{.SwaggerURL}}"></redoc>
      </div>
    </div>
    {{ template "footer" .}}
    <script src="https://cdn.jsdelivr.net/npm/redoc@next/bundles/redoc.standalone.js"></script>
  </body>
</html>
{{ end }}
```

* Restart your dashboard service

* Browse your portal documentation

![Tyk Portal Catalogue API Documentation with ReDoc][1]

[1]: /docs/img/dashboard/portal-management/redoc-petstore-tyk.png
