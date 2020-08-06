---
title: Reporting Services での外部データセットの使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- DataSet objects [Reporting Services]
- data processing extensions [Reporting Services], custom DataSet objects
- custom DataSet objects [Reporting Services]
- external DataSet objects [Reporting Services]
ms.assetid: 11daa013-ec17-4760-80e3-6d84cd8d5722
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2f41ba4461386e235cefe66819318106d0e72904
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741577"
---
# <a name="using-an-external-dataset-with-reporting-services"></a><span data-ttu-id="85688-102">Reporting Services での外部データセットの使用</span><span class="sxs-lookup"><span data-stu-id="85688-102">Using an External Dataset with Reporting Services</span></span>
  <span data-ttu-id="85688-103">非接続の分散データ シナリオを [!INCLUDE[vstecado](../../../includes/vstecado-md.md)] でサポートする場合、その中心となるのが **DataSet** オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="85688-103">The **DataSet** object is central to supporting disconnected, distributed data scenarios with [!INCLUDE[vstecado](../../../includes/vstecado-md.md)].</span></span> <span data-ttu-id="85688-104">**DataSet** オブジェクトはメモリ上に保持されたデータを表し、データ ソースとは無関係に一貫したリレーショナル プログラミング モデルを提供します。</span><span class="sxs-lookup"><span data-stu-id="85688-104">The **DataSet** object is a memory-resident representation of data that provides a consistent relational programming model regardless of the data source.</span></span> <span data-ttu-id="85688-105">また、複数の異なるデータ ソースや XML データで使用でき、アプリケーションのデータをローカルに管理することも可能です。</span><span class="sxs-lookup"><span data-stu-id="85688-105">It can be used with multiple different data sources, with XML data, or to manage data local to the application.</span></span> <span data-ttu-id="85688-106">**DataSet** オブジェクトは、関連テーブル、制約、およびテーブル間のリレーションシップを含む、完全なデータセットを表します。</span><span class="sxs-lookup"><span data-stu-id="85688-106">The **DataSet** object represents a complete set of data, including related tables, constraints, and relationships among the tables.</span></span> <span data-ttu-id="85688-107">**DataSet** オブジェクトには、データを格納し、表示するための柔軟な機能が備わっています。そのため、データに関するレポートを生成するときは、多くの場合、事前にそのデータが処理され、**DataSet** オブジェクトに変換されます。</span><span class="sxs-lookup"><span data-stu-id="85688-107">Because of the **DataSet** object's versatility in storing and exposing data, your data may often be processed and transformed into a **DataSet** object before any reporting on that data occurs.</span></span>  
  
 <span data-ttu-id="85688-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のデータ処理拡張機能を使用すると、外部アプリケーションによって作成されたあらゆるカスタム **DataSet** オブジェクトを統合できます。</span><span class="sxs-lookup"><span data-stu-id="85688-108">With [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] data processing extensions, you can integrate any custom **DataSet** objects that are created by external applications.</span></span> <span data-ttu-id="85688-109">そのためには、**DataSet** オブジェクトとレポート サーバー間の橋渡し役となるカスタム データ処理拡張機能を [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] に作成してください。</span><span class="sxs-lookup"><span data-stu-id="85688-109">To accomplish this, you create a custom data processing extension in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] that acts like a bridge between your **DataSet** object and the report server.</span></span> <span data-ttu-id="85688-110">この **DataSet** オブジェクトを処理するためのコードのほとんどは、作成する **DataReader** クラスに含まれています。</span><span class="sxs-lookup"><span data-stu-id="85688-110">Most of the code for processing this **DataSet** object is contained in the **DataReader** class that you create.</span></span>  
  
 <span data-ttu-id="85688-111">**DataSet** オブジェクトをレポート サーバーに公開する場合、最初に **DataSet** オブジェクトを設定できるプロバイダー固有のメソッドを **DataReader** クラスに実装します。</span><span class="sxs-lookup"><span data-stu-id="85688-111">The first step in exposing your **DataSet** object to the report server is to implement a provider specific method in your **DataReader** class that can populate a **DataSet** object.</span></span> <span data-ttu-id="85688-112">次の例は、**DataReader** クラスのプロバイダー固有メソッドを使用して、静的データを **DataSet** オブジェクトに読み込む方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="85688-112">The following example shows how to load static data into a **DataSet** object by using a provider-specific method in your **DataReader** class.</span></span>  
  
