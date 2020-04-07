# Ansible 关键字

> ansible 2.9

这些是常见剧本对象上可用的关键字。

## Play

> 在 play 下可用的关键字

| key                 | desc                                                         |
| ------------------- | ------------------------------------------------------------ |
| any_errors_fatal    | 有任务错误时，立即停止                                       |
| become              | 是否提权                                                     |
| become_exe          |                                                              |
| become_flags        | 提权命令的参数                                               |
| become_method       | 提权得方式                                                   |
| become_user         | 提权的用户                                                   |
| check_mode          | 当为 True 时，只检查，不做修改                               |
| collections         |                                                              |
| connection          | 连接方式                                                     |
| debugger            | 开启 debugger 模式                                           |
| diff                | 对比更改的文件                                               |
| environment         | 定义远端系统的环境变量                                       |
| fact_path           | 指定存储 fact 的目录                                         |
| force_handlers      | 任务失败后，是否依然执行 handlers 中的任务                   |
| gather_facts        | 是否获取远端系统得 facts                                     |
| gather_subset       | 获取 facts 得哪些键值                                        |
| gather_timeout      | 获取 facts 的超时时间                                        |
| handlers            | 定义 task 执行完成以后需要调用的任务                         |
| hosts               | 指定运行得主机                                               |
| ignore_errors       | 布尔值，是否忽略错误                                         |
| ignore_unreachable  | 布尔值，可以忽略无法访问的主机并继续                         |
| max_fail_percentage | 单位百分比。最大的错误主机数，超过则立即停止 ansbile         |
| module_defaults     | 指定模块的默认参数值。                                       |
| name                | 定义名称                                                     |
| no_log              | 不记录日志                                                   |
| order               | 执行主机的顺序                                               |
| port                | 定义 ssh 的连接端口                                          |
| post_tasks          | 执行任务后要执行的任务                                       |
| pre_tasks           | 执行任务前要执行的任务                                       |
| remote_user         | 远程登陆的用户                                               |
| roles               | 定义角色                                                     |
| run_once            | 任务只运行一次                                               |
| serial              | 任务每次执行的主机数                                         |
| strategy            | play 运行策略                                                |
| tags                | 标记标签                                                     |
| tasks               | 定义任务                                                     |
| throttle            | 限制并发任务在 tasks，blocks 和 playbook 级别上运行的数量。不能高于 serial 和 forks 数 |
| vars                | 定义变量                                                     |
| vars_files          | 包含变量文件                                                 |
| vars_prompt         | 要求用户输入内容                                             |

## Role

> 在 role 下可用的关键字

| key                | desc                                                         |
| ------------------ | ------------------------------------------------------------ |
| any_errors_fatal   | 有任务错误时，立即停止                                       |
| become             | 是否提权                                                     |
| become_exe         |                                                              |
| become_flags       | 提权命令的参数                                               |
| become_method      | 提权的方式                                                   |
| become_user        | 提权的用户                                                   |
| check_mode         | 当为 True 时，只检查，不做修改                               |
| collections        |                                                              |
| connection         | 连接方式                                                     |
| debugger           | 开启 debugger 模式                                           |
| delegate_facts     | 委托 facts                                                   |
| delegate_to        | 任务委派                                                     |
| diff               | 对比更改的文件                                               |
| environment        | 定义远端系统的环境变量                                       |
| ignore_errors      | 是否忽略错误                                                 |
| ignore_unreachable | 布尔值，可以忽略无法访问的主机并继续                         |
| module_defaults    | 指定模块的默认参数值。                                       |
| name               | 定义任务得名称                                               |
| no_log             | 不记录日志                                                   |
| port               | 定义 ssh 的连接端口                                          |
| remote_user        | 远端系统的执行用户                                           |
| run_once           | 只运行一次                                                   |
| tags               | 标记标签                                                     |
| throttle           | 限制并发任务在 tasks，blocks 和 playbook 级别上运行的数量。不能高于 serial 和 forks 数 |
| vars               | 定义变量                                                     |
| when               | 条件表达式结果为 True 则执行 block                           |

## Block

> 在 block 下可用的关键字

