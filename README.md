
                                                +-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
                                                |                                                                                                                                                                                                                                         |
                                                |                                                                                                                                                                                                 +---------------------+                 |
                                                |                                                                                                                                                                                    :2 169 0:    | Services_dhcp_w0_c5 |                 |
  +---------------------------------------------+                                   +-----------------------------------------------------------------------------------------------------------------------------------------------------------> |        DHCP         | ----------------+--------------------------------------------------------------------------------------------------------------------------+
  |                                                                                 |                                                                                                                                                             +---------------------+                 |                                                                                                                          |
  |                                                                                 |                                                                                                                                                                                                     |                                                                                                                          |
  |                                                                                 |                                                                                                                                                                                                     |                                                                                                                          |                                                +-------------------------------------------------------------------------------------------+
  |                                                                                 |                                                                                                                                                                                                     |                                                                                                                          |                                                |                                                                                           |
  |                                                                                 |            +----------------------------------+                                                                                                             +---------------------+                 |                                                                                                                          |           +---------------------------------+  |  +-----------------------------------+                                                    |
  |                                                                                 |            |        Services_iobstate         |                                                                                                             |  Services_ar_w0_c5  |                 |                                                                                                                          |           | SwPorts_pOut_feff0b3d0902_w0_c5 |  |  | SwPorts_pOut_if02000300238E_w0_c5 |                                                    |
  |                                                                                 |            |           IobrickState           |                                                                                                             |    ArpResponder     |                 |                                                                                                                          |           |             PortOut             |  |  |              PortOut              |                                                    |
  |                                                                                 |            |                                  |                                                                                                             |                     | ----------------+------------------------------------------------------------------------------------------------------------+             |           |      feff0b3d0902/PMDPort       |  |  |      if02000300238E/PMDPort       |                                                    |
  |                                                                                 |            +----------------------------------+                                                                                                             +---------------------+                 |                                                                                                            |             |           +---------------------------------+  |  +-----------------------------------+                                                    |
  |                                                                                 |                                                                                                                                                               ^                                     |                                                           :0 0 0:                                          |             |             ^                                  |    ^                                                                                      |
  |                                                                                 |                                                                                                                                                               | :1 140 0:                           | :1 129 0:                        +-------------------------------------+                                   | :0 140 0:   | :0 168 0:   | :1 0 0:                          |    | :4 297 0:                                                                            | :5 130 0:
  |                                                                                 |                                                                                                                                                               |                                     v                                  v                                     |                                   v             v             |                                  |    |                                                                                      v
  |                                                                                 |            +----------------------------------+                +-----------------------------+                +------------------------------+              +---------------------+               +-------------------+              +------------------------+            +--------------------+              +-------------------------------------------------------------------------------------------------------+            +------------------------+            +-----------------------------------+     +------------------------------+
  |                                                                                 |            |      Services_qIn_p0_w0_c5       |                |  Services_bpf_vxlan_w0_c5   |                |      Services_vx_w0_c5       |              |                     |               |                   |              |                        |            | Services_rep_w0_c5 |              |                                                                                                       |            | Services_qOut_p0_w0_c5 |            | SwPorts_pOut_if02000400238E_w0_c5 |     |  Services_pIn_host_in_w0_c5  |
  |                                                                                 |            |             QueueInc             |  :0 77864 0:   |             BPF             |  :1 0 0:       |          VXLANDecap          |  :0 0 0:     |                     |  :0 2079 0:   |                   |  :1 132 1:   |                        |  :1 0 0:   |     Replicate      |  :1 0 0:     |                                                                                                       |  :0 0 0:   |        QueueOut        |            |              PortOut              |     |           PortInc            |
  |                                                                                 |            |          pmd0:0/PMDPort          | -------------> |                             | -------------> |                              | -----------> |                     | ------------> |                   | -----------> |                        | ---------> |                    | -----------> |                                                                                                       | ---------> |     pmd0:0/PMDPort     | <+         |      if02000400238E/PMDPort       |  +- | net_tap_iobricks_eth/PMDPort |
  |                                                                                 |            +----------------------------------+                +-----------------------------+                +------------------------------+              |                     |               |                   |              |                        |            +--------------------+              |                                                                                                       |            +------------------------+  |         +-----------------------------------+  |  +------------------------------+
  |                                                                                 |                                                                  |                                                                                          | Services_bpf_w0_c5  |               | Services_fw_w0_c5 |              | PortMirroring_pm_w0_c5 |                                   :2 132 0:    |                                                                                                       |              ^                         |          :0 181 0:                             |
  |                                                                                 +------------------------------------------------------------------+----------------------------------------------------------------------------------------- |         BPF         |               |    FwServices     |              |       PortMirror       | ---------------------------------------------> |                                                                                                       |              | :0 0 0:                 +------------------------------------------------+
  |                                                                                                                                                    v                                                                                          |                     |               |                   |              |                        |                                                |                                                                                                       |              |
  |                                                                                              +----------------------------------+                +-----------------------------+                +------------------------------+              |                     |               |                   |              |                        |                                                |                                                                                                       |              |                                   +-----------------------------------+
  |                                                                                              |    SwPorts_pIn_iftest2_w0_c5     |                |                             |                | Services_pOut_host_out_w0_c5 |              |                     |               |                   |              |                        |                                                |                                         SwPorts_bpf_out_w0_c5                                         |              |                                   | SwPorts_pOut_if02000700238E_w0_c5 |
  |                                                                                              |             PortInc              |                |                             |  :1 77864 0:   |           PortOut            |              |                     |               |                   |              |                        |                                                |                                                  BPF                                                  |              |                        :6 0 0:    |              PortOut              |
  |                                                                                              |         iftest2/PMDPort          |                |                             | -------------> | net_tap_iobricks_eth/PMDPort |  +---------- |                     |  +----------- |                   | -+           |                        |                                                |                                                                                                       | -------------+---------------------------------> |      if02000700238E/PMDPort       |
  |                                                                                              +----------------------------------+                |                             |                +------------------------------+  |           +---------------------+  |            +-------------------+  |           +------------------------+                                                |                                                                                                       |              |                                   +-----------------------------------+
  |                                                                                                |                                                 |      Services_ac_w0_c5      |                                                  |             ^                      |              ^                    |                                                                                     |                                                                                                       |              |
  |                                                                                                | :0 19 3:                                        |          ArpCache           |                  +-------------------------------+             | :0 2389 0:           |              | :1 3 1:            |                                                                                     |                                                                                                       |              |
  |                                                                                                v                                                 |                             |                  |                                             |                      |              |                    |                                                                                     |                                                                                                       |              |
  |  +----------------------------------+     +----------------------------------+               +----------------------------------+                |                             |                  |                                             |                      |              |                    |                                                                                     |                                                                                                       |              |                                   +-----------------------------------+
  |  | SwPorts_pIn_if02000700238E_w0_c5 |     |  SwPorts_pIn_feff0b3d0902_w0_c5  |               |                                  |                |                             |                  |                                             |                      |              |                    |                                                                                     |                                                                                                       |              |                                   |    SwPorts_pOut_iftest2_w0_c5     |
  |  |             PortInc              |     |             PortInc              |  :0 36 1:     |                                  |                |                             |                  |                                             |                      |              |                    |                                                                                     |                                                                                                       |              |                        :3 0 0:    |              PortOut              |
  |  |      if02000700238E/PMDPort      | -+  |       feff0b3d0902/PMDPort       | ------------> |                                  |                |                             | -----------------+---------------------------------------------+----------------------+--------------+--------------------+-------------------------------------------------------------------------+           |                                                                                                       | -------------+---------------------------------> |          iftest2/PMDPort          |
  |  +----------------------------------+  |  +----------------------------------+               |                                  |                +-----------------------------+                  |                                             |                      |              |                    |                                                                         |           +-------------------------------------------------------------------------------------------------------+              |                                   +-----------------------------------+
  |                                        |                                       :0 1 6:       |         SwPorts_as_w0_c5         |                                                                 |                                             |                      |              |                    |                                                                         |             ^                                                                                                                    |
  |                                        +---------------------------------------------------> |           AntiSpoofing           | ----------------------------------------------------------------+---------------------------------------------+                      |              |                    |                                                                         +-------------+--------------------------------------------------------------------------------------------------------------------+
  |                                                                                              |                                  |                                                                 |                                                                    |              |                    |                                                                                       |
  |                                           +----------------------------------+               |                                  |                                                                 |                                                                    |              |                    |                                                                                       |
  |                                           | SwPorts_pIn_if02000300238E_w0_c5 |               |                                  |                                                                 |                                                                    |              |                    |                                                                                       |
  |                                           |             PortInc              |  :0 2364 4:   |                                  |                                                                 |                                                                    | :0 2062 1:   |                    |                                                                                       | :2 0 0:
  |                                           |      if02000300238E/PMDPort      | ------------> |                                  |                                                                 |                                                                    |              |                    |                                                                                       |
  |                                           +----------------------------------+               +----------------------------------+                                                                 |                                                                    |              |                    |                                                                                       |
  |                                                                                :0 393 5:       ^                                                                                                  |                                                                    |              |                    |                                                                                       |
  |                                             +--------------------------------------------------+                                                                                                  | :3 0 1:                                     +----------------------+              |                    |                                                                                       |
  |                                             |                                                                                                                                                     v                                             v                                     |                    |                                                                                       |
  |                                             |                                                +----------------------------------+                +-----------------------------------------------------------------------------+              +---------------------+                 |                    |                                                                                       |
  |                                             |                                                |    Services_pIn_pub_in_w0_c5     |                |                                                                             |              |                     |                 |                    |                                                                                       |
  |                                             |                                                |             PortInc              |  :0 1361 1:    |                                                                             |  :3 0 2:     |                     |                 |                    |                                                                                       |
  |                                             |                                                |     vport_iobricks_pub/VPort     | -------------> |                                                                             | -----------> |                     | ----------------+                    |                                                                                       |
  |                                             |                                                +----------------------------------+                |                                                                             |              |                     |                                      |                                                                                       |
  |                                             |                                                                                                    |                             Services_nat_w0_c5                              |              |  Services_fp_w0_c5  |  :2 17 0:                            |                                                                                       |
  |                                             |                                                                                                    |                                     NAT                                     |              |     FirstPacket     | <------------------------------------+                                                                                       |
  |                                             |                                                                                                    |                                  0 entries                                  |              |                     |                                                                                                                              |
  |                                             |                                                +----------------------------------+                |                                                                             |              |                     |                                                                                                                              |
  |                                             |                                                | SwPorts_pIn_if02000400238E_w0_c5 |                |                                                                             |              |                     |                                                                                                                              |
  |                                             |                                                |             PortInc              |                |                                                                             |              |                     |                                                                                                                              |
  |                                             +----------------------------------------------- |      if02000400238E/PMDPort      |  +------------ |                                                                             |              |                     |                                                                                                                              |
  |                                                                                              +----------------------------------+  |             +-----------------------------------------------------------------------------+              +---------------------+                                                                                                                              |
  |                                                                                                                                    |               |                              |               ^                                             |                                                                                                                                                  |
  +------------------------------------------------------------------------------------------------------------------------------------+               | :0 3258 0:                   |               | :0 2059 0:                                  | :2 2059 0:                                                                                                                                       |
                                                                                                                                                       v                              |               |                                             v                                                                                                                                                  |
                                                                                                                                                     +-----------------------------+  |               |                                           +---------------------+                                                                                                                              |
                                                                                                                                                     | Services_pOut_pub_out_w0_c5 |  |               |                                           |  Services_ud_w0_c5  |                                                                                                                              |
                                                                                                                                                     |           PortOut           |  |               |                                           |       Update        |                                                                                                                              |
                                                                                                                                                     |  vport_iobricks_pub/VPort   |  |               +------------------------------------------ |                     |                                                                                                                              |
                                                                                                                                                     +-----------------------------+  |                                                           +---------------------+                                                                                                                              |
                                                                                                                                                                                      |                                                                                                                                                                                                                |
                                                                                                                                                                                      +----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
