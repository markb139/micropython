.. currentmodule:: rp2
.. _rp2.DMA:

class DMA -- access to direct memory access functionality
===============================================

This class gives access to DMA - direct memory access.


Constructors
------------

.. class:: DMA()

    Gets the singleton object for accessing DMA.


Methods
-------

.. method:: DMA.claim()

    Used to claim an underlying DMA channel.

    Raises a `RuntimeError` if no DMA channels are available to claim.

.. method:: DMA.unclaim()

    Used to release an underlying DMA channel.

.. method:: DMA.isclaimed()

    Returns True if the underlying DMA channel is claimed.

    :rtype: bool
   
.. method:: DMA.copy(from_buffer, to_buffer, handler=None, irq=DMA_IRQ_0|DMA_IRQ_1)
    
    Copies data from one buffer to another using DMA.
    If `handler`` is provider, IRQ will be used to call back, otherwise no IRQ will be set.

.. method:: DMA.read_into(from_address, to_buffer, data_size=DMA_SIZE_8|DMA_SIZE16|DMA_SIZE_32, transfer_count=0, dreq=0, handler=None, irq=DMA_IRQ_0|DMA_IRQ_1)

    Reads data from an address into a buffer using DMA.
    If `handler`` is provider, IRQ will be used to call back, otherwise no IRQ will be set.

    from_address - address to send data
    to_buffer - bytearray
    data_size - 1,2,4 bytes (use constant)
    transfer_count -
    dreq - optional throttle transfer. Default is to go as fast as possible
    handler - optional IRQ handler
    irq - optional irq channel. Either DMA_IRQ_0 or DMA_IRQ_1

.. method:: DMA.write_from(from_buffer, to_address, data_size=DMA_SIZE_8|DMA_SIZE16|DMA_SIZE_32, transfer_count=0, dreq=0, handler=None, irq=DMA_IRQ_0|DMA_IRQ_1)

    Writes data from a buffer to an address using DMA.
    If `handler`` is provider, IRQ will be used to call back, otherwise no IRQ will be set.

    from_buffer - bytearray
    to_address - address to send data
    data_size - 1,2,4 bytes (use constant)
    transfer_count -
    dreq - optional throttle transfer. Default is to go as fast as possible
    handler - optional IRQ handler
    irq - optional irq channel. Either DMA_IRQ_0 or DMA_IRQ_1

.. method:: DMA.error_status():

    Returns the error status of the DMA channel.

    :rtype: int

.. method:: DMA.clear_error()

    Clears the error status of the DMA channel.

.. method:: DMA.isbusy()

    Returns True if the DMA channel is busy.

    :rtype: bool

.. method:: DMA.request_count()

    Returns the number of requests made by the DMA channel.

    :rtype: int



Constants
---------

.. data:: DMA.DMA_SIZE_16
          DMA.DMA_SIZE_32
          DMA.DMA_SIZE_8

    These constants are used for the **

.. data:: DMA.DMA_IRQ_0
          DMA.DMA_IRQ_1

    These constants are used for the *irq* argument to `DMA.copy`.