| key                | desc                                                                                   |
| ------------------ | -------------------------------------------------------------------------------------- |
| always             | Block 中执行的任务列表，无论是否存在错误都会执行。                                     |
| any_errors_fatal   | 有错误时立即中断 ansbile                                                               |
| become             | 是否提权                                                                               |
| become_exe         |                                                                                        |
| become_flags       | 提权命令的参数                                                                         |
| become_method      | 提权的方式                                                                             |
| become_user        | 提权的用户                                                                             |
| block              | 分组里的任务列表                                                                       |
| check_mode         | 当为 True 时，只检查，不做修改                                                         |
| collections        |                                                                                        |
| connection         | 连接方式                                                                               |
| debugger           | 开启 debugger 模式                                                                     |
| delegate_facts     | 布尔值，将 facts 应用于委派的主机。                                                    |
| delegate_to        | 任务委派                                                                               |
| diff               | 对比更改的文件                                                                         |
| environment        | 定义远端系统的环境变量                                                                 |
| ignore_errors      | 是否忽略错误                                                                           |
| ignore_unreachable | 布尔值，可以忽略无法访问的主机并继续                                                   |
| module_defaults    | 指定模块的默认参数值。                                                                 |
| name               | 定义 block 名称                                                                        |
| no_log             | 不记录日志                                                                             |
| port               | 定义 ssh 的连接端口                                                                    |
| remote_user        | 远端系统的执行用户                                                                     |
| rescue             | block 中的任务在执行中，如果有任何错误，将执行 rescue 中的任务。                       |
| run_once           | 只运行一次                                                                             |
| tags               | 标记标签                                                                               |
| throttle           | 限制并发任务在 tasks，blocks 和 playbook 级别上运行的数量。不能高于 serial 和 forks 数 |
| vars               | 定义变量                                                                               |
| when               | 条件表达式结果为 True 则执行 block                                                     |

## Task

> 在 task 下可用的关键字

| key                   | desc                                                         |
| --------------------- | ------------------------------------------------------------ |
| action                | 执行动作                                                     |
| any_errors_fatal      | 为 True 时，只要任务有错误，就立即停止 ansible               |
| args                  | 定义任务得参数                                               |
| async                 | 是否异步执行任务                                             |
| become                | 是否提权                                                     |
| become_exe            |                                                              |
| become_flags          | 提权命令的参数                                               |
| become_method         | 提权的方式                                                   |
| become_user           | 提权的用户                                                   |
| changed_when          | 条件表达式为 True 时，使任务状态为 changed                   |
| check_mode            | 为 True 时，只检查运行状态，在远端不做任何修改               |
| collections           |                                                              |
| connection            | 连接方式                                                     |
| debugger              | 开启 debugger 模式                                           |
| delay                 | 等待多少秒，才执行任务                                       |
| delegate_facts        | 布尔值，将 facts 应用于委派的主机。                          |
| delegate_to           | 任务委派                                                     |
| diff                  | 对比更改的文件                                               |
| environment           | 定义远端的环境变量                                           |
| failed_when           | 条件表达式为 True 时，使任务为失败状态                       |
| ignore_errors         | 是否忽略错误                                                 |
| ignore_unreachable    | 布尔值，可以忽略无法访问的主机并继续                         |
| local_action          | 本地执行                                                     |
| loop                  | 循环                                                         |
| loop_control          | 改变循环的变量项                                             |
| module_defaults       | 指定模块的默认参数值。                                       |
| name                  | 定义名称                                                     |
| no_log                | 不记录日志                                                   |
| notify                | 用于任务执行完，执行 handlers 里的任务                       |
| poll                  | 轮询时间                                                     |
| port                  | 定义 ssh 的连接端口                                          |
| register              | 注册变量                                                     |
| remote_user           | 远端系统的执行用户                                           |
| retries               | 重试次数                                                     |
| run_once              | 只运行一次                                                   |
| tags                  | 标记为标签                                                   |
| throttle              | 限制并发任务在 tasks，blocks 和 playbook 级别上运行的数量。不能高于 serial 和 forks 数 |
| until                 | 直到为真时，才继续执行任务                                   |
| vars                  | 定义变量                                                     |
| when                  | 条件表达式，结果为 True 则执行 task                          |
| with\_<lookup_plugin> | 循环插件                                                     |
