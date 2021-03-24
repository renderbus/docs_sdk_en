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


Default path
-------------

Centos:

  ~/.cache/<AppName>/log/Logs/<hostname>.log

Window:

  C:\\Users\\<username>\\AppData\\Local\\<AppAuthor>\\<AppName>\\Logs\\<hostname>.log


The custom path is divided into 2 setting methods
----------------------------------------------------

   - Set the environment variable to change the log path: `RAYVISION_LOG_ROOT`

    *RAYVISION_LOG_ROOT* set as system environment variable,
    The log path will be saved in the *RAYVISION_LOG_ROOT* folder。

   - Set the log path by parameter: `log_folder`, take Maya as an example:

    `analyze_obj = AnalyzeMaya(**analyze_info, log_folder=r"D:\test\vs")`


Custom log file name
----------------------

   - Set the log file name (including file suffix) by parameter: `log_name`, take Maya as an example:

    `analyze_obj = AnalyzeMaya(**analyze_info, log_name=r"api.log")`


Custom log level
------------------

   - Set the log level by parameter: `log_level`, take maya as an example:

   `analyze_obj = AnalyzeMaya(**analyze_info, log_level=r"api.log")`
