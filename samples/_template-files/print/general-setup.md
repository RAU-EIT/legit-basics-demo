---
css: ../../../style-rau-base/rau-print.css
docType: lab
chunk:
  id: ITM1234
  revisionDate: "June 2026"
  classification: Internal
---

# General Setup

This setup contains information about the hardware, software, job aids, and setup procedures required for the lab exercises.

## Hardware

The following hardware is required:

* ControlLogix® with Compact I/O™ Workstation (Catalog Number ABT-TDCLX4) or equivalent hardware
* Computer hardware and cables for an EtherNet/IP™ network
* USB cable for communication between computer and controller
* 3 millimeter (mm) flat head screwdriver, or similar tool, to change rotary switch settings

The following firmware is required:

| Catalog Number | Description | Version |
|:--:|:------|:--:|
| 7756-L83E | ControlLogix 5583 Controller | 30 |
| 1756-OB16D | ControlLogix Digital Output Module | 3.0 |


## Software

The following software is required:

* Studio 5000 Logix Designer® V30, with the following components installed:
    * Online books
    * Firmware kit
* Logix Designer Compare Tool V6.1
* Studio 5000 Clock Sync Service V1.1
* RSLinx® Classic V3.80

RSLinx Classic software and the firmware files for the controller are included with the Studio 5000 Logix Designer installation files.

## Materials

### Required 

The following materials are required to complete this training. They are provided with the course materials and should be used to help complete the exercises: 

* Studio 5000 Logix Designer and Logix5000 Procedures Guide (Publication Number ABT-1756-TSJ50)
* ControlLogix Troubleshooting Guide (Publication Number ABT-1756-TSJ20)
* ControlLogix Workstation I/O Wiring Diagrams Appendix

### Recommended

The following materials are recommended to support the concepts in this training but they are not required to complete the exercises:

* 5000 Series Analog I/O Modules in Logix5000 Control Systems User Manual (Publication Number 5000-UM004)
* Kinetix 3 Motion Control Indexing Application Connected Components Accelerator Toolkit Quick Start (Publication Number CC-QS025)
* ControlLogix 5580 Controllers User Manual (Publication Number 1756-UM543)

## Student Setup

### Initial

Before beginning the exercises, complete the following setup:

1. Verify that the workstation is configured as follows:

    **Note:** "/24" indicates a subnet mask of 255.255.255.0

    
    [ControlLogix Chassis]{style="font-size:1.5em;font-weight:600;display:inline-block;width:100%;text-align:center;"}

    | Slot | Module | Configuration Details |
    |:-:|:----:|:---------:|
    |0 | 1756-OB16D | N/A |
    |1|	1756-L83 (5583)|	IP address: 192.168.100.1/24|
    |2|	1756-IB16D|	N/A|
    |3|	1756-EN2T|	IP address: 192.168.100.2/24|

    [Compact I/O Chassis]{style="font-size:1.5em;font-weight:600;display:inline-block;width:100%;text-align:center;"}

    | Slot | Module | Configuration Details |
    |:-:|:----:|:---------:|
    | 0 | 5069-AEN2TR | IP address: 192.168.100.3/24  |
    | 1 | 5069-IY4 | N/A |
    | 2 | 5069-OF4 | N/A |

    **Note:** In order to set the 5069-AEN2TR IP address via RSLinx Classic software, the rotary switches must be set to 999. You will need to cycle power to the module for the rotary switch change to take effect.

2. Apply power to the workstation.
3. Establish EtherNet/IP network communications:
    a. Connect the Ethernet cables as follows:
        * Computer to Port 1 of the Stratix® 2000 Ethernet switch 
        * 1756-L83 to Port 2 of the Stratix 2000 switch
        * 1756-EN2T to Port 3 of the Stratix 2000 switch
        * 5069-AEN2TR Port 1 to Port 4 of the Stratix 2000 switch
    b. Set the computer’s IP address to 192.168.100.5/24, no gateway.
    c. Assign (or verify) the IP addresses listed in Step 1, via the USB connection, using RSLinx Classic software.
    d. Configure an Ethernet devices communications driver in RSLinx Classic software.
    e. In the RSWho window, verify EtherNet/IP communications.



### Objective 1

Before beginning the exercises, complete the following setup:

1. Verify that the workstation is configured as follows:

    **Note:** "/24" indicates a subnet mask of 255.255.255.0

    
    [ControlLogix Chassis]{style="font-size:1.5em;font-weight:600;display:inline-block;width:100%;text-align:center;"}

    | Slot | Module | Configuration Details |
    |:-:|:----:|:---------:|
    |0 | 1756-OB16D | N/A |
    |1|	1756-L83 (5583)|	IP address: 192.168.100.1/24|
    |2|	1756-IB16D|	N/A|
    |3|	1756-EN2T|	IP address: 192.168.100.2/24|

    [Compact I/O Chassis]{style="font-size:1.5em;font-weight:600;display:inline-block;width:100%;text-align:center;"}

    | Slot | Module | Configuration Details |
    |:-:|:----:|:---------:|
    | 0 | 5069-AEN2TR | IP address: 192.168.100.3/24  |
    | 1 | 5069-IY4 | N/A |
    | 2 | 5069-OF4 | N/A |

    **Note:** In order to set the 5069-AEN2TR IP address via RSLinx Classic software, the rotary switches must be set to 999. You will need to cycle power to the module for the rotary switch change to take effect.

