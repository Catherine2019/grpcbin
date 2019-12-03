```

       +-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
       |                                                                                                                                                                                   |
       |  +--------------------------------+                                                                                                          +---------------------+              |                                                                                                                  +---------------------------------+
       |  |       Services_iobstate        |                                                                                                          |  Services_ar_w0_c5  |              |                                                                                                                  | SwPorts_pOut_feff0b3d0b02_w0_c5 |
       |  |          IobrickState          |                                                                                                          |    ArpResponder     |              |                                                                                                                  |             PortOut             |
       |  |                                |                                                                                                          |                     | -------------+--------------------------------------------------------------------------------------------------------+         |      feff0b3d0b02/PMDPort       |
       |  +--------------------------------+                                                                                                          +---------------------+              |                                                                                                        |         +---------------------------------+
       |                                                                                                                                                ^                                  |                                                         :0 0 0:                                        |           ^
       |                                                                                                                                                | :1 0 0:                          |                                +-------------------------------------+                                 | :0 0 0:   | :1 0 0:
       |                                                                                                                                                |                                  |                                v                                     |                                 v           |
       |  +--------------------------------+               +-----------------------------+               +------------------------------+             +---------------------+            +-------------------+            +------------------------+            +--------------------+            +---------------------------------------------+            +------------------------+              +------------------------------+
       |  |     Services_qIn_p0_w0_c5      |               |  Services_bpf_vxlan_w0_c5   |               |      Services_vx_w0_c5       |             |                     |            |                   |            |                        |            | Services_rep_w0_c5 |            |                                             |            | Services_qOut_p0_w0_c5 |              |  Services_pIn_host_in_w0_c5  |
       |  |            QueueInc            |  :0 6077 0:   |             BPF             |  :1 0 0:      |          VXLANDecap          |  :0 0 0:    |                     |  :0 9 0:   |                   |  :1 0 1:   |                        |  :1 0 0:   |     Replicate      |  :1 0 0:   |                                             |  :0 0 0:   |        QueueOut        |  :0 149 0:   |           PortInc            |
       |  |         pmd0:0/PMDPort         | ------------> |                             | ------------> |                              | ----------> |                     | ---------> |                   | ---------> |                        | ---------> |                    | ---------> |                                             | ---------> |     pmd0:0/PMDPort     | <----------- | net_tap_iobricks_eth/PMDPort |
       |  +--------------------------------+               +-----------------------------+               +------------------------------+             |                     |            |                   |            |                        |            +--------------------+            |                                             |            +------------------------+              +------------------------------+
       |                                                     |                                                                            :0 11 0:    | Services_bpf_w0_c5  |            | Services_fw_w0_c5 |            | PortMirroring_pm_w0_c5 |                                   :2 0 0:    |            SwPorts_bpf_out_w0_c5            |              ^
       |                                      +--------------+--------------------------------------------------------------------------------------> |         BPF         |            |    FwServices     |            |       PortMirror       | -------------------------------------------> |                     BPF                     |              | :0 0 0:
       |                                      |              v                                                                                        |                     |            |                   |            |                        |                                              |                                             |              |
       |  +--------------------------------+  |            +-----------------------------+               +------------------------------+             |                     |            |                   |            |                        |                                              |                                             |              |
       |  | SwPorts_pIn_feff0b3d0b02_w0_c5 |  |            |                             |               | Services_pOut_host_out_w0_c5 |             |                     |            |                   |            |                        |                                              |                                             |              |
       |  |            PortInc             |  |            |                             |  :1 6074 0:   |           PortOut            |             |                     |            |                   |            |                        |                                              |                                             |              |
       |  |      feff0b3d0b02/PMDPort      |  |            |                             | ------------> | net_tap_iobricks_eth/PMDPort |  +--------- |                     |  +-------> |                   | -+         |                        |                                              |                                             |              |
       |  +--------------------------------+  |            |                             |               +------------------------------+  |          +---------------------+  |         +-------------------+  |         +------------------------+                                              +---------------------------------------------+              |
       |    |                                 |            |      Services_ac_w0_c5      |                                                 |            |                      |           ^                    |           |                                                                       ^           ^                                              |
       |    | :0 22 1:                        |            |          ArpCache           |                                                 |            |                      | :1 0 0:   | :1 0 1:            |           |                                                                       | :0 0 0:   | :2 0 0:                                      |
       |    v                                 |            |                             |                                                 |            |                      |           |                    |           |                                                                       |           |                                              |
       |  +--------------------------------+  |            |                             |                                                 |            |                      |           |                    |           |                                                                       |           |                                              |
       |  |        SwPorts_as_w0_c5        |  |            |                             |                                                 |            |                      |           |                    |           |                                                                       |           |                                              |
       |  |          AntiSpoofing          | -+            |                             | ------------------------------------------------+------------+----------------------+-----------+--------------------+-----------+-----------------------------------------------------------------------+-----------+----------------------------------------------+
       |  +--------------------------------+               +-----------------------------+                                                 |            |                      |           |                    |           |                                                                       |           |
       |                                     :0 0 0:         ^                                                                             |            |                      |           |                    |           |                                                                       |           |
  +----+-----------------------------------------------------+                                                                             | :3 0 1:    | :2 0 0:              +-----------+--------------------+-----------+-------------------------+                                             |           |
  |    |                                                                                                                                   |            v                                  |                    |           |                         |                                             |           |
  |    |  +--------------------------------+               +----------------------------------------------------------------------------+  |          +---------------------+              |                    |           |                         |                                             |           |
  |    |  |   Services_pIn_pub_in_w0_c5    |               |                                                                            |  |          | Services_dhcp_w0_c5 |              |                    |           |                         |                                             |           |
  |    |  |            PortInc             |  :0 12 1:     |                                                                            |  |          |        DHCP         |              |                    |           |                         |                                             |           |
  |    |  |    vport_iobricks_pub/VPort    | ------------> |                                                                            | <+          |                     | -------------+--------------------+-----------+-------------------------+---------------------------------------------+           |
  |    |  +--------------------------------+               |                             Services_nat_w0_c5                             |             +---------------------+              |                    |           |                         |                                                         |
  |    |                                                   |                                    NAT                                     |                                                  |                    |           |                         |                                                         |
  |    |                                                   |                                 0 entries                                  | -------------------------------------------------+--------------------+-----------+-------------------------+                                                         |
  |    |                                                   |                                                                            |                                                  |                    |           |                                                                                   |
  |    |                                                   |                                                                            |  :3 0 2:    +---------------------+              |                    |           |                                                                                   |
  |    |                                                   |                                                                            | ----------> |                     | -------------+                    |           |                                                                                   |
  |    |                                                   +----------------------------------------------------------------------------+             |                     |                                   |           |                                                                                   |
  |    |                                                     |                              |              ^                                          |  Services_fp_w0_c5  |  :2 9 0:                          |           |                                                                                   |
  |    |                                                     |                              |              | :0 0 0:                                  |     FirstPacket     | <---------------------------------+           |                                                                                   |
  |    |                                                     |                              |              |                                          |                     |                                               |                                                                                   |
  |    |                                                     |                              |              |                              :0 0 1:     |                     |                                               |                                                                                   |
  |    +-----------------------------------------------------+------------------------------+--------------+----------------------------------------> |                     |                                               |                                                                                   |
  |                                                          |                              |              |                                          +---------------------+                                               |                                                                                   |
  |                                                          |                              |              |                                            |                                                                   |                                                                                   |
  |                                                          | :0 0 0:                      |              |                                            | :2 0 0:                                                           |                                                                                   |
  |                                                          v                              |              |                                            v                                                                   |                                                                                   |
  |                                                        +-----------------------------+  |              |                                          +---------------------+                                               |                                                                                   |
  |                                                        | Services_pOut_pub_out_w0_c5 |  |              |                                          |  Services_ud_w0_c5  |                                               |                                                                                   |
  |                                                        |           PortOut           |  |              |                                          |       Update        |                                               |                                                                                   |
  |                                                        |  vport_iobricks_pub/VPort   |  |              +----------------------------------------- |                     |                                               |                                                                                   |
  |                                                        +-----------------------------+  |                                                         +---------------------+                                               |                                                                                   |
  |                                                                                         |                                                                                                                               |                                                                                   |
  +-----------------------------------------------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+                                                                                   |
                                                                                            |                                                                                                                                                                                                                   |
                                                                                            |                                                                                                                                                                                                                   |
                                                                                            +-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
```
