---
title: データベースの作成、変更、および削除 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- databases [SMO]
- databases [SMO], creating
- databases [SMO], modifying
- databases [SMO], deleting
ms.assetid: fcfb3ec2-7556-4f72-971a-501295892cb0
author: stevestein
ms.author: sstein
ms.openlocfilehash: e8bd34e939fcbc1ecfc5238f5fc4524d187d3f30
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739649"
---
# <a name="creating-altering-and-removing-databases"></a><span data-ttu-id="456bf-102">データベースの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="456bf-102">Creating, Altering, and Removing Databases</span></span>
  <span data-ttu-id="456bf-103">SMO では、データベースは <xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクトで表現されます。</span><span class="sxs-lookup"><span data-stu-id="456bf-103">In SMO, a database is represented by the <xref:Microsoft.SqlServer.Management.Smo.Database> object.</span></span>  
  
 <span data-ttu-id="456bf-104">修正または削除のために、<xref:Microsoft.SqlServer.Management.Smo.Database> オブジェクトを作成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="456bf-104">It is not necessary to create a <xref:Microsoft.SqlServer.Management.Smo.Database> object to modify or remove it.</span></span> <span data-ttu-id="456bf-105">データベースは、コレクションを使用して参照することができます。</span><span class="sxs-lookup"><span data-stu-id="456bf-105">The database can be referenced by using a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="456bf-106">例</span><span class="sxs-lookup"><span data-stu-id="456bf-106">Example</span></span>  
 <span data-ttu-id="456bf-107">提供されているコード例を使用するには、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="456bf-107">To use any code example that is provided, you will have to choose the programming environment, the programming template, and the programming language in which to create your application.</span></span> <span data-ttu-id="456bf-108">詳細については、「 [Visual studio .net で VISUAL BASIC SMO プロジェクトを作成する](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」または「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="456bf-108">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) or [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="creating-altering-and-removing-a-database-in-visual-basic"></a><span data-ttu-id="456bf-109">Visual Basic でのデータベースの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="456bf-109">Creating, Altering, and Removing a Database in Visual Basic</span></span>  
 <span data-ttu-id="456bf-110">このコード例では、新しいデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="456bf-110">This code example creates a new database.</span></span> <span data-ttu-id="456bf-111">このデータベースに対し、ファイルおよびファイル グループが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="456bf-111">Files and file groups are automatically created for the database.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBDatabase1](SMO How to#SMO_VBDatabase1)]  -->  
  
## <a name="creating-altering-and-removing-a-database-in-visual-c"></a><span data-ttu-id="456bf-112">Visual C# でのデータベースの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="456bf-112">Creating, Altering, and Removing a Database in Visual C#</span></span>  
 <span data-ttu-id="456bf-113">このコード例では、新しいデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="456bf-113">This code example creates a new database.</span></span> <span data-ttu-id="456bf-114">このデータベースに対し、ファイルおよびファイル グループが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="456bf-114">Files and file groups are automatically created for the database.</span></span>  
  
```csharp
{  
                //Connect to the local, default instance of SQL Server.   
                Server srv;  
                srv = new Server();  
                //Define a Database object variable by supplying the server and the database name arguments in the constructor.   
                Database db;  
                db = new Database(srv, "Test_SMO_Database");  
                //Create the database on the instance of SQL Server.   
                db.Create();  
                //Reference the database and display the date when it was created.   
                db = srv.Databases["Test_SMO_Database"];  
                Console.WriteLine(db.CreateDate);  
                //Remove the database.   
                db.Drop();  
            }  
```  
  
## <a name="creating-altering-and-removing-a-database-in-powershell"></a><span data-ttu-id="456bf-115">PowerShell でのデータベースの作成、変更、および削除</span><span class="sxs-lookup"><span data-stu-id="456bf-115">Creating, Altering, and Removing a Database in PowerShell</span></span>  
 <span data-ttu-id="456bf-116">このコード例では、新しいデータベースを作成します。</span><span class="sxs-lookup"><span data-stu-id="456bf-116">This code example creates a new database.</span></span> <span data-ttu-id="456bf-117">このデータベースに対し、ファイルおよびファイル グループが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="456bf-117">Files and file groups are automatically created for the database.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance  
cd \sql\localhost\  
$srv = Get-Item default  
  
#Create a new database  
$db = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Database -argumentlist $srv, "Test_SMO_Database"  
$db.Create()  
  
#Reference the database and display the date when it was created.
$db = $srv.Databases["Test_SMO_Database"]  
$db.CreateDate  
  
#Drop the database  
$db.Drop()  
```  
  
## <a name="see-also"></a><span data-ttu-id="456bf-118">参照</span><span class="sxs-lookup"><span data-stu-id="456bf-118">See Also</span></span>  
 <xref:Microsoft.SqlServer.Management.Smo.Database>  
