# Hyper: HTTP/2.0 in Pure Python

The HTTP specification will be changing soon. Our old friend HTTP/1.1 will 
soon be replaced by HTTP/2.0. The new specification includes a lot of cool new 
mechanisms and goodies but all previous implementations for HTTP/1.1 will be 
incapable of handling them. [Hyper][] is a pure Python implemenation of the 
current draft (9) of HTTP/2.0's specification (and draft 5 of the HPACK 
specification).

As it is now, Hyper can be used as an almost drop-in replacement for Python's 
standard library `http.client`.

Here's a sample of Hyper's excellent API:

    from hyper import HTTP20Connection

    conn = HTTP20Connection('twitter.com:443')
    conn.request('GET', '/')
    response = conn.getresponse()

    print(response.read())

Cory Benfield, Hyper's author, intends to only support Python 3.3 and beyond.  
There is a distinctly strong possibility that `asyncio` will be leveraged when 
it is released as part of Python 3.4. There is also already an 
[adapter](https://github.com/Lukasa/hyper/blob/master/hyper/contrib.py#L20) 
written for [requests](https://github.com/kennethreitz/requests).

[Hyper]: https://github.com/Lukasa/hyper

---

Link: [https://github.com/Lukasa/hyper][Hyper]

Tags: Python, HTTP
