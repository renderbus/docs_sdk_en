FAQ
===========


.. _header-n3:

1. What versions of Python does the RenderBus SDK support?
-----------------------------------------------------------

RenderBus SDK currently supports Python 2.7 and Python 3.6

.. _header-n5:

2. How to download the SDK package with pycharm?
--------------------------------------------------

Please refer to `Installation Guide <installation_guide.html>`__

.. _header-n13:

3. To download only the first frame, how to set?
--------------------------------------------------

- Get a task instance

   ``task = RayvisionTask(cg_file=cg_file, **render_para)``

- Set to download only the first frame

   ``task.task_info['task_info']['pre_frames'] = "100"``

.. _header-n14:

4. After the priority frame rendered, how to set to automatically render at full speed?
-------------------------------------------------------------------------------------------

- Get a task instance

   ``task = RayvisionTask(cg_file=cg_file, **render_para)``

- Set automatic full speed rendering

   ``task.task_info['task_info']['stop_after_test'] = "2"``

For details, please refer to `Detailed Parameter Configuration <json_file>`__


.. _header-n34:

5. How to set to download the rendering result immediately after current rendered frame rendered?
----------------------------------------------------------------------------------------------------

We provide 2 downloading methods:

- Download after all frames finish rendering

- Download after current frame finishes rendering

For details, please refer to `SDK Usage <SDK_tutorial.html#header-n209>`__

.. _header-n9:

6. What is the easiest way to use?
------------------------------------

If you want to use it directly without customization, you can download the corresponding rendering package directly,
then select the corresponding [common full process sample] to experience the full process rendering. For details, please refer to the `SDK Getting Started Tutorial <SDK_tutorial.html>`__
