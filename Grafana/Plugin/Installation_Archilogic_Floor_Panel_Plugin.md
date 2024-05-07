# **Installation: Archilogic Floor Panel Plugin**

**Goal：**
* Successfully install Archilogic Floor Panel Plugin on Grafana
* Understand how Archilogic Floor Panel Plugin works

**Main Reference：**

* [Archilogic Floor Panel Plugin - Grafana Labs](https://grafana.com/grafana/plugins/archilogic-floor-panel/?tab=relatedcontent)

## **Table of Contents**
- [**Archilogic Floor Panel Plugin**](#archilogic-floor-panel-plugin)
  - [**Table of Contents**](#table-of-contents)
  - [**Overview**](#overview)
  - [**Installation (Ubuntu 22.04)**](#installation-ubuntu-2204)

##  **Overview**

![floor-plan-screenshot-01](https://github.com/NTUST-BMW-Lab/internship/assets/87703952/3542e3c8-2798-49db-a712-ba3433293db9)

The Archilogic Floor Panel plugin for Grafana empowers users to integrate floor plans from Archilogic into Grafana dashboards, enabling the mapping of information from data sources to spatial elements and visualizing data on floor plans.

## **Installation (Ubuntu 22.04)**
1. Open terminal

2. Navigate to the /usr/share/grafana/bin/ directory in the terminal using the command below:
```
cd /usr/share/grafana/bin/
```

3. If you are already in the bin directory, you can use this command to install the plugins:
```
grafana-cli plugins install archilogic-floor-panel
```

4. Add the Panel to a Dashboard
Installed panels are available immediately in the Dashboards section in your Grafana main menu, and can be added like any other core panel in Grafana.

To see a list of installed panels, click the Plugins item in the main menu. Both core panels and installed panels will appear.