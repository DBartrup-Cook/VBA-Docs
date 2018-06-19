---
title: Section.Properties Property (Access)
keywords: vbaac10.chm12188
f1_keywords:
- vbaac10.chm12188
ms.prod: access
api_name:
- Access.Section.Properties
ms.assetid: 012fade4-e62e-9e23-c436-82f1d6f92c89
ms.date: 06/08/2017
---


# Section.Properties Property (Access)

Returns a reference to a control's **[Properties](Access.Properties.md)** collection object. Read-only.


## Syntax

 _expression_. 'Properties'

 _expression_ A variable that represents a **Section** object.


## Remarks

The  **Properties** collection object is the collection of all the properties related to a control. You can refer to individual members of the collection by using the member object's index or a string expression that is the name of the member object. The first member object in the collection has an index value of 0 and the total number of member objects in the collection is the value of the **Properties** collection's **Count** property minus 1.


## Example

The following procedure uses the  **Properties** property to print all the properties associated with the controls on a form to the Debug window. To run this code, place a command button named cmdListProperties on a form and paste the following code into the form's Declarations section. Click the command button to print the list of properties in the Debug window.


```vb
Private Sub cmdListProperties_Click() 
 ListControlProps Me 
End Sub 
 
Public Sub ListControlProps(ByRef frm As Form) 
 Dim ctl As Control 
 Dim prp As Property 
 
 On Error GoTo props_err 
 
 For Each ctl In frm.Controls 
 Debug.Print ctl.Properties("Name") 
 For Each prp In ctl.Properties 
 Debug.Print vbTab &; prp.Name &; " = " &; prp.Value 
 Next prp 
 Next ctl 
 
props_exit: 
 Set ctl = Nothing 
 Set prp = Nothing 
Exit Sub 
 
props_err: 
 If Err = 2187 Then 
 Debug.Print vbTab &; prp.Name &; " = Only available at design time." 
 Resume Next 
 Else 
 Debug.Print vbTab &; prp.Name &; " = Error Occurred: " &; Err.Description 
 Resume Next 
 End If 
End Sub
```


## See also


[Section Object](Access.Section.md)
