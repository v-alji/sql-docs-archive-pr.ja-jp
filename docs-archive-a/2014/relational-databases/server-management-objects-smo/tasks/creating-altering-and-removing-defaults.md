---
title: 既定値の作成、変更、および削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- defaults [SMO]
ms.assetid: c30ac3b9-8150-4264-ba4c-c549f44261ab
author: stevestein
ms.author: sstein
ms.openlocfilehash: 747f7ff60122c5265cd68060063946a3e22d0301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739643"
---
# <a name="creating-altering-and-removing-defaults"></a><span data-ttu-id="3a104-102">既定値の作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="3a104-102">Creating, Altering, and Removing Defaults</span></span>
  <span data-ttu-id="3a104-103">SMO ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 管理オブジェクト) では、既定の制約は <xref:Microsoft.SqlServer.Management.Smo.Default> オブジェクトで表現します。</span><span class="sxs-lookup"><span data-stu-id="3a104-103">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Management Objects (SMO), the default constraint is represented by the <xref:Microsoft.SqlServer.Management.Smo.Default> object.</span></span>  
  
 <span data-ttu-id="3a104-104">挿入する値を設定するには、<xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> オブジェクトの <xref:Microsoft.SqlServer.Management.Smo.Default> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="3a104-104">The <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property of the <xref:Microsoft.SqlServer.Management.Smo.Default> object is used to set the value to be inserted.</span></span> <span data-ttu-id="3a104-105">挿入する値は、定数であっても、GETDATE() などの定数値を返す [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントであってもかまいません。</span><span class="sxs-lookup"><span data-stu-id="3a104-105">This can be a constant or a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement that returns a constant value, such as GETDATE().</span></span> <span data-ttu-id="3a104-106"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> プロパティは、<xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> メソッドを使用して変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="3a104-106">The <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.TextBody%2A> property cannot be modified by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="3a104-107"><xref:Microsoft.SqlServer.Management.Smo.Default> オブジェクトをいったん削除してから再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a104-107">Instead, the <xref:Microsoft.SqlServer.Management.Smo.Default> object must be dropped and re-created.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a104-108">例</span><span class="sxs-lookup"><span data-stu-id="3a104-108">Example</span></span>  
 <span data-ttu-id="3a104-109">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a104-109">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="3a104-110">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3a104-110">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-default-in-visual-basic"></a><span data-ttu-id="3a104-111">Visual Basic での既定値の作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="3a104-111">Creating, Altering, and Removing a Default in Visual Basic</span></span>  
 <span data-ttu-id="3a104-112">このコード例では、シンプル テキストである既定値と [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントである別の既定値を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3a104-112">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="3a104-113">既定値を列にアタッチするには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> メソッドを使用し、列からのデタッチには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a104-113">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDefaults1](SMO How to#SMO_VBDefaults1)]  -->  
  
## <a name="creating-altering-and-removing-a-default-in-visual-c"></a><span data-ttu-id="3a104-114">Visual C# での既定値の作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="3a104-114">Creating, Altering, and Removing a Default in Visual C#</span></span>  
 <span data-ttu-id="3a104-115">このコード例では、シンプル テキストである既定値と [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントである別の既定値を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3a104-115">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="3a104-116">既定値を列にアタッチするには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> メソッドを使用し、列からのデタッチには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a104-116">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
```csharp
{
          Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database  db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Default object variable by supplying the parent database and the default name   
            //in the constructor.   
            Default def = new Default(db, "Test_Default2");  
  
            //Set the TextHeader and TextBody properties that define the default.   
            def.TextHeader = "CREATE DEFAULT [Test_Default2] AS";  
            def.TextBody = "GetDate()";  
  
            //Create the default on the instance of SQL Server.   
            def.Create();  
  
            //Bind the default to a column in a table in AdventureWorks2012  
            def.BindToColumn("SpecialOffer", "StartDate", "Sales");  
  
            //Unbind the default from the column and remove it from the database.   
            def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales");  
            def.Drop();  
        }  
```  
  
## <a name="creating-altering-and-removing-a-default-in-powershell"></a><span data-ttu-id="3a104-117">PowerShell での既定値の作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="3a104-117">Creating, Altering, and Removing a Default in PowerShell</span></span>  
 <span data-ttu-id="3a104-118">このコード例では、シンプル テキストである既定値と [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントである別の既定値を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="3a104-118">This code example shows how to create one default that is simple text, and another default that is a [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="3a104-119">既定値を列にアタッチするには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> メソッドを使用し、列からのデタッチには <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3a104-119">The default must be attached to the column by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.BindToColumn%2A> method and detached by using the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.UnbindFromColumn%2A> method.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = Get-Item Adventureworks2012  
  
#Define a Default object variable by supplying the parent database and the default name in the constructor.  
$def = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Default `  
-argumentlist $db, "Test_Default2"  
  
#Set the TextHeader and TextBody properties that define the default.   
$def.TextHeader = "CREATE DEFAULT [Test_Default2] AS"  
$def.TextBody = "GetDate()"  
  
#Create the default on the instance of SQL Server.   
$def.Create()  
  
#Bind the default to the column.   
$def.BindToColumn("SpecialOffer", "StartDate", "Sales")  
  
#Unbind the default from the column and remove it from the database.   
$def.UnbindFromColumn("SpecialOffer", "StartDate", "Sales")  
$def.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a104-120">参照</span><span class="sxs-lookup"><span data-stu-id="3a104-120">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Default>  
