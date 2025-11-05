# Ground Control Station: Mission Progress Feature

## Overview
During my internship at Autonosky, I contributed to the **Ground Control Station (GCS)** by implementing a real-time mission progress feature for UAV operations. This feature provides operators with live visibility into drone mission completion across the fleet.  

**Note:** Due to proprietary restrictions, the repository does not include the actual codebase. It documents the approach, architecture decisions, and implementation strategy.

## Problem Statement
Operators required real-time visibility of each drone's mission progress. Although the backend streamed waypoint data via WebSockets, there was no frontend representation of mission status.

## My Contribution
I designed and implemented the feature, including:  
- Parsing and normalizing mission progress data from the backend  
- Creating type-safe TypeScript interfaces for mission state  
- Building React UI components showing a progress bar for each drone  
- Displaying current vs. total waypoints and last update timestamps  
- Rendering progress indicators only when a mission is active  
- Using **Lucide React** icons for clear visual feedback  

## Technical Stack
- **Frontend:** React, TypeScript  
- **State Management:** React Hooks (custom WebSocket hook)  
- **Real-time Communication:** WebSockets  
- **UI Components:** Custom progress bars  
- **Data Flow:** Event-driven architecture  

## Architecture & Data Flow

**Data flow overview:**  
Backend (Drone) → WebSocket → useWebSocket Hook → State Management → UI Components
                   drone_data   mapRawDrone       DroneData        DroneCard/Detail


**Key UI Components:**  
- **DroneCard:** Mission progress summary, progress bar, visible only during active missions  
- **DroneDetailPanel:** Expanded view showing waypoint count, progress bar, and last update  

![Mission Progress Bar Example](images/mission_progress_bar.png)  
*Example of mission progress bar in the UI*

![Data Flow Diagram](images/data_flow_diagram.png)  
*Simplified data flow from drone to UI*

## Implementation Highlights
- Type-safe mission state management in TypeScript  
- Conditional rendering for live missions only  
- Normalized timestamps and clamped percentages for edge cases  
- Efficient state updates to maintain UI responsiveness  

## Challenges & Solutions
- **Inconsistent timestamps:** Implemented normalization logic  
- **Progress exceeding 100%:** Added clamping logic  
- **Drones with no active mission:** Conditional rendering to hide progress  

## Impact
The feature improved **operator situational awareness**, providing real-time mission visibility across the drone fleet and reducing manual monitoring.
