# CONFIGURACION NAGIOS - NETWORK DEVICES

# HOST DEFINITIONS
define host {
    use             generic-switch
    host_name       R1-Cisco7200
    alias           R1 Cisco7200
    address         10.10.0.1
    hostgroups      routers
    max_check_attempts 5
    check_interval 5
    retry_interval 1
}

define host {
    use             generic-switch
    host_name       R2-MikroTikRB450
    alias           R2 MikroTik RB450
    address         10.10.1.2
    hostgroups      routers
    max_check_attempts 5
    check_interval 5
    retry_interval 1
}

define host {
    use             generic-switch
    host_name       R3-Cisco7200
    alias           R3 Cisco7200
    address         192.168.2.1
    hostgroups      routers
    max_check_attempts 5
    check_interval 5
    retry_interval 1
}

define host {
    use             generic-switch
    host_name       SW1-MikroTikCRS328
    alias           SW1 MikroTik CRS328
    address         192.168.1.2
    hostgroups      network_switches_nd
    max_check_attempts 5
    check_interval 5
    retry_interval 1
}

define host {
    use             generic-switch
    host_name       SW2-MikroTikCRS328
    alias           SW2 MikroTik CRS328
    address         192.168.2.2
    hostgroups      network_switches_nd
    max_check_attempts 5
    check_interval 5
    retry_interval 1
}

# HOSTGROUP DEFINITIONS
define hostgroup {
    hostgroup_name  routers
    alias           Network Routers
}

define hostgroup {
    hostgroup_name  network_switches_nd
    alias           Network Switches ND
}

# PING Service
define service {
    use                 generic-service
    host_name           R1-Cisco7200,R2-MikroTikRB450,R3-Cisco7200,SW1-MikroTikCRS328,SW2-MikroTikCRS328
    service_description PING
    check_command       check_ping!200.0,20%!600.0,60%
    check_interval      5
    retry_interval      1
}

# Uptime via SNMP
define service {
    use                 generic-service
    host_name           R1-Cisco7200,R2-MikroTikRB450,R3-Cisco7200,SW1-MikroTikCRS328,SW2-MikroTikCRS328
    service_description Uptime
    check_command       check_snmp!-C public -o sysUpTime.0
    check_interval      5
    retry_interval      1
}

# Bandwidth via MRTG
define service {
    use                 generic-service
    host_name           R1-Cisco7200,R2-MikroTikRB450,R3-Cisco7200,SW1-MikroTikCRS328,SW2-MikroTikCRS328
    service_description Bandwidth Usage
    check_command       check_local_mrtgtraf!/var/lib/mrtg/$HOSTADDRESS$_1.log!AVG!1000000,1000000!5000000,5000000!10
    check_interval      5
    retry_interval      1
}
