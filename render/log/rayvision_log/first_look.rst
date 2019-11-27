.. warning::
   Make sure local Python environment and PIP are available before use.

Demo
-------------
`rayvision_log <https://pip.renderbus.com/simple/rayvision-log/>`_ An example is given as follows: **demo** ::

    import logging
    from rayvision_log import init_logger

    package_name = 'mylog'
    init_logger(package_name)
    logging.info('test')


Set the log path
-----------------
1. Default path

Mac OS X:

* ~/Library/Logs/<AppName>/Logs/<username>/<hostname>.log
Unix:

* ~/.cache/<AppName>/log/Logs/<username>/<hostname>.log
Window:

* C:\Users\<username>\AppData\Local\<AppAuthor>\<AppName>\Logs\<username>\<hostname>.log

2. Customized path

* Define parameter： ``RAYVISION_LOG_ROOT = "xxxx"``
* Set *RAYVISION_LOG_ROOT* as environment variable
* The log files will be saved in *RAYVISION_LOG_ROOT*