```vb  
'Private members of the DataReader class  
Private m_dataSet As System.Data.DataSet  
Private m_currentRow As Integer  
  
'Method to create a dataset  
Friend Sub CreateDataSet()  
   ' Create a dataset.  
   Dim ds As New System.Data.DataSet("myDataSet")  
   ' Create a data table.   
   Dim dt As New System.Data.DataTable("myTable")  
   ' Create a data column and set various properties.   
   Dim dc As New System.Data.DataColumn()  
   dc.DataType = System.Type.GetType("System.Decimal")  
   dc.AllowDBNull = False  
   dc.Caption = "Number"  
   dc.ColumnName = "Number"  
   dc.DefaultValue = 25  
   ' Add the column to the table.   
   dt.Columns.Add(dc)  
   ' Add 10 rows and set values.   
   Dim dr As System.Data.DataRow  
   Dim i As Integer  
   For i = 0 To 9  
      dr = dt.NewRow()  
      dr("Number") = i + 1  
      ' Be sure to add the new row to the DataRowCollection.   
      dt.Rows.Add(dr)  
   Next i  
  
   ' Fill the dataset.  
   ds.Tables.Add(dt)  
  
   ' Use a private variable to store the dataset in your  
   ' DataReader.  
   m_dataSet = ds  
  
   ' Set the current row to -1.  
   m_currentRow = - 1  
End Sub 'CreateDataSet  
```  
  
```csharp  
// Private members of the DataReader class  
private System.Data.DataSet m_dataSet;  
private int m_currentRow;  
  
// Method to create a dataset  
internal void CreateDataSet()  
{  
   // Create a dataset.  
   System.Data.DataSet ds = new System.Data.DataSet("myDataSet");  
   // Create a data table.   
   System.Data.DataTable dt = new System.Data.DataTable("myTable");  
   // Create a data column and set various properties.   
   System.Data.DataColumn dc = new System.Data.DataColumn();   
   dc.DataType = System.Type.GetType("System.Decimal");   
   dc.AllowDBNull = false;   
   dc.Caption = "Number";   
   dc.ColumnName = "Number";   
   dc.DefaultValue = 25;   
   // Add the column to the table.   
   dt.Columns.Add(dc);   
   // Add 10 rows and set values.   
   System.Data.DataRow dr;   
   for(int i = 0; i < 10; i++)  
   {   
      dr = dt.NewRow();   
      dr["Number"] = i + 1;   
      // Be sure to add the new row to the DataRowCollection.   
      dt.Rows.Add(dr);  
   }  
  
   // Fill the dataset.  
   ds.Tables.Add(dt);  
  
   // Use a private variable to store the dataset in your  
   // DataReader.  
   m_dataSet = ds;  
  
   // Set the current row to -1.  
   m_currentRow = -1;  
}  
```  
  
```csharp  
public bool Read()  
{  
   m_currentRow++;  
   if (m_currentRow >= m_dataSet.Tables[0].Rows.Count)   
   {  
      return (false);  
   }   
   else   
   {  
      return (true);  
   }  
}  
  
public int FieldCount  
{  
   // Return the count of the number of columns, which in  
   // this case is the size of the column metadata  
   // array.  
   get { return m_dataSet.Tables[0].Columns.Count; }  
}  
  
public string GetName(int i)  
{  
   return m_dataSet.Tables[0].Columns[i].ColumnName;  
}  
  
public Type GetFieldType(int i)  
{  
   // Return the actual Type class for the data type.  
   return m_dataSet.Tables[0].Columns[i].DataType;  
}  
  
public Object GetValue(int i)  
{  
   return m_dataSet.Tables[0].Rows[m_currentRow][i];  
}  
  
public int GetOrdinal(string name)  
{  
   // Look for the ordinal of the column with the same name and return it.  
   // Returns -1 if not found.  
   return m_dataSet.Tables[0].Columns[name].Ordinal;  
}  
```  
  
 <span data-ttu-id="85688-113">データセットを作成または取得したら、**DataReader** クラスの **Read**、**GetValue**、**GetName**、**GetOrdinal**、**GetFieldType**、および **FieldCount** の各メンバーの実装に **DataSet** オブジェクトを使用できます。</span><span class="sxs-lookup"><span data-stu-id="85688-113">Once you create or retrieve your dataset, you can use the **DataSet** object in your implementations of the **Read**, **GetValue**, **GetName**, **GetOrdinal**, **GetFieldType**, and **FieldCount** members of the **DataReader** class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85688-114">参照</span><span class="sxs-lookup"><span data-stu-id="85688-114">See Also</span></span>  
 <span data-ttu-id="85688-115">[Reporting Services の拡張機能](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="85688-115">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="85688-116">[データ処理拡張機能の実装](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="85688-116">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="85688-117">Reporting Services 拡張機能ライブラリ</span><span class="sxs-lookup"><span data-stu-id="85688-117">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
