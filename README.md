# SNR_Ansible
Playbooks, roles and other Ansible stuff to use on SNR switches.

!!! Перед использованием необходимо применить workaround из https://github.com/SomeGitRepo33/SNR_workaround.

Q: Зачем для каждой модели свича в show_snr_ver свой таск?1?!11

A: При выполнении вывод получается сгруппирован + можно легко добавить переменные с актуальными прошивками, и фильтровать вывод, например выводить только коммутаторы с отличающимся/неактуальным BootROM:
- name: S2985
      debug:
        msg:
          - ...
          - ...
  when:
    - '"S2985" in switch_facts[0]["Model"]'
    - 'actual_2985_bootrom != switch_facts[0]["BootROMVersion"]'
