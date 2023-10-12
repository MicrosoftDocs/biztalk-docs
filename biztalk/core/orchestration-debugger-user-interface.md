---
description: "Learn more about: Orchestration Debugger User Interface"
title: "Orchestration Debugger User Interface"
ms.custom: ""
ms.date: "06/08/2017"
ms.prod: "biztalk-server"
ms.reviewer: ""
ms.suite: ""
ms.topic: "article"
f1_keywords: 
  - "bts10.hat.orchdebugger"
---
# Orchestration Debugger User Interface
In interactive (debug) mode, the Orchestration Debugger view contains three areas: Service pane, Tracked Events pane, and the Orchestration pane. In addition, in interactive mode, the Variable list and Variable properties display across the bottom of the view.  
  
> [!NOTE]
>  The Orchestration Debugger cannot display the true state of the service unless it appears in **In Breakpoint** mode and you have attached it to the instance.  
  
## Service Pane in Orchestration Debugger  
 The top pane of the Orchestration Debugger window displays the following information.  
  
|Tag|Detail|  
|---------|------------|  
|Name|Indicates the current view (Orchestration Debugger), and allows you to navigate to the Message Flow view.|  
|Instance Details|Displays the service name and the GUID that uniquely identifies the current orchestration instance.|  
|Modes|Debug mode (Replay/Live), Orchestration state (Started, Suspended, Completed, etc.), Attached (Yes or No), and Breakpoint mode (On Class or On Instance).|  
|Service Options|Drop-down list of actions that you can perform based on the state of the debugger and the instance.|  
  
 Below this information, the Orchestration Debugger has two panes—the Tracked Events pane on the left, and the Orchestration pane on the right.  
  
## Tracked Events Pane in Orchestration Debugger  
 The Tracked Events pane lists the status of every action performed in the orchestration, such as whether it started or completed. As you select each of the rows in this pane, the corresponding shape in the Orchestration pane appears highlighted in green when the shape starts and blue when the shape finishes.  
  
 The Tracked Events pane shows the following columns.  
  
|Option|Action|  
|------------|------------|  
|Action Status (left column)|Status of the particular action. An arrow indicates the action has started and a termination shape indicates it has completed.|  
|Action Name|Name of the action in the orchestration.|  
|Action Type|Type of shape that represents the action. An arrow indicates that the action has started and a termination shape indicates it has completed.|  
|Time|Time the action was performed.|  
|Date|Date the action was performed.|  
  
## Orchestration Pane in Orchestration Debugger  
 The Orchestration pane in message event and service instance tracking output in the Group Hub page is the area where the orchestration instance renders with all of its shapes. The following table shows the Context menu actions for the Orchestration pane.  
  
|Option|Action|  
|------------|------------|  
|Set Breakpoint on Class|Right-click a shape for the **Set Breakpoint on Class** option. A red dot appears on the shape indicating the breakpoint has been set.|  
|Set Breakpoint on Instance|Right-click a shape for the **Set Breakpoint on Instance** option. A red dot appears on the shape indicating the breakpoint has been set.|  
|Remove Breakpoint on Class|Right-click a shape for the **Remove Breakpoint** option. The red dot disappears from the shape indicating the breakpoint has been removed.|  
|Remove Breakpoint on Instance|Right-click a shape for the **Set Breakpoint on Instance** option. The red dot disappears from the shape indicating the breakpoint has been removed.|  
  
### Variable List and Variable Properties panes  
 These panes only appear for interactive debugging when attached to the Orchestration runtime using the **Attach** service option. These panes appear at the bottom of the screen.  
  
 The Variable List displays the Name, Value, and Type of the variable. The Value indicates if the variable is Null or, if not, then what kind of object it contains. Type is the **Assembly.Namespace.Name** of the object.  
  
 The Variable Properties pane displays properties for the variable that vary according to the type of object. For example, for ports this includes Address, Name, Scope, Type, and Value. Messages show the shortcut; for each part in the message, there is Name, Size, Properties, Type, and Value. Collections such as Context and Properties display in a pop-up. A partial display of the Value appears as a ToolTip.  
  
 The user advances through the schedule from breakpoint to breakpoint and examines the state of these variables.  
  
 The following table shows the Context menu actions for the Variable List.  
  
|Option|Action|  
|------------|------------|  
|Save Message|Right-click a Message that is non-null in the Variable List pane for the **Save Message** option. A message appears prompting you to select a directory to which to save it.|  
  
### Service Options drop-down list  
 The Service Options drop-down list shows you the valid actions based on the state of the instance and the debugger. The following table shows the available actions in the Service Options drop-down list.  
  
|Option|Action|  
|------------|------------|  
|Continue Service|Continues an orchestration instance that stopped at a breakpoint if you attached the service.|  
|Resume in Debug mode|Resumes a suspended orchestration instance in debug mode. This enables you to go into interactive mode, attach to the instance, and debug it interactively.<br /><br /> Available from the Operations views and the Orchestration Debugger. It only applies to orchestrations.|  
|Terminate Service|Terminates an orchestration instance.|  
|Attach|Attaches the service to the orchestration instance and retrieves the current state and variables|  
|Remove all Breakpoints on Class|Removes all the breakpoints in the orchestration class. Only available when not attached.|  
|Remove all Breakpoints|Removes all the breakpoints in the orchestration instance. Only available when attached.|  
|Save All Messages|Saves all the messages associated with the orchestration instance as long as you have selected to track all inbound/outbound messages.|  
|Show Action in Breakpoint|Highlights the shape as yellow for the last action executed before breaking.|  
|View Calling Orchestration|Returns the view to the orchestration instance that made the call. That is, it takes you back to the parent orchestration.<br /><br /> Only available on a called orchestration instance.|  
  
## In This Section  
  
-   [Reporting Mode in Orchestration Debugger](../core/reporting-mode-in-orchestration-debugger.md)  
  
-   [Interactive Mode in Orchestration Debugger](../core/interactive-mode-in-orchestration-debugger.md)  
  
## See Also  
 [Debugging an Orchestration](../core/debugging-an-orchestration.md)
