---
title: Hello World のサンプル |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
ms.assetid: fed6c358-f5ee-4d4c-9ad6-089778383ba7
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 0d5616c1d4ef6428a011c8e36be3757931039c9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742505"
---
# <a name="hello-world-sample"></a><span data-ttu-id="41659-102">Hello World サンプル</span><span class="sxs-lookup"><span data-stu-id="41659-102">Hello World Sample</span></span>
  <span data-ttu-id="41659-103">Hello World サンプルでは、共通言語ランタイム (CLR) 統合ベースの単純なストアド プロシージャの作成、展開、およびテストにかかわる基本的な操作について示します。</span><span class="sxs-lookup"><span data-stu-id="41659-103">The Hello World sample demonstrates the basic operations that are involved in creating, deploying, and testing a simple common language runtime (CLR) integration-based stored procedure.</span></span> <span data-ttu-id="41659-104">また、このサンプルでは、ストアド プロシージャによって動的に構築されて呼び出し元に返されるレコードを使用してデータを返す方法についても示します。</span><span class="sxs-lookup"><span data-stu-id="41659-104">This sample also demonstrates how to return data through a record, which is dynamically constructed by the stored procedure and returned to the caller.</span></span>  
  
 <span data-ttu-id="41659-105">この `HelloWorld` ストアドプロシージャは、文字列 "Hello world!" を返します。</span><span class="sxs-lookup"><span data-stu-id="41659-105">The `HelloWorld` stored procedure returns the string "Hello world!"</span></span> <span data-ttu-id="41659-106">1つの行で構成される結果セット。</span><span class="sxs-lookup"><span data-stu-id="41659-106">in a result set consisting of one row.</span></span> <span data-ttu-id="41659-107">この例では、 [SqlDataRecord](https://go.microsoft.com/fwlink/?LinkID=193573)および[microsoft](https://go.microsoft.com/fwlink/?LinkID=193571). sqlserver. サーバーのクラスのいくつかの使用[方法を示し](https://go.microsoft.com/fwlink/?LinkID=193572)ています。この例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="41659-107">This example illustrates some uses for the classes [Microsoft.SqlServer.Server.SqlMetaData](https://go.microsoft.com/fwlink/?LinkID=193572), [Microsoft.SqlServer.Server.SqlDataRecord](https://go.microsoft.com/fwlink/?LinkID=193573) and [Microsoft.SqlServer.Server.Pipe](https://go.microsoft.com/fwlink/?LinkID=193571).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="41659-108">[前提条件]</span><span class="sxs-lookup"><span data-stu-id="41659-108">Prerequisites</span></span>  
 <span data-ttu-id="41659-109">このプロジェクトを作成して実行するには、次のソフトウェアがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="41659-109">To create and run this project the following the following software must be installed:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="41659-110">または [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express。</span><span class="sxs-lookup"><span data-stu-id="41659-110">or [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express.</span></span> <span data-ttu-id="41659-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express ドキュメントとサンプルの [Web サイト](https://www.microsoft.com/sql-server/sql-server-editions-express)から無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="41659-111">You can obtain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express free of charge from the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express Documentation and Samples [Web site](https://www.microsoft.com/sql-server/sql-server-editions-express)</span></span>  
  
-   <span data-ttu-id="41659-112">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] デベロッパー [Web サイト](https://go.microsoft.com/fwlink/?linkid=62796)から入手できる AdventureWorks データベース。</span><span class="sxs-lookup"><span data-stu-id="41659-112">The AdventureWorks database that is available at the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Developer [Web site](https://go.microsoft.com/fwlink/?linkid=62796)</span></span>  
  
-   <span data-ttu-id="41659-113">.NET Framework SDK 2.0 以降または Microsoft Visual Studio 2005 以降。</span><span class="sxs-lookup"><span data-stu-id="41659-113">.NET Framework SDK 2.0 or later or Microsoft Visual Studio 2005 or later.</span></span> <span data-ttu-id="41659-114">.NET Framework SDK は無償で入手できます。</span><span class="sxs-lookup"><span data-stu-id="41659-114">You can obtain .NET Framework SDK free of charge.</span></span>  
  
-   <span data-ttu-id="41659-115">また、次の条件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="41659-115">In addition, the following conditions must be met:</span></span>  
  
-   <span data-ttu-id="41659-116">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで CLR 統合が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="41659-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using must have CLR integration enabled.</span></span>  
  
-   <span data-ttu-id="41659-117">CLR 統合を有効にするには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="41659-117">In order to enable CLR integration, perform the following steps:</span></span>  
  
    #### <a name="enabling-clr-integration"></a><span data-ttu-id="41659-118">CLR 統合の有効化</span><span class="sxs-lookup"><span data-stu-id="41659-118">Enabling CLR Integration</span></span>  
  
    -   <span data-ttu-id="41659-119">以下の [!INCLUDE[tsql](../../includes/tsql-md.md)] コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="41659-119">Execute the following [!INCLUDE[tsql](../../includes/tsql-md.md)] commands:</span></span>  
  
     `sp_configure 'clr enabled', 1`  
  
     `GO`  
  
     `RECONFIGURE`  
  
     `GO`  
  
    > [!NOTE]  
    >  <span data-ttu-id="41659-120">CLR を有効にするには、 `ALTER SETTINGS` サーバーレベルの権限が必要です。この権限は、 `sysadmin` 固定サーバーロールおよびのメンバーによって暗黙的に保持されてい `serveradmin` ます。</span><span class="sxs-lookup"><span data-stu-id="41659-120">To enable CLR, you must have `ALTER SETTINGS` server level permission, which is implicitly held by members of the `sysadmin` and `serveradmin` fixed server roles.</span></span>  
  
-   <span data-ttu-id="41659-121">使用している [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに AdventureWorks データベースがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="41659-121">The AdventureWorks database must be installed on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using.</span></span>  
  
-   <span data-ttu-id="41659-122">使用しているインスタンスの管理者ではない場合 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、インストールを完了するには、 **createassembly**アクセス許可を管理者に付与する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41659-122">If you are not an administrator for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you are using, you must have an administrator grant you **CreateAssembly** permission to complete the installation.</span></span>  
  
## <a name="building-the-sample"></a><span data-ttu-id="41659-123">サンプルのビルド</span><span class="sxs-lookup"><span data-stu-id="41659-123">Building the Sample</span></span>  
  
#### <a name="create-and-run-the-sample-by-using-the-following-instructions"></a><span data-ttu-id="41659-124">次の手順に従ってサンプルを作成し、実行します。</span><span class="sxs-lookup"><span data-stu-id="41659-124">Create and run the sample by using the following instructions:</span></span>  
  
1.  <span data-ttu-id="41659-125">Visual Studio または .NET Framework のコマンド プロンプトを開きます。</span><span class="sxs-lookup"><span data-stu-id="41659-125">Open a Visual Studio or .NET Framework command prompt.</span></span>  
  
2.  <span data-ttu-id="41659-126">必要な場合は、サンプル用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="41659-126">If necessary, create a directory for your sample.</span></span> <span data-ttu-id="41659-127">この例では C:\MySample を使用します。</span><span class="sxs-lookup"><span data-stu-id="41659-127">For this example, we will use C:\MySample.</span></span>  
  
3.  <span data-ttu-id="41659-128">c:\MySample で、`HelloWorld.vb` (Visual Basic サンプル) または `HelloWorld.cs` (C# サンプル) を作成し、適切な Visual Basic または C# のサンプル コード (下記) をこのファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="41659-128">In c:\MySample, create `HelloWorld.vb` (for the Visual Basic sample) or `HelloWorld.cs` (for the C# sample) and copy the appropriate Visual Basic or C# sample code (below) into the file.</span></span>  
  
4.  <span data-ttu-id="41659-129">選択した言語に応じて次のいずれかをコマンド プロンプトで実行し、サンプル コードをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="41659-129">Compile the sample code from the command line prompt by executing one of the following, depending on your choice of language.</span></span>  
  
    -   `vbc C:HelloWorld.vb /target:library`  
  
    -   `csc /target:library HelloWorld.cs`  
  
5.  <span data-ttu-id="41659-130">[!INCLUDE[tsql](../../includes/tsql-md.md)] インストール コードをファイルにコピーし、`Install.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="41659-130">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation code into a file and save it as `Install.sql` in the sample directory.</span></span>  
  
6.  <span data-ttu-id="41659-131">次のコマンドを実行して、アセンブリとストアド プロシージャを配置します。</span><span class="sxs-lookup"><span data-stu-id="41659-131">Deploy the assembly and stored procedure by executing</span></span>  
  
    -   `sqlcmd -E -I -i install.sql -v root = "C:\MySample\"`  
  
7.  <span data-ttu-id="41659-132">[!INCLUDE[tsql](../../includes/tsql-md.md)]テストコマンドスクリプトをファイルにコピーし、として `test.sql` サンプルディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="41659-132">Copy [!INCLUDE[tsql](../../includes/tsql-md.md)] test command script into a file and save it as `test.sql` in the sample directory.</span></span>  
  
8.  <span data-ttu-id="41659-133">次のコマンドを使用してテスト スクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="41659-133">Execute the test script with the following command</span></span>  
  
    -   `sqlcmd -E -I -i test.sql`  
  
9. <span data-ttu-id="41659-134">[!INCLUDE[tsql](../../includes/tsql-md.md)] クリーンアップ スクリプトをファイルにコピーし、`cleanup.sql` としてサンプル ディレクトリに保存します。</span><span class="sxs-lookup"><span data-stu-id="41659-134">Copy the [!INCLUDE[tsql](../../includes/tsql-md.md)] cleanup script into a file and save it as `cleanup.sql` in the sample directory.</span></span>  
  
10. <span data-ttu-id="41659-135">次のコマンドを使用してこのスクリプトを実行します。</span><span class="sxs-lookup"><span data-stu-id="41659-135">Execute the script with the  following command</span></span>  
  
    -   `sqlcmd -E -I -i cleanup.sql`  
  
## <a name="sample-code"></a><span data-ttu-id="41659-136">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="41659-136">Sample Code</span></span>  
 <span data-ttu-id="41659-137">このサンプルのコード リストを次に示します。</span><span class="sxs-lookup"><span data-stu-id="41659-137">The following are the code listings for this sample.</span></span>  
  
 <span data-ttu-id="41659-138">C#</span><span class="sxs-lookup"><span data-stu-id="41659-138">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
public partial class StoredProcedures  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld()  
    {  
        Microsoft.SqlServer.Server.SqlMetaData columnInfo  
                = new Microsoft.SqlServer.Server.SqlMetaData("Column1", SqlDbType.NVarChar, 12);  
        SqlDataRecord greetingRecord  
            = new SqlDataRecord(new Microsoft.SqlServer.Server.SqlMetaData[] { columnInfo });  
        greetingRecord.SetString(0, "Hello world!");  
        SqlContext.Pipe.Send(greetingRecord);  
    }  
};  
  
```  
  
 <span data-ttu-id="41659-139">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41659-139">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public NotInheritable Class StoredProcedures  
    <Microsoft.SqlServer.Server.SqlProcedure()> _  
    Public Shared Sub HelloWorld()  
        Dim columnInfo As New Microsoft.SqlServer.Server.SqlMetaData("Column1", _  
            SqlDbType.NVarChar, 12)  
        Dim greetingRecord As New SqlDataRecord(New  _  
            Microsoft.SqlServer.Server.SqlMetaData() {columnInfo})  
        greetingRecord.SetString(0, "Hello World!")  
        SqlContext.Pipe.Send(greetingRecord)  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="41659-140">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] インストール スクリプト (`Install.sql`) は、アセンブリを展開し、データベースにストアド プロシージャを作成します。</span><span class="sxs-lookup"><span data-stu-id="41659-140">This is the [!INCLUDE[tsql](../../includes/tsql-md.md)] installation script (`Install.sql`), which deploys the assembly and creates the stored procedure in the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
DECLARE @SamplesPath nvarchar(1024)  
set @SamplesPath = '$(root)'  
CREATE ASSEMBLY HelloWorld   
FROM @SamplesPath + 'HelloWorld.dll'  
WITH permission_set = Safe;  
GO  
  
CREATE PROCEDURE usp_HelloWorld  
--(  
--    @Greeting nvarchar(12) OUTPUT  
--)  
AS EXTERNAL NAME HelloWorld.[StoredProcedures].HelloWorld;  
GO  
```  
  
 <span data-ttu-id="41659-141">次の `test.sql` は、ストアド プロシージャを実行してサンプルをテストします。</span><span class="sxs-lookup"><span data-stu-id="41659-141">This is `test.sql`, which tests the sample by executing the stored procedure.</span></span>  
  
```  
use AdventureWorks  
go  
execute usp_HelloWorld  
  
USE AdventureWorks;  
GO  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
```  
  
 <span data-ttu-id="41659-142">次の [!INCLUDE[tsql](../../includes/tsql-md.md)] は、データベースからアセンブリとストアド プロシージャを削除します。</span><span class="sxs-lookup"><span data-stu-id="41659-142">The following [!INCLUDE[tsql](../../includes/tsql-md.md)] removes the assembly and stored procedure from the database.</span></span>  
  
```  
USE AdventureWorks  
GO  
  
IF EXISTS (SELECT * FROM sys.procedures WHERE [name] = 'usp_HelloWorld')  
DROP PROCEDURE usp_HelloWorld;  
GO  
  
IF EXISTS (SELECT * FROM sys.assemblies WHERE [name] = 'HelloWorld')  
DROP ASSEMBLY HelloWorld;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="41659-143">参照</span><span class="sxs-lookup"><span data-stu-id="41659-143">See Also</span></span>  
 [<span data-ttu-id="41659-144">CLR &#40;共通言語ランタイム&#41; 統合の使用シナリオと例</span><span class="sxs-lookup"><span data-stu-id="41659-144">Usage Scenarios and Examples for Common Language Runtime &#40;CLR&#41; Integration</span></span>](../../../2014/database-engine/dev-guide/usage-scenarios-and-examples-for-common-language-runtime-clr-integration.md)  
  
  
