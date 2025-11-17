# JARDesigner Architecture - Overview

## What is JARDesigner?
A web-based tool for designing and simulating neurons with their electrical and chemical activities.

---

## Simple Architecture Diagram

```
┌─────────────────────────────────────────┐
│         WEB BROWSER                     │
│      (What users see and interact)      │
│                                         │
│  - Design neuron shapes                 │
│  - Configure properties                 │
│  - Run simulations                      │
│  - View 3D animations                   │
└──────────────┬──────────────────────────┘
               │
               │ Internet
               │
┌──────────────▼──────────────────────────┐
│         WEB SERVER                      │
│      (Manages requests)                 │
│                                         │
│  - Receives user configurations         │
│  - Handles file uploads                 │
│  - Sends back results                   │
└──────────────┬──────────────────────────┘
               │
               │
               │
┌──────────────▼──────────────────────────┐
│    SIMULATION ENGINE (MOOSE)            │
│      (Does the math)                    │
│                                         │
│  - Calculates electrical signals        │
│  - Simulates chemical reactions         │
│  - Generates 3D visualization data      │
└─────────────────────────────────────────┘
```

---

## Three Main Parts

### 1. Frontend (User Interface)
**What it does**: The part users interact with in their web browser

**Technology Used**:
- **React** - For building the interactive interface
- **Three.js** - For 3D visualization of neurons
- **Material-UI** - For buttons, menus, and forms

**User Actions**:
- Design neuron structure
- Set electrical properties
- Configure chemical reactions
- Start/stop simulations
- View results in 3D

---

### 2. Backend (Web Server)
**What it does**: Connects the user interface to the simulation engine

**Technology Used**:
- **Flask** (Python) - Web server
- **WebSocket** - For real-time updates during simulation

**Responsibilities**:
- Receive user's model design
- Start simulations
- Send live updates to browser
- Manage file uploads (neuron morphology files)

---

### 3. Simulation Engine (MOOSE)
**What it does**: Performs all the scientific calculations

**Technology Used**:
- **MOOSE** - Computational neuroscience framework
- **Python** - Programming language
- **NumPy** - For numerical calculations

**What it calculates**:
- Electrical signals in neurons (voltage)
- Chemical reactions (molecules, concentrations)
- Diffusion of molecules
- Interaction between electrical and chemical systems

---

## How They Work Together

**Step-by-step flow**:

1. **User designs a model** in the web browser
   - Draws or loads neuron shape
   - Sets properties (channels, reactions, etc.)

2. **Browser sends configuration** to the web server
   - JSON format (structured data)

3. **Web server starts simulation**
   - Passes configuration to MOOSE
   - Creates a dedicated process

4. **MOOSE runs the simulation**
   - Calculates voltage changes
   - Simulates chemical reactions
   - Generates 3D visualization frames

5. **Results stream back to browser**
   - Real-time updates via WebSocket
   - 3D animation plays
   - Graphs display data

---

## Key Features

 **Web-based** - No installation needed, works in browser
 **Real-time** - See simulation results as they happen
 **Interactive 3D** - Rotate and zoom the neuron model
 **Flexible** - Design simple or complex neuron networks
 **Visual** - Color-coded display of electrical and chemical activity

---

## Technology Summary

| Component | Technology | Purpose |
|-----------|-----------|---------|
| Frontend | React + Three.js | User interface & 3D graphics |
| Backend | Flask + WebSocket | Server & real-time communication |
| Simulation | MOOSE + Python | Scientific calculations |

---
