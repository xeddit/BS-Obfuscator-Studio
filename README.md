<div align="center">

# BADSECTOR — BS-Obfuscator Studio

### Commercial C# / .NET Protection & Anti-Reverse-Engineering Suite

[![Platform](https://img.shields.io/badge/Platform-Windows%20(.NET%20Framework%20%7C%20.NET%206%2F7%2F8%2F9)-0a0a0a?style=for-the-badge&logo=dotnet&logoColor=c8ff00)](https://badsector.cc)
[![Layers](https://img.shields.io/badge/Protection%20Layers-24%20Active%20Modules-0a0a0a?style=for-the-badge&logo=shield&logoColor=c8ff00)](https://badsector.cc)
[![AV-Safe](https://img.shields.io/badge/AV%20Engine-Low--Entropy%20(~3.95)%20%7C%20Clean%20PE-0a0a0a?style=for-the-badge&logo=virustotal&logoColor=c8ff00)](https://badsector.cc)
[![License](https://img.shields.io/badge/License-Commercial%20Studio-c8ff00?style=for-the-badge&logoColor=000000)](https://badsector.cc)

<p align="center">
  <b>Built for developers who take software protection seriously.</b><br/>
  Lock down commercial C# / .NET applications, desktop clients, loaders, and class libraries with <b>24 layered IL &amp; runtime protection modules</b>, <b>3-Gate ARX polymorphic string vaults</b>, <b>EH-safe Control Flow Flattening</b>, <b>Single-EXE encrypted DLL packing</b>, and a <b>built-in C# Startup Code Injector</b>.
</p>

<p align="center">
  <a href="#why-bs-obfuscator">Why BS-Obfuscator</a> &bull;
  <a href="#24-layer-protection-pipeline">24-Layer Pipeline</a> &bull;
  <a href="#exclusive-studio-modules">Exclusive Modules</a> &bull;
  <a href="#cloud-presets-vault--telemetry">Cloud &amp; Vault</a> &bull;
  <a href="#quick-start">Quick Start</a> &bull;
  <a href="#licensing--access">Get License</a>
</p>

<br/>

<img src="https://i.imgur.com/K6oTiIC.png" alt="BS-Obfuscator Studio — Main Protection Pipeline" width="100%" />

</div>

---

## Why BS-Obfuscator?

Most off-the-shelf .NET obfuscators fail in one of two ways: either automated tools (`de4dot`, `dnSpy`, `ILSpy`, `MegaDumper`) unpack them in seconds, or aggressive packing spikes binary entropy and triggers false positives across antivirus scanners.

**BS-Obfuscator Studio** by **BADSECTOR** (`badsector.cc`) is engineered from the ground up to deliver maximum resistance against static and dynamic analysis while keeping commercial builds clean and stable:

- **Uncompromising Anti-Reverse-Engineering** — Combines IL-level Control Flow Flattening (safe inside `try/catch` blocks), Mixed Boolean-Arithmetic (MBA), `ldftn`/`calli` unmanaged-style pointers, Dynamic Delegate Proxies, and runtime SHA-256 Anti-Tamper sealing.
- **AV-Clean Commercial Output** — The dedicated **AV Low-Entropy &amp; CheckSum** engine drops resource entropy to `~3.95` and stamps valid PE CheckSums, designed specifically for clean commercial software distribution.
- **Zero-Breakage WinForms / Guna.UI2 / WPF Compatibility** — Form-safe renaming, an interactive **Exclusions &amp; Assembly Type Inspector**, and battle-tested official Cloud Presets keep UI designers, serialization models, and reflection intact.
- **Unified Studio Workflow** — No fragile CLI flags or manual XML configs. Drag and drop your `.exe` or `.dll`, select a preset, optionally inject custom startup C# code or bundle dependencies, and protect in milliseconds with automatic local Vault archiving.

---

## 24-Layer Protection Pipeline

Every layer in BS-Obfuscator Studio can be toggled individually or applied via one-click presets, backed by a configurable **Symbol &amp; Identifier Engine** supporting custom charsets (including Mixed Cyrillic + JP + Glitch, CleanCompiler, and configurable symbol lengths from 6 to 64 characters) plus custom assembly signature watermarks.

### 1. Renamer &amp; Resources

| Module | Description |
| :--- | :--- |
| **Classes &amp; Namespaces** | Aggressively renames types and namespaces while preserving WinForms / Form compatibility. |
| **Methods &amp; Overloads** | Overloads and renames methods using configurable custom charsets. |
| **Fields, Props &amp; Events** | Strips readable identifiers across fields, properties, and event handlers. |
| **Polymorphic Strings (3-Gate)** | Encrypts string literals inside a **3-Gate ARX stream vault** — zero plaintext strings remain in IL or memory dumps. |
| **Encrypt Resources (`.pak`)** | Compresses and encrypts embedded manifest resources to block asset extraction. |
| **Strip Debug / PDB Info** | Permanently removes debug symbols, parameter names, local variable names, and sequence points. |

### 2. Control Flow &amp; Math

| Module | Description |
| :--- | :--- |
| **Control Flow Flattening** | Rebuilds method IL into an encrypted switch-based state machine, destroying linear execution flow. |
| **Opaque Predicates (EH Safe)** | Injects mathematically complex conditions inside both standard and `try/catch` exception-handling blocks. |
| **Junk State Blocks** | Inserts unreachable decoy state blocks to exhaust static analyzers and manual reversers. |
| **Const &amp; Float Melting** | Mutates `int32`, `int64`, and `double` constants into multi-step XOR and arithmetic chains. |
| **MBA Arithmetic (`sizeof`)** | Replaces straightforward operations with Mixed Boolean-Arithmetic and `sizeof()` bitwise identities. |
| **IL Stack Confusion** | Entangles local stack registers to crash or severely distort AST-based decompilers (`dnSpy`, `ILSpy`, `dotPeek`). |

### 3. Calls &amp; Metadata

| Module | Description |
| :--- | :--- |
| **Hide Calls (Reference Proxy)** | Wraps method calls inside per-class hidden proxy methods. |
| **Calli Pointers (`ldftn`)** | Dispatches static calls through raw `ldftn` + `calli` function pointers. |
| **Dynamic Delegate Proxy** | Binds call targets dynamically into `.cctor` `MulticastDelegate` fields at runtime. |
| **Anti-De4dot &amp; Trap Types** | Injects trap interfaces, invalid metadata attributes, and structural signatures that break `de4dot` and `ILDasm`. |
| **Custom Watermark** | Embeds your own custom signature attribute directly into the protected assembly. |
| **Export Symbol Map (`.txt`)** | Generates a `_mapping.txt` file alongside builds so you can decode customer crash stack traces instantly. |

### 4. Runtime Shield &amp; Packer

| Module | Description |
| :--- | :--- |
| **Anti-Tamper (SHA-256 Seal)** | Verifies binary SHA-256 integrity inside `<Module>..cctor` — any byte patch or hex edit terminates execution. |
| **Anti-Debugger + Watchdog** | Continuously detects and blocks native/managed debuggers and reverse-engineering tools. |
| **Anti-Dump (Erase PE)** | Wipes the PE section table in RAM after load to neutralize `MegaDumper` and memory dumpers. |
| **Pack .NET DLLs** | Embeds and encrypts external `.dll` dependencies into a single standalone `.exe`. |
| **Caller Assembly Guard** | Verifies `GetCallingAssembly()` inside string decryptors to stop external reflection and invoker tools. |
| **AV Low-Entropy &amp; CheckSum** | Drops resource entropy to `~3.95` and stamps a valid PE CheckSum to minimize antivirus false positives. |

---

## Exclusive Studio Modules

BS-Obfuscator Studio integrates four specialized power-user modules directly into the main workspace.

### Single-EXE .NET DLL Packer Studio

Distribute your software as **one self-contained, encrypted executable**. Automatically detect and bundle referenced `.NET` DLLs from your target assembly folder, or drag and drop specific `.dll` dependencies directly into the queue.

<div align="center">
  <img src="https://i.imgur.com/2z7YAuV.png" alt="Single-EXE .NET DLL Packer Studio" width="90%" />
</div>

---

### Custom C# Startup Code Injector Studio

Write, format, syntax-check, and compile your own custom C# payload directly into `<Module>..cctor` **before obfuscation runs** — meaning your injected startup logic is automatically protected by the full 24-layer pipeline alongside your main application.

Includes **1-click ready-to-use templates**:
- **Single-Instance Mutex** — Prevent multiple simultaneous instances of your application.
- **Anti-VM / Sandbox Guard** — Detect and block execution inside virtualized analysis environments.
- **Trial Expiration Lock** — Enforce time-limited demo/trial builds without modifying your original source code.
- **MsgBox Gates &amp; Notices** — `Startup Notice`, `Timed Delay (5s)`, `Loop / Interval`, and `Confirm / EULA Gate`.

<div align="center">
  <img src="https://i.imgur.com/iB8Q7Bk.png" alt="Custom C# Startup Code Injector Studio" width="90%" />
</div>

---

### Exclusions &amp; Assembly Type Inspector

Protect your codebase aggressively without breaking JSON serialization, reflection, or public SDK boundaries. Inspect loaded assembly types visually with live filtering, or define wildcard rules (such as `MyNamespace.Models.*; JsonConfig; OnSerialize`).

<div align="center">
  <img src="https://i.imgur.com/VIKLRQs.png" alt="Exclusions and Assembly Type Inspector" width="90%" />
</div>

---

### Live Build Terminal &amp; Diagnostic Trace

Inspect every stage of the protection pipeline in real time through the built-in diagnostic execution console, with timestamped logs and one-click log export.

<div align="center">
  <img src="https://i.imgur.com/8QqDHFj.png" alt="Badsector Live Protection Console" width="90%" />
</div>

---

## Cloud Presets, Vault &amp; Telemetry

### Shared Cloud Presets &amp; Community Configurations

Deploy proven protection profiles in one click or publish your own verified setups to the **Badsector Cloud**:
- **WinForms + Guna.UI2 Standalone Packer** — Tuned for desktop loaders and clients with automatic adjacent `.NET` DLL packing into a single `.exe`.
- **AV-Clean Zero False-Positive Studio** — CleanCompiler naming, low-entropy resource encoding (`~3.95`), and valid PE CheckSum for clean commercial distribution.
- **Badsector Maximum Commercial v2** — Full 24-layer protection featuring 3-Gate ARX strings, Dynamic Delegate Proxy, EH-safe Control Flow Flattening, and SHA-256 Anti-Tamper.

<div align="center">
  <img src="https://i.imgur.com/iy0oHZe.png" alt="Shared Cloud Presets and Community Configurations" width="90%" />
</div>

---

### Local Protected Binaries Vault &amp; Build History

Every build is automatically archived in your personal **Vault** together with its `_mapping.txt` symbol map, SHA-256 seal, build duration, size delta, exact layer telemetry (types, methods, strings, consts, CFF blocks, proxies), and configuration backup.

<div align="center">
  <img src="https://i.imgur.com/TuobVRh.png" alt="Local Protected Binaries Vault and Build History" width="90%" />
</div>

---

### Profile, Licensing &amp; Global Telemetry

Track your personal Studio metrics alongside live global network telemetry, manage your hardware-bound license, and stay synchronized with Badsector Cloud updates.

<div align="center">
  <img src="https://i.imgur.com/K6oTiIC.png" alt="Profile, Licensing and Global Telemetry" width="90%" />
</div>

---

## Quick Start

1. **Authenticate** — Launch **BS-Obfuscator Studio** and sign in with your active **badsector.cc** license.
2. **Load Target** — Drag and drop your `.exe` or `.dll` into the Studio, or select it via **Browse...**.
3. **Select a Preset** — Choose a built-in protection preset (e.g., `Maximum (Commercial)`) or apply a verified profile from **Cloud &amp; Presets**.
4. **Configure Modules (Optional)** — Exclude specific types via the **Type Inspector**, bundle dependencies in the **Single-EXE DLL Packer**, or add pre-obfuscation startup hooks in the **C# Startup Code Injector**.
5. **Protect Assembly** — Click **PROTECT ASSEMBLY**. Your protected binary is built in milliseconds and archived automatically in your **Vault** along with its `_mapping.txt`.

---

## Frequently Asked Questions

<details>
<summary><b>Which .NET versions and application types are supported?</b></summary>
<br/>
BS-Obfuscator Studio supports <b>.NET Framework (4.x)</b> and modern <b>.NET 6 / 7 / 8 / 9</b> assemblies (<code>.exe</code> and <code>.dll</code>), including Console applications, WinForms, Guna.UI2, WPF, and class libraries.
</details>

<details>
<summary><b>How does BS-Obfuscator minimize antivirus false positives?</b></summary>
<br/>
The built-in <b>AV Low-Entropy &amp; CheckSum</b> layer keeps resource entropy around <code>~3.95</code> and stamps a valid PE CheckSum. Combined with the official <b>AV-Clean Zero False-Positive Studio</b> preset, commercial binaries remain clean across major AV engines.
</details>

<details>
<summary><b>How can I read stack traces from customer crash reports after obfuscation?</b></summary>
<br/>
Enable <b>Export Symbol Map (.txt)</b>. Every protected build stores a <code>_mapping.txt</code> file directly in your Vault so you can translate obfuscated stack traces back to original class and method names at any time.
</details>

<details>
<summary><b>What if my project relies on Reflection or JSON serialization?</b></summary>
<br/>
Use the <b>Exclusions &amp; Assembly Type Inspector</b> to uncheck specific types or enter wildcard rules (for example: <code>MyNamespace.Models.*; JsonConfig; OnSerialize</code>). Those members stay intact while the rest of your assembly receives full protection.
</details>

---

## Licensing &amp; Access

Lock down your .NET intellectual property with **BS-Obfuscator Studio**.

<div align="center">

| Included Capabilities | BS-Obfuscator Studio |
| :--- | :---: |
| Full 24-Layer Protection Pipeline (CFF, MBA, 3-Gate ARX, Anti-Tamper, Anti-Dump) | &#10003; |
| Single-EXE Encrypted .NET DLL Packer | &#10003; |
| Custom C# Startup Code Injector + Ready-to-Use Templates | &#10003; |
| Visual Assembly Type Inspector &amp; Wildcard Exclusions | &#10003; |
| Official &amp; Community Badsector Cloud Presets | &#10003; |
| Automatic Local Vault, Preset Backups &amp; Symbol Maps | &#10003; |
| Continuous Engine Updates &amp; Customer Support | &#10003; |

<br/>

[![Get BS-Obfuscator](https://img.shields.io/badge/GET%20LICENSE%20AT-BADSECTOR.CC-c8ff00?style=for-the-badge&logoColor=000000)](https://badsector.cc)

<br/>

<sub>&copy; BADSECTOR &mdash; <a href="https://badsector.cc">badsector.cc</a> &bull; BS-Obfuscator Studio</sub>

</div>
