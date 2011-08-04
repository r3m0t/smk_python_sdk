# smk

Python API client for Smarkets.

## Installation

    $ sudo python setup.py install


## Getting Started

    >>> import logging
    >>> logging.basicConfig(level=logging.DEBUG)
    >>> import smk
    >>> from smk.seto_pb2 import buy,sell
    >>> session = smk.Session('hunter.morris@smarkets.com', 'abc,123', 'api-dev.corp.smarkets.com', 3701)
    >>> client = smk.Smarkets(session)
    >>> client.login()
    Session 37087943-b12f-4753-9af8-32814061097d
    >>> client.ping()
    >>> client.read()
    Pong
    >>> c.subscribe('000000000000000000000001dc91c024') # subscribe to a market
    >>> c.order(400000, '25', buy, '000000000000000000000001dc91c024', '000000000000000000000002ab9acccc')
    >>> client.read()

### Resuming a session

When resuming a session you need to know the incoming and outgoing sequence numbers you were using when the session was last used, from the example above they will now both be 3.

    session = smk.Session('you@domain.com', 'password', 'api-dev.corp.smarkets.com', 3701, '37087943-b12f-4753-9af8-32814061097d', 3, 3)
