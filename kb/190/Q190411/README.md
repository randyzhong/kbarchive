---
layout: page
title: "Q190411: HOWTO: Bind a DataReport To an ADO Recordset at Run Time"
permalink: /kb/190/Q190411/
---

## Q190411: HOWTO: Bind a DataReport To an ADO Recordset at Run Time

{% raw %}

	Article: Q190411
	Product(s): Microsoft Visual Basic for Windows
	Version(s): 2.5,2.6,6.0
	Operating System(s): 
	Keyword(s): kbcode kbADO200 kbDataBinding kbVBp600 kbGrpDSVBDB kbGrpDSMDAC kbDSupport kbMDAC250 kbA
	Last Modified: 23-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual Basic Professional Edition for Windows, version 6.0 
	- Microsoft Visual Basic Enterprise Edition for Windows, version 6.0 
	- Microsoft Data Access Components versions 2.5, 2.6, 2.7 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The DataReport is a powerful tool and it's easy to build complex reports by
	dragging and dropping fields out of the DataEnvironment window. However, there
	are times when you may want to bind the DataReport directly to an ActiveX Data
	Objects (ADO) recordset rather than to the DataEnvironment. For example, you may
	have built a hierarchical query with ADO, or you may have an n-tier application
	that receives a recordset from a business object.
	
	This article helps you understand how to bind a DataReport directly to an ADO
	recordset.
	
	MORE INFORMATION
	================
	
	First, build a hierarchical query with the DataEnvironment. Next, create a
	simple DataReport that is based on your query and bound to the DataEnvironment.
	
	Use the DataEnvironment to connect to the Northwind database (NWind.mdb) that is
	included with Visual Basic by following these steps:
	
	1. Create a new Standard EXE project in Visual Basic.
	
	2. Add a DataEnvironment to that project and rename it deCustomerOrders.
	
	3. Rename the initial connection to cnNWind.
	
	4. Set the connection to use the Microsoft.Jet.OLEDB.4.0 OLE DB provider.
	
	5. Locate the Northwind database on your machine.
	
	6. Add a command to the connection and rename it Customers.
	
	7. Set the Customers command to query the Customers table.
	
	8. Add a child command to the Customers command and rename it Orders.
	
	9. Set the Orders command to query the Orders table.
	
	10. Relate the two commands on the CustomerID field on the Relation tab.
	
	11. Add a DataReport to the project and rename it rptCustomerOrders.
	
	12. Set the DataSource property of the DataReport to deCustomerOrders.
	
	13. Set the DataMember property of the DataReport to Customers.
	
	14. Right-click on the DataReport and clear "Show Report Header/Footer".
	
	15. Right-click on the DataReport and clear "Show Page Header/Footer".
	
	16. Right-click on the DataReport and select "Insert Group Header/Footer".
	
	17. Drag the CustomerID and CompanyName fields from the Customers command in the
	  DataEnvironment onto the Group Header section.
	
	18. Drag the OrderID and OrderDate fields from the Orders command in the
	  DataEnvironment onto the Detail section.
	
	19. Add a CommandButton to your form.
	
	20. Add the following code to your form:
	
	     Private Sub Command1_Click()
	         rptCustomerOrders.Show
	     End Sub
	
	21. Run the project, click on the CommandButton and you should see the report
	  with the customer and order information.
	
	22. To bind the DataReport directly to the hierarchical recordset generated by
	  the DataEnvironment, add the following code:
	
	     Private Sub Form_Load()
	         Dim intCtrl As Integer
	         With rptCustomerOrders
	             Set .DataSource = Nothing
	             .DataMember = ""
	             Set .DataSource = deCustomerOrders.rsCustomers
	             With .Sections("Section2").Controls
	                 For intCtrl = 1 To .Count
	                     If TypeOf .Item(intCtrl) Is RptTextBox Or _
	                        TypeOf .Item(intCtrl) Is RptFunction Then
	                         .Item(intCtrl).DataMember = ""
	                     End If
	                 Next intCtrl
	             End With
	             .Show
	         End With
	     End Sub
	
	NOTE: If you omit steps 13 and 14, you need to change "Section2" to "Section6" in
	the preceding code.
	
	RESULT: Run the project, and you should see the report with the customer and
	order information.
	
	The DataReport uses the DataSource and DataMember properties to find the
	top-level command on which the report is based. For example, if you have a
	hierarchical query in the DataEnvironment containing Customers, Orders, and
	Order Details information but you only want to show the Orders and Order Details
	information, then you should set the DataSource property to be the
	DataEnvironment, and the DataMember property to be the Orders command.
	
	Each field on the DataReport has two properties that allow the DataEnvironment to
	determine what information to show on the report:
	
	- DataMember
	- DataField.
	
	Use the DataMember property to select the level of the hierarchy that contains
	the information you want to display. Use the DataField property to select the
	field you want to display.
	
	For example, the CustomerID field is in both the Customers and the Orders table.
	If you want to show the CustomerID field with the rest of the customer
	information, set DataMember to Customers. If you want to show the CustomerID
	with the rest of the Order information, set DataMember to Orders.
	
	When you bind directly to a recordset object as shown in step 21, the DataSource
	property of the DataReport should be set to the recordset object and the
	DataMember property should be set to an empty string. For the fields on the
	report, the DataMember property of the top-level recordset information (customer
	information in this case) should be set to an empty string. For information
	other than that which is in the top-level recordset (Order information in this
	case), the DataMember property of the report TextBoxes should be set to the name
	of the command (Orders in this case).
	
	Additional query words: DataReport runtime
	
	======================================================================
	Keywords          : kbcode kbADO200 kbDataBinding kbVBp600 kbGrpDSVBDB kbGrpDSMDAC kbDSupport kbMDAC250 kbADO250 kbMDAC260 kbmdac270 kbado270 
	Technology        : kbVBSearch kbAudDeveloper kbZNotKeyword6 kbZNotKeyword2 kbVB600Search kbVB600 kbMDACSearch kbMDAC250 kbMDAC260 kbMDAC270
	Version           : :2.5,2.6,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
