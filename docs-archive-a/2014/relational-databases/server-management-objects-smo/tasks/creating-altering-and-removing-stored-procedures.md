---
title: ストアドプロシージャの作成、変更、および削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [SMO]
ms.assetid: 2a072f9c-8f11-4364-ab71-3990735a8d66
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73e8313f3befd4c7c5cb20cdb6649c87ea72b037
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644947"
---
# <a name="creating-altering-and-removing-stored-procedures"></a><span data-ttu-id="3c9d5-102">ストアド プロシージャの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="3c9d5-102">Creating, Altering, and Removing Stored Procedures</span></span>
  <span data-ttu-id="3c9d5-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト (SMO) では、ストアド プロシージャは <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> オブジェクトで表現されます。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), stored procedures are represented by the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object.</span></span>  
  
 <span data-ttu-id="3c9d5-104">SMO で <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> オブジェクトを作成する場合は、<xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> プロパティに、ストアド プロシージャを定義する [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-104">Creating a <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object in SMO requires setting the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure.TextBody%2A> property to the [!INCLUDE[tsql](../../../includes/tsql-md.md)] script that defines the stored procedure.</span></span> <span data-ttu-id="3c9d5-105">パラメーターにはプレフィックスが必要で \@ あり、オブジェクトを使用 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> してオブジェクトのコレクションに追加することで、個別に作成する必要があり <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> ます。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-105">Parameters require the \@ prefix and must be created individually by using <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> objects and adding to the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedureParameter> collection of the <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c9d5-106">例</span><span class="sxs-lookup"><span data-stu-id="3c9d5-106">Example</span></span>  
 <span data-ttu-id="3c9d5-107">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="3c9d5-108">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-basic"></a><span data-ttu-id="3c9d5-109">Visual Basic でのストアド プロシージャの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="3c9d5-109">Creating, Altering, and Removing a Stored Procedure in Visual Basic</span></span>  
 <span data-ttu-id="3c9d5-110">このコード例では、 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースのストアド プロシージャを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-110">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="3c9d5-111">この例では、従業員 ID 番号が指定されると、従業員の姓を返します。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-111">The example returns the last name of an employee when it is given the employee ID number.</span></span> <span data-ttu-id="3c9d5-112">このストアド プロシージャには、従業員 ID 番号を指定する 1 つの入力パラメーターと、従業員の姓を返す 1 つの出力パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-112">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBStoredProcs1](SMO How to#SMO_VBStoredProcs1)]  -->  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-visual-c"></a><span data-ttu-id="3c9d5-113">Visual C# でのストアド プロシージャの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="3c9d5-113">Creating, Altering, and Removing a Stored Procedure in Visual C#</span></span>  
 <span data-ttu-id="3c9d5-114">このコード例では、 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースのストアド プロシージャを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-114">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="3c9d5-115">この例では、従業員 ID 番号 (`BusinessEntityID`) が指定されると、従業員の姓を返します。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-115">The example returns the last name of an employee when it is given the employee ID number (`BusinessEntityID`).</span></span> <span data-ttu-id="3c9d5-116">このストアド プロシージャには、従業員 ID 番号を指定する 1 つの入力パラメーターと、従業員の姓を返す 1 つの出力パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-116">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv;  
            srv = new Server();  
            //Reference the AdventureWorks2012 database.   
            Database db;  
            db = srv.Databases["AdventureWorks2012"];  
            //Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.   
            StoredProcedure sp;  
            sp = new StoredProcedure(db, "GetLastNameByBusinessEntityID");  
            //Set the TextMode property to false and then set the other object properties.   
            sp.TextMode = false;  
            sp.AnsiNullsStatus = false;  
            sp.QuotedIdentifierStatus = false;  
            //Add two parameters.   
            StoredProcedureParameter param;  
            param = new StoredProcedureParameter(sp, "@empval", DataType.Int);  
            sp.Parameters.Add(param);  
            StoredProcedureParameter param2;  
            param2 = new StoredProcedureParameter(sp, "@retval", DataType.NVarChar(50));  
            param2.IsOutputParameter = true;  
            sp.Parameters.Add(param2);  
            //Set the TextBody property to define the stored procedure.   
            string stmt;  
            stmt = " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )";  
            sp.TextBody = stmt;  
            //Create the stored procedure on the instance of SQL Server.   
            sp.Create();  
            //Modify a property and run the Alter method to make the change on the instance of SQL Server.   
            sp.QuotedIdentifierStatus = true;  
            sp.Alter();  
            //Remove the stored procedure.   
            sp.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-stored-procedure-in-powershell"></a><span data-ttu-id="3c9d5-117">PowerShell でのストアド プロシージャの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="3c9d5-117">Creating, Altering, and Removing a Stored Procedure in PowerShell</span></span>  
 <span data-ttu-id="3c9d5-118">このコード例では、 [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] データベースのストアド プロシージャを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-118">This code example shows how to create a stored procedure for the [!INCLUDE[ssSampleDBnormal](../../../includes/sssampledbnormal-md.md)] database.</span></span> <span data-ttu-id="3c9d5-119">この例では、従業員 ID 番号 (`BusinessEntityID`) が指定されると、従業員の姓を返します。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-119">The example returns the last name of an employee when it is given the employee ID number (`BusinessEntityID`).</span></span> <span data-ttu-id="3c9d5-120">このストアド プロシージャには、従業員 ID 番号を指定する 1 つの入力パラメーターと、従業員の姓を返す 1 つの出力パラメーターが必要です。</span><span class="sxs-lookup"><span data-stu-id="3c9d5-120">The stored procedure requires one input parameter to specify the employee ID number and one output parameter to return the last name of the employee.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
# Define a StoredProcedure object variable by supplying the parent database and name arguments in the constructor.
$sp = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedure -argumentlist $db, "GetLastNameByBusinessEntityID"  
  
#Set the TextMode property to false and then set the other object properties.
$sp.TextMode = $false  
$sp.AnsiNullsStatus = $false  
$sp.QuotedIdentifierStatus = $false  
  
# Add two parameters  
$type = [Microsoft.SqlServer.Management.SMO.Datatype]::Int  
$param  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter -argumentlist $sp,"@empval",$type  
$sp.Parameters.Add($param)  
  
$type = [Microsoft.SqlServer.Management.SMO.DataType]::NVarChar(50)  
$param2  = New-Object -TypeName Microsoft.SqlServer.Management.SMO.StoredProcedureParameter -argumentlist $sp,"@retval",$type  
$param2.IsOutputParameter = $true  
$sp.Parameters.Add($param2)  
  
#Set the TextBody property to define the stored procedure.
$sp.TextBody =  " SELECT @retval = (SELECT LastName FROM Person.Person,HumanResources.Employee WHERE Person.Person.BusinessEntityID = HumanResources.Employee.BusinessentityID AND HumanResources.Employee.BusinessEntityID = @empval )"  
  
# Create the stored procedure on the instance of SQL Server.
$sp.Create()  
  
# Modify a property and run the Alter method to make the change on the instance of SQL Server.
$sp.QuotedIdentifierStatus = $true  
$sp.Alter()  
  
#Remove the stored procedure.
$sp.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c9d5-121">参照</span><span class="sxs-lookup"><span data-stu-id="3c9d5-121">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.StoredProcedure>  
