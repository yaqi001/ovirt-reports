# vm_interface_hourly_history

~~~ bash
ovirt_engine_history=# \d vm_interface_hourly_history
                                           Table "public.vm_interface_hourly_history"
               Column               |           Type           |                            Modifiers                            
------------------------------------+--------------------------+-----------------------------------------------------------------
 history_id                         | integer                  | not null default nextval('vm_interface_history_seq2'::regclass)
 history_datetime                   | timestamp with time zone | not null
 vm_interface_id                    | uuid                     | not null
 receive_rate_percent               | smallint                 | 
 max_receive_rate_percent           | smallint                 | 
 transmit_rate_percent              | smallint                 | 
 max_transmit_rate_percent          | smallint                 | 
 vm_interface_configuration_version | integer                  | 
~~~

* receive_rate_percent
* max_receive_rate_percent
* transmit_rate_percent
* max_transmit_rate_percent

~~~ bash
ovirt_engine_history=# select receive_rate_percent, max_receive_rate_percent, transmit_rate_percent, max_transmit_rate_percent from vm_interface_hourly_history where receive_rate_percent is not null order by receive_rate_percent desc;
 receive_rate_percent | max_receive_rate_percent | transmit_rate_percent | max_transmit_rate_percent 
----------------------+--------------------------+-----------------------+---------------------------
                    1 |                        1 |                     0 |                         0
                    1 |                        1 |                     0 |                         0
                    1 |                        1 |                     0 |                         0
                    1 |                        1 |                     0 |                         0
                    1 |                        1 |                     0 |                         0
                    1 |                        1 |                     0 |                         0
                    1 |                        1 |                     0 |                         0
~~~

~~~ bash
ovirt_engine_history=# select receive_rate_percent, max_receive_rate_percent, transmit_rate_percent, max_transmit_rate_percent from vm_interface_hourly_history where transmit_rate_percent is not null order by transmit_rate_percent desc;
 receive_rate_percent | max_receive_rate_percent | transmit_rate_percent | max_transmit_rate_percent 
----------------------+--------------------------+-----------------------+---------------------------
                    0 |                        0 |                     1 |                         1
                    0 |                        0 |                     1 |                         1
                    0 |                        0 |                     1 |                         1
                    0 |                        0 |                     1 |                         1
                    0 |                        0 |                     1 |                         1
                    0 |                        0 |                     1 |                         1
                    0 |                        0 |                     1 |                         1
                    0 |                        0 |                     1 |                         2
~~~
