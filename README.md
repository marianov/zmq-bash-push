zmq-bash-push
=============

Very simple script to send ZeroMQ messages on the Linux command line

Based on the example by Daniel Lundin http://zeromq.org/bindings:bash, just rearranged to read stdin.

Usage
========

    echo hello world! |./zmq-push.sh localhost 8080


    cat README.md |./zmq-push.sh localhost 8080

It sends each line read from stdin to a PULL socket listening on port 8080

Example of such a  listening socket (in Python):

    import sys
    import zmq
    import time


    context = zmq.Context()
    sock = context.socket(zmq.PULL)
    sock.bind("tcp://*8080")

    while True:
        message= sock.recv()
        print message
