---
title: CLR トリガー |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- inserted tables
- database objects [CLR integration], triggers
- common language runtime [SQL Server], triggers
- updated columns
- building database objects [CLR integration], triggers
- triggers [CLR integration]
- deleted tables
- EventData property
- SqlTriggerContext class
- transactions [CLR integration]
ms.assetid: 302a4e4a-3172-42b6-9cc0-4a971ab49c1c
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 91f12b0d97d2e2065c5bb08d175253c22dffb032
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633995"
---
# <a name="clr-triggers"></a><span data-ttu-id="465b4-102">CLR トリガー</span><span class="sxs-lookup"><span data-stu-id="465b4-102">CLR Triggers</span></span>
  <span data-ttu-id="465b4-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] と [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR (共通言語ランタイム) との統合により、任意の [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 言語を使用して CLR トリガーを作成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="465b4-103">Because of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] integration with the [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language runtime (CLR), you can use any [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] language to create CLR triggers.</span></span> <span data-ttu-id="465b4-104">ここでは、CLR 統合によって実装されたトリガー固有の情報について説明します。</span><span class="sxs-lookup"><span data-stu-id="465b4-104">This section covers information specific to triggers implemented with CLR integration.</span></span> <span data-ttu-id="465b4-105">トリガーの詳細については、「 [DDL トリガー](../../relational-databases/triggers/ddl-triggers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="465b4-105">For a complete discussion of triggers, see [DDL Triggers](../../relational-databases/triggers/ddl-triggers.md).</span></span>  
  
## <a name="what-are-triggers"></a><span data-ttu-id="465b4-106">トリガーとは</span><span class="sxs-lookup"><span data-stu-id="465b4-106">What Are Triggers?</span></span>  
 <span data-ttu-id="465b4-107">トリガーは、言語イベントが実行されると自動的に実行される特殊な種類のストアド プロシージャです。</span><span class="sxs-lookup"><span data-stu-id="465b4-107">A trigger is a special type of stored procedure that automatically runs when a language event executes.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="465b4-108">には、DML (データ操作言語) トリガーと DDL (データ定義言語) トリガーという 2 種類の一般的なトリガーがあります。</span><span class="sxs-lookup"><span data-stu-id="465b4-108">includes two general types of triggers: data manipulation language (DML) and data definition language (DDL) triggers.</span></span> <span data-ttu-id="465b4-109">DML トリガーは、`INSERT` ステートメント、`UPDATE` ステートメント、または `DELETE` ステートメントにより、指定されたテーブルやビューのデータが変更されるときに使用できます。</span><span class="sxs-lookup"><span data-stu-id="465b4-109">DML triggers can be used when `INSERT`, `UPDATE`, or `DELETE` statements modify data in a specified table or view.</span></span> <span data-ttu-id="465b4-110">DDL トリガーは、主に `CREATE`、`ALTER`、および `DROP` で始まるさまざまな DDL ステートメントに応じてストアド プロシージャを起動します。</span><span class="sxs-lookup"><span data-stu-id="465b4-110">DDL triggers fire stored procedures in response to a variety of DDL statements, which are primarily statements that begin with `CREATE`, `ALTER`, and `DROP`.</span></span> <span data-ttu-id="465b4-111">DDL トリガーは、データベース操作の監査や管理などの管理作業に使用できます。</span><span class="sxs-lookup"><span data-stu-id="465b4-111">DDL triggers can be used for administrative tasks, such as auditing and regulating database operations.</span></span>  
  
## <a name="unique-capabilities-of-clr-triggers"></a><span data-ttu-id="465b4-112">CLR トリガー独自の機能</span><span class="sxs-lookup"><span data-stu-id="465b4-112">Unique Capabilities of CLR Triggers</span></span>  
 <span data-ttu-id="465b4-113">[!INCLUDE[tsql](../../includes/tsql-md.md)] で記述されたトリガーには、トリガーを起動するビューやテーブルの列が `UPDATE(column)` 関数および `COLUMNS_UPDATED()` 関数を使用して更新されたかどうかを判断する機能があります。</span><span class="sxs-lookup"><span data-stu-id="465b4-113">Triggers written in [!INCLUDE[tsql](../../includes/tsql-md.md)] have the capability of determining which columns from the firing view or table have been updated by using the `UPDATE(column)` and `COLUMNS_UPDATED()` functions.</span></span>  
  
 <span data-ttu-id="465b4-114">CLR 言語で記述されたトリガーは、いくつかの重要な点で他の CLR 統合オブジェクトとは異なります。</span><span class="sxs-lookup"><span data-stu-id="465b4-114">Triggers written in a CLR language differ from other CLR integration objects in several significant ways.</span></span> <span data-ttu-id="465b4-115">CLR トリガーでは次のことを行えます。</span><span class="sxs-lookup"><span data-stu-id="465b4-115">CLR triggers can:</span></span>  
  
-   <span data-ttu-id="465b4-116">`INSERTED` テーブルや `DELETED` テーブル内のデータの参照</span><span class="sxs-lookup"><span data-stu-id="465b4-116">Reference data in the `INSERTED` and `DELETED` tables</span></span>  
  
-   <span data-ttu-id="465b4-117">`UPDATE` 操作の結果として変更された列の判断</span><span class="sxs-lookup"><span data-stu-id="465b4-117">Determine which columns have been modified as a result of an `UPDATE` operation</span></span>  
  
