---
title: Designing Metadata Artifacts for 3270 Applications
description: Learn how to design metadata artifacts for 3270 applications with the 3270 Design Tool.
ms.prod: "host-integration-server"
ms.topic: how-to
ms.date: "10/17/2023"

#CustomerIntent: As a programmer I need to create metadata artifacts for 3270 applications
---

# Designing Metadata Artifacts for 3270 Applications 

In this article, we will show you how to design Metadata Artifacts for 3270 Applications. Metadata artifacts are saved as Host Integration Server Definition XML (HIDX) files.

## Capture Screens

In this mode, you mark an item on each 3270 screen that uniquely identifies that screen. For example, you might specify a line of text or a more complex set of conditions, such as specific text and a non-empty field. You can either record these screens over a live connection to the host server, or import this information from an IBM Basic Mapping Support (BMS) map. The live connection uses a TN3270 emulator for connecting to the host. Each connector action must map to a single task that starts with connecting to your session and ends with disconnecting from your session.

1. If you haven't already, open the 3270 Design Tool. On the toolbar, select **Capture** so that you enter Capture mode.

1. From the **Session** menu, select **Connect**.

1. To start recording, from the **Recording** menu, select **Start Recording**. (Keyboard: Ctrl + E)

1. In the **Capture** pane, starting from the first screen in your app, step through your app for the specific task that you're recording.

1. After you finish the task, sign out from your app as you usually do.

1. From the **Session** menu, select **Disconnect**.

