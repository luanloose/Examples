# Cookies workthough

## Delete cookies

### You can delete cookies in 2 ways

* By name

```PHP
$this->driver->manage()->deleteCookieNamed('Cookie-Name');
```

* Or all of them

```PHP
$this->driver->manage()->deleteAllCookies();
```
