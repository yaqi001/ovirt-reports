# vm_samples_history

~~~ bash
ovirt_engine_history=# \d vm_samples_history
                                           Table "public.vm_samples_history"
               Column               |           Type           |                       Modifiers                       
------------------------------------+--------------------------+-------------------------------------------------------
 history_id                         | bigint                   | not null default nextval('vm_history_seq1'::regclass)
 history_datetime                   | timestamp with time zone | not null
 vm_id                              | uuid                     | not null
 vm_status                          | smallint                 | not null
 minutes_in_status                  | numeric(7,2)             | not null default 1
 cpu_usage_percent                  | smallint                 | default 0
 memory_usage_percent               | smallint                 | default 0
 vm_ip                              | text                     | 
 current_user_name                  | character varying(255)   | 
 currently_running_on_host          | uuid                     | 
 vm_configuration_version           | integer                  | 
 current_host_configuration_version | integer                  | 
 vm_client_ip                       | character varying(255)   | 
 user_logged_in_to_guest            | boolean                  | 
 user_cpu_usage_percent             | smallint                 | 
 system_cpu_usage_percent           | smallint                 | 
 current_user_id                    | uuid                     | 
~~~

里面存放了不到两天的 vm 数据（包括 cpu，memory 的 使用率）

* cpu_usage_percent
* user_cpu_usage_percent
* system_cpu_usage_percent

~~~ bash
# 片段
ovirt_engine_history=# select cpu_usage_percent, user_cpu_usage_percent, system_cpu_usage_percent from vm_samples_history where user_cpu_usage_percent is not null order by user_cpu_usage_percent desc;
 cpu_usage_percent | user_cpu_usage_percent | system_cpu_usage_percent 
-------------------+------------------------+--------------------------
                96 |                     96 |                        1
                95 |                     96 |                        0
                89 |                     90 |                        0
                85 |                     85 |                        0
                70 |                     70 |                        1
                70 |                     70 |                        0
                67 |                     67 |                        0
                62 |                     62 |                        1
                64 |                     61 |                        4
                61 |                     58 |                        5
~~~
