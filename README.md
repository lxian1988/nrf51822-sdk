# LXNrf51Kit
A event-driven framework for Nordic nrf51822 MCU.

This framework is mostly for Nordic Industry's MCU nrf51822, but it can be easily changed for other MCUs.

I wrote this because the official's SDK is really SUCK, especially those involved with "schedule" stuff. So ond day I decided to write a SDK which is clean, easy to use.

OK, let's talk about something important.

The LXNrf51Kit has these features.

1. The whole framework is based on a simple, tiny heap, with which you can use dynamic memory allocation instead of declare large C arrays for all the variables in you code, such as buffers for UART or RADIO, or even the temp values like structs.

2. There is queue and FIFO. The queue and FIFO are used by some modules in the framework, but they can also be used for general purpose. 

3. And there is even a notification center. The notification center is easy to use. Just pop a message once and handle it each time. You can see the event loop in app.c. 

4. All the drives, like GPIOTE, UART, RADIO, SPI or ADC has been re-written. And UART and RADIO were re-written based on FIFO, which is based on heap. All interrupt handers have been placed inside the drive C file, and calling back to application layer using function pointers.

5. There is a new app button module, which supports single click and double click. The click event is pushed into notification center when it has been detected.

6. There is also a new app timer module, and it's also working with notification center. When a timer is elapsed, it pushs the event into notification center.
The time module supports dynamic timer instance creation for both repeat and singleshot! And I assure you it's much better than the official one.

7. Finally, I add a debug module to the framework. It's support re-direction, you can decide to print log through UART or RADIO, or even write it to a FLASH chip, and you can do them at same time.
And of course it's support error level (log, warning and error).

