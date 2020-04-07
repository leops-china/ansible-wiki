# 12. Blocks分组

`Blocks`允许任务的逻辑分组和`play`中的错误处理。您可以应用于单个任务的大部分内容(循环除外)都可以应用于块级别，这也使得设置任务通用的数据或指令变得更加容易。这并不意味着指令影响块本身，而是由块所包含的任务继承。例如，一个`when`将应用于任务，而不是块本身。

```yaml
 tasks:
   - name: Install, configure, and start Apache
     block:
       - name: install httpd and memcached
         yum:
           name:
           - httpd
           - memcached
           state: present

       - name: apply the foo config template
         template:
           src: templates/src.j2
           dest: /etc/foo.conf
       - name: start service bar and enable it
         service:
           name: bar
           state: started
           enabled: True
     when: ansible_facts['distribution'] == 'CentOS'
     become: true
     become_user: root
     ignore_errors: yes
```

 在上面的例子中，这3个任务都是在从块中继承`when`条件并在任务上判断之后执行的。它们还继承了特权升级指令，使`become`能够应用到block所包含的所有任务。最后，`ignore_errors: yes`即使有任务失败了，也将继续执行剧本。



## 块的错误处理

块还引入了以类似于大多数编程语言中的异常的方式处理错误的能力。块只处理任务的失败状态。错误的任务定义或无法访问的主机是不能触发块的错误处理。

```yaml
- name: Attempt and graceful roll back demo
  block:
    - debug:
        msg: 'I execute normally'
    - name: i force a failure
      command: /bin/false
    - debug:
        msg: 'I never execute, due to the above task failing, :-('
  rescue:
    - debug:
        msg: 'I caught an error'
    - name: i force a failure in middle of recovery! >:-)
      command: /bin/false
    - debug:
        msg: 'I also never execute :-('
  always:
    - debug:
        msg: "This always executes"
```

block中的任务在执行中，如果有任何错误，将执行**rescue**中的任务。 无论在block和rescue中发生或没有发生错误，**always**部分都运行。

需要注意的是，如果**rescue**部分成功完成，那么`play`将继续进行，因为它将擦除错误状态(但不包括报告),这意味着它不会触发`max_fail_percentage`或`any_errors_fatal`的配置，但将出现在playbook统计。



  发生错误后，依然运行handlers

```yaml
tasks:
   - name: Attempt and graceful roll back demo
     block:
       - debug:
           msg: 'I execute normally'
         changed_when: yes
         notify: run me even after an error
       - command: /bin/false
     rescue:
       - name: make sure all handlers run
         meta: flush_handlers
 handlers:
    - name: run me even after an error
      debug:
        msg: 'This handler runs even on error'
```



Ansible还为block的rescue部分的任务提供了两个变量

- ansible_failed_task 返回触发`rescue` 的失败任务。例如，要获取名称，请使用`ansible_failed_task.name`。
- ansible_failed_result  返回触发`rescue` 的失败任务的返回结果。这相当于在失败任务中添加 `register: ansible_failed_result `

 