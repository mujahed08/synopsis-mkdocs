# UNIQUE ID GENERATOR IN DISTRIBUTED SYSTEMS

The *`auto_increment`* does not work in a distributed environment because a
single database server is not large enough and generating unique IDs across 
multiple databases with minimal delay is challenging and if it do so, 
it can be a single point of failure.

