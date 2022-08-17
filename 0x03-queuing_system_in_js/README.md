Queuing System in JS
=

<h2>Redis CLI</h2>

The Redis command line interface (redis-cli) is a terminal program used to send commands to and read replies from the Redis server. It has two main modes: an interactive Read Eval Print Loop (REPL) mode where the user types Redis commands and receives replies, and a command mode where redis-cli is executed with additional arguments and the reply is printed to the standard output.

                $ redis-cli INCR mycounter
                (integer) 7

The reply of the command is "7". Since Redis replies are typed (strings, arrays, integers, nil, errors, etc.), you see the type of the reply between parentheses. This additional information may not be ideal when the output of redis-cli must be used as input of another command or redirected into a file.


Host, port, password, and database
=

By default, redis-cli connects to the server at the address 127.0.0.1 with port 6379. You can change the port using several command line options. To specify a different host name or an IP address, use the -h option. In order to set a different port, use -p.

                     $ redis-cli -h redis15.localnet.org -p 6390 PING
                      PONG

 it's possible to send a command that operates on a database number other than the default number zero by using the -n <dbnum> option:
 

              $ redis-cli FLUSHALL
              OK
              $ redis-cli -n 1 INCR a
              (integer) 1
              $ redis-cli -n 1 INCR a
              (integer) 2
              $ redis-cli -n 2 INCR a
              (integer) 1


