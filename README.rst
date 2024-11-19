======
Pyping
======

A pure python ping implementation using raw sockets.

Note that ICMP messages can only be sent from processes running as root
(in Windows, you must run this script as 'Administrator').

Original Version from Matthew Dixon Cowles.
  
* Copyleft 1989-2011 by the python-ping team, see `AUTHORS <https://raw.github.com/toxinu/pyping/master/AUTHORS>`_ for more details.
* License: GNU GPL v2, see `LICENCE <https://raw.github.com/toxinu/pyping/master/LICENSE>`_ for more details.

Usage
-----
Use as a cli tool::

    $ sudo pyping example.com

    PYTHON-PING example.com (92.243.5.143): 55 data bytes
    241 bytes from example.com (92.243.5.143): icmp_seq=0 ttl=55 time=64.5 ms
    241 bytes from example.com (92.243.5.143): icmp_seq=1 ttl=55 time=67.7 ms
    241 bytes from example.com (92.243.5.143): icmp_seq=2 ttl=55 time=66.6 ms

    ----example.com PYTHON PING Statistics----
    3 packets transmitted, 3 packets received, 0.0% packet loss
    round-trip (ms)  min/avg/max = 64.457/66.244/67.677

    $ pyping --help

Use as a Python lib::

    >>> import pyping
    >>> r = pyping.ping('example.com')                # Need to be root or
    >>> r = pyping.ping('example.com', udp = True)    # But it's udp, not real icmp
    >>> r.ret_code
    0
    >>> r.destination
    'example.com'
    >>> r.max_rtt
    '69.374'
    >>> r.avg_rtt
    '68.572'
    >>> r.min_rtt
    '67.681'
    >>> r.destination_ip
    '92.243.5.143'

Exeuctable
----------

Run pyinstaller against pyping/__main__.py to generate an executable program::

    % pyinstaller pyping/__main__.py --onefile --name pyping
    42 INFO: PyInstaller: 6.11.1, contrib hooks: 2024.10
    43 INFO: Python: 3.13.0
    44 INFO: Platform: Linux-6.11.7-300.fc41.x86_64-x86_64-with-glibc2.40
    44 INFO: Python environment: /home/peter/venv/pyping
    44 INFO: wrote /home/peter/repos/pyping/pyping.spec
    44 INFO: Module search paths (PYTHONPATH):
    ['/usr/lib64/python313.zip',
    '/usr/lib64/python3.13',
    '/usr/lib64/python3.13/lib-dynload',
    '/home/peter/venv/pyping/lib64/python3.13/site-packages',
    '/home/peter/venv/pyping/lib/python3.13/site-packages',
    '/home/peter/venv/pyping/lib64/python3.13/site-packages/setuptools/_vendor',
    '/home/peter/repos/pyping']
    139 INFO: checking Analysis
    139 INFO: Building Analysis because Analysis-00.toc is non existent
    139 INFO: Running Analysis Analysis-00.toc
    139 INFO: Target bytecode optimization level: 0
    139 INFO: Initializing module dependency graph...
    139 INFO: Initializing module graph hook caches...
    145 INFO: Analyzing base_library.zip ...
    619 INFO: Processing standard module hook 'hook-encodings.py' from '/home/peter/venv/pyping/lib64/python3.13/site-packages/PyInstaller/hooks'
    1703 INFO: Processing standard module hook 'hook-pickle.py' from '/home/peter/venv/pyping/lib64/python3.13/site-packages/PyInstaller/hooks'
    2478 INFO: Processing standard module hook 'hook-heapq.py' from '/home/peter/venv/pyping/lib64/python3.13/site-packages/PyInstaller/hooks'
    2705 INFO: Caching module dependency graph...
    2747 INFO: Looking for Python shared library...
    2752 INFO: Using Python shared library: /lib64/libpython3.13.so.1.0
    2752 INFO: Analyzing /home/peter/repos/pyping/pyping/__main__.py
    /home/peter/venv/pyping/lib64/python3.13/site-packages/clint/packages/colorama/ansitowin32.py:43: SyntaxWarning: invalid escape sequence '\['
    ANSI_RE = re.compile('\033\[((?:\d|;)*)([a-zA-Z])')
    /home/peter/venv/pyping/lib64/python3.13/site-packages/clint/textui/colored.py:118: SyntaxWarning: invalid escape sequence '\$'
    strip = re.compile("([^-_a-zA-Z0-9!@#%&=,/'\";:~`\$\^\*\(\)\+\[\]\.\{\}\|\?\<\>\\]+|[^\s]+)")
    /home/peter/venv/pyping/lib64/python3.13/site-packages/clint/textui/prompt.py:68: SyntaxWarning: "is not" with 'str' literal. Did you mean "!="?
    if prompt[-1] is not ' ':
    2852 INFO: Processing module hooks (post-graph stage)...
    2856 INFO: Performing binary vs. data reclassification (2 entries)
    2862 INFO: Looking for ctypes DLLs
    2866 INFO: Analyzing run-time hooks ...
    2867 INFO: Including run-time hook 'pyi_rth_inspect.py' from '/home/peter/venv/pyping/lib64/python3.13/site-packages/PyInstaller/hooks/rthooks'
    2870 INFO: Looking for dynamic libraries
    3099 INFO: Warnings written to /home/peter/repos/pyping/build/pyping/warn-pyping.txt
    3106 INFO: Graph cross-reference written to /home/peter/repos/pyping/build/pyping/xref-pyping.html
    3111 INFO: checking PYZ
    3111 INFO: Building PYZ because PYZ-00.toc is non existent
    3111 INFO: Building PYZ (ZlibArchive) /home/peter/repos/pyping/build/pyping/PYZ-00.pyz
    3193 INFO: Building PYZ (ZlibArchive) /home/peter/repos/pyping/build/pyping/PYZ-00.pyz completed successfully.
    3202 INFO: checking PKG
    3202 INFO: Building PKG because PKG-00.toc is non existent
    3202 INFO: Building PKG (CArchive) pyping.pkg
    3753 INFO: Building PKG (CArchive) pyping.pkg completed successfully.
    3754 INFO: Bootloader /home/peter/venv/pyping/lib64/python3.13/site-packages/PyInstaller/bootloader/Linux-64bit-intel/run
    3754 INFO: checking EXE
    3754 INFO: Building EXE because EXE-00.toc is non existent
    3754 INFO: Building EXE from EXE-00.toc
    3754 INFO: Copying bootloader EXE to /home/peter/repos/pyping/dist/pyping
    3754 INFO: Appending PKG archive to custom ELF section in EXE
    3773 INFO: Building EXE from EXE-00.toc completed successfully.
    % 

Todo
----

- Docs
- Refactor core.py
- Tests

Contribute
----------

`Fork <http://help.github.com/fork-a-repo/>`_ this repo on `GitHub <https://github.com/toxinu/pyping>`_ and `send <http://help.github.com/send-pull-requests>`_ pull requests. Thank you.

Links
-----

 - Sourcecode at GitHub: https://github.com/toxinu/pyping
 - Python Package Index: http://pypi.python.org/pypi/pyping/
