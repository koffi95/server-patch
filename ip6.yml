---
- name: Disable IPv6 on Windows Server
  hosts: windows
  gather_facts: yes
  tasks:

    - name: Disable IPv6 via registry setting
      win_regedit:
        path: HKLM:\SYSTEM\CurrentControlSet\Services\Tcpip6\Parameters
        name: DisabledComponents
        data: "0xFF"
        type: dword
        state: present

    - name: Restart the server for changes to take effect
      win_reboot:
        reboot_timeout: 600
        test_command: hostname
        pre_reboot_delay: 5
        post_reboot_delay: 10

    - name: Verify IPv6 is disabled
      win_shell: Get-NetAdapterBinding -ComponentID ms_tcpip6
      register: ipv6_binding_status

    - name: Output result of IPv6 binding status
      debug:
        msg: "IPv6 Binding Status: {{ ipv6_binding_status.stdout }}"
