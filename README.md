# Atlassian JWT authentication
This package provides an implementation of the [Service to Service Authentication](https://extranet.atlassian.com/display/I/Service+to+Service+Authentication+-+Specification) specification.

----

## Using this library

### To create a JWT for authentication

```python
    from atlassian_jwt_auth.key import KeyIdentifier
    from atlassian_jwt_auth.signer import JWTAuthSigner


    signer = JWTAuthSigner('issuer', KeyIdentifier('issuer/key'), private_key_pem)
    a_jwt = signer.generate_jwt('audience')
```


### To verify a JWT
```python
    from atlassian_jwt_auth.key import HTTPSPublicKeyRetriever
    from atlassian_jwt_auth.verifier import JWTAuthVerifier


    public_key_retriever = HTTPSPublicKeyRetriever('https://example.com')
    verifier = JWTAuthVerifier(public_key_retriever)
    verified_claims = verifier.verify_jwt(a_jwt, 'audience')
```

## Installation
To install simply run
```
$ pip install git+ssh://git@bitbucket.org/db_atlass/jwt-authentication-python.git@master
```

### CI builds
CI builds are found at [https://identity-bamboo.internal.atlassian.com/browse/SEC-SECENG](https://identity-bamboo.internal.atlassian.com/browse/SEC-SECENG) .