1. To stop recording, from the **Recording** menu, select **Stop Recording**. (Keyboard: Ctrl + Shift + E)

   After you capture the screens for a task, the designer tool shows thumbnails that represent those screens. Some notes about these thumbnails:

   * Included with your captured screens, you have a screen that's named "Empty".

     When you first connect to 
     [CICS](https://www.ibm.com/it-infrastructure/z/cics), 
     you must send the "Clear" key before you can enter the name 
     for the transaction you want to run. The screen where you 
     send the "Clear" key doesn't have any *recognition attributes*, 
     such as a screen title, which you can add by using the Screen 
     Recognition editor. To represent this screen, the thumbnails 
     includes a screen named "Empty". You can later use this screen 
     for representing the screen where you enter the transaction name.

   * By default, the name for a captured screen uses the first word on 
   the screen. If that name already exists, the design tool appends 
   the name with an underscore and a number, for example, "WBGB" and "WBGB_1".

1. To give a more meaningful name to a captured screen, follow these steps:

   1. In the **Host Screens** pane, select the screen you want to rename.

   1. In the same pane, near the bottom in the same pane, find the **Screen Name** property.

   1. Change the current screen name to a more descriptive name.

1. Now specify the fields for identifying each screen.

   With the 3270 data stream, screens don't have default identifiers, so you need to select unique text on each screen. For complex scenarios, you can specify multiple conditions, for example unique text and a field with a specific condition.

After you finish selecting the recognition fields, move to the next mode.

### Conditions for identifying repeated screens

For the connector to navigate and differentiate between screens, you usually find unique text on a screen that you can use as an identifier among the captured screens. For repeated screens, youmight need more identification methods. For example, suppose you have two screens that look the same except one screen returns a valid value, while the other screen returns an error message.

In the design tool, you can add *recognition attributes*, for example, a screen title such as "Get Account Balance", by using the Screen Recognition editor. If you have a forked path and both branches return the same screen but with different results, you need other recognition attributes.  At run time, the connector uses these attributes for determining the current branch and fork. Here are the conditions you can use:

* Specific value: This value matches the specified string at the specified location.
* NOT a specific value: This value doesn't match the specified string at the specified location.
* Empty: This field is empty.
* NOT empty: This field isn't empty.

To learn more, see the [Example navigation plan](#example-plan) later in this topic.

<a name="define-navigation"></a>

## Define navigation plans

In this mode, you define the flow or steps for navigating 
through your mainframe app's screens for your specific task. 
For example, sometimes, you might have more than one path that 
your app can take where one path produces the correct result, 
while the other path produces an error. For each screen, specify the 
keystrokes necessary for moving to the next screen, such as `CICSPROD <enter>`.

> [!TIP]
> If you're automating several tasks that use the same connect 
> and disconnect screens, the design tool provides special 
> Connect and Disconnect plan types. When you define these plans, 
> you can add them to your navigation plan's beginning and end.

### Guidelines for plan definitions

* Include all screens, starting with connecting and ending with disconnecting.

* You can create a standalone plan or use the Connect and Disconnect plans, which let you reuse a series of screens common to all your transactions.

  * The last screen in your Connect plan must be the same screen as the first screen in your navigation plan.

  * The first screen in your Disconnect plan must be same screen as the last screen in your navigation plan.

* Your captured screens might contain many repeated screens, so select and use only one instance of any repeated screens in your plan. Here are some examples of repeated screens:

  * The sign-in screen, for example, the **MSG-10** screen
  * The welcome screen for CICS
  * The "Clear" or **Empty** screen

<a name="create-plans"></a>

### Create plans

1. On the 3270 Design Tool's toolbar, select **Navigation** so that you enter Navigation mode.

1. To start your plan, in the **Navigation** pane, select **New Plan**.

1. Under **Choose New Plan Name**, enter a name for your plan. From the **Type** list, select the plan type:

   | Plan type | Description |
   |-----------|-------------|
   | **Process** | For standalone or combined plans |
   | **Connect** | For Connect plans |
   | **Disconnect** | For Disconnect plans |
   |||

1. From the **Host Screens** pane, drag the captured thumbnails to the navigation plan surface in the **Navigation** pane.

   To represent the blank screen where you enter the transaction name, use the "Empty" screen.

1. Arrange the screens in the order that describes the task that you're defining.

1. To define the flow path between screens, including forks and joins, on the design tool's toolbar, select **Flow**.

1. Choose the first screen in the flow. Drag and draw a connection to the next screen in the flow.

1. For each screen, provide the values for the **AID Key** property (Attention Identifier) and for the **Fixed Text** property, which moves the flow to the next screen.

   You might have just the AID key, or both the AID key and fixed text.

After you finish your navigation plan, you can [define methods in the next mode](#define-method).

<a name="example-plan"></a>

### Example

In this example, suppose you run a CICS transaction named "WBGB" that has these steps: 

* On the first screen, you enter a name and an account.
* On the second screen, you get the account balance.
* You exit to the "Empty" screen.
* You sign out from CICS to the "MSG-10" screen.

Also suppose that you repeat these steps, but you enter incorrect data so you can capture the screen that shows the error. Here are the screens you capture:

* MSG-10
* CICS Welcome
* Empty
* WBGB_1 (input)
* WBGB_2 (error)
* Empty_1
* MSG-10_1

Although many screens here get unique names, some screens are the same screen, for example, "MSG-10" and "Empty". For a repeated screen, use only one instance for that screen in your plan. Here are examples that show how a standalone plan, Connect plan, Disconnect plan, and a combined plan might look:

* Standalone plan

  ![Standalone navigation plan](./media/standalone-plan.png)

* Connect plan

  ![Connect plan](./media/connect-plan.png)

* Disconnect plan

  ![Disconnect plan](./media/disconnect-plan.png)

* Combined plan

  ![Combined plan](./media/combined-plan.png)

#### Example: Identify repeated screens

For the connector to navigate and differentiate screens, you usually find unique text on a screen that you can use as an identifier across the captured screens. For repeated screens, you might need more identification methods. The example plan has a fork where you can get screens that look similar. One screen returns an account balance, while the other screen returns an error message.

The design tool lets you add recognition attributes, for example, a screen title named "Get Account Balance", by using the Screen Recognition editor. In the case with similar screens, you need other attributes. At run time, the connector uses these attributes for determining the branch and fork.

* In the branch that returns valid input, which is the screen with the account balance, you can add a field that has a "not empty" condition.

* In the branch that returns with an error, you can add a field that has an "empty" condition.

<a name="define-method"></a>

## Define methods

In this mode, you define a method that's associated with your navigation plan. For each method parameter, you specify the data type, such as a string, integer, date or time, and so on. When you're done, you can test your method on the live host and confirm that the method works as expected. You then generate the metadata file, or Host Integration Designer XML (HIDX) file, which now has the method definitions to use for creating and running an action for the IBM 3270 connector.

1. On the 3270 Design Tool's toolbar, select **Methods** so that you enter Methods mode. 

1. In the **Navigation** pane, select the screen that has the input fields you want.

1. To add the first input parameter for your method, follow these steps:

   1. In the **Capture** pane, on the 3270 emulator screen, select the whole field, not just text inside the field, that you want as the first input.

      > [!TIP]
      > To display all the fields and make sure 
      > that you select the complete field, 
      > on the **View** menu, select **All Fields**.

   1. On the design tool's toolbar, select **Input Field**. 

   To add more input parameters, repeat the previous steps for each parameter.

1. To add the first output parameter for your method, follow these steps:

   1. In the **Capture** pane, on the 3270 emulator screen, select the whole field, not just text inside the field, that you want as the first output.

      > [!TIP]
      > To display all the fields and make sure 
      > that you select the complete field, 
      > on the **View** menu, select **All Fields**.

   1. On the design tool's toolbar, select **Output Field**.

   To add more output parameters, repeat the previous steps for each parameter.

1. After you add all your method's parameters, 
define these properties for each parameter:

   | Property name | Possible values | 
   |---------------|-----------------|
   | **Data Type** | Byte, Date Time, Decimal, Int, Long, Short, String |
   | **Field Fill Technique** | Parameters support these fill types, filling with blanks if necessary: <p><p>- **Type**: Enter characters sequentially into the field. <p>- **Fill**: Replace the field's contents with characters, filling with blanks if necessary. <p>- **EraseEofType**: Clear the field, and then enter characters sequentially into the field. |
   | **Format String** | Some parameter data types use a format string, which informs the 3270 connector how to convert text from the screen into a .NET data type: <p><p>- **DateTime**: The DateTime format string follows the [.NET custom date and time format strings](/dotnet/standard/base-types/custom-date-and-time-format-strings). For example, the date `06/30/2019` uses the format string `MM/dd/yyyy`. <p>- **Decimal**: The decimal format string uses the [COBOL Picture clause](https://www.ibm.com/support/knowledgecenter/ssw_ibm_i_73/rzasb/picture.htm). For example, the number `100.35` uses the format string `999V99`. |
   |||

## Save and view metadata

After you define your method, but before you test your method, 
save all the information that you defined so far to a RAP (.rap) file.
You can save to this RAP file at any time during any mode. The design 
tool also includes a sample RAP file that you can open and review by 
browsing to the design tool's installation folder at this location 
and opening the "WoodgroveBank.rap" file:

`..\Program Files\Microsoft Host Integration Server - 3270 Design Tool\SDK\WoodgroveBank.rap`

However, if you try saving changes to the sample RAP file or generating an HIDX file from the sample RAP file while the file stays in the design tool's installation folder, you might get an 
"access denied" error. By default, the design tool installs in your Program Files folder without elevated permissions. If you get an error, try one of these solutions:

* Copy the sample file to a different location.
* Run the design tool as an administrator.
* Make yourself the owner for the SDK folder.

## Test your method

1. To run your method against the live host, while still in Methods mode, press the F5 key, or from the design tool's toolbar, select **Test**.

   > [!TIP]
   > You can change modes at any time. On the **File** menu, select **Mode**, and then select the mode you want.

1. Enter your parameters' values, and select **OK**.

1. To continue to the next screen, select **Next**.

1. When you're finished, select **Done**, which shows your output parameter values.

<a name="add-metadata-integration-account"></a>

## Generate and upload HIDX file

When you're ready, generate the HIDX file so you can upload to your integration account. The 3270 
Design Tool creates the HIDX file in a new subfolder where you saved your RAP file.

1. In the 3270 Design Tool, from the **Tools** menu, select **Generate Definitions**. (Keyboard: F6)

1. Go to the folder that contains your RAP file, and open the subfolder that the tool created after generating your HIDX file. Confirm that the tool created the HIDX file.


## Related content

- [Integrate 3270 screen-driven apps on IBM mainframes with Azure by using Azure Logic Apps and IBM 3270 connector](/azure/connectors/connectors-run-3270-apps-ibm-mainframe-create-api-3270)