2. Apply power to the workstation.
3. Establish EtherNet/IP network communications:
    a. Connect the Ethernet cables as follows:
        * Computer to Port 1 of the Stratix® 2000 Ethernet switch 
        * 1756-L83 to Port 2 of the Stratix 2000 switch
        * 1756-EN2T to Port 3 of the Stratix 2000 switch
        * 5069-AEN2TR Port 1 to Port 4 of the Stratix 2000 switch
    b. Set the computer’s IP address to 192.168.100.5/24, no gateway.
    c. Assign (or verify) the IP addresses listed in Step 1, via the USB connection, using RSLinx Classic software.
    d. Configure an Ethernet devices communications driver in RSLinx Classic software.
    e. In the RSWho window, verify EtherNet/IP communications.

### Objective 2

Certain exercises require additional setup that should be performed by an individual experienced with the topics covered in this lab book:

| Exercise | Required Setup |
|:--|:--|
|Identifying and Connecting to Industrial Networks in a Logix5000 System |	Stop and delete all configured communications drivers in RSLinx Classic software. |

## Instructor 

### Initial

Before beginning the exercises, complete the following setup:

1. Verify that the workstation is configured as follows:

    **Note:** "/24" indicates a subnet mask of 255.255.255.0

    
    [ControlLogix Chassis]{style="font-size:1.5em;font-weight:600;display:inline-block;width:100%;text-align:center;"}

    | Slot | Module | Configuration Details |
    |:-:|:----:|:---------:|
    |0 | 1756-OB16D | N/A |
    |1|	1756-L83 (5583)|	IP address: 192.168.100.1/24|
    |2|	1756-IB16D|	N/A|
    |3|	1756-EN2T|	IP address: 192.168.100.2/24|

    [Compact I/O Chassis]{style="font-size:1.5em;font-weight:600;display:inline-block;width:100%;text-align:center;"}

    | Slot | Module | Configuration Details |
    |:-:|:----:|:---------:|
    | 0 | 5069-AEN2TR | IP address: 192.168.100.3/24  |
    | 1 | 5069-IY4 | N/A |
    | 2 | 5069-OF4 | N/A |

    **Note:** In order to set the 5069-AEN2TR IP address via RSLinx Classic software, the rotary switches must be set to 999. You will need to cycle power to the module for the rotary switch change to take effect.

2. Apply power to the workstation.
3. Establish EtherNet/IP network communications:
    a. Connect the Ethernet cables as follows:
        * Computer to Port 1 of the Stratix® 2000 Ethernet switch 
        * 1756-L83 to Port 2 of the Stratix 2000 switch
        * 1756-EN2T to Port 3 of the Stratix 2000 switch
        * 5069-AEN2TR Port 1 to Port 4 of the Stratix 2000 switch
    b. Set the computer’s IP address to 192.168.100.5/24, no gateway.
    c. Assign (or verify) the IP addresses listed in Step 1, via the USB connection, using RSLinx Classic software.
    d. Configure an Ethernet devices communications driver in RSLinx Classic software.
    e. In the RSWho window, verify EtherNet/IP communications.



### Objective 1

Before beginning the exercises, complete the following setup:

1. Verify that the workstation is configured as follows:

    **Note:** "/24" indicates a subnet mask of 255.255.255.0

    
    [ControlLogix Chassis]{style="font-size:1.5em;font-weight:600;display:inline-block;width:100%;text-align:center;"}

    | Slot | Module | Configuration Details |
    |:-:|:----:|:---------:|
    |0 | 1756-OB16D | N/A |
    |1|	1756-L83 (5583)|	IP address: 192.168.100.1/24|
    |2|	1756-IB16D|	N/A|
    |3|	1756-EN2T|	IP address: 192.168.100.2/24|

    [Compact I/O Chassis]{style="font-size:1.5em;font-weight:600;display:inline-block;width:100%;text-align:center;"}

    | Slot | Module | Configuration Details |
    |:-:|:----:|:---------:|
    | 0 | 5069-AEN2TR | IP address: 192.168.100.3/24  |
    | 1 | 5069-IY4 | N/A |
    | 2 | 5069-OF4 | N/A |

    **Note:** In order to set the 5069-AEN2TR IP address via RSLinx Classic software, the rotary switches must be set to 999. You will need to cycle power to the module for the rotary switch change to take effect.

2. Apply power to the workstation.
3. Establish EtherNet/IP network communications:
    a. Connect the Ethernet cables as follows:
        * Computer to Port 1 of the Stratix® 2000 Ethernet switch 
        * 1756-L83 to Port 2 of the Stratix 2000 switch
        * 1756-EN2T to Port 3 of the Stratix 2000 switch
        * 5069-AEN2TR Port 1 to Port 4 of the Stratix 2000 switch
    b. Set the computer’s IP address to 192.168.100.5/24, no gateway.
    c. Assign (or verify) the IP addresses listed in Step 1, via the USB connection, using RSLinx Classic software.
    d. Configure an Ethernet devices communications driver in RSLinx Classic software.
    e. In the RSWho window, verify EtherNet/IP communications.

### Objective 2

Certain exercises require additional setup that should be performed by an individual experienced with the topics covered in this lab book:

| Exercise | Required Setup |
|:--|:--|
|Identifying and Connecting to Industrial Networks in a Logix5000 System |	Stop and delete all configured communications drivers in RSLinx Classic software. |






## Frequently Asked Questions

### Question

Answer

### Question

Answer

### Question

Answer
