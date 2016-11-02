Cron
=========

Configure crontab and setup crons on hosts.

Generaly Dev and Preprod plateform are stopped the night and weekend. By default daily, weekly and monthly are run during the night. Because dev and preprod are stopped, Daily cron are never run. Cron module allow us to override the schedule and run cron during the day.


Role Variables
--------------

  * crons: Used to define crons.
  * crontab_time: Used to override the crontab run time.

Example Playbook
----------------

```bash

- hosts: servers

  vars:
    crontab_time:
      hourly: "17 *    * * *"
      daily: "25 6    * * *"
      weekly: "47 6    * * 7"
      monthly: "52 6    1 * *"

    crons:
      - name: first cron to add
        job: "/my/first/cron/command"
        minute: "30"
        hour: "*"
        day: "*"
        month: "*"
        weekday: "*"
        user: foo
        state: present

  roles:
    - {role: cycloid.cron, tags: cron}
```
