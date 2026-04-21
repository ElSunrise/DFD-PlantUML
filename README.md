# DFD-PlantUML
[ArmanAvanesyan](https://github.com/ArmanAvanesyan/DFD-PlantUML/tree/main)

DFD-PlantUML provides a structured way to visualize **Data Flow Diagrams (DFD)** using [PlantUML](http://en.plantuml.com/). It enables system designers and analysts to create **clear and concise representations of data movement** within a system, aiding in **system analysis, security assessment, and process documentation**. With an intuitive syntax, DFD-PlantUML simplifies the creation of DFDs, ensuring consistency and clarity across **various system design and data processing scenarios**.

DFD-PlantUML includes **macros** for creating Data Flow Diagrams using PlantUML.

* [Features Status Overview](#-feature-status-overview)
* [Getting Started](#getting-started)
* [Supported Diagram Types](#supported-diagram-types)
* [Data Flow Types](#data-flow-types)
* [Background](#background)
* [License](#license)

## 📌 Feature Status Overview

| **Feature Category**            | **Feature**                                        | **Status**    | **Priority** |
|---------------------------------|----------------------------------------------------|--------------|-------------|
| **✅ Core Features**            | DFD Base Elements (External Entities, Processes, Data Stores, Data Flows) | ✅ Done | 🔥 High |
|                                 | DFD Diagram Levels (Level 0, Level 1)            | ✅ Done | 🔥 High |
| **🔹 Multi-Level Diagram Support** | Extend DFD Level 2+ support (detailed process decomposition) | 🔲 To Be Done | 🔥 High |
|                                 | Enable hierarchical linking between diagrams     | 🔲 To Be Done | 🔥 High |
| **🎨 Visual Enhancements**      | Color Customization (Define custom colors for elements and flows) | 🔲 To Be Done | ⚡ Medium |
|                                 | Style Customization (Border styles, element sizes, custom shapes) | 🔲 To Be Done | ⚡ Medium |
|                                 | Layout Configurations (Automatic positioning, spacing control) | 🔲 To Be Done | ⚡ Medium |
|                                 | Theme Support (Predefined & customizable themes for visual consistency) | 🔲 To Be Done | 💡 Low |
| **🔄 Multi-Notation Support**   | Yourdon and DeMarco (1978) Notation               | 🔲 To Be Done | ⚡ Medium |
|                                 | Gane and Sarson (1979) Notation                   | 🔲 To Be Done | ⚡ Medium |
|                                 | Yourdon and Coad (1989) Notation                  | 🔲 To Be Done | ⚡ Medium |
| **📂 Different Diagram Types**  | Logical DFDs (Conceptual flow, focusing on business logic) | 🔲 To Be Done | 🔥 High |
|                                 | Physical DFDs (Implementation details like databases & interfaces) | 🔲 To Be Done | ⚡ Medium |
| **🛠 Automated Tests & Syntax Validation** | Linting & Validation Rules to detect syntax errors | 🔲 To Be Done | 🔥 High |
|                                 | Integration with CI/CD Pipelines for automated checks | 🔲 To Be Done | 🔥 High |
| **📖 Documentation & Developer Resources** | Comprehensive README (Installation, usage, examples) | 🟡 In Progress | 🔥 High |
|                                 | Scripts & CLI Tools (Easy DFD generation and conversion) | 🔲 To Be Done | ⚡ Medium |
|                                 | Contribution Guidelines (How to contribute, PR review process) | 🟡 In Progress | 🔥 High |
|                                 | Versioning & Release Plan (Semantic Versioning approach) | 🟡 In Progress | ⚡ Medium |
| **🔧 Editor & IDE Support** | Snippets for VS Code (Predefined DFD templates for quick modeling) | 🔲 To Be Done | 💡 Low |
|                                 | Live Templates for IntelliJ (Reusable DFD structures for faster development) | 🔲 To Be Done | 💡 Low |

<table>
<tr>
<td width="50%" valign="top">

### 📌 Explanation of Status Indicators
- ✅ **Done** → Implemented & released.
- 🟡 **In Progress** → Under development, expected in upcoming minor versions.
- 🔲 **To Be Done** → Planned for future releases.

</td>
<td width="50%" valign="top">

### 📌 Priority Labels Explanation
- 🔥 **High Priority** → Features required for critical functionality.
- ⚡ **Medium Priority** → Enhancements that improve usability and maintainability.
- 💡 **Low Priority** → Nice-to-have features for improved user experience.

</td>
</tr>
</table>

---

## Getting Started

At the top of your DFD PlantUML `.puml` file, you need to include the `DFD_Level_0.puml` or `DFD_Level_1.puml` file found in the `root` of this repo.

To be independent of any internet connectivity, you can also download the files found in the `root` and reference it locally with

```
!include path/to/DFD_Level_0.puml
```

Just remember to change the `!include` statements inside the top of the files.

If you want to use the always up-to-date version in this repo, use the following:

```
!includeurl https://github.com/ElSunrise/DFD-PlantUML/main/DFD_Level_1.puml
```

Now let's create a DFD Context(Level 0) diagram:

After you have included `DFD_Level_1.puml` you can use the defined macro definitions for the DFD elements: `Process`, `External_Entity`, `SubProcess`, `DataFlows`, `Flow`, `Flow_Back` and `BiFlow`

```
@startuml DFD_Elements
!includeurl https://github.com/ElSunrise/DFD-PlantUML/main/DFD_Level_1.puml
startDfd(Simple)
External(e1, "ExternalEntity1")
External(e2, "ExternalEntity2")
Process("Main Process")
    SubProcess(sp1,"1.0", "Process 1")
    SubProcess(sp2, "2.0", "Process 2")
    DataStore(d1, "DataStore")
DataFlows()
Flow(e1, sp1, "Input Data")
Flow(sp1, d1, "Output Data")
Flow_Back(sp2, d1, "Input Data")
Flow_Back(e2, sp2, "Output Data")
endDfd()
@enduml
@enduml
```



---

## Supported Diagram Types

* Context diagram (Data Flow diagram level 0)
  * Import: `!includeurl https://github.com/ElSunrise/DFD-PlantUML/main/DFD_Level_0.puml`
  * Macros: `Process`, `External_Entity`
* Data Flow diagram level 1
  * Import: `!includeurl https://github.com/ElSunrise/DFD-PlantUML/main/DFD_Level_1.puml`
  * Macros: `External_Entity`, `Process`, `SubProcess`, `DataStore`

---

## Data Flow Types

- `Flow(from, to, ?label)` (forward direction data flow)
- `BiFlow(from, to, ?label)` (bidirectional data flow)
- `Flow_Back(from, to, ?label)` (back direction data flow)

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
