# ansible
Ansible Learning


root@demo-user-PC:/home/demo-user/folder/ansible# ansible-playbook test.yml -vv
ansible-playbook [core 2.12.0]
  config file = None
  configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
  ansible python module location = /usr/lib/python3/dist-packages/ansible
  ansible collection location = /root/.ansible/collections:/usr/share/ansible/collections
  executable location = /usr/bin/ansible-playbook
  python version = 3.10.6 (main, Mar 10 2023, 10:55:28) [GCC 11.3.0]
  jinja version = 3.0.3
  libyaml = True
No config file found; using defaults
[WARNING]: No inventory was parsed, only implicit localhost is available
[WARNING]: provided hosts list is empty, only localhost is available. Note that the implicit localhost does not match 'all'
Skipping callback 'default', as we already have a stdout callback.
Skipping callback 'minimal', as we already have a stdout callback.
Skipping callback 'oneline', as we already have a stdout callback.

PLAYBOOK: test.yml **********************************************************************************************************************************************************************************************
1 plays in test.yml

PLAY [localhost] ************************************************************************************************************************************************************************************************

TASK [Gathering Facts] ******************************************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/test.yml:2
ok: [localhost]

TASK [this is first pretask] ************************************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/test.yml:23
changed: [localhost] => {"changed": true, "cmd": "whoami", "delta": "0:00:00.004987", "end": "2023-09-24 16:35:03.040078", "msg": "", "rc": 0, "start": "2023-09-24 16:35:03.035091", "stderr": "", "stderr_lines": [], "stdout": "root", "stdout_lines": ["root"]}
META: ran handlers

TASK [running the first task] ***********************************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/test.yml:5
changed: [localhost] => {"changed": true, "cmd": "whoami", "delta": "0:00:00.005219", "end": "2023-09-24 16:35:03.371019", "msg": "", "rc": 0, "start": "2023-09-24 16:35:03.365800", "stderr": "", "stderr_lines": [], "stdout": "root", "stdout_lines": ["root"]}

TASK [invoking test role] ***************************************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/test.yml:7

TASK [test-role : this is the role task1] ***********************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/test-role/tasks/main.yml:7
NOTIFIED HANDLER test-role : task1 handler for localhost
changed: [localhost] => {"changed": true, "cmd": "echo test", "delta": "0:00:00.004126", "end": "2023-09-24 16:35:03.753425", "msg": "", "rc": 0, "start": "2023-09-24 16:35:03.749299", "stderr": "", "stderr_lines": [], "stdout": "test", "stdout_lines": ["test"]}
META: role_complete for localhost

TASK [invoking debug role] **************************************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/test.yml:10

TASK [debug-role : this is the role task1] **********************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/debug-role/tasks/main.yml:8
NOTIFIED HANDLER debug-role : task1 handler for localhost
changed: [localhost] => {"changed": true, "cmd": "echo test", "delta": "0:00:00.003663", "end": "2023-09-24 16:35:04.140420", "msg": "", "rc": 0, "start": "2023-09-24 16:35:04.136757", "stderr": "", "stderr_lines": [], "stdout": "test", "stdout_lines": ["test"]}

TASK [debug-role : this is the role task1 but handler wont be invoked] ******************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/debug-role/tasks/main.yml:17
changed: [localhost] => {"changed": true, "cmd": "echo test", "delta": "0:00:00.004016", "end": "2023-09-24 16:35:04.460363", "msg": "", "rc": 0, "start": "2023-09-24 16:35:04.456347", "stderr": "", "stderr_lines": [], "stdout": "test", "stdout_lines": ["test"]}

TASK [debug-role : flushing all the pending handlers] ***********************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/debug-role/tasks/main.yml:25

RUNNING HANDLER [test-role : task1 handler] *********************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/test-role/handlers/main.yml:4
ok: [localhost] => {
    "msg": "task1 handler for test-role"
}

RUNNING HANDLER [debug-role : task1 handler] ********************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/debug-role/handlers/main.yml:7
ok: [localhost] => {
    "msg": "task1 handler"
}
META: ran handlers

TASK [debug-role : once again calling task1 handler] ************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/debug-role/tasks/main.yml:32
NOTIFIED HANDLER test-role : task1 handler for localhost
NOTIFIED HANDLER debug-role : task1 handler for localhost
changed: [localhost] => {"changed": true, "cmd": "echo test", "delta": "0:00:00.003776", "end": "2023-09-24 16:35:04.867015", "msg": "", "rc": 0, "start": "2023-09-24 16:35:04.863239", "stderr": "", "stderr_lines": [], "stdout": "test", "stdout_lines": ["test"]}

TASK [debug-role : once again calling task2 handler] ************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/debug-role/tasks/main.yml:40
NOTIFIED HANDLER debug-role : task2 handler for localhost
changed: [localhost] => {"changed": true, "cmd": "echo test", "delta": "0:00:00.003796", "end": "2023-09-24 16:35:05.184880", "msg": "", "rc": 0, "start": "2023-09-24 16:35:05.181084", "stderr": "", "stderr_lines": [], "stdout": "test", "stdout_lines": ["test"]}

TASK [debug-role : creating a file temp] ************************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/debug-role/tasks/main.yml:45
NOTIFIED HANDLER debug-role : executing temp handler for localhost
changed: [localhost] => {"changed": true, "dest": "/tmp/a.txt", "gid": 0, "group": "root", "mode": "0644", "owner": "root", "size": 0, "state": "file", "uid": 0}
META: role_complete for localhost

TASK [invoking test role] ***************************************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/test.yml:13

TASK [test-role : this is the role task1] ***********************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/test-role/tasks/main.yml:7
changed: [localhost] => {"changed": true, "cmd": "echo test", "delta": "0:00:00.003677", "end": "2023-09-24 16:35:06.117229", "msg": "", "rc": 0, "start": "2023-09-24 16:35:06.113552", "stderr": "", "stderr_lines": [], "stdout": "test", "stdout_lines": ["test"]}
META: role_complete for localhost

TASK [running the last task] ************************************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/test.yml:16
changed: [localhost] => {"changed": true, "cmd": "whoami", "delta": "0:00:00.005419", "end": "2023-09-24 16:35:06.445534", "msg": "", "rc": 0, "start": "2023-09-24 16:35:06.440115", "stderr": "", "stderr_lines": [], "stdout": "root", "stdout_lines": ["root"]}

RUNNING HANDLER [test-role : task1 handler] *********************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/test-role/handlers/main.yml:4
ok: [localhost] => {
    "msg": "task1 handler for test-role"
}

RUNNING HANDLER [debug-role : task2 handler] ********************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/debug-role/handlers/main.yml:3
ok: [localhost] => {
    "msg": "task2 handler"
}

RUNNING HANDLER [debug-role : task1 handler] ********************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/debug-role/handlers/main.yml:7
ok: [localhost] => {
    "msg": "task1 handler"
}

RUNNING HANDLER [debug-role : executing temp handler] ***********************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/roles/debug-role/handlers/main.yml:11
changed: [localhost] => {"changed": true, "path": "/tmp/a.txt", "state": "absent"}
META: ran handlers

TASK [this is last post task] ***********************************************************************************************************************************************************************************
task path: /home/demo-user/folder/ansible/test.yml:26
changed: [localhost] => {"changed": true, "cmd": "whoami", "delta": "0:00:00.005314", "end": "2023-09-24 16:35:07.216230", "msg": "", "rc": 0, "start": "2023-09-24 16:35:07.210916", "stderr": "", "stderr_lines": [], "stdout": "root", "stdout_lines": ["root"]}
META: ran handlers

PLAY RECAP ******************************************************************************************************************************************************************************************************
localhost                  : ok=18   changed=12   unreachable=0    failed=0    skipped=0    rescued=0    ignored=0