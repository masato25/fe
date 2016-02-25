# API URL doc

## API list
* `POST` /api/v1/auth/register
  * params:
    * `name` string [useraccount]
    * `password` string
    * `repeat_password` string
    * `email` string
  * response:
    * ok

      ```
      {
        "value": "v1",
        "method": "POST",
        "status": "success",
        "data": {
          "expired": 1458815516,
          "sig": "a9de7114da1811e5adb7001500c6ca5a"
        }
      }
      ```
      * sig: user session token
      * expired: token expired time
    * failed

      ```
      {
        "value": "v1",
        "method": "POST",
        "status": "failed",
        "error": {
          "message": "name is already existent"
        }
      }
      ```
* `POST` /api/v1/auth/login
  * params:
    * `name` string [useraccount]
    * `password` string
  * response:
    * ok

      ```
      {
        "value": "v1",
        "method": "POST",
        "status": "success",
        "data": {
          "expired": 1458875558,
          "sig": "75981f64daa411e59eaa001500c6ca5a"
        }
      }
      ```
      * sig: user session token
      * expired: token expired time
    * failed

      ```
      {
        "value": "v1",
        "method": "POST",
        "status": "failed",
        "error": {
          "message": "password error"
        }
      }
      ```
* `GET` `POST` /api/v1/auth/logout
  * params:
    * `name` string [useraccount] option
    * `sig` string option
  * if params are null, will check the same key on cookie set
  * response:
    * ok

      ```
      {
        "value": "v1",
        "method": "POST",
        "status": "success",
        "data": {
          "message": "session is removed"
        }
      }
      ```
    * failed

      ```
      {
        "value": "v1",
        "method": "POST",
        "status": "failed",
        "error": {
          "message": "name or sig is empty, please check again"
        }
      }
      ```
* `GET` `POST` /api/v1/auth/sessioncheck
  * params:
    * `name` string [useraccount] option
    * `sig` string option
  * if params are null, will check the same key on cookie set
  * response:
    * ok

      ```
      {
        "value": "v1",
        "method": "POST",
        "status": "success",
        "data": {
          "expired": 1458889692,
          "message": "session passed!",
          "sig": "5dda5bacdac511e5b83b001500c6ca5a"
        }
      }
      ```
      * sig: user session token
      * expired: token expired time
    * failed

      ```
      {
        "value": "v1",
        "method": "POST",
        "status": "failed",
        "error": {
          "message": "can not find this kind of session"
        }
      }
      ```