# vm_daily_history

~~~ bash
ovirt_engine_history=# \d vm_daily_history
                                           Table "public.vm_daily_history"
               Column               |          Type          |                       Modifiers                       
------------------------------------+------------------------+-------------------------------------------------------
 history_id                         | bigint                 | not null default nextval('vm_history_seq3'::regclass)
 history_datetime                   | date                   | not null
 vm_id                              | uuid                   | not null
 vm_status                          | smallint               | not null
 minutes_in_status                  | numeric(7,2)           | not null default 1
 cpu_usage_percent                  | smallint               | default 0
 max_cpu_usage                      | smallint               | 
 memory_usage_percent               | smallint               | default 0
 max_memory_usage                   | smallint               | 
 vm_ip                              | text                   | 
 current_user_name                  | character varying(255) | 
 currently_running_on_host          | uuid                   | 
 vm_configuration_version           | integer                | 
 current_host_configuration_version | integer                | 
 user_cpu_usage_percent             | smallint               | 
 max_user_cpu_usage_percent         | smallint               | 
 system_cpu_usage_percent           | smallint               | 
 max_system_cpu_usage_percent       | smallint               | 
 current_user_id                    | uuid                   | 
~~~

记录了从 2015-05-12 至 2016-04-06 的信息，今天是 2016-04-08

* cpu_usage_percent
* max_cpu_usage
* user_cpu_usage_percent
* max_user_cpu_usage_percent
* system_cpu_usage_percent
* max_system_cpu_usage_percent

~~~ bash
# 片段
ovirt_engine_history=# select cpu_usage_percent, max_cpu_usage, user_cpu_usage_percent, max_user_cpu_usage_percent, system_cpu_usage_percent, max_system_cpu_usage_percent from vm_daily_history order by cpu_usage_percent desc;
 cpu_usage_percent | max_cpu_usage | user_cpu_usage_percent | max_user_cpu_usage_percent | system_cpu_usage_percent | max_system_cpu_usage_percent 
-------------------+---------------+------------------------+----------------------------+--------------------------+------------------------------
                70 |            71 |                     68 |                         70 |                        3 |                            6
                63 |            63 |                     63 |                         64 |                        0 |                            0
                62 |            63 |                     60 |                         61 |                        3 |                            6
                62 |            63 |                     59 |                         61 |                        3 |                            6
                62 |            63 |                     60 |                         61 |                        3 |                            3
                62 |            63 |                     60 |                         61 |                        3 |                            4
                62 |            63 |                     60 |                         61 |                        3 |                            4
                60 |            61 |                     59 |                         60 |                        2 |                            2
                60 |            61 |                     59 |                         60 |                        2 |                            2
                59 |            61 |                     58 |                         59 |                        2 |                            3
                59 |            61 |                     58 |                         60 |                        2 |                            3
                59 |            63 |                     58 |                         61 |                        2 |                            3
                59 |            63 |                     58 |                         61 |                        2 |                            4
                59 |            61 |                     58 |                         60 |                        2 |                            2
                59 |            63 |                     56 |                         61 |                        3 |                            7
~~~
