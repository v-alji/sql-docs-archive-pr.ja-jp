---
title: シノニムの使用 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- synonyms [SMO]
ms.assetid: db0a9022-9549-43e5-b6b3-deb236f05fb8
author: stevestein
ms.author: sstein
ms.openlocfilehash: 5e8416dc3daea3b173fae92e5454a8a65c399e53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645472"
---
# <a name="using-synonyms"></a><span data-ttu-id="0810f-102">シノニムの使用</span><span class="sxs-lookup"><span data-stu-id="0810f-102">Using Synonyms</span></span>
  <span data-ttu-id="0810f-103">シノニムは、スキーマ スコープ オブジェクトの別名です。</span><span class="sxs-lookup"><span data-stu-id="0810f-103">A synonym is an alternative name for a schema-scoped object.</span></span> <span data-ttu-id="0810f-104">SMO では、シノニムは <xref:Microsoft.SqlServer.Management.Smo.Synonym> オブジェクトで表現します。</span><span class="sxs-lookup"><span data-stu-id="0810f-104">In SMO, synonyms are represented by the <xref:Microsoft.SqlServer.Management.Smo.Synonym> object.</span></span> <span data-ttu-id="0810f-105"><xref:Microsoft.SqlServer.Management.Smo.Synonym> オブジェクトは、<xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクトの子です。</span><span class="sxs-lookup"><span data-stu-id="0810f-105">The <xref:Microsoft.SqlServer.Management.Smo.Synonym> object is a child of the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span> <span data-ttu-id="0810f-106">これは、シノニムは、そのシノニムが定義されているデータベースのスコープ内でのみ有効であることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="0810f-106">This means that synonyms are valid only within the scope of the database in which they are defined.</span></span> <span data-ttu-id="0810f-107">ただし、シノニムは、別のデータベース上または [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のリモート インスタンス上のオブジェクトを参照することができます。</span><span class="sxs-lookup"><span data-stu-id="0810f-107">However, the synonym can refer to objects on another database, or on a remote instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="0810f-108">別名を持つオブジェクトは、ベース オブジェクトと呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="0810f-108">The object that is given an alternative name is known as the base object.</span></span> <span data-ttu-id="0810f-109"><xref:Microsoft.SqlServer.Management.Smo.Synonym> オブジェクトの名前プロパティは、ベース オブジェクトの別名です。</span><span class="sxs-lookup"><span data-stu-id="0810f-109">The name property of the <xref:Microsoft.SqlServer.Management.Smo.Synonym> object is the alternative name given to the base object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0810f-110">例</span><span class="sxs-lookup"><span data-stu-id="0810f-110">Example</span></span>  
 <span data-ttu-id="0810f-111">次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0810f-111">For the following code example, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="0810f-112">詳細については、「 [Visual studio .net での VISUAL BASIC Smo プロジェクトの作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」および「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0810f-112">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-a-synonym-in-visual-basic"></a><span data-ttu-id="0810f-113">Visual Basic でのシノニムの作成</span><span class="sxs-lookup"><span data-stu-id="0810f-113">Creating a Synonym in Visual Basic</span></span>  
 <span data-ttu-id="0810f-114">このコード例では、シノニム、またはスキーマ スコープ オブジェクトの別名を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0810f-114">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="0810f-115">クライアント アプリケーションは、マルチパート名を使用してベース オブジェクトを参照するのではなく、シノニムを使用することによって、ベース オブジェクトの単一参照を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0810f-115">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBSynonyms1](SMO How to#SMO_VBSynonyms1)]  -->  
  
## <a name="creating-a-synonym-in-visual-c"></a><span data-ttu-id="0810f-116">Visual C# でのシノニムの作成</span><span class="sxs-lookup"><span data-stu-id="0810f-116">Creating a Synonym in Visual C#</span></span>  
 <span data-ttu-id="0810f-117">このコード例では、シノニム、またはスキーマ スコープ オブジェクトの別名を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0810f-117">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="0810f-118">クライアント アプリケーションは、マルチパート名を使用してベース オブジェクトを参照するのではなく、シノニムを使用することによって、ベース オブジェクトの単一参照を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0810f-118">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
```csharp
{  
            //Connect to the local, default instance of SQL Server.   
            Server srv = new Server();  
  
            //Reference the AdventureWorks2012 database.   
            Database db = srv.Databases["AdventureWorks2012"];  
  
            //Define a Synonym object variable by supplying the   
            //parent database, name, and schema arguments in the constructor.   
            //The name is also a synonym of the name of the base object.   
            Synonym syn = new Synonym(db, "Shop", "Sales");  
  
            //Specify the base object, which is the object on which   
            //the synonym is based.   
            syn.BaseDatabase = "AdventureWorks2012";  
            syn.BaseSchema = "Sales";  
            syn.BaseObject = "Store";  
            syn.BaseServer = srv.Name;  
  
            //Create the synonym on the instance of SQL Server.   
            syn.Create();  
        }  
```  
  
## <a name="creating-a-synonym-in-powershell"></a><span data-ttu-id="0810f-119">PowerShell でのシノニムの作成</span><span class="sxs-lookup"><span data-stu-id="0810f-119">Creating a Synonym in PowerShell</span></span>  
 <span data-ttu-id="0810f-120">このコード例では、シノニム、またはスキーマ スコープ オブジェクトの別名を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0810f-120">The code example shows how to create a synonym or an alternate name for a schema scoped object.</span></span> <span data-ttu-id="0810f-121">クライアント アプリケーションは、マルチパート名を使用してベース オブジェクトを参照するのではなく、シノニムを使用することによって、ベース オブジェクトの単一参照を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="0810f-121">Client applications can use a single reference for the base object via a synonym instead of using a multiple part name to reference the base object.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
$srv = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Server  
  
#And the database object corresponding to Adventureworks  
$db = $srv.Databases["AdventureWorks2012"]  
  
$syn = New-Object -TypeName Microsoft.SqlServer.Management.SMO.Synonym -ArgumentList $db, "Shop", "Sales"  
  
#Specify the base object, which is the object on which the synonym is based.  
$syn.BaseDatabase = "AdventureWorks2012"  
$syn.BaseSchema = "Sales"  
$syn.BaseObject = "Store"  
$syn.BaseServer = $srv.Name  
  
#Create the synonym on the instance of SQL Server.  
$syn.Create()  
```  
  
## <a name="see-also"></a><span data-ttu-id="0810f-122">参照</span><span class="sxs-lookup"><span data-stu-id="0810f-122">See Also</span></span>  
 [<span data-ttu-id="0810f-123">CREATE SYNONYM &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0810f-123">CREATE SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-synonym-transact-sql)  
