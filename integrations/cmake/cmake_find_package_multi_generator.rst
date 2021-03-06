
.. _cmake_find_package_multi_generator:


``cmake_find_package_multi``
============================


.. warning::

    This is an **experimental** feature subject to breaking changes in future releases.

This generator is similar to the :ref:`cmake_find_package<cmake_find_package_generator>` generator but it allows working with
multi-configuration projects like ``Visual Studio`` with both ``Debug`` and ``Release``. But there are some differences:

- Only works with CMake > 3.0
- It doesn't generate ``FindXXX.cmake`` modules but ``XXXConfig.cmake`` files.
- The "global" approach is not supported, only "modern" CMake by using targets.


Usage
-----

.. code-block:: bash

    $ conan install . -g cmake_find_package_multi -s build_type=Debug
    $ conan install . -g cmake_find_package_multi -s build_type=Release

These commands will generate several files for each dependency in your graph, including a ``XXXConfig.cmake`` that can be located
by the CMake `find_package(XXX) <https://cmake.org/cmake/help/v3.0/command/find_package.html>`_ command, with XXX as the package name.

The name of the files follows the pattern ``<package_name>Config.cmake``. So for the ``zlib/1.2.11@conan/stable`` package,
a ``zlibConfig.cmake`` file will be generated.


.. seealso::

    Check the section :ref:`cmake_find_package_multi_generator_reference` to read more about this generator and the adjusted CMake
    variables/targets.
