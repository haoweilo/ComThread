# ComThread
ComThread is a class used for UART port control programming.

@ Support valid port search
@ Support data receiving and keyword search in thread.
@ Support Ymodem data xmit (windows only)
@ Support data xmit (one time sending or keep sending)

# How to use it?

from ComThread import *;
rt = ComThread();

# List all valid ports
ports = serial_ports();

# assign port to rt
rt.port = ports[0];

# assign a Queue to get the received data.
# all the received data would be push in rt.dq

rt.dq = Queue();

esc_chars="1B"
hex_esc = esc_chars.decode("hex");

## Keep sending ESC until ">>" is received ###
if rt.start(">>", hex_esc): 
	rt.waiting();
	rt.stop();

### Send "hello" then stop receiving
if rt.start("NONE", "NONE"):
	rt.Write_once("hello");
	rt.stop();

