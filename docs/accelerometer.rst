Accelerometer
*************

.. py:module:: microbit.accelerometer

This object gives you access to the on-board accelerometer. The accelerometer
also provides convenience functions for detecting gestures. The
recognised gestures are: ``up``, ``down``, ``left``, ``right``, ``face up``,
``face down``, ``freefall``, ``3g``, ``6g``, ``8g``, ``shake``.

By default MicroPython sets the accelerometer range to +/- 2g, changing the
accelerometer range is currently not possible in MicroPython.
The accelerometer returns a value in the range 0..1024 for each axis, which is
then scaled accordingly.

Functions
=========

.. py:function:: get_x()

    Get the acceleration measurement in the ``x`` axis, as a positive or
    negative integer, depending on the direction. The measurement is given in
    milli-g. By default the accelerometer is configured with a range of +/- 2g,
    and so this method will return within the range of +/- 2000mg.

.. py:function:: get_y()

    Get the acceleration measurement in the ``y`` axis, as a positive or
    negative integer, depending on the direction. The measurement is given in
    milli-g. By default the accelerometer is configured with a range of +/- 2g,
    and so this method will return within the range of +/- 2000mg.

.. py:function:: get_z()

    Get the acceleration measurement in the ``z`` axis, as a positive or
    negative integer, depending on the direction. The measurement is given in
    milli-g. By default the accelerometer is configured with a range of +/- 2g,
    and so this method will return within the range of +/- 2000mg.

.. py:function:: get_values()

    Get the acceleration measurements in all axes at once, as a three-element
    tuple of integers ordered as X, Y, Z.
    By default the accelerometer is configured with a range of +/- 2g, and so
    X, Y, and Z will be within the range of +/-2000mg.

.. py:function:: get_strength()

    Get the acceleration measurement of all axes combined, as a positive
    integer.  This is the Pythagorean sum of the X, Y and Z axes, with the
    measurement given in milli-g.

.. py:function:: current_gesture()

    Return the name of the current gesture.

.. note::

    MicroPython understands the following gesture names: ``"up"``, ``"down"``,
    ``"left"``, ``"right"``, ``"face up"``, ``"face down"``, ``"freefall"``,
    ``"3g"``, ``"6g"``, ``"8g"``, ``"shake"``. Gestures are always
    represented as strings.

.. py:function:: is_gesture(name)

    Return True or False to indicate if the named gesture is currently active.

.. py:function:: was_gesture(name)

    Return True or False to indicate if the named gesture was active since the
    last call.

.. py:function:: get_gestures()

    Return a tuple of the gesture history. The most recent is listed last.
    Also clears the gesture history before returning.
    
.. note::

    Gestures are not updated in the background so there needs to be constant 
    calls to some accelerometer method to do the gesture detection. Usually 
    gestures can be detected using a loop with a small :func:`microbit.sleep` delay.

Examples
--------

A fortune telling magic 8-ball. Ask a question then shake the device for an
answer.

.. include:: ../examples/magic8.py
    :code: python

Simple Slalom. Move the device to avoid the obstacles.

.. include:: ../examples/simple_slalom.py
    :code: python
