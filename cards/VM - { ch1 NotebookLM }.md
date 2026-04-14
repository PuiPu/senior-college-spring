1. Managing Complexity: Abstraction and Interfaces
	- **Abstraction** is the primary method for managing computer system complexity by dividing the system into levels.
	- **Levels of Abstraction** allow lower-level implementation details (like disk sectors) to be simplified into higher-level logical representations (like files).
	- **Well-defined Interfaces** decouple system components, allowing hardware and software teams to work independently as long as they satisfy the interface specifications.
	- While diversity in interfaces encourages innovation, it limits **interoperability (互通性)**, tying binary programs to specific hardware and operating systems.

2. Fundamental Computer Interfaces
	- **ISA (Instruction Set Architecture):** The boundary between hardware and software.
	    - **User ISA:** The subset of instructions visible to application programs.
	    - **System ISA:** The instructions used by supervisor software (OS) to manage hardware resources.
	- **ABI (Application Binary Interface):** Composed of the **User ISA** and **System Calls**. It provides programs access to hardware resources and OS services.
	- **API (Application Programming Interface):** Typically defined at the source code level, consisting of high-level language libraries and the User ISA. It allows software to be **ported** to different systems via recompilation.

3. Formal Description of Virtualization
	- Virtualization is formally defined as the construction of an **Isomorphism** between a guest system and a host platform.
	- The mapping is expressed by the formula: e′∘V(Si​)=V∘e(Si​).
	- **Virtualization vs. Abstraction:** Abstraction simplifies or hides details to reduce complexity, whereas virtualization maps resources without necessarily hiding details; a virtual system often provides the same level of detail as the real one.

4. Process Virtual Machines
	- A Process VM supports **individual guest applications** on a host platform.
	- The virtualizing software is placed at the **ABI interface** on top of the host OS and hardware.
	- **Key Types:**
	    - **Emulators:** Allow programs compiled for a **source ISA** to run on a different **target ISA** (e.g., FX!32).
	    - **Same-ISA Optimizers:** Used to optimize binary code on the fly where the host and guest ISAs are identical (e.g., HP Dynamo).
	    - **High-Level Language (HLL) VMs:** Achieve full **platform independence** by using a "Virtual ISA" (e.g., Java Bytecode or Microsoft .NET).

5. System Virtual Machines
	- A System VM provides a complete system environment capable of supporting a **full guest operating system**.
	- The **VMM (Virtual Machine Monitor)** manages all physical hardware resources and intercepts(攔截) privileged instructions from the guest OS.
	- **Key Types:**
	    - **Classic System VMs:** Replicate the underlying hardware to support multiple OS environments.
	    - **Hosted VMs:** Installed on top of an existing host OS (e.g., VMware Workstation).
	    - **Whole System VMs:** Virtualize the entire software stack when the guest and host have different ISAs (e.g., Virtual PC on Macintosh).
	    - **Co-designed VMs:** Hardware and VMM are designed together to improve performance or power efficiency (e.g., Transmeta Crusoe).

6. Taxonomy Summary
	- VMs are categorized first by their supported interface: **ABI (Process VM)** or **ISA (System VM)**.
	- They are further divided by whether the guest and host ISAs are the **Same** or **Different**.
	- **Process VM (Different ISA):** Dynamic Translators and HLL VMs.
	- **System VM (Different ISA):** Whole-system VMs and Co-designed VMs.