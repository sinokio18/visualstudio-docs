---
title: "How to: Execute a Stored Procedure that Returns No Value | Microsoft Docs"
ms.custom: ""
ms.date: 11/15/2016
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "ExecuteNonQuery method"
  - "stored procedures, creating"
  - "stored procedures, executing"
ms.assetid: 8a929e96-2cf5-43a5-b5b7-c0a5a397bbc5
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: "ghogen"
robots: noindex,nofollow
---
# How to: Execute a Stored Procedure that Returns No Value
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

To execute a stored procedure that returns no value, you can run a TableAdapter query that is configured to run a stored procedure (for example, `CustomersTableAdapter.UpdateTableData(CustomersDataTable)`).  
  
 If your application does not use TableAdapters, call the `ExecuteNonQuery` method on a command object, setting its `CommandType` property to <xref:System.Data.CommandType>. ("Command object" refers to the specific command for the [.NET Framework Data Provider](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) your application is using. For example, if your application is using the .NET Framework Data Provider for SQL Server, then the command object would be <xref:System.Data.SqlClient.SqlCommand>.)  
  
 The following examples show how to execute stored procedures that return no value from a database using either TableAdapters or command objects. For more information on querying with TableAdapters and commands, see [Fill datasets by using TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## Executing Stored Procedures that Return No Values Using a TableAdapter  
 This example shows how to create a TableAdapter query using the [Editing TableAdapters](../data-tools/editing-tableadapters.md), and then it provides information on how to declare an instance of the TableAdapter and execute the query.  
  
#### To create a stored procedure that returns no value using a TableAdapter  
  
1.  Open a dataset in the **Dataset Designer**. For more information, see [How to: Open a Dataset in the Dataset Designer](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  If you do not already have one, create a TableAdapter. For more information on creating TableAdapters, see [Create and configure TableAdapters](../data-tools/create-and-configure-tableadapters.md).  
  
3.  If you already have a query on your TableAdapter that uses a stored procedure that returns no value, skip to the next procedure, "To declare an instance of the TableAdapter and execute the query." Otherwise, continue with step 4 to create a new query that returns no value.  
  
4.  Right-click the TableAdapter that you want, and use the shortcut menu to add a query.  
  
     The **TableAdapter Query Configuration Wizard** opens.  
  
5.  Select **Use existing stored procedure**, and then click **Next**.  
  
6.  Select a stored procedure from the drop-down list, and then click **Next**.  
  
7.  Select the option to return **No value**, and then click **Next**.  
  
8.  Provide a name for the query.  
  
9. Click **Next**, or **Finish** to complete the wizard; the query is added to the TableAdapter.  
  
10. Build your project.  
  
#### To declare an instance of the TableAdapter and execute the query  
  
1.  Declare an instance of the TableAdapter that contains the query that you want to execute.  
  
    -   To create an instance using design-time tools, drag the TableAdapter that you want from the **Toolbox**. (Components in your project now appear in the **Toolbox** under a heading that matches your project name.) If the TableAdapter does not appear in the **Toolbox**, then you may need to build your project.  
  
         -or-  
  
    -   To create an instance in code, replace the following code with the names of your <xref:System.Data.DataSet> and TableAdapter.  
  
         `Dim tableAdapter As New DataSetTableAdapters.TableAdapter`  
  
        > [!NOTE]
        >  TableAdapters are not actually located inside their associated dataset classes. Each dataset has a corresponding collection of TableAdapters in its own namespace. For example, if you have a dataset named `SalesDataSet`, then there would be a `SalesDataSetTableAdapters` namespace that contains its TableAdapters.  
  
2.  Call your query as you would call any other method in code. Your query is a method on the TableAdapter. Replace the following code with the names of your TableAdapter and query. You will also need to pass in any parameters required by your query. If you are not sure if your query requires parameters, or what parameters it requires, then check IntelliSense for the required signature of the query. Depending on whether your query takes parameters or not, the code would look similar to one of the following examples:  
  
     `TableAdapter.Query()`  
  
     `TableAdapter.Query(Parameters)`  
  
     The complete code to declare an instance of the TableAdapter and execute the query should look similar to the following:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#11)]
     [!code-vb[VbRaddataFillingAndExecuting#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#11)]  
  
## Executing Stored Procedures that Return No Value Using a Command Object  
 The following example shows how to create a command and execute a stored procedure that returns no value. For information on setting and getting parameter values for a command, see [How to: Set and Get Parameters for Command Objects](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787).  
  
 This example uses the <xref:System.Data.SqlClient.SqlCommand> object and requires:  
  
-   References to the <xref:System>, <xref:System.Data>, and <xref:System.Xml> namespaces.  
  
#### To execute a stored procedure that returns no value using a DataCommand  
  
-   Add the following code to a method that you want to execute the stored procedure from. Call the `ExecuteNonQuery` method of a command to return no value (for example, <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A>).  
  
     [!code-csharp[VbRaddataFillingAndExecuting#15](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#15)]
     [!code-vb[VbRaddataFillingAndExecuting#15](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#15)]  
  
## .NET Framework Security  
 The application requires permission to access the database and execute the SQL statement.  
  
## See Also  
 <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OleDb.OleDbCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.Odbc.OdbcCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 <xref:System.Data.OracleClient.OracleCommand.ExecuteNonQuery%2A?displayProperty=fullName>   
 [How to: Create TableAdapter Queries](../data-tools/how-to-create-tableadapter-queries.md)   
 [How to: Edit TableAdapter Queries](../data-tools/how-to-edit-tableadapter-queries.md)   
 [How to: Fill a dataset with data](../data-tools/how-to-fill-a-dataset-with-data.md)   
 [Fill datasets by using TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [How to: Set and Get Parameters for Command Objects](http://msdn.microsoft.com/library/10110ecc-d2ed-4796-bb8f-74f2ecd40787)