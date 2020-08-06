---
title: CLR データベースオブジェクトのデバッグ |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- database objects [CLR integration], debugging
- permissions [CLR integration]
- debugging [CLR integration]
- building database objects [CLR integration], debugging
- common language runtime [SQL Server], debugging
ms.assetid: 1332035c-d6ed-424d-8234-46ad21168319
author: rothja
ms.author: jroth
ms.openlocfilehash: 084b2494ec55b502f71154ca1f174a6de6d2ab70
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631085"
---
# <a name="debugging-clr-database-objects"></a><span data-ttu-id="9ab43-102">CLR データベース オブジェクトのデバッグ</span><span class="sxs-lookup"><span data-stu-id="9ab43-102">Debugging CLR Database Objects</span></span>
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="9ab43-103">では、データベース内の [!INCLUDE[tsql](../../../includes/tsql-md.md)] オブジェクトと CLR (共通言語ランタイム) オブジェクトのデバッグがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-103">provides support for debugging [!INCLUDE[tsql](../../../includes/tsql-md.md)] and common language runtime (CLR) objects in the database.</span></span> <span data-ttu-id="9ab43-104">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] でのデバッグの重要な特徴は、セットアップと使用が容易になったことと、SQL Server デバッガーと Microsoft Visual Studio デバッガーが統合されたことです。</span><span class="sxs-lookup"><span data-stu-id="9ab43-104">The key aspects of debugging in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] are the ease of setup and use, and the integration of the SQL Server debugger with the Microsoft Visual Studio debugger.</span></span> <span data-ttu-id="9ab43-105">さらに、複数の言語にまたがったデバッグを実行できます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-105">Furthermore, debugging works across languages.</span></span> <span data-ttu-id="9ab43-106">ユーザーは [!INCLUDE[tsql](../../../includes/tsql-md.md)] から CLR オブジェクト (またはその逆) にシームレスにステップインできます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-106">Users can step seamlessly into CLR objects from [!INCLUDE[tsql](../../../includes/tsql-md.md)], and vice versa.</span></span> <span data-ttu-id="9ab43-107">SQL Server Management Studio の Transact-SQL デバッガーを使用してマネージド データベース オブジェクトをデバッグすることはできませんが、Visual Studio のデバッガーを使用すると、このオブジェクトをデバッグすることができます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-107">The Transact-SQL debugger in SQL Server Management Studio cannot be used to debug managed database objects, but you can debug the objects by using the debuggers in Visual Studio.</span></span> <span data-ttu-id="9ab43-108">Visual Studio でのマネージド データベース オブジェクトのデバッグでは、サーバーで実行するルーチン内の "step into" ステートメントや "step over" ステートメントなど、一般的なデバッグ機能すべてがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-108">Managed database object debugging in Visual Studio supports all common debugging features, such as "step into" and "step over" statements within routines executing on the server.</span></span> <span data-ttu-id="9ab43-109">デバッグ中は、ブレークポイントの設定、呼び出し履歴の調査、変数の調査、変数値の変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-109">Debuggers can set breakpoints, inspect the call stack, inspect variables, and modify variable values while debugging.</span></span> <span data-ttu-id="9ab43-110">Visual Studio .NET 2003 は、CLR 統合プログラミングまたはデバッグには使用できない点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="9ab43-110">Note that Visual Studio .NET 2003 cannot be used for CLR integration programming or debugging.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="9ab43-111">には .NET Framework がプレインストールされていますが、Visual Studio .NET 2003 では .NET Framework 2.0 アセンブリを使用できません。</span><span class="sxs-lookup"><span data-stu-id="9ab43-111">includes the .NET Framework pre-installed, and Visual Studio .NET 2003 cannot use the .NET Framework 2.0 assemblies.</span></span>  
  
 <span data-ttu-id="9ab43-112">Visual Studio を使用したマネージコードのデバッグの詳細については、Visual Studio ドキュメントの「[マネージコードのデバッグ](https://go.microsoft.com/fwlink/?LinkId=120377)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ab43-112">For more information about debugging managed code using Visual Studio, see the "[Debugging Managed Code](https://go.microsoft.com/fwlink/?LinkId=120377)" topic in the Visual Studio documentation.</span></span>  
  
## <a name="debugging-permissions-and-restrictions"></a><span data-ttu-id="9ab43-113">デバッグに関する権限と制限事項</span><span class="sxs-lookup"><span data-stu-id="9ab43-113">Debugging Permissions and Restrictions</span></span>  
 <span data-ttu-id="9ab43-114">デバッグは高度な権限を持つ操作であるため、では**sysadmin**固定サーバーロールのメンバーだけがこの操作を実行でき [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-114">Debugging is a highly privileged operation, and therefore only members of the **sysadmin** fixed server role are allowed to do so in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="9ab43-115">デバッグ中には、次の制限事項が適用されます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-115">The following restrictions apply while debugging:</span></span>  
  
-   <span data-ttu-id="9ab43-116">CLR ルーチンを同時にデバッグできるデバッガー インスタンスは 1 つに制限されます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-116">Debugging CLR routines is restricted to one debugger instance at a time.</span></span> <span data-ttu-id="9ab43-117">この制限が適用されるのは、ブレークポイントに到達するとすべての CLR コードの実行が停止し、デバッガーがブレークポイントから先に動作を進めるまで、コードの実行を再開できないことが理由です。</span><span class="sxs-lookup"><span data-stu-id="9ab43-117">This limitation applies because all CLR code execution freezes when a break point is hit and execution does not continue until the debugger advances from the break point.</span></span> <span data-ttu-id="9ab43-118">ただし、他の接続での [!INCLUDE[tsql](../../../includes/tsql-md.md)] のデバッグは続行できます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-118">However, you can continue debugging [!INCLUDE[tsql](../../../includes/tsql-md.md)] in other connections.</span></span> <span data-ttu-id="9ab43-119">[!INCLUDE[tsql](../../../includes/tsql-md.md)] デバッグによりサーバーの他の実行が停止することはありませんが、デバッグがロックをかけると、他の接続が待機することになる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9ab43-119">Although [!INCLUDE[tsql](../../../includes/tsql-md.md)] debugging does not freeze other executions on the server, it could cause other connections to wait by holding a lock.</span></span>  
  
-   <span data-ttu-id="9ab43-120">デバッグできるのは、既存の接続ではなく新しい接続のみです。これは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] が、接続が行われる前のクライアントとデバッガーの環境に関する情報を必要とするためです。</span><span class="sxs-lookup"><span data-stu-id="9ab43-120">Existing connections cannot be debugged, only new connections, as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] requires information about the client and debugger environment before the connection can be made.</span></span>  
  
 <span data-ttu-id="9ab43-121">[!INCLUDE[tsql](../../../includes/tsql-md.md)] コードと CLR コードのデバッグは、上記の制限事項により、実稼働サーバーではなくテスト サーバーで行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="9ab43-121">Due to the above restrictions, we recommend that [!INCLUDE[tsql](../../../includes/tsql-md.md)] and CLR code be debugged on a test server, and not on a production server.</span></span>  
  
