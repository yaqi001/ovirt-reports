# vm_interface_samples_history

~~~ bash
ovirt_engine_history=# \d vm_interface_samples_history
                                           Table "public.vm_interface_samples_history"
               Column               |           Type           |                            Modifiers                            
------------------------------------+--------------------------+-----------------------------------------------------------------
 history_id                         | integer                  | not null default nextval('vm_interface_history_seq1'::regclass)
 history_datetime                   | timestamp with time zone | not null
 vm_interface_id                    | uuid                     | not null
 receive_rate_percent               | smallint                 | 
 transmit_rate_percent              | smallint                 | 
 vm_interface_configuration_version | integer                  | 
~~~

* receive_rate_percent
* transmit_rate_percent

~~~ bash
ovirt_engine_history=# select receive_rate_percent, transmit_rate_percent from vm_interface_samples_history where receive_rate_percent is not null order by receive_rate_percent desc
ovirt_engine_history-# ;
 receive_rate_percent | transmit_rate_percent 
----------------------+-----------------------
                    1 |                     0
                    1 |                     0
                    1 |                     0
                    1 |                     0
                    1 |                     0
                    1 |                     0
~~~

~~~ bash
 receive_rate_percent | transmit_rate_percent 
----------------------+-----------------------
                    0 |                     0
                    0 |                     0
                    0 |                     0
                    0 |                     0
                    0 |                     0
                    0 |                     0
                    0 |                     0
~~~

