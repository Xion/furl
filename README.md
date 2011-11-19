# furl

### furl is a small Python library that makes manipulating URLs simple.

Python's standard __urllib__ and __urlparse__ modules provide a number of URL
manipulation functions, but using these functions to perform common URL
manipulations proves tedious. Furl makes manipulating URLs simple.

Query arguments are easy. Really easy.

    >>> furl('http://www.google.com/?one=1').add(args={'two':'2'}).url
    'http://www.google.com/?two=2&one=1'

    >>> furl('http://www.google.com/?one=1&two=2').set(args={'three':'3'}).url
    'http://www.google.com/?three=3'

    >>> furl('http://www.google.com/?one=1&two=2').remove(args=['one']).url
    'http://www.google.com/?two=2'

Encoding is handled for you.

    >>> f = furl('http://www.google.com/')
    >>> f.path = 'some encoding here'
    >>> f.args['and some encoding'] = 'here, too'
    >>> f.url
    'http://www.google.com/some%20encoding%20here?and+some+encoding=here%2C+too'

Fragments have a path and a query, too.

    >>> f = furl('http://www.google.com/')
    >>> f.fragment.path.segments = ['two', 'directories']
    >>> f.fragment.args = {'one':'argument'}
    >>> str(f)
    'http://www.google.com/#two/directories?one=argument'

Or in one line

    >>> furl('http://www.google.com/').set(fragment_path=['some', 'directories'],
                                           fragment_args={'some':'parameters'}).url
    'http://www.google.com/#some/directories?some=parameters'

### API

See more examples and details of furl's API in the API.md document.
