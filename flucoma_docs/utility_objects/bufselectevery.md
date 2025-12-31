# BufSelectEvery

Extract values by frame/channel hop

BufSelectEvery facilitates copying values from a source buffer to a destination buffer by specifiying a channel and index “hop”. This allows you to flexibly copy data that exists in a certain repetitive pattern, such as that produced by BufStats.

The widget below visually exposes how this copying procedure works. Try changing the Frame Hop and Channel Hop while observin which values from the source “buffer” are copied to the destination.
