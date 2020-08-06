---
title: CLR 統合を使用したはじめに |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
dev_langs:
- TSQL
- VB
- CSharp
helpviewer_keywords:
- database objects [CLR integration]
- namespaces [CLR integration]
- database objects [CLR integration], about CLR integration
- stored procedures [CLR integration]
- common language runtime [SQL Server], about CLR integration
- building database objects [CLR integration], about CLR integration
- common language runtime [SQL Server], stored procedures
- common language runtime [SQL Server], namespaces
- Hello World example [CLR integration]
- library [CLR integration]
ms.assetid: c73e628a-f54a-411a-bfe3-6dae519316cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 43c97e411a4d74aa48b88f2edbbe420ae17f3534
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631086"
---
# <a name="getting-started-with-clr-integration"></a><span data-ttu-id="99d7d-102">CLR 統合の概要</span><span class="sxs-lookup"><span data-stu-id="99d7d-102">Getting Started with CLR Integration</span></span>
  <span data-ttu-id="99d7d-103">このトピックでは、 [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] .NET Framework 共通言語ランタイム (CLR) との統合を使用してデータベースオブジェクトをコンパイルするために必要な名前空間とライブラリの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-103">This topic provides an overview of the namespaces and libraries required to compile database objects using the [!INCLUDE[msCoName](../../../includes/ssnoversion-md.md)] integration with the .NET Framework common language runtime (CLR).</span></span> <span data-ttu-id="99d7d-104">また、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# を使用した簡単な CLR ストアド プロシージャを記述、コンパイル、および実行する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-104">The topic also shows you how to write, compile, and run a simple CLR stored procedure written in [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C#.</span></span>  
  
## <a name="required-namespaces"></a><span data-ttu-id="99d7d-105">必要な名前空間</span><span class="sxs-lookup"><span data-stu-id="99d7d-105">Required Namespaces</span></span>  
 <span data-ttu-id="99d7d-106">以降 [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="99d7d-106">Beginning with [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="99d7d-107">CLR 統合機能は、.NET Framework の一部である system.data.dll というアセンブリで公開されます。</span><span class="sxs-lookup"><span data-stu-id="99d7d-107">CLR integration functionality is exposed in an assembly called system.data.dll, which is part of the .NET Framework.</span></span> <span data-ttu-id="99d7d-108">このアセンブリは、.NET Framework ディレクトリ内だけでなく、GAC (グローバル アセンブリ キャッシュ) 内にもあります。</span><span class="sxs-lookup"><span data-stu-id="99d7d-108">This assembly can be found in the Global Assembly Cache (GAC) as well as in the .NET Framework directory.</span></span> <span data-ttu-id="99d7d-109">通常、このアセンブリへの参照は、コマンド ライン ツールと [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio の両方で自動的に追加されるので、手動で追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="99d7d-109">A reference to this assembly is typically added automatically by both command line tools and [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Studio, so there is no need to add it manually.</span></span>  
  
 <span data-ttu-id="99d7d-110">system.data.dll アセンブリには、CLR データベース オブジェクトのコンパイルに必要な次の名前空間が含まれています。</span><span class="sxs-lookup"><span data-stu-id="99d7d-110">The system.data.dll assembly contains the following namespaces, which are required for compiling CLR database objects:</span></span>  
  
 `System.Data`  
  
 `System.Data.Sql`  
  
 `Microsoft.SqlServer.Server`  
  
 `System.Data.SqlTypes`  
  
## <a name="writing-a-simple-hello-world-stored-procedure"></a><span data-ttu-id="99d7d-111">簡単な "Hello World" ストアド プロシージャの作成</span><span class="sxs-lookup"><span data-stu-id="99d7d-111">Writing A Simple "Hello World" Stored Procedure</span></span>  
 <span data-ttu-id="99d7d-112">次の Visual C# コードまたは [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic コードをコピーしてテキスト エディターに貼り付け、"helloworld.cs" または "helloworld.vb" というファイル名を付けて保存してください。</span><span class="sxs-lookup"><span data-stu-id="99d7d-112">Copy and paste the following Visual C# or [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic code into a text editor, and save it in a file named "helloworld.cs" or "helloworld.vb".</span></span>  
  
```csharp  
using System;  
using System.Data;  
using Microsoft.SqlServer.Server;  
using System.Data.SqlTypes;  
  
public class HelloWorldProc  
{  
    [Microsoft.SqlServer.Server.SqlProcedure]  
    public static void HelloWorld(out string text)  
    {  
        SqlContext.Pipe.Send("Hello world!" + Environment.NewLine);  
        text = "Hello world!";  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.Data  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlTypes  
Imports System.Runtime.InteropServices  
  
Public Class HelloWorldProc  
    <Microsoft.SqlServer.Server.SqlProcedure> _   
    Public Shared  Sub HelloWorld(<Out()> ByRef text as String)  
        SqlContext.Pipe.Send("Hello world!" & Environment.NewLine)  
        text = "Hello world!"  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="99d7d-113">この簡単なプログラムには、パブリック クラスの静的メソッドが 1 つ含まれています。</span><span class="sxs-lookup"><span data-stu-id="99d7d-113">This simple program contains a single static method on a public class.</span></span> <span data-ttu-id="99d7d-114">このメソッドでは、`SqlContext` と `SqlPipe` という 2 つの新しいクラスを使用して、簡単なテキスト メッセージを出力するマネージド データベース オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-114">This method uses two new classes, `SqlContext` and `SqlPipe`, for creating managed database objects to output a simple text message.</span></span> <span data-ttu-id="99d7d-115">また、このメソッドは文字列 "Hello world!" を</span><span class="sxs-lookup"><span data-stu-id="99d7d-115">The method also assigns the string "Hello world!"</span></span> <span data-ttu-id="99d7d-116">out パラメーターの値として指定します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-116">as the value of an out parameter.</span></span> <span data-ttu-id="99d7d-117">このメソッドは、ストアドプロシージャでストアドプロシージャとして宣言でき [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="99d7d-117">This method can be declared as a stored procedure in [!INCLUDE[ssNoVersion](../../../includes/tsql-md.md)] stored procedure.</span></span>  
  
 <span data-ttu-id="99d7d-118">ここでは、このプログラムをライブラリとしてコンパイルし、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に読み込んで、ストアド プロシージャとして実行します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-118">We will now compile this program as a library, load it into [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], and run it as a stored procedure.</span></span>  
  
## <a name="compiling-the-hello-world-stored-procedure"></a><span data-ttu-id="99d7d-119">"Hello World" ストアド プロシージャのコンパイル</span><span class="sxs-lookup"><span data-stu-id="99d7d-119">Compiling the "Hello World" Stored Procedure</span></span>  
 [!INCLUDE[ssNoVersion](../../../includes/msconame-md.md)]<span data-ttu-id="99d7d-120">既定で再配布ファイルを .NET Framework します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-120">.NET Framework redistribution files by default.</span></span> <span data-ttu-id="99d7d-121">インストールされるファイルには、Visual C# プログラムと Visual Basic プログラム用のコマンド ライン コンパイラである csc.exe と vbc.exe が含まれています。</span><span class="sxs-lookup"><span data-stu-id="99d7d-121">These files include csc.exe and vbc.exe, the command-line compilers for Visual C# and Visual Basic programs.</span></span> <span data-ttu-id="99d7d-122">サンプルをコンパイルする前に、csc.exe または vbc.exe が格納されたディレクトリを指すようにパス変数を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d7d-122">In order to compile our sample, you must modify your path variable to point to the directory containing csc.exe or vbc.exe.</span></span> <span data-ttu-id="99d7d-123">.NET Framework の既定のインストール パスは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="99d7d-123">The following is the default installation path of the .NET Framework.</span></span>  
  
```  
C:\Windows\Microsoft.NET\Framework\(version)  
```  
  
 <span data-ttu-id="99d7d-124">version は、インストールされた再配布可能な .NET Framework のバージョン番号を表します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-124">Version contains the version number of the installed .NET Framework redistributable.</span></span> <span data-ttu-id="99d7d-125">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-125">For example:</span></span>  
  
```  
C:\Windows\Microsoft.NET\Framework\v2.0.31113  
```  
  
 <span data-ttu-id="99d7d-126">.NET Framework ディレクトリをパスに追加した後、次のコマンドを実行してサンプル ストアド プロシージャをアセンブリにコンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="99d7d-126">Once you have added the .NET Framework directory to your path, you can compile the sample stored procedure into an assembly with the following command.</span></span> <span data-ttu-id="99d7d-127">アセンブリへのコンパイルを可能にするのは `/target` オプションです。</span><span class="sxs-lookup"><span data-stu-id="99d7d-127">The `/target` option allows you to compile it into an assembly.</span></span>  
  
 <span data-ttu-id="99d7d-128">Visual C# ソース ファイルの場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-128">For Visual C# source files:</span></span>  
  
```  
csc /target:library helloworld.cs   
```  
  
 <span data-ttu-id="99d7d-129">Visual Basic ソース ファイルの場合は、次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-129">For Visual Basic source files:</span></span>  
  
```  
vbc /target:library helloworld.vb  
```  
  
 <span data-ttu-id="99d7d-130">これらのコマンドでは、/target オプションを使用してライブラリ DLL をビルドすることを指定し、Visual C# コンパイラまたは Visual Basic コンパイラを起動します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-130">These commands launch the Visual C# or Visual Basic compiler using the /target option to specify building a library DLL.</span></span>  
  
## <a name="loading-and-running-the-hello-world-stored-procedure-in-sql-server"></a><span data-ttu-id="99d7d-131">"Hello World" ストアド プロシージャの SQL Server への読み込みと実行</span><span class="sxs-lookup"><span data-stu-id="99d7d-131">Loading and Running the "Hello World" Stored Procedure in SQL Server</span></span>  
 <span data-ttu-id="99d7d-132">サンプルプロシージャが正常にコンパイルされたら、それをテスト [!INCLUDE[ssNoVersion](../../../includes/ssmanstudiofull-md.md)] し、適切なテストデータベース (AdventureWorks サンプルデータベースなど) に接続して、新しいクエリを作成できます。</span><span class="sxs-lookup"><span data-stu-id="99d7d-132">Once the sample procedure has successfully compiled, you can test it in [!INCLUDE[ssNoVersion](../../../includes/ssmanstudiofull-md.md)] and create a new query, connecting to a suitable test database (for example, the AdventureWorks sample database).</span></span>  
  
 <span data-ttu-id="99d7d-133">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、CLR (共通言語ランタイム) コードを実行する機能は、既定ではオフに設定されています。</span><span class="sxs-lookup"><span data-stu-id="99d7d-133">The ability to execute common language runtime (CLR) code is set to OFF by default in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="99d7d-134">CLR コードを有効にするには、 **sp_configure**システムストアドプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-134">The CLR code can be enabled by using the **sp_configure** system stored procedure.</span></span> <span data-ttu-id="99d7d-135">詳細については、「 [CLR 統合の有効化](../clr-integration-enabling.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99d7d-135">For more information, see [Enabling CLR Integration](../clr-integration-enabling.md).</span></span>  
  
 <span data-ttu-id="99d7d-136">ストアド プロシージャにアクセスするには、アセンブリを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="99d7d-136">We will need to create the assembly so we can access the stored procedure.</span></span> <span data-ttu-id="99d7d-137">この例では、C:\ ディレクトリに helloworld.dll アセンブリが作成されているものとします。</span><span class="sxs-lookup"><span data-stu-id="99d7d-137">For this example, we will assume that you have created the helloworld.dll assembly in the C:\ directory.</span></span> <span data-ttu-id="99d7d-138">クエリに次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-138">Add the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement to your query.</span></span>  
  
```  
CREATE ASSEMBLY helloworld from 'c:\helloworld.dll' WITH PERMISSION_SET = SAFE  
```  
  
 <span data-ttu-id="99d7d-139">アセンブリを作成した後、次のように CREATE PROCEDURE ステートメントを使用すると、HelloWorld メソッドにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="99d7d-139">Once the assembly has been created, we can now access our HelloWorld method by using the create procedure statement.</span></span> <span data-ttu-id="99d7d-140">ここではストアド プロシージャ "hello" を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-140">We will call our stored procedure "hello":</span></span>  
  
```  
  
CREATE PROCEDURE hello  
@i nchar(25) OUTPUT  
AS  
EXTERNAL NAME helloworld.HelloWorldProc.HelloWorld  
-- if the HelloWorldProc class is inside a namespace (called MyNS),  
-- the last line in the create procedure statement would be  
-- EXTERNAL NAME helloworld.[MyNS.HelloWorldProc].HelloWorld  
```  
  
 <span data-ttu-id="99d7d-141">作成したプロシージャは、[!INCLUDE[tsql](../../../includes/tsql-md.md)] で記述された通常のストアド プロシージャと同様に実行できます。</span><span class="sxs-lookup"><span data-stu-id="99d7d-141">Once the procedure has been created, it can be run just like a normal stored procedure written in [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="99d7d-142">次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-142">Execute the following command:</span></span>  
  
```  
DECLARE @J nchar(25)  
EXEC hello @J out  
PRINT @J  
```  
  
 <span data-ttu-id="99d7d-143">これにより、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] のメッセージ ウィンドウに次の出力結果が表示されます。</span><span class="sxs-lookup"><span data-stu-id="99d7d-143">This should result in the following output in the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] messages window.</span></span>  
  
```  
Hello world!  
Hello world!  
```  
  
## <a name="removing-the-hello-world-stored-procedure-sample"></a><span data-ttu-id="99d7d-144">"Hello World" サンプル ストアド プロシージャの削除</span><span class="sxs-lookup"><span data-stu-id="99d7d-144">Removing the "Hello World" Stored Procedure Sample</span></span>  
 <span data-ttu-id="99d7d-145">サンプル ストアド プロシージャの実行を完了したら、テスト データベースからこのプロシージャとアセンブリを削除できます。</span><span class="sxs-lookup"><span data-stu-id="99d7d-145">When you are finished running the sample stored procedure, you can remove the procedure and the assembly from your test database.</span></span>  
  
 <span data-ttu-id="99d7d-146">最初に、次のように drop procedure コマンドを使用してプロシージャを削除します。</span><span class="sxs-lookup"><span data-stu-id="99d7d-146">First, remove the procedure using the drop procedure command.</span></span>  
  
```  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'hello')  
   drop procedure hello  
```  
  
 <span data-ttu-id="99d7d-147">プロシージャを削除したら、サンプル コードが含まれたアセンブリを次のように削除できます。</span><span class="sxs-lookup"><span data-stu-id="99d7d-147">Once the procedure has been dropped, you can remove the assembly containing your sample code.</span></span>  
  
```  
IF EXISTS (SELECT name FROM sys.assemblies WHERE name = 'helloworld')  
   drop assembly helloworld  
```  
  
## <a name="see-also"></a><span data-ttu-id="99d7d-148">参照</span><span class="sxs-lookup"><span data-stu-id="99d7d-148">See Also</span></span>  
 <span data-ttu-id="99d7d-149">[CLR ストアドプロシージャ](../../../database-engine/dev-guide/clr-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="99d7d-149">[CLR Stored Procedures](../../../database-engine/dev-guide/clr-stored-procedures.md) </span></span>  
 <span data-ttu-id="99d7d-150">[ADO.NET に対するインプロセス固有の拡張機能の SQL Server](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md) </span><span class="sxs-lookup"><span data-stu-id="99d7d-150">[SQL Server In-Process Specific Extensions to ADO.NET](../../clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md) </span></span>  
 <span data-ttu-id="99d7d-151">[CLR データベースオブジェクトのデバッグ](../debugging-clr-database-objects.md) </span><span class="sxs-lookup"><span data-stu-id="99d7d-151">[Debugging CLR Database Objects](../debugging-clr-database-objects.md) </span></span>  
 [<span data-ttu-id="99d7d-152">CLR 統合のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="99d7d-152">CLR Integration Security</span></span>](../security/clr-integration-security.md)  
  
  