-   <span data-ttu-id="465b4-118">DDL ステートメントの実行によって影響を受けたデータベース オブジェクトに関する情報へのアクセス</span><span class="sxs-lookup"><span data-stu-id="465b4-118">Access information about database objects affected by the execution of DDL statements.</span></span>  
  
 <span data-ttu-id="465b4-119">このような機能は、クエリ言語の本質として提供されます。`SqlTriggerContext` クラスによって提供することもできます。</span><span class="sxs-lookup"><span data-stu-id="465b4-119">These capabilities are provided inherently in the query language, or by the `SqlTriggerContext` class.</span></span> <span data-ttu-id="465b4-120">CLR 統合の利点とマネージコードとの使い分けの詳細については [!INCLUDE[tsql](../../includes/tsql-md.md)] 、「 [clr 統合の概要](../../relational-databases/clr-integration/clr-integration-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="465b4-120">For information about the advantages of CLR integration and choosing between managed code and [!INCLUDE[tsql](../../includes/tsql-md.md)], see [Overview of CLR Integration](../../relational-databases/clr-integration/clr-integration-overview.md).</span></span>  
  
## <a name="using-the-sqltriggercontext-class"></a><span data-ttu-id="465b4-121">SqlTriggerContext クラスの使用</span><span class="sxs-lookup"><span data-stu-id="465b4-121">Using the SqlTriggerContext Class</span></span>  
 <span data-ttu-id="465b4-122">`SqlTriggerContext` クラスをパブリックに生成することはできません。このクラスは、CLR トリガー本体に含まれる `SqlContext.TriggerContext` プロパティにアクセスすることによってのみ取得できます。</span><span class="sxs-lookup"><span data-stu-id="465b4-122">The `SqlTriggerContext` class cannot be publicly constructed and can only be obtained by accessing the `SqlContext.TriggerContext` property within the body of a CLR trigger.</span></span> <span data-ttu-id="465b4-123">`SqlTriggerContext` クラスは、`SqlContext` プロパティを呼び出すことにより、アクティブな `SqlContext.TriggerContext` から取得できます。</span><span class="sxs-lookup"><span data-stu-id="465b4-123">The `SqlTriggerContext` class can be obtained from the active `SqlContext` by calling the `SqlContext.TriggerContext` property:</span></span>  
  
 `SqlTriggerContext myTriggerContext = SqlContext.TriggerContext;`  
  
 <span data-ttu-id="465b4-124">`SqlTriggerContext` クラスでは、トリガーに関するコンテキスト情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="465b4-124">The `SqlTriggerContext` class provides context information about the trigger.</span></span> <span data-ttu-id="465b4-125">このコンテキスト情報には、トリガーを起動した動作の種類、UPDATE 操作で変更された列、および DDL トリガーの場合はトリガー操作が記述されている XML `EventData` 構造体が含まれます。</span><span class="sxs-lookup"><span data-stu-id="465b4-125">This contextual information includes the type of action that caused the trigger to fire, which columns were modified in an UPDATE operation, and, in the case of a DDL trigger, an XML `EventData` structure which describes the triggering operation.</span></span> <span data-ttu-id="465b4-126">詳細については、「 [EVENTDATA &#40;transact-sql&#41;](/sql/t-sql/functions/eventdata-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="465b4-126">For more information, see [EVENTDATA &#40;Transact-SQL&#41;](/sql/t-sql/functions/eventdata-transact-sql).</span></span>  
  
### <a name="determining-the-trigger-action"></a><span data-ttu-id="465b4-127">トリガー動作の判断</span><span class="sxs-lookup"><span data-stu-id="465b4-127">Determining the Trigger Action</span></span>  
 <span data-ttu-id="465b4-128">`SqlTriggerContext` を取得すると、これを使用してトリガーを起動した動作の種類を判断できます。</span><span class="sxs-lookup"><span data-stu-id="465b4-128">Once you have obtained a `SqlTriggerContext`, you can use it to determine the type of action that caused the trigger to fire.</span></span> <span data-ttu-id="465b4-129">この情報は、`TriggerAction` クラスの `SqlTriggerContext` プロパティから入手できます。</span><span class="sxs-lookup"><span data-stu-id="465b4-129">This information is available through the `TriggerAction` property of the `SqlTriggerContext` class.</span></span>  
  
 <span data-ttu-id="465b4-130">DML トリガーの場合、`TriggerAction` プロパティは次のいずれかの値になります。</span><span class="sxs-lookup"><span data-stu-id="465b4-130">For DML triggers, the `TriggerAction` property can be one of the following values:</span></span>  
  
-   <span data-ttu-id="465b4-131">TriggerAction.Update (0x1)</span><span class="sxs-lookup"><span data-stu-id="465b4-131">TriggerAction.Update (0x1)</span></span>  
  
-   <span data-ttu-id="465b4-132">TriggerAction.Insert (0x2)</span><span class="sxs-lookup"><span data-stu-id="465b4-132">TriggerAction.Insert (0x2)</span></span>  
  
-   <span data-ttu-id="465b4-133">TriggerAction.Delete(0x3)</span><span class="sxs-lookup"><span data-stu-id="465b4-133">TriggerAction.Delete(0x3)</span></span>  
  
-   <span data-ttu-id="465b4-134">DDL トリガーの場合、TriggerAction の有効な値は非常に多くなります。</span><span class="sxs-lookup"><span data-stu-id="465b4-134">For DDL triggers, the list of possible TriggerAction values is considerably longer.</span></span> <span data-ttu-id="465b4-135">詳細については、.NET Framework SDK の「TriggerAction Enumeration」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="465b4-135">Please see "TriggerAction Enumeration" in the .NET Framework SDK for more information.</span></span>  
  
### <a name="using-the-inserted-and-deleted-tables"></a><span data-ttu-id="465b4-136">Inserted テーブルと Deleted テーブルの使用</span><span class="sxs-lookup"><span data-stu-id="465b4-136">Using the Inserted and Deleted Tables</span></span>  
 <span data-ttu-id="465b4-137">DML トリガーステートメントでは、 **inserted**テーブルと**deleted**テーブルの2つの特殊なテーブルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="465b4-137">Two special tables are used in DML trigger statements: the **inserted** table and the **deleted** table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="465b4-138">では、これらのテーブルを自動的に作成および管理します。</span><span class="sxs-lookup"><span data-stu-id="465b4-138">automatically creates and manages these tables.</span></span> <span data-ttu-id="465b4-139">これらの一時テーブルを使用して、あるデータ変更の影響を調べたり、DML トリガー動作の条件を設定することができます。ただし、このテーブル内のデータを直接変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="465b4-139">You can use these temporary tables to test the effects of certain data modifications and to set conditions for DML trigger actions; however, you cannot alter the data in the tables directly.</span></span>  
  
 <span data-ttu-id="465b4-140">Clr トリガーは、CLR インプロセスプロバイダーを介して**inserted**テーブルおよび**deleted**テーブルにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="465b4-140">CLR triggers can access the **inserted** and **deleted** tables through the CLR in-process provider.</span></span> <span data-ttu-id="465b4-141">この操作は、SqlContext オブジェクトから `SqlCommand` オブジェクトを取得することによって行います。</span><span class="sxs-lookup"><span data-stu-id="465b4-141">This is done by obtaining a `SqlCommand` object from the SqlContext object.</span></span> <span data-ttu-id="465b4-142">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="465b4-142">For example:</span></span>  
  
 <span data-ttu-id="465b4-143">C#</span><span class="sxs-lookup"><span data-stu-id="465b4-143">C#</span></span>  
  
```  
SqlConnection connection = new SqlConnection ("context connection = true");  
connection.Open();  
SqlCommand command = connection.CreateCommand();  
command.CommandText = "SELECT * from " + "inserted";  
```  
  
 <span data-ttu-id="465b4-144">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="465b4-144">Visual Basic</span></span>  
  
```  
Dim connection As New SqlConnection("context connection=true")  
Dim command As SqlCommand  
connection.Open()  
command = connection.CreateCommand()  
command.CommandText = "SELECT * FROM " + "inserted"  
```  
  
### <a name="determining-updated-columns"></a><span data-ttu-id="465b4-145">更新された列の判断</span><span class="sxs-lookup"><span data-stu-id="465b4-145">Determining Updated Columns</span></span>  
 <span data-ttu-id="465b4-146">`ColumnCount` オブジェクトの `SqlTriggerContext` プロパティを使用して、UPDATE 操作によって変更された列の数を判断できます。</span><span class="sxs-lookup"><span data-stu-id="465b4-146">You can determine the number of columns that were modified by an UPDATE operation by using the `ColumnCount` property of the `SqlTriggerContext` object.</span></span> <span data-ttu-id="465b4-147">入力パラメーターとして列序数を受け取る `IsUpdatedColumn` メソッドを使用すると、列が更新されたかどうかを判断できます。</span><span class="sxs-lookup"><span data-stu-id="465b4-147">You can use the `IsUpdatedColumn` method, which takes the column ordinal as an input parameter, to determine whether the column was updated.</span></span> <span data-ttu-id="465b4-148">値 `True` は、列が更新されたことを示します。</span><span class="sxs-lookup"><span data-stu-id="465b4-148">A `True` value indicates that the column has been updated.</span></span>  
  
 <span data-ttu-id="465b4-149">たとえば、後半で示す EmailAudit トリガーからの次のコードでは、更新されたすべての列が一覧されます。</span><span class="sxs-lookup"><span data-stu-id="465b4-149">For example, this code snippet (from the EmailAudit trigger later in this topic) lists all of the columns updated:</span></span>  
  
 <span data-ttu-id="465b4-150">C#</span><span class="sxs-lookup"><span data-stu-id="465b4-150">C#</span></span>  
  
```  
reader = command.ExecuteReader();  
reader.Read();  
for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
{  
   pipe.Send("Updated column "  
      + reader.GetName(columnNumber) + "? "  
   + triggContext.IsUpdatedColumn(columnNumber).ToString());  
 }  
  
 reader.Close();  
```  
  
 <span data-ttu-id="465b4-151">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="465b4-151">Visual Basic</span></span>  
  
```  
reader = command.ExecuteReader()  
reader.Read()  
Dim columnNumber As Integer  
  
For columnNumber=0 To triggContext.ColumnCount-1  
  
   pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
   "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
Next  
  
reader.Close()  
```  
  
### <a name="accessing-eventdata-for-clr-ddl-triggers"></a><span data-ttu-id="465b4-152">CLR DDL トリガーの EventData へのアクセス</span><span class="sxs-lookup"><span data-stu-id="465b4-152">Accessing EventData for CLR DDL Triggers</span></span>  
 <span data-ttu-id="465b4-153">DDL トリガーは標準的なトリガーと同様、イベントに応じてストアド プロシージャを起動します。</span><span class="sxs-lookup"><span data-stu-id="465b4-153">DDL triggers, like regular triggers, fire stored procedures in response to an event.</span></span> <span data-ttu-id="465b4-154">ただし、DML トリガーとは異なり、テーブルやビューでの UPDATE、INSERT、または DELETE ステートメントに応じて DDL トリガーが起動されることはありません。</span><span class="sxs-lookup"><span data-stu-id="465b4-154">But unlike DML triggers, they do not fire in response to UPDATE, INSERT, or DELETE statements on a table or view.</span></span> <span data-ttu-id="465b4-155">代わりに、DDL トリガーは、さまざまな DDL ステートメントに応じて起動されます。このような DDL ステートメントは、主に CREATE、ALTER、DROP で始まるステートメントです。</span><span class="sxs-lookup"><span data-stu-id="465b4-155">Instead, they fire in response to a variety of DDL statements, which are primarily statements that begin with CREATE, ALTER, and DROP.</span></span> <span data-ttu-id="465b4-156">DDL トリガーは、データベース操作やスキーマの変更の監査や管理などの管理作業に使用できます。</span><span class="sxs-lookup"><span data-stu-id="465b4-156">DDL triggers can be used for administrative tasks, such as auditing and monitoring of database operations and schema changes.</span></span>  
  
 <span data-ttu-id="465b4-157">DDL トリガーを起動するイベントに関する情報は、`EventData` クラスの `SqlTriggerContext` プロパティで入手できます。</span><span class="sxs-lookup"><span data-stu-id="465b4-157">Information about an event that fires a DDL trigger is available in the `EventData` property of the `SqlTriggerContext` class.</span></span> <span data-ttu-id="465b4-158">このプロパティには、`xml` 値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="465b4-158">This property contains an `xml` value.</span></span> <span data-ttu-id="465b4-159">xml スキーマには、次の項目に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="465b4-159">The xml schema includes information about:</span></span>  
  
-   <span data-ttu-id="465b4-160">イベントの時刻。</span><span class="sxs-lookup"><span data-stu-id="465b4-160">The time of the event.</span></span>  
  
-   <span data-ttu-id="465b4-161">トリガーが実行されている間の接続のシステム プロセス ID (SPID)。</span><span class="sxs-lookup"><span data-stu-id="465b4-161">The System Process ID (SPID) of the connection during which the trigger executed.</span></span>  
  
-   <span data-ttu-id="465b4-162">トリガーを起動したイベントの種類。</span><span class="sxs-lookup"><span data-stu-id="465b4-162">The type of event that fired the trigger.</span></span>  
  
 <span data-ttu-id="465b4-163">イベントの種類に応じて、イベントが発生したデータベース、イベントが発生したオブジェクト、イベントの [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドなどの追加情報がスキーマに含まれます。</span><span class="sxs-lookup"><span data-stu-id="465b4-163">Then, depending on the event type, the schema includes additional information, such as the database in which the event occurred, the object against which the event occurred, and the [!INCLUDE[tsql](../../includes/tsql-md.md)] command of the event.</span></span>  
  
 <span data-ttu-id="465b4-164">次の例では、DDL トリガーは `EventData` プロパティをそのまま返します。</span><span class="sxs-lookup"><span data-stu-id="465b4-164">In the following example, the following DDL trigger returns the raw `EventData` property.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="465b4-165">`SqlPipe` オブジェクトを使用して結果やメッセージを送信する例は、説明をわかりやすくするために記載しているものです。通常、CLR トリガーをプログラミングするときに、この処理を実稼働コードに実装することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="465b4-165">Sending results and messages through the `SqlPipe` object is shown here for illustrative purposes only and is generally discouraged for production code when programming CLR triggers.</span></span> <span data-ttu-id="465b4-166">予期しない追加データが返され、アプリケーション エラーの原因となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="465b4-166">Additional data returned may be unexpected and lead to application errors.</span></span>  
  
 <span data-ttu-id="465b4-167">C#</span><span class="sxs-lookup"><span data-stu-id="465b4-167">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   public static void DropTableTrigger()  
   {  
       SqlTriggerContext triggContext = SqlContext.TriggerContext;             
  
       switch(triggContext.TriggerAction)  
       {  
           case TriggerAction.DropTable:  
           SqlContext.Pipe.Send("Table dropped! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
  
           default:  
           SqlContext.Pipe.Send("Something happened! Here's the EventData:");  
           SqlContext.Pipe.Send(triggContext.EventData.Value);  
           break;  
       }  
   }  
}  
```  
  
 <span data-ttu-id="465b4-168">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="465b4-168">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    Public Shared Sub DropTableTrigger()  
        Dim triggContext As SqlTriggerContext  
        triggContext = SqlContext.TriggerContext  
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.DropTable  
              SqlContext.Pipe.Send("Table dropped! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
           Case Else  
              SqlContext.Pipe.Send("Something else happened! Here's the EventData:")  
              SqlContext.Pipe.Send(triggContext.EventData.Value)  
  
        End Select  
    End Sub  
End Class     
```  
  
 <span data-ttu-id="465b4-169">次のサンプル出力は、`EventData` イベントによって DDL トリガーを起動された後の `CREATE TABLE` プロパティの値です。</span><span class="sxs-lookup"><span data-stu-id="465b4-169">The following sample output is the `EventData` property value after a DDL trigger fired by a `CREATE TABLE` event:</span></span>  
  
 `<EVENT_INSTANCE><PostTime>2004-04-16T21:17:16.160</PostTime><SPID>58</SPID><EventType>CREATE_TABLE</EventType><ServerName>MACHINENAME</ServerName><LoginName>MYDOMAIN\myname</LoginName><UserName>MYDOMAIN\myname</UserName><DatabaseName>AdventureWorks</DatabaseName><SchemaName>dbo</SchemaName><ObjectName>UserName</ObjectName><ObjectType>TABLE</ObjectType><TSQLCommand><SetOptions ANSI_NULLS="ON" ANSI_NULL_DEFAULT="ON" ANSI_PADDING="ON" QUOTED_IDENTIFIER="ON" ENCRYPTED="FALSE" /><CommandText>create table dbo.UserName  
(  
 UserName varchar(50),  
 RealName varchar(50)  
)  
</CommandText></TSQLCommand></EVENT_INSTANCE>`  
  
 <span data-ttu-id="465b4-170">クエリでは、`SqlTriggerContext` クラスからアクセスできる情報のほか、インプロセスで実行されるコマンドのテキスト内で `COLUMNS_UPDATED`、COLUMNS_INSERTED、および COLUMNS_DELETED を引き続き参照できます。</span><span class="sxs-lookup"><span data-stu-id="465b4-170">In addition to the information accessible through the `SqlTriggerContext` class, queries can still refer to `COLUMNS_UPDATED` and inserted/deleted within the text of a command executed in-process.</span></span>  
  
## <a name="sample-clr-trigger"></a><span data-ttu-id="465b4-171">サンプル CLR トリガー</span><span class="sxs-lookup"><span data-stu-id="465b4-171">Sample CLR Trigger</span></span>  
 <span data-ttu-id="465b4-172">この例では、ユーザーに必要な任意の ID を選択させ、具体的に ID として電子メール アドレスを入力したユーザーを知りたい場合のシナリオについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="465b4-172">In this example, consider the scenario in which you let the user choose any ID they want, but you want to know the users that specifically entered an e-mail address as an ID.</span></span> <span data-ttu-id="465b4-173">次のトリガーは、その情報を検出し、監査テーブルにログを記録します。</span><span class="sxs-lookup"><span data-stu-id="465b4-173">The following trigger would detect that information and log it to an audit table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="465b4-174">`SqlPipe` オブジェクトを使用して結果とメッセージを送信する例は、説明をわかりやすくするために記載しているものです。通常、この処理を実稼働コードに実装することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="465b4-174">Sending results and messages through the `SqlPipe` object is shown here for illustrative purposes only and is generally discouraged for production code.</span></span> <span data-ttu-id="465b4-175">これは、予期しない追加データが返されることで、アプリケーション エラーが発生する可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="465b4-175">Additional data returned may be unexpected and lead to application errors</span></span>  
  
```csharp  
using System;  
using System.Data;  
using System.Data.Sql;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using System.Xml;  
using System.Text.RegularExpressions;  
  
public class CLRTriggers  
{  
   [SqlTrigger(Name = @"EmailAudit", Target = "[dbo].[Users]", Event = "FOR INSERT, UPDATE, DELETE")]  
   public static void EmailAudit()  
   {  
      string userName;  
      string realName;  
      SqlCommand command;  
      SqlTriggerContext triggContext = SqlContext.TriggerContext;  
      SqlPipe pipe = SqlContext.Pipe;  
      SqlDataReader reader;  
  
      switch (triggContext.TriggerAction)  
      {  
         case TriggerAction.Insert:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
            reader.Close();  
  
            if (IsValidEMailAddress(userName))  
            {  
               command = new SqlCommand(  
                  @"INSERT [dbo].[UserNameAudit] VALUES ('"  
                  + userName + @"', '" + realName + @"');",  
                  connection);  
               pipe.Send(command.CommandText);  
               command.ExecuteNonQuery();  
               pipe.Send("You inserted: " + userName);  
            }  
         }  
  
         break;  
  
         case TriggerAction.Update:  
         // Retrieve the connection that the trigger is using  
         using (SqlConnection connection  
            = new SqlConnection(@"context connection=true"))  
         {  
            connection.Open();  
            command = new SqlCommand(@"SELECT * FROM INSERTED;",  
               connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
  
            userName = (string)reader[0];  
            realName = (string)reader[1];  
  
            pipe.Send(@"You updated: '" + userName + @"' - '"  
               + realName + @"'");  
  
            for (int columnNumber = 0; columnNumber < triggContext.ColumnCount; columnNumber++)  
            {  
               pipe.Send("Updated column "  
                  + reader.GetName(columnNumber) + "? "  
                  + triggContext.IsUpdatedColumn(columnNumber).ToString());  
            }  
  
            reader.Close();  
         }  
  
         break;  
  
         case TriggerAction.Delete:  
            using (SqlConnection connection  
               = new SqlConnection(@"context connection=true"))  
               {  
                  connection.Open();  
                  command = new SqlCommand(@"SELECT * FROM DELETED;",  
                     connection);  
                  reader = command.ExecuteReader();  
  
                  if (reader.HasRows)  
                  {  
                     pipe.Send(@"You deleted the following rows:");  
                     while (reader.Read())  
                     {  
                        pipe.Send(@"'" + reader.GetString(0)  
                        + @"', '" + reader.GetString(1) + @"'");  
                     }  
  
                     reader.Close();  
  
                     //alternately, to just send a tabular resultset back:  
                     //pipe.ExecuteAndSend(command);  
                  }  
                  else  
                  {  
                     pipe.Send("No rows affected.");  
                  }  
               }  
  
               break;  
            }  
        }  
  
     public static bool IsValidEMailAddress(string email)  
     {  
         return Regex.IsMatch(email, @"^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$");  
     }  
}  
```  
  
 <span data-ttu-id="465b4-176">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="465b4-176">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
Imports System.Text.RegularExpressions  
  
'The Partial modifier is only required on one class definition per project.  
Partial Public Class CLRTriggers   
  
    <SqlTrigger(Name:="EmailAudit", Target:="[dbo].[Users]", Event:="FOR INSERT, UPDATE, DELETE")> _  
    Public Shared Sub EmailAudit()  
        Dim userName As String  
        Dim realName As String  
        Dim command As SqlCommand  
        Dim triggContext As SqlTriggerContext  
        Dim pipe As SqlPipe  
        Dim reader As SqlDataReader    
  
        triggContext = SqlContext.TriggerContext      
        pipe = SqlContext.Pipe    
  
        Select Case triggContext.TriggerAction  
           Case TriggerAction.Insert  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 reader.Close()  
  
                 If IsValidEmailAddress(userName) Then  
                     command = New SqlCommand("INSERT [dbo].[UserNameAudit] VALUES ('" & _  
                       userName & "', '" & realName & "');", connection)  
  
                    pipe.Send(command.CommandText)  
                    command.ExecuteNonQuery()  
                    pipe.Send("You inserted: " & userName)  
  
                 End If  
              End Using  
  
           Case TriggerAction.Update  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM INSERTED;", connection)  
  
                 reader = command.ExecuteReader()  
                 reader.Read()  
  
                 userName = CType(reader(0), String)  
                 realName = CType(reader(1), String)  
  
                 pipe.Send("You updated: " & userName & " - " & realName)  
  
                 Dim columnNumber As Integer  
  
                 For columnNumber=0 To triggContext.ColumnCount-1  
  
                    pipe.Send("Updated column " & reader.GetName(columnNumber) & _  
                      "? " & triggContext.IsUpdatedColumn(columnNumber).ToString() )  
  
                 Next  
  
                 reader.Close()  
              End Using  
  
           Case TriggerAction.Delete  
              Using connection As New SqlConnection("context connection=true")  
                 connection.Open()  
                 command = new SqlCommand("SELECT * FROM DELETED;", connection)  
  
                 reader = command.ExecuteReader()  
  
                 If reader.HasRows Then  
                    pipe.Send("You deleted the following rows:")  
  
                    While reader.Read()  
  
                       pipe.Send( reader.GetString(0) & ", " & reader.GetString(1) )  
  
                    End While   
  
                    reader.Close()  
  
                    ' Alternately, just send a tabular resultset back:  
                    ' pipe.ExecuteAndSend(command)  
  
                 Else  
                   pipe.Send("No rows affected.")  
                 End If  
  
              End Using   
        End Select  
    End Sub  
  
    Public Shared Function IsValidEMailAddress(emailAddress As String) As Boolean  
  
       return Regex.IsMatch(emailAddress, "^([\w-]+\.)*?[\w-]+@[\w-]+\.([\w-]+\.)*?[\w]+$")  
    End Function      
End Class  
```  
  
 <span data-ttu-id="465b4-177">次の定義では 2 つのテーブルが存在することを前提にしています。</span><span class="sxs-lookup"><span data-stu-id="465b4-177">Assuming two tables exist with the following definitions:</span></span>  
  
```  
CREATE TABLE Users  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
);  
GO CREATE TABLE UserNameAudit  
(  
    UserName nvarchar(200) NOT NULL,  
    RealName nvarchar(200) NOT NULL  
)  
```  
  
 <span data-ttu-id="465b4-178">[!INCLUDE[tsql](../../includes/tsql-md.md)]でトリガーを作成するステートメント [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は次のとおりです。また、 **sqlclrtest**アセンブリが現在のデータベースに既に登録されていることを前提としてい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="465b4-178">The [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that creates the trigger in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is as follows, and assumes assembly **SQLCLRTest** is already registered in the current [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
```  
CREATE TRIGGER EmailAudit  
ON Users  
FOR INSERT, UPDATE, DELETE  
AS  
EXTERNAL NAME SQLCLRTest.CLRTriggers.EmailAudit  
```  
  
## <a name="validating-and-canceling-invalid-transactions"></a><span data-ttu-id="465b4-179">無効なトランザクションの検証およびキャンセル</span><span class="sxs-lookup"><span data-stu-id="465b4-179">Validating and Canceling Invalid Transactions</span></span>  
 <span data-ttu-id="465b4-180">無効な INSERT、UPDATE、または DELETE トランザクションの検証および取り消しを行う場合や、データベース スキーマへの変更を回避する場合には、トリガーを使用するのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="465b4-180">Using triggers to validate and cancel invalid INSERT, UPDATE, or DELETE transactions or to prevent changes to your database schema is common.</span></span> <span data-ttu-id="465b4-181">これは、検証ロジックをトリガーに組み込み、アクションが検証条件に合わない場合は現在のトランザクションをロールバックすることにより、行うことができます。</span><span class="sxs-lookup"><span data-stu-id="465b4-181">This can be accomplished by incorporating validation logic into your trigger and then rolling back the current transaction if the action does not meet the validation criteria.</span></span>  
  
 <span data-ttu-id="465b4-182">トリガー内で呼び出されると、`Transaction.Rollback` メソッドまたはコマンド テキスト "TRANSACTION ROLLBACK" の SqlCommand は、不明確なエラー メッセージを発生して例外をスローし、これを try/catch ブロックにラップする必要が生じます。</span><span class="sxs-lookup"><span data-stu-id="465b4-182">When called within a trigger, the `Transaction.Rollback` method or a SqlCommand with the command text "TRANSACTION ROLLBACK" throws an exception with an ambiguous error message and must be wrapped in a try/catch block.</span></span> <span data-ttu-id="465b4-183">次のようなエラーメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="465b4-183">The error message you see is similar to the following:</span></span>  
  
```  
Msg 6549, Level 16, State 1, Procedure trig_InsertValidator, Line 0  
A .NET Framework error occurred during execution of user defined routine or aggregate 'trig_InsertValidator':   
System.Data.SqlClient.SqlException: Transaction is not allowed to roll back inside a user defined routine, trigger or aggregate because the transaction is not started in that CLR level. Change application logic to enforce strict transaction nesting... User transaction, if any, will be rolled back.  
```  
  
 <span data-ttu-id="465b4-184">この例外は想定されるものであり、コードの実行を継続するには try/catch ブロックが必要です。</span><span class="sxs-lookup"><span data-stu-id="465b4-184">This exception is expected and the try/catch block is necessary for code execution to continue.</span></span> <span data-ttu-id="465b4-185">トリガー コードが実行を終了すると、別の例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="465b4-185">When the trigger code finishes execution, another exception is raised</span></span>  
  
```  
Msg 3991, Level 16, State 1, Procedure trig_InsertValidator, Line 1   
The context transaction which was active before entering user defined routine, trigger or aggregate "trig_InsertValidator" has been ended inside of it, which is not allowed. Change application logic to enforce strict transaction nesting.  
The statement has been terminated.  
```  
  
 <span data-ttu-id="465b4-186">この例外も想定されており、実行を続行するには、トリガーを起動するアクションを実行するステートメントを囲む try/catch ブロック [!INCLUDE[tsql](../../includes/tsql-md.md)] が必要です。</span><span class="sxs-lookup"><span data-stu-id="465b4-186">This exception is also expected, and a try/catch block around the [!INCLUDE[tsql](../../includes/tsql-md.md)] statement that performs the action that fires the trigger is necessary so that execution can continue.</span></span> <span data-ttu-id="465b4-187">この 2 つの例外がスローされても、トランザクションはロールバックされ、変更はテーブルにコミットされません。</span><span class="sxs-lookup"><span data-stu-id="465b4-187">Despite the two exceptions thrown, the transaction is rolled back and the changes are not committed to the table.</span></span> <span data-ttu-id="465b4-188">CLR トリガーと [!INCLUDE[tsql](../../includes/tsql-md.md)] トリガーの主な違いは、トランザクションがロールバックされた後、[!INCLUDE[tsql](../../includes/tsql-md.md)] トリガーは、動作を継続してさらに実行を行えるということです。</span><span class="sxs-lookup"><span data-stu-id="465b4-188">A major difference between CLR triggers and [!INCLUDE[tsql](../../includes/tsql-md.md)] triggers is that [!INCLUDE[tsql](../../includes/tsql-md.md)] triggers can continue to perform more work after the transaction is rolled back.</span></span>  
  
### <a name="example"></a><span data-ttu-id="465b4-189">例</span><span class="sxs-lookup"><span data-stu-id="465b4-189">Example</span></span>  
 <span data-ttu-id="465b4-190">次のトリガーでは、テーブルで INSERT ステートメントの簡単な検証を実行します。</span><span class="sxs-lookup"><span data-stu-id="465b4-190">The following trigger performs simple validation of INSERT statements on a table.</span></span> <span data-ttu-id="465b4-191">挿入された整数値が 1 に等しい場合、トランザクションはロールバックされ、値はテーブルに挿入されません。</span><span class="sxs-lookup"><span data-stu-id="465b4-191">If the inserted integer value is equal to one, the transaction is rolled back and the value is not inserted into the table.</span></span> <span data-ttu-id="465b4-192">その他のすべての整数値はテーブルに挿入されます。</span><span class="sxs-lookup"><span data-stu-id="465b4-192">All other integer values are inserted into the table.</span></span> <span data-ttu-id="465b4-193">`Transaction.Rollback` メソッドの前後の try/catch ブロックに注意してください。</span><span class="sxs-lookup"><span data-stu-id="465b4-193">Note the try/catch block around the `Transaction.Rollback` method.</span></span> <span data-ttu-id="465b4-194">[!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトは、テスト テーブル、アセンブリ、およびマネージド ストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="465b4-194">The [!INCLUDE[tsql](../../includes/tsql-md.md)] script creates a test table, assembly, and managed stored procedure.</span></span> <span data-ttu-id="465b4-195">トリガーにより実行が終了されたときにスローされる例外をキャッチするため、2 つの INSERT ステートメントが try/catch ブロックにラップされることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="465b4-195">Note that the two INSERT statements are wrapped in a try/catch block so that the exception thrown when the trigger finishes execution is caught.</span></span>  
  
 <span data-ttu-id="465b4-196">C#</span><span class="sxs-lookup"><span data-stu-id="465b4-196">C#</span></span>  
  
```  
using System;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;  
using System.Transactions;  
  
public partial class Triggers  
{  
    // Enter existing table or view for the target and uncomment the attribute line  
    // [Microsoft.SqlServer.Server.SqlTrigger (Name="trig_InsertValidator", Target="Table1", Event="FOR INSERT")]  
    public static void trig_InsertValidator()  
    {  
        using (SqlConnection connection = new SqlConnection(@"context connection=true"))  
        {  
            SqlCommand command;  
            SqlDataReader reader;  
            int value;  
  
            // Open the connection.  
            connection.Open();  
  
            // Get the inserted value.  
            command = new SqlCommand(@"SELECT * FROM INSERTED", connection);  
            reader = command.ExecuteReader();  
            reader.Read();  
            value = (int)reader[0];  
            reader.Close();  
  
            // Rollback the transaction if a value of 1 was inserted.  
            if (1 == value)  
            {  
                try  
                {  
                    // Get the current transaction and roll it back.  
                    Transaction trans = Transaction.Current;  
                    trans.Rollback();                      
                }  
                catch (SqlException ex)  
                {  
                    // Catch the expected exception.                      
                }  
            }  
            else  
            {  
                // Perform other actions here.  
            }  
  
            // Close the connection.  
            connection.Close();              
        }  
    }  
}  
```  
  
 <span data-ttu-id="465b4-197">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="465b4-197">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Transactions  
  
Partial Public Class Triggers  
' Enter existing table or view for the target and uncomment the attribute line  
' <Microsoft.SqlServer.Server.SqlTrigger(Name:="trig_InsertValidator", Target:="Table1", Event:="FOR INSERT")> _  
Public Shared Sub  trig_InsertValidator ()  
    Using connection As New SqlConnection("context connection=true")  
  
        Dim command As SqlCommand  
        Dim reader As SqlDataReader  
        Dim value As Integer  
  
        ' Open the connection.  
        connection.Open()  
  
        ' Get the inserted value.  
        command = New SqlCommand("SELECT * FROM INSERTED", connection)  
        reader = command.ExecuteReader()  
        reader.Read()  
        value = CType(reader(0), Integer)  
        reader.Close()  
  
        ' Rollback the transaction if a value of 1 was inserted.  
        If value = 1 Then  
  
            Try  
                ' Get the current transaction and roll it back.  
                Dim trans As Transaction  
                trans = Transaction.Current  
                trans.Rollback()  
  
            Catch ex As SqlException  
  
                ' Catch the exception.                      
            End Try  
        Else  
  
            ' Perform other actions here.  
        End If  
  
        ' Close the connection.  
        connection.Close()  
    End Using  
End Sub  
End Class  
```  
  
 <span data-ttu-id="465b4-198">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="465b4-198">Transact-SQL</span></span>  
  
```  
-- Create the test table, assembly, and trigger.  
CREATE TABLE Table1(c1 int);  
go  
  
CREATE ASSEMBLY ValidationTriggers from 'E:\programming\ ValidationTriggers.dll';  
go  
  
CREATE TRIGGER trig_InsertValidator  
ON Table1  
FOR INSERT  
AS EXTERNAL NAME ValidationTriggers.Triggers.trig_InsertValidator;  
go  
  
-- Use a Try/Catch block to catch the expected exception  
BEGIN TRY  
   INSERT INTO Table1 VALUES(42)  
   INSERT INTO Table1 VALUES(1)  
END TRY  
BEGIN CATCH  
  SELECT ERROR_NUMBER() AS ErrorNum, ERROR_MESSAGE() AS ErrorMessage  
END CATCH;  
  
-- Clean up.  
DROP TRIGGER trig_InsertValidator;  
DROP ASSEMBLY ValidationTriggers;  
DROP TABLE Table1;  
```  
  
## <a name="see-also"></a><span data-ttu-id="465b4-199">参照</span><span class="sxs-lookup"><span data-stu-id="465b4-199">See Also</span></span>  
 <span data-ttu-id="465b4-200">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="465b4-200">[CREATE TRIGGER &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-trigger-transact-sql) </span></span>  
 <span data-ttu-id="465b4-201">[DML トリガー](../../relational-databases/triggers/dml-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="465b4-201">[DML Triggers](../../relational-databases/triggers/dml-triggers.md) </span></span>  
 <span data-ttu-id="465b4-202">[DDL トリガー](../../relational-databases/triggers/ddl-triggers.md) </span><span class="sxs-lookup"><span data-stu-id="465b4-202">[DDL Triggers](../../relational-databases/triggers/ddl-triggers.md) </span></span>  
 <span data-ttu-id="465b4-203">[TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="465b4-203">[TRY...CATCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/try-catch-transact-sql) </span></span>  
 <span data-ttu-id="465b4-204">[CLR&#41; 統合 &#40;共通言語ランタイムを使用したデータベースオブジェクトの構築](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md) </span><span class="sxs-lookup"><span data-stu-id="465b4-204">[Building Database Objects with Common Language Runtime &#40;CLR&#41; Integration](../../relational-databases/clr-integration/database-objects/building-database-objects-with-common-language-runtime-clr-integration.md) </span></span>  
 [<span data-ttu-id="465b4-205">EVENTDATA &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="465b4-205">EVENTDATA &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