## <a name="overview-of-debugging-managed-database-objects"></a><span data-ttu-id="9ab43-122">マネージド データベース オブジェクトのデバッグの概要</span><span class="sxs-lookup"><span data-stu-id="9ab43-122">Overview of Debugging Managed Database Objects</span></span>  
 <span data-ttu-id="9ab43-123">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のデバッグは、接続ごとのモデルに準拠します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-123">Debugging in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] follows a per-connection model.</span></span> <span data-ttu-id="9ab43-124">デバッガーは、デバッガーがアタッチされているクライアント接続のみに関係したアクティビティを検出してデバッグを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-124">A debugger can detect and debug activities only to the client connection to which it is attached.</span></span> <span data-ttu-id="9ab43-125">デバッガーの機能は、接続の種類による制限を受けないので、表形式のデータ ストリーム (TDS) 接続と HTTP 接続の両方をデバッグできます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-125">Because the functionality of the debugger is not limited by the type of connection, both tabular data stream (TDS) and HTTP connections can be debugged.</span></span> <span data-ttu-id="9ab43-126">ただし、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、既存の接続をデバッグできません。</span><span class="sxs-lookup"><span data-stu-id="9ab43-126">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not allow debugging existing connections.</span></span> <span data-ttu-id="9ab43-127">デバッグでは、サーバーで実行するルーチン内のすべての一般的なデバッグ機能をサポートします。</span><span class="sxs-lookup"><span data-stu-id="9ab43-127">Debugging supports all common debugging features within routines executing on the server.</span></span> <span data-ttu-id="9ab43-128">デバッガーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] との間のやり取りは、分散 COM (コンポーネント オブジェクト モデル) 経由で行われます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-128">The interaction between a debugger and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] happens through distributed Component Object Model (COM).</span></span>  
  
 <span data-ttu-id="9ab43-129">マネージストアドプロシージャ、関数、トリガー、ユーザー定義型、および集計のデバッグの詳細およびシナリオについては、Visual Studio ドキュメントの「[SQL SERVER CLR Integration Database デバッグ](https://go.microsoft.com/fwlink/?LinkId=120378)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ab43-129">For more information and scenarios about debugging managed stored procedures, functions, triggers, user-defined types, and aggregates, see the "[SQL Server CLR Integration Database Debugging](https://go.microsoft.com/fwlink/?LinkId=120378)" topic in the Visual Studio documentation.</span></span>  
  
 <span data-ttu-id="9ab43-130">Visual Studio を使用してリモートで開発およびデバッグを行うには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インスタンスで TCP/IP ネットワーク プロトコルを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9ab43-130">The TCP/IP network protocol must be enabled on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance in order to use Visual Studio for remote development, debugging, and development.</span></span> <span data-ttu-id="9ab43-131">サーバーで TCP/IP プロトコルを有効にする方法の詳細については、「[クライアントプロトコルを構成する](../../database-engine/configure-windows/configure-client-protocols.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ab43-131">For more information about enabling TCP/IP protocol on the server, see [Configure Client Protocols](../../database-engine/configure-windows/configure-client-protocols.md).</span></span>  
  
#### <a name="to-debug-a-managed-database-object"></a><span data-ttu-id="9ab43-132">マネージド データベース オブジェクトをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="9ab43-132">To debug a managed database object</span></span>  
  
1.  <span data-ttu-id="9ab43-133">Microsoft Visual Studio を開き、新しい [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] プロジェクトを作成して、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスでデータベースへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-133">Open Microsoft Visual Studio, create a new [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] project, and establish a connection to a database on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="9ab43-134">新しい型を作成します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-134">Create a new type.</span></span> <span data-ttu-id="9ab43-135">**ソリューションエクスプローラー**で、プロジェクトを右クリックし、[**追加**]、[**新しい項目...** ] の順に選択します。[**新しい項目の追加**] ウィンドウで、[**ストアドプロシージャ**]、[**ユーザー定義関数**]、[**ユーザー定義型**]、[**トリガー**]、[**集計**]、または [**クラス**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-135">In **Solution Explorer**, right-click the project, select **Add** and **New Item...** From the **Add New Item** window, select **Stored Procedure**, **User-Defined Function**, **User-Defined Type**, **Trigger**, **Aggregate**, or **Class**.</span></span> <span data-ttu-id="9ab43-136">新しい種類のソースファイルの名前を指定し、[**追加**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9ab43-136">Specify a name for the source file of the new type and click **Add**.</span></span>  
  
3.  <span data-ttu-id="9ab43-137">テキスト エディターに新しい型のコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-137">Add code for the new type to the text editor.</span></span> <span data-ttu-id="9ab43-138">ストアド プロシージャの例のサンプル コードについては、後のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ab43-138">For sample code for an example stored procedure, see the section later in this topic.</span></span>  
  
4.  <span data-ttu-id="9ab43-139">型をテストするスクリプトを追加します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-139">Add a script that tests the type.</span></span> <span data-ttu-id="9ab43-140">**ソリューションエクスプローラー**で、[ **TestScripts** ] ディレクトリを展開し、[ **test .sql** ] をダブルクリックして、既定のテストスクリプトソースファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-140">In **Solution Explorer**, expand the **TestScripts** directory double-click **Test.sql** to open the default test script source file.</span></span> <span data-ttu-id="9ab43-141">デバッグするコードを呼び出すテスト スクリプトをテキスト エディターに追加します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-141">Add the test script, one that invokes the code to be debugged, to the text editor.</span></span> <span data-ttu-id="9ab43-142">サンプル スクリプトについては、下記を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ab43-142">See below for a sample script.</span></span>  
  
5.  <span data-ttu-id="9ab43-143">ソース コードに 1 つ以上のブレークポイントを配置します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-143">Place one or more breakpoints in the source code.</span></span> <span data-ttu-id="9ab43-144">テキストエディターで、デバッグする関数またはルーチン内のコード行を右クリックし、[**ブレークポイント**] と [**ブレークポイントの挿入**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-144">Right-click on a line of code in the text editor, within the function or routine you want to debug, and select **Breakpoint** and **Insert Breakpoint**.</span></span> <span data-ttu-id="9ab43-145">ブレークポイントが追加され、コード行が赤で強調表示されます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-145">The breakpoint is added, highlighting the line of code in red.</span></span>  
  
6.  <span data-ttu-id="9ab43-146">[**デバッグ**] メニューの [**デバッグ開始**] をクリックして、プロジェクトをコンパイル、配置、およびテストします。</span><span class="sxs-lookup"><span data-stu-id="9ab43-146">In the **Debug** menu, select **Start Debugging** to compile, deploy, and test the project.</span></span> <span data-ttu-id="9ab43-147">Test.sql のテスト スクリプトが実行され、マネージド データベース オブジェクトが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-147">The test script in Test.sql will be run and the managed database object will be invoked.</span></span>  
  
7.  <span data-ttu-id="9ab43-148">命令ポインターを表す黄色い矢印がブレークポイントに表示されると、コードの実行が一時停止され、マネージド データベース オブジェクトのデバッグを開始できます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-148">When the yellow arrow designating the instruction pointer appears at the breakpoint code execution pauses and you can begin debugging your managed database object.</span></span> <span data-ttu-id="9ab43-149">[**デバッグ**] メニューから**ステップオーバー**して、命令ポインターを次のコード行に進めることができます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-149">You can **Step Over** from the **Debug** menu to advance the instruction pointer to the next line of code.</span></span> <span data-ttu-id="9ab43-150">[**ローカル**] ウィンドウは、命令ポインターで現在強調表示されているオブジェクトの状態を確認するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-150">The **Locals** window is used to observe the state of the objects currently highlighted by the instruction pointer.</span></span> <span data-ttu-id="9ab43-151">変数は [**ウォッチ**] ウィンドウに追加できます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-151">Variables can be added to the **Watch** window.</span></span> <span data-ttu-id="9ab43-152">監視される変数の状態は、変数が命令ポインターにより現在強調表示されているコード行にあるときだけでなく、デバッグ セッション全体で見ることができます。</span><span class="sxs-lookup"><span data-stu-id="9ab43-152">The state of watched variables can be observed throughout the entire debugging session, not only when the variable is in the line of code currently highlighted by instruction pointer.</span></span> <span data-ttu-id="9ab43-153">[デバッグ] メニューの [続行] をクリックし、命令ポインターを次のブレークポイントに進めるか、ブレークポイントがこれ以上ない場合にはルーチンの実行を完了します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-153">Select Continue from the Debug menu to advance the instruction pointer to the next breakpoint or to complete execution of the routine if there are no more breakpoints.</span></span>  
  
### <a name="example"></a><span data-ttu-id="9ab43-154">例</span><span class="sxs-lookup"><span data-stu-id="9ab43-154">Example</span></span>  
 <span data-ttu-id="9ab43-155">次の例では、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のバージョンを呼び出し元に返します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-155">The following example returns the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] version to the caller.</span></span>  
  
 <span data-ttu-id="9ab43-156">C#</span><span class="sxs-lookup"><span data-stu-id="9ab43-156">C#</span></span>  
  
```  
using System;  
using System.Data;  
using System.Data.SqlTypes;  
using System.Data.SqlClient;  
using Microsoft.SqlServer.Server;   
  
public class StoredProcedures   
{  
   [Microsoft.SqlServer.Server.SqlProcedure]  
   public static void GetVersion()  
   {  
   using(SqlConnection connection = new SqlConnection("context connection=true"))   
   {  
      connection.Open();  
      SqlCommand command = new SqlCommand("select @@version",  
                                           connection);  
      SqlContext.Pipe.ExecuteAndSend(command);  
      }  
   }  
}  
```  
  
 <span data-ttu-id="9ab43-157">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ab43-157">Visual Basic</span></span>  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.Sql  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
Imports System.Data.SqlClient  
  
Partial Public Class StoredProcedures   
    <Microsoft.SqlServer.Server.SqlProcedure> _  
    Public Shared Sub GetVersion()  
        Using connection As New SqlConnection("context connection=true")  
            connection.Open()  
            Dim command As New SqlCommand("SELECT @@VERSION", connection)  
            SqlContext.Pipe.ExecuteAndSend(command)  
        End Using  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="9ab43-158">上で定義した GetVersion ストアド プロシージャを呼び出すテスト スクリプトを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9ab43-158">The following is a test script that invokes the GetVersion stored procedure defined above.</span></span>  
  
```  
EXEC GetVersion  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ab43-159">参照</span><span class="sxs-lookup"><span data-stu-id="9ab43-159">See Also</span></span>  
 [<span data-ttu-id="9ab43-160">CLR &#40;共通言語ランタイム&#41; 統合のプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="9ab43-160">Common Language Runtime &#40;CLR&#41; Integration Programming Concepts</span></span>](common-language-runtime-clr-integration-programming-concepts.md)  
  
  
