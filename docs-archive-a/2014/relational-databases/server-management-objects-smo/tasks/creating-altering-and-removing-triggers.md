---
title: トリガーの作成、変更、および削除 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- triggers [SMO]
ms.assetid: 8ddbe23b-6e31-4f8e-8a70-17bd5072413e
author: stevestein
ms.author: sstein
ms.openlocfilehash: c2cdd1573c488fbe7b2309f656cd6bf42e82a527
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644943"
---
# <a name="creating-altering-and-removing-triggers"></a><span data-ttu-id="0bf67-102">トリガーの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="0bf67-102">Creating, Altering, and Removing Triggers</span></span>
  <span data-ttu-id="0bf67-103">SMO では、<xref:Microsoft.SqlServer.Management.Smo.Trigger> オブジェクトを使用してトリガーが表現されます。</span><span class="sxs-lookup"><span data-stu-id="0bf67-103">In SMO, triggers are represented by using the <xref:Microsoft.SqlServer.Management.Smo.Trigger> object.</span></span> <span data-ttu-id="0bf67-104">トリガーが [!INCLUDE[tsql](../../../includes/tsql-md.md)] 起動されたときに実行されるコードは、 <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> トリガーオブジェクトのプロパティによって設定されます。</span><span class="sxs-lookup"><span data-stu-id="0bf67-104">The [!INCLUDE[tsql](../../../includes/tsql-md.md)] code that runs when the trigger that is fired is set by the <xref:Microsoft.SqlServer.Management.Smo.Trigger.TextBody%2A> property of the Trigger object.</span></span> <span data-ttu-id="0bf67-105">トリガーの型は、<xref:Microsoft.SqlServer.Management.Smo.Trigger> プロパティなど、<xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A> オブジェクトのその他のプロパティを使用することで設定します。</span><span class="sxs-lookup"><span data-stu-id="0bf67-105">The type of trigger is set by using other properties of the <xref:Microsoft.SqlServer.Management.Smo.Trigger> object, such as the <xref:Microsoft.SqlServer.Management.Smo.Trigger.Update%2A> property.</span></span> <span data-ttu-id="0bf67-106">これは、親テーブル上のレコードの `UPDATE` によってトリガーが起動されるかどうかを指定する、ブール型のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="0bf67-106">This is a Boolean property that specifies whether the trigger is fired by an `UPDATE` of records on the parent table.</span></span>  
  
 <span data-ttu-id="0bf67-107"><xref:Microsoft.SqlServer.Management.Smo.Trigger> オブジェクトは、従来のデータ操作言語 (DML) トリガーを表します。</span><span class="sxs-lookup"><span data-stu-id="0bf67-107">The <xref:Microsoft.SqlServer.Management.Smo.Trigger> object represents traditional, data manipulation language (DML) triggers.</span></span> <span data-ttu-id="0bf67-108">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以降のバージョンでは、データ定義言語 (DDL) トリガーもサポートされます。</span><span class="sxs-lookup"><span data-stu-id="0bf67-108">In [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] and later versions, data definition language (DDL) triggers are also supported.</span></span> <span data-ttu-id="0bf67-109">DDL トリガーは、<xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> オブジェクトおよび <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger> オブジェクトで表現します。</span><span class="sxs-lookup"><span data-stu-id="0bf67-109">DDL triggers are represented by the <xref:Microsoft.SqlServer.Management.Smo.DatabaseDdlTrigger> object and the <xref:Microsoft.SqlServer.Management.Smo.ServerDdlTrigger> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bf67-110">例</span><span class="sxs-lookup"><span data-stu-id="0bf67-110">Example</span></span>  
 [!INCLUDE[ssChooseProgEnv](../../../includes/sschooseprogenv-md.md)]  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-basic"></a><span data-ttu-id="0bf67-111">Visual Basic でのトリガーの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="0bf67-111">Creating, Altering, and Removing a Trigger in Visual Basic</span></span>  
 <span data-ttu-id="0bf67-112">このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースにある `Sales` という名前の既存のテーブル上に、更新トリガーを作成および挿入する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0bf67-112">This code example shows how to create and insert an update trigger on an existing table, named `Sales`, in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="0bf67-113">トリガーによって、テーブルの更新時、または新規レコードの挿入時に通知メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="0bf67-113">The trigger sends a reminder message when the table is updated or a new record is inserted.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBTriggers1](SMO How to#SMO_VBTriggers1)]  -->  
  
## <a name="creating-altering-and-removing-a-trigger-in-visual-c"></a><span data-ttu-id="0bf67-114">Visual C# でのトリガーの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="0bf67-114">Creating, Altering, and Removing a Trigger in Visual C#</span></span>  
 <span data-ttu-id="0bf67-115">このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースにある `Sales` という名前の既存のテーブル上に、更新トリガーを作成および挿入する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0bf67-115">This code example shows how to create and insert an update trigger on an existing table, named `Sales`, in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="0bf67-116">トリガーによって、テーブルの更新時、または新規レコードの挿入時に通知メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="0bf67-116">The trigger sends a reminder message when the table is updated or a new record is inserted.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server mysrv;  
            mysrv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database mydb;  
            mydb = mysrv.Databases["AdventureWorks2012"];  
            //Declare a Table object variable and reference the Customer table.   
            Table mytab;  
            mytab = mydb.Tables["Customer", "Sales"];  
            //Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.   
            Trigger tr;  
            tr = new Trigger(mytab, "Sales");  
            //Set TextMode property to False, then set other properties to define the trigger.   
            tr.TextMode = false;  
            tr.Insert = true;  
            tr.Update = true;  
            tr.InsertOrder = ActivationOrder.First;  
            string stmt;  
            stmt = " RAISERROR('Notify Customer Relations',16,10) ";  
            tr.TextBody = stmt;  
            tr.ImplementationType = ImplementationType.TransactSql;  
            //Create the trigger on the instance of SQL Server.   
            tr.Create();  
            //Remove the trigger.   
            tr.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-trigger-in-powershell"></a><span data-ttu-id="0bf67-117">PowerShell でのトリガーの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="0bf67-117">Creating, Altering, and Removing a Trigger in PowerShell</span></span>  
 <span data-ttu-id="0bf67-118">このコード例では、[!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースにある `Sales` という名前の既存のテーブル上に、更新トリガーを作成および挿入する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0bf67-118">This code example shows how to create and insert an update trigger on an existing table, named `Sales`, in the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="0bf67-119">トリガーによって、テーブルの更新時、または新規レコードの挿入時に通知メッセージが送信されます。</span><span class="sxs-lookup"><span data-stu-id="0bf67-119">The trigger sends a reminder message when the table is updated or a new record is inserted.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and to the  
#database tables in Adventureworks2012  
CD \sql\localhost\default\databases\AdventureWorks2012\Tables\  
  
#Get reference to the trigger's target table  
$mytab = Get-Item Sales.Customer  
  
# Define a Trigger object variable by supplying the parent table, schema ,and name in the constructor.  
$tr = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Trigger -argumentlist $mytab, "Sales"  
  
# Set TextMode property to False, then set other properties to define the trigger.
$tr.TextMode = $false  
$tr.Insert = $true  
$tr.Update = $true  
$tr.InsertOrder = [Microsoft.SqlServer.Management.SMO.Agent.ActivationOrder]::First  
$tr.TextBody = " RAISERROR('Notify Customer Relations',16,10) "  
$tr.ImplementationType = [Microsoft.SqlServer.Management.SMO.ImplementationType]::TransactSql  
  
# Create the trigger on the instance of SQL Server.
$tr.Create()  
  
#Remove the trigger.
$tr.Drop()  
```  
