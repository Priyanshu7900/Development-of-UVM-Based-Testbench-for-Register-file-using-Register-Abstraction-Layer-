# **Development of UVM-Based Testbench for Register File using RAL**

## **Project Overview**

This project implements the **verification of a Register File** using **SystemVerilog** and the **Universal Verification Methodology (UVM)** with **Register Abstraction Layer (RAL)**.  
The DUT is a **Register File module** supporting **read** and **write** operations.  
Verification is performed using a **reusable, layered UVM testbench** with RAL, ensuring protocol compliance, functional correctness, and coverage-driven validation.  

The testbench verifies both **direct access** and **frontdoor/backdoor register access** using the UVM RAL model, while also supporting **randomized and directed tests**.

---

## **Features**

- **UVM-based layered testbench** for modularity and reuse  
- Integration of **Register Abstraction Layer (RAL)** for register modeling  
- Supports **directed** and **constrained-random** register transactions  
- **Scoreboard** for automatic data checking  
- **Coverage collection** (code + functional) to ensure completeness  
- Verification of:
  - Register **read/write functionality**  
  - **Frontdoor and backdoor access methods**  
  - **Reset values and register predict mechanism**  

---

## **Architecture**

The project consists of the following main files and components:

- **register_file.sv** – RTL implementation of the Register File DUT.  
- **register_file_tb.sv** – Top-level testbench that instantiates the DUT and UVM environment.  
- **UVM Components** – Following standard UVM layering:
  - `reg_model.sv` – Register Abstraction Layer (RAL) model describing the DUT registers.  
  - `transaction.sv` – Defines register access transactions.  
  - `sequence.sv` – Generates test stimulus (directed + constrained random).  
  - `sequencer.sv` – Sends generated transactions to the driver.  
  - `driver.sv` – Drives DUT signals based on transactions.  
  - `monitor.sv` – Observes register operations and collects data.  
  - `scoreboard.sv` – Compares expected vs actual DUT responses.  
  - `env.sv` – UVM environment connecting all components.  
  - `test.sv` – UVM tests implementing various scenarios.  
- **verification_results/** – Contains logs, coverage reports, and waveforms (VCD/FSDB).  

---

## **Run on EDA Playground**

1. Go to [EDA Playground](https://www.edaplayground.com/)  
2. Set **Language** to *SystemVerilog* and select *UVM 1.2*  
3. In the testbench pane, include:
```systemverilog
`include "register_file.sv"
`include "register_file_tb.sv"
```
4. Select a simulator supporting UVM (e.g., **Questa** or **Riviera-PRO**)  
5. Enable waveform viewer (EPWave or GTKWave)  
6. Run simulation to verify results  

---

## **Verification Methodology**

- **UVM + RAL-based testbench** for scalable register verification  
- **Directed + constrained-random test generation**  
- **Scoreboard-based checking** for automated result validation  
- **Functional coverage** to ensure all register scenarios are tested  
- **Waveform and logs** for debugging and analysis  

---

## **Repository Structure**

```
UVM-REGISTER-FILE-VERIFICATION/
│
├── src/                     # DUT and interface files
│   └── register_file.sv     # RTL of Register File
│
├── tb/                      # UVM testbench files
│   ├── reg_model.sv
│   ├── transaction.sv
│   ├── sequence.sv
│   ├── sequencer.sv
│   ├── driver.sv
│   ├── monitor.sv
│   ├── scoreboard.sv
│   ├── env.sv
│   └── test.sv
│
├── verification_results/    # Simulation logs, waveforms, coverage
├── register_file_tb.sv      # Top-level testbench
└── README.md
```
