# vm_hourly_history

~~~ bash
ovirt_engine_history=# \d vm_hourly_history
                                           Table "public.vm_hourly_history"
               Column               |           Type           |                       Modifiers                       
------------------------------------+--------------------------+-------------------------------------------------------
 history_id                         | bigint                   | not null default nextval('vm_history_seq2'::regclass)
 history_datetime                   | timestamp with time zone | not null
 vm_id                              | uuid                     | not null
 vm_status                          | smallint                 | not null
 minutes_in_status                  | numeric(7,2)             | not null default 1
 cpu_usage_percent                  | smallint                 | default 0
 max_cpu_usage          user_cpu_usage_percentmax_system_cpu_usage_percent      | smallint                 | 
 memory_usage_percent               | smallint                 | default 0
 max_memory_usage                   | smallint                 | 
 vm_ip                              | text                     | 
 current_user_name                  | character varying(255)   | 
 currently_running_on_host          | uuid                     | 
 vm_configuration_version           | integer                  | 
 current_host_configuration_version | integer                  | 
 user_cpu_usage_percent             | smallint                 | 
 max_user_cpu_usage_percent         | smallint                 | 
 system_cpu_usage_percent           | smallint                 | 
 max_system_cpu_usage_percent       | smallint                 | 
 current_user_id                    | uuid                     | 
~~~

* cpu_usage_percent
* max_cpu_usage
* user_cpu_usage_percent
* max_user_cpu_usage_percent
* system_cpu_usage_percent
* max_system_cpu_usage_percent
* memory_usage_percent
* max_memory_usage

~~~ bash
# 片段
ovirt_engine_history=# select cpu_usage_percent, max_cpu_usage, user_cpu_usage_percent, max_user_cpu_usage_percent, system_cpu_usage_percent, max_system_cpu_usage_percent from vm_hourly_history where cpu_usage_percent is not null order by cpu_usage_percent desc;
 cpu_usage_percent | max_cpu_usage | user_cpu_usage_percent | max_user_cpu_usage_percent | system_cpu_usage_percent | max_system_cpu_usage_percent 
-------------------+---------------+------------------------+----------------------------+--------------------------+------------------------------
                50 |            53 |                     18 |                         21 |                       33 |                           34
                50 |            50 |                     18 |                         19 |                       33 |                           34
                50 |            51 |                     18 |                         18 |                       33 |                           34
                50 |            51 |                     18 |                         19 |                       33 |                           34
                47 |            57 |                     18 |                         52 |                       30 |                           34
                46 |            52 |                     17 |                         20 |                       30 |                           34
                43 |            51 |                     34 |                         46 |                        9 |                           29
                43 |            51 |                     34 |                         50 |                        9 |                           20
                42 |            50 |                     34 |                         44 |                        8 |                           24
                42 |            51 |                     35 |                         46 |                        8 |                           25
                42 |            52 |                     34 |                         45 |                        8 |                           16
~~~
