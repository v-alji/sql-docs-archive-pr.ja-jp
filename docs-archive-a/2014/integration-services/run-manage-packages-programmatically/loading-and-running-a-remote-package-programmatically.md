---
title: プログラムによるリモート パッケージの読み込みと実行 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- remote packages [Integration Services]
ms.assetid: 9f6ef376-3408-46bf-b5fa-fc7b18c689c9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 06565140ae8ea3603461e2944e242aa91213de47
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740153"
---
# <a name="loading-and-running-a-remote-package-programmatically"></a><span data-ttu-id="b53a5-102">プログラムによるリモート パッケージの読み込みと実行</span><span class="sxs-lookup"><span data-stu-id="b53a5-102">Loading and Running a Remote Package Programmatically</span></span>
  <span data-ttu-id="b53a5-103">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] がインストールされていないローカル コンピューターからリモート パッケージを実行するには、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] がインストールされているリモート コンピューター上でパッケージが実行されるように、パッケージを起動します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-103">To run remote packages from a local computer that does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, start the packages so that they run on the remote computer on which [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is installed.</span></span> <span data-ttu-id="b53a5-104">この操作を行うには、ローカル コンピューターで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント、Web サービス、またはリモート コンポーネントを使用して、リモート コンピューターでパッケージを起動します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-104">You do this by having the local computer use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent, a Web service, or a remote component to start the packages on the remote computer.</span></span> <span data-ttu-id="b53a5-105">ローカル コンピューターから直接リモート パッケージを起動しようとすると、パッケージがローカル コンピューターに読み込まれ、ローカル コンピューターから実行されます。</span><span class="sxs-lookup"><span data-stu-id="b53a5-105">If you try to start the remote packages directly from the local computer, the packages will load onto and try to run from the local computer.</span></span> <span data-ttu-id="b53a5-106">ローカル コンピューターに [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] がインストールされていない場合、パッケージは実行されません。</span><span class="sxs-lookup"><span data-stu-id="b53a5-106">If the local computer does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, the packages will not run.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b53a5-107">[!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] がインストールされていないクライアント コンピューターでは、パッケージを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] の外部で実行することはできません。また、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ライセンスの条項により、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] を他のコンピューターにインストールできない場合があります</span><span class="sxs-lookup"><span data-stu-id="b53a5-107">You cannot run packages outside [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] on a client computer that does not have [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed, and the terms of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] licensing might not let you install [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] on additional computers.</span></span> <span data-ttu-id="b53a5-108">([!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] はサーバー コンポーネントであるため、クライアント コンピューターに再配布できません)。</span><span class="sxs-lookup"><span data-stu-id="b53a5-108">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] is a server component and is not redistributable to client computers.</span></span>  
  
 <span data-ttu-id="b53a5-109">また、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] がインストールされているローカル コンピューターからリモート パッケージを実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="b53a5-109">Alternately, you can run a remote package from a local computer that has [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] installed.</span></span> <span data-ttu-id="b53a5-110">詳細については、「[プログラムによるローカル パッケージの読み込みと実行](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b53a5-110">For more information, see [Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md).</span></span>  
  
##  <a name="running-a-remote-package-on-the-remote-computer"></a><a name="top"></a> <span data-ttu-id="b53a5-111">リモート コンピューターでのリモート パッケージの実行</span><span class="sxs-lookup"><span data-stu-id="b53a5-111">Running a Remote Package on the Remote Computer</span></span>  
 <span data-ttu-id="b53a5-112">上で説明しましたが、リモート サーバーでリモート パッケージを実行する方法は複数あります。</span><span class="sxs-lookup"><span data-stu-id="b53a5-112">As mentioned above, there are multiple ways in which you can run a remote package on a remote server:</span></span>  
  
-   [<span data-ttu-id="b53a5-113">SQL Server エージェントを使用して、プログラムでリモート パッケージを実行する</span><span class="sxs-lookup"><span data-stu-id="b53a5-113">Use SQL Server Agent to run the remote package programmatically</span></span>](#agent)  
  
-   [<span data-ttu-id="b53a5-114">Web サービスまたはリモート コンポーネントを使用して、プログラムでリモート パッケージを実行する</span><span class="sxs-lookup"><span data-stu-id="b53a5-114">Use a Web service or remote component to run the remote package programmatically</span></span>](#service)  
  
 <span data-ttu-id="b53a5-115">このトピックでパッケージを読み込み、保存するために使用するほとんどすべてのメソッドには、`Microsoft.SqlServer.ManagedDTS` アセンブリへの参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="b53a5-115">Almost all the methods that are used in this topic to load and save packages require a reference to the `Microsoft.SqlServer.ManagedDTS` assembly.</span></span> <span data-ttu-id="b53a5-116">例外は、このトピックで説明する ADO.NET アプローチであり、への参照のみを必要とする**sp_start_job**ストアドプロシージャを実行する場合に使用し `System.Data` ます。</span><span class="sxs-lookup"><span data-stu-id="b53a5-116">The exception is the ADO.NET approach demonstrated in this topic for executing the **sp_start_job** stored procedure, which requires only a reference to `System.Data`.</span></span> <span data-ttu-id="b53a5-117">`Microsoft.SqlServer.ManagedDTS` アセンブリへの参照を新しいプロジェクトに追加した後、`using` ステートメントまたは `Imports` ステートメントを使用して <xref:Microsoft.SqlServer.Dts.Runtime> 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="b53a5-117">After you add the reference to the `Microsoft.SqlServer.ManagedDTS` assembly in a new project, import the <xref:Microsoft.SqlServer.Dts.Runtime> namespace with a `using` or `Imports` statement.</span></span>  
  
###  <a name="using-sql-server-agent-to-run-a-remote-package-programmatically-on-the-server"></a><a name="agent"></a> <span data-ttu-id="b53a5-118">SQL Server エージェントを使用した、サーバー上でのプログラムによるリモート パッケージの実行</span><span class="sxs-lookup"><span data-stu-id="b53a5-118">Using SQL Server Agent to Run a Remote Package Programmatically on the Server</span></span>  
 <span data-ttu-id="b53a5-119">次のコード例では、プログラムで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントを使用して、サーバー上のリモート パッケージを実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-119">The following code sample demonstrates how to programmatically use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent to run a remote package on the server.</span></span> <span data-ttu-id="b53a5-120">このコード例では、**sp_start_job** システム ストアド プロシージャを呼び出し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント ジョブを開始します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-120">The code sample calls the system stored procedure, **sp_start_job**, which launches a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job.</span></span> <span data-ttu-id="b53a5-121">プロシージャによって開始されるジョブの名前は `RunSSISPackage` で、このジョブはリモート コンピューターに保存されています。</span><span class="sxs-lookup"><span data-stu-id="b53a5-121">The job that the procedure launches is named `RunSSISPackage`, and this job is on the remote computer.</span></span> <span data-ttu-id="b53a5-122">その後、`RunSSISPackage` ジョブにより、リモート コンピューターでパッケージが実行されます。</span><span class="sxs-lookup"><span data-stu-id="b53a5-122">The `RunSSISPackage` job then runs the package on the remote computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b53a5-123">**sp_start_job** ストアド プロシージャの戻り値は、ストアド プロシージャが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブを正常に開始できたかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-123">The return value of the **sp_start_job** stored procedure indicates whether the stored procedure was able to start the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job successfully.</span></span> <span data-ttu-id="b53a5-124">この戻り値は、パッケージが成功したか失敗したかを示しません。</span><span class="sxs-lookup"><span data-stu-id="b53a5-124">The return value does not indicate whether the package succeeded or failed.</span></span>  
  
 <span data-ttu-id="b53a5-125">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのジョブから実行するパッケージのトラブルシューティングについては、Microsoft の記事「[SQL Server エージェントのジョブ ステップから SSIS パッケージを呼び出したときに SSIS パッケージが実行されない](https://support.microsoft.com/kb/918760)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b53a5-125">For information on troubleshooting packages that are run from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs, see the Microsoft article, [An SSIS package does not run when you call the SSIS package from a SQL Server Agent job step](https://support.microsoft.com/kb/918760).</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="b53a5-126">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="b53a5-126">Sample Code</span></span>  
  
```vb  
Imports System.Data  
Imports System.Data.SqlClient  
  
Module Module1  
  
  Sub Main()  
  
    Dim jobConnection As SqlConnection  
    Dim jobCommand As SqlCommand  
    Dim jobReturnValue As SqlParameter  
    Dim jobParameter As SqlParameter  
    Dim jobResult As Integer  
  
    jobConnection = New SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI")  
    jobCommand = New SqlCommand("sp_start_job", jobConnection)  
    jobCommand.CommandType = CommandType.StoredProcedure  
  
    jobReturnValue = New SqlParameter("@RETURN_VALUE", SqlDbType.Int)  
    jobReturnValue.Direction = ParameterDirection.ReturnValue  
    jobCommand.Parameters.Add(jobReturnValue)  
  
    jobParameter = New SqlParameter("@job_name", SqlDbType.VarChar)  
    jobParameter.Direction = ParameterDirection.Input  
    jobCommand.Parameters.Add(jobParameter)  
    jobParameter.Value = "RunSSISPackage"  
  
    jobConnection.Open()  
    jobCommand.ExecuteNonQuery()  
    jobResult = DirectCast(jobCommand.Parameters("@RETURN_VALUE").Value, Integer)  
    jobConnection.Close()  
  
    Select Case jobResult  
      Case 0  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.")  
      Case Else  
        Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.")  
    End Select  
    Console.Read()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using System.Data;  
using System.Data.SqlClient;  
  
namespace LaunchSSISPackageAgent_CS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      SqlConnection jobConnection;  
      SqlCommand jobCommand;  
      SqlParameter jobReturnValue;  
      SqlParameter jobParameter;  
      int jobResult;  
  
      jobConnection = new SqlConnection("Data Source=(local);Initial Catalog=msdb;Integrated Security=SSPI");  
      jobCommand = new SqlCommand("sp_start_job", jobConnection);  
      jobCommand.CommandType = CommandType.StoredProcedure;  
  
      jobReturnValue = new SqlParameter("@RETURN_VALUE", SqlDbType.Int);  
      jobReturnValue.Direction = ParameterDirection.ReturnValue;  
      jobCommand.Parameters.Add(jobReturnValue);  
  
      jobParameter = new SqlParameter("@job_name", SqlDbType.VarChar);  
      jobParameter.Direction = ParameterDirection.Input;  
      jobCommand.Parameters.Add(jobParameter);  
      jobParameter.Value = "RunSSISPackage";  
  
      jobConnection.Open();  
      jobCommand.ExecuteNonQuery();  
      jobResult = (Int32)jobCommand.Parameters["@RETURN_VALUE"].Value;  
      jobConnection.Close();  
  
      switch (jobResult)  
      {  
        case 0:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, started successfully.");  
          break;  
        default:  
          Console.WriteLine("SQL Server Agent job, RunSISSPackage, failed to start.");  
          break;  
      }  
      Console.Read();  
    }  
  }  
}  
```  
  
 
  
###  <a name="using-a-web-service-or-remote-component-to-run-a-remote-package-programmatically"></a><a name="service"></a> <span data-ttu-id="b53a5-127">Web サービスまたはリモート コンポーネントを使用した、プログラムによるリモート パッケージの実行</span><span class="sxs-lookup"><span data-stu-id="b53a5-127">Using a Web Service or Remote Component to Run a Remote Package Programmatically</span></span>  
 <span data-ttu-id="b53a5-128">上記のサーバー上でプログラムによってパッケージを実行するためのソリューションでは、サーバー上にカスタム コードを用意する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b53a5-128">The previous solution for running packages programmatically on the server does not require any custom code on the server.</span></span> <span data-ttu-id="b53a5-129">ただし、SQL Server エージェントに依存せずにパッケージを実行するソリューションが好ましいこともあります。</span><span class="sxs-lookup"><span data-stu-id="b53a5-129">However, you may prefer a solution that does not rely on SQL Server Agent to execute packages.</span></span> <span data-ttu-id="b53a5-130">次の例では、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージをローカルで起動するためにサーバー上で作成できる Web サービスと、この Web サービスをクライアント コンピューターから呼び出すために使用できるテスト アプリケーションを示します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-130">The following example demonstrates a Web service that can be created on the server to start [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages locally, and a test application that can be used to call the Web service from a client computer.</span></span> <span data-ttu-id="b53a5-131">Web サービスではなくリモート コンポーネントを作成する場合は、同じコード ロジックをほとんど変更せずにリモート コンポーネントで使用できます。</span><span class="sxs-lookup"><span data-stu-id="b53a5-131">If you prefer to create a remote component instead of a Web service, you can use the same code logic with very few changes in a remote component.</span></span> <span data-ttu-id="b53a5-132">ただし、リモート コンポーネントを使用する場合は、Web サービスよりも広範な設定が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="b53a5-132">However a remote component may require more extensive configuration than a Web service.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b53a5-133">認証および承認が既定の設定である場合、Web サービスには一般に SQL Server またはファイル システムにアクセスしてパッケージを読み込み、実行するための十分な権限がありません。</span><span class="sxs-lookup"><span data-stu-id="b53a5-133">With its default settings for authentication and authorization, a Web service generally does not have sufficient permissions to access SQL Server or the file system to load and execute packages.</span></span> <span data-ttu-id="b53a5-134">**web.config** ファイルで認証と承認の設定を構成し、必要に応じてデータベースおよびファイル システム アクセス許可を割り当てることにより、Web サービスに適切なアクセス許可を割り当てる必要がある場合があります。</span><span class="sxs-lookup"><span data-stu-id="b53a5-134">You may have to assign appropriate permissions to the Web service by configuring its authentication and authorization settings in the **web.config** file and assigning database and file system permissions as appropriate.</span></span> <span data-ttu-id="b53a5-135">Web、データベース、およびファイル システムの権限の詳細については、このトピックでは説明しません。</span><span class="sxs-lookup"><span data-stu-id="b53a5-135">A complete discussion of Web, database, and file system permissions is beyond the scope of this topic.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b53a5-136">SSIS パッケージ ストアを操作するための <xref:Microsoft.SqlServer.Dts.Runtime.Application> クラスのメソッドでは、"."、localhost、またはローカル サーバーのサーバー名のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b53a5-136">The methods of the <xref:Microsoft.SqlServer.Dts.Runtime.Application> class for working with the SSIS Package Store support only ".", localhost, or the server name for the local server.</span></span> <span data-ttu-id="b53a5-137">"(local)" は使用できません。</span><span class="sxs-lookup"><span data-stu-id="b53a5-137">You cannot use "(local)".</span></span>  
  
### <a name="sample-code"></a><span data-ttu-id="b53a5-138">サンプル コード</span><span class="sxs-lookup"><span data-stu-id="b53a5-138">Sample Code</span></span>  
 <span data-ttu-id="b53a5-139">次のコード例では、Web サービスを作成およびテストする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-139">The following code samples show how to create and test the Web service.</span></span>  
  
#### <a name="creating-the-web-service"></a><span data-ttu-id="b53a5-140">Web サービスの作成</span><span class="sxs-lookup"><span data-stu-id="b53a5-140">Creating the Web Service</span></span>  
 <span data-ttu-id="b53a5-141">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] パッケージは、ファイルや SQL Server から直接読み込んだり、SSIS パッケージ ストアから読み込んだりすることができます。SSIS パッケージ ストアは、SQL Server および特別なファイル システム フォルダー内のパッケージ ストレージを管理します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-141">An [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package can be loaded directly from a file, directly from SQL Server, or from the SSIS Package Store, which manages package storage in both SQL Server and special file system folders.</span></span> <span data-ttu-id="b53a5-142">このサンプルは、`Select Case` コンストラクトまたは `switch` コンストラクトを使用してパッケージを起動するための適切な構文を選択し、入力引数を適切に連結することで、すべての使用可能なオプションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="b53a5-142">This sample supports all the available options by using a `Select Case` or `switch` construct to select the appropriate syntax for starting the package and to concatenate the input arguments appropriately.</span></span> <span data-ttu-id="b53a5-143">LaunchPackage Web サービス メソッドは、クライアント コンピューターで [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] アセンブリへの参照が不要になるように、パッケージの実行結果を <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 値ではなく、整数として返します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-143">The LaunchPackage Web service method returns the result of package execution as an integer instead of a <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> value so that client computers do not require a reference to any [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] assemblies.</span></span>  
  
###### <a name="to-create-a-web-service-to-run-packages-on-the-server-programmatically"></a><span data-ttu-id="b53a5-144">プログラムによってサーバー上でパッケージを実行するための Web サービスを作成するには</span><span class="sxs-lookup"><span data-stu-id="b53a5-144">To create a Web service to run packages on the server programmatically</span></span>  
  
1.  <span data-ttu-id="b53a5-145">Visual Studio を開き、任意のプログラミング言語で Web サービス プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-145">Open Visual Studio and create a Web service project in your preferred programming language.</span></span> <span data-ttu-id="b53a5-146">サンプル コードでは、プロジェクトに LaunchSSISPackageService という名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-146">The sample code uses the name LaunchSSISPackageService for the project.</span></span>  
  
2.  <span data-ttu-id="b53a5-147">への参照を追加 `Microsoft.SqlServer.ManagedDTS` し、 `Imports` ステートメントまたは `using` ステートメントを、Microsoft の**SqlServer**名前空間のコードファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-147">Add a reference to `Microsoft.SqlServer.ManagedDTS` and add an `Imports` or `using` statement to the code file for the **Microsoft.SqlServer.Dts.Runtime** namespace.</span></span>  
  
3.  <span data-ttu-id="b53a5-148">LaunchPackage Web サービス メソッドのサンプル コードをクラスに貼り付けます</span><span class="sxs-lookup"><span data-stu-id="b53a5-148">Paste the sample code for the LaunchPackage Web service method into the class.</span></span> <span data-ttu-id="b53a5-149">(このサンプルはコード ウィンドウの内容全体を表しています)。</span><span class="sxs-lookup"><span data-stu-id="b53a5-149">(The sample shows the whole contents of the code window.)</span></span>  
  
4.  <span data-ttu-id="b53a5-150">LaunchPackage メソッドの入力引数に既存のパッケージを指し示す一連の有効な値を指定することにより、Web サービスをビルドしてテストします。</span><span class="sxs-lookup"><span data-stu-id="b53a5-150">Build and test the Web service by providing a set of valid values for the input arguments of the LaunchPackage method that point to an existing package.</span></span> <span data-ttu-id="b53a5-151">たとえば、package1.dtsx がサーバーの C:\My Packages に格納されている場合、sourceType の値として "file"、sourceLocation の値として "C:\My Packages"、packageName の値として "package1" (拡張子なし) を渡します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-151">For example, if package1.dtsx is stored on the server in C:\My Packages, pass "file" as the value of the sourceType, "C:\My Packages" as the value of sourceLocation, and "package1" (without the extension) as the value of packageName.</span></span>  
  
```vb  
Imports System.Web  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports Microsoft.SqlServer.Dts.Runtime  
Imports System.IO  
  
<WebService(Namespace:="http://dtsue/")> _  
<WebServiceBinding(ConformsTo:=WsiProfiles.BasicProfile1_1)> _  
<Global.Microsoft.VisualBasic.CompilerServices.DesignerGenerated()> _  
Public Class LaunchSSISPackageService  
  Inherits System.Web.Services.WebService  
  
  ' LaunchPackage Method Parameters:  
  ' 1. sourceType: file, sql, dts  
  ' 2. sourceLocation: file system folder, (none), logical folder  
  ' 3. packageName: for file system, ".dtsx" extension is appended  
  
  <WebMethod()> _  
  Public Function LaunchPackage( _  
    ByVal sourceType As String, _  
    ByVal sourceLocation As String, _  
    ByVal packageName As String) As Integer 'DTSExecResult  
  
    Dim packagePath As String  
    Dim myPackage As Package  
    Dim integrationServices As New Application  
  
    ' Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName)  
  
    Select Case sourceType  
      Case "file"  
        ' Package is stored as a file.  
        ' Add extension if not present.  
        If String.IsNullOrEmpty(Path.GetExtension(packagePath)) Then  
          packagePath = String.Concat(packagePath, ".dtsx")  
        End If  
        If File.Exists(packagePath) Then  
          myPackage = integrationServices.LoadPackage(packagePath, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid file location: " & packagePath)  
        End If  
      Case "sql"  
        ' Package is stored in MSDB.  
        ' Combine logical path and package name.  
        If integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty) Then  
          myPackage = integrationServices.LoadFromSqlServer( _  
            packageName, "(local)", String.Empty, String.Empty, Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case "dts"  
        ' Package is managed by SSIS Package Store.  
        ' Default logical paths are File System and MSDB.  
        If integrationServices.ExistsOnDtsServer(packagePath, ".") Then  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", Nothing)  
        Else  
          Throw New ApplicationException( _  
            "Invalid package name or location: " & packagePath)  
        End If  
      Case Else  
        Throw New ApplicationException( _  
          "Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.")  
    End Select  
  
    Return myPackage.Execute()  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using System.Web;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using Microsoft.SqlServer.Dts.Runtime;  
using System.IO;  
  
[WebService(Namespace = "http://dtsue/")]  
[WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
public class LaunchSSISPackageServiceCS : System.Web.Services.WebService  
{  
  public LaunchSSISPackageServiceCS()  
  {  
    }  
  
  // LaunchPackage Method Parameters:  
  // 1. sourceType: file, sql, dts  
  // 2. sourceLocation: file system folder, (none), logical folder  
  // 3. packageName: for file system, ".dtsx" extension is appended  
  
  [WebMethod]  
  public int LaunchPackage(string sourceType, string sourceLocation, string packageName)  
  {   
  
    string packagePath;  
    Package myPackage;  
    Application integrationServices = new Application();  
  
    // Combine path and file name.  
    packagePath = Path.Combine(sourceLocation, packageName);  
  
    switch(sourceType)  
    {  
      case "file":  
        // Package is stored as a file.  
        // Add extension if not present.  
        if (String.IsNullOrEmpty(Path.GetExtension(packagePath)))  
        {  
          packagePath = String.Concat(packagePath, ".dtsx");  
        }  
        if (File.Exists(packagePath))  
        {  
          myPackage = integrationServices.LoadPackage(packagePath, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid file location: "+packagePath);  
        }  
        break;  
      case "sql":  
        // Package is stored in MSDB.  
        // Combine logical path and package name.  
        if (integrationServices.ExistsOnSqlServer(packagePath, ".", String.Empty, String.Empty))  
        {  
          myPackage = integrationServices.LoadFromSqlServer(packageName, "(local)", String.Empty, String.Empty, null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      case "dts":  
        // Package is managed by SSIS Package Store.  
        // Default logical paths are File System and MSDB.  
        if (integrationServices.ExistsOnDtsServer(packagePath, "."))  
        {  
          myPackage = integrationServices.LoadFromDtsServer(packagePath, "localhost", null);  
        }  
        else  
        {  
          throw new ApplicationException("Invalid package name or location: "+packagePath);  
        }  
        break;  
      default:  
        throw new ApplicationException("Invalid sourceType argument: valid values are 'file', 'sql', and 'dts'.");  
    }  
  
    return (Int32)myPackage.Execute();  
  
  }  
  
}  
```  
  
#### <a name="testing-the-web-service"></a><span data-ttu-id="b53a5-152">Web サービスのテスト</span><span class="sxs-lookup"><span data-stu-id="b53a5-152">Testing the Web Service</span></span>  
 <span data-ttu-id="b53a5-153">次のサンプル コンソール アプリケーションでは、Web サービスを使用してパッケージを実行します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-153">The following sample console application uses the Web service to run a package.</span></span> <span data-ttu-id="b53a5-154">Web サービスの LaunchPackage メソッドは、クライアント コンピューターで [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] アセンブリへの参照が不要になるように、パッケージの実行結果を <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 値ではなく、整数として返します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-154">The LaunchPackage method of the Web service returns the result of package execution as an integer instead of a <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> value so that client computers do not require a reference to any [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] assemblies.</span></span> <span data-ttu-id="b53a5-155">このサンプルでは、実行結果を報告するために、<xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> 値を反映する値を持つプライベート列挙を作成します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-155">The sample creates a private enumeration whose values mirror the <xref:Microsoft.SqlServer.Dts.Runtime.DTSExecResult> values to report the results of execution.</span></span>  
  
###### <a name="to-create-a-console-application-to-test-the-web-service"></a><span data-ttu-id="b53a5-156">Web サービスをテストするためのコンソール アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="b53a5-156">To create a console application to test the Web service</span></span>  
  
1.  <span data-ttu-id="b53a5-157">Visual Studio で任意のプログラミング言語を使用して、新しいコンソール アプリケーションを、Web サービス プロジェクトと同じソリューションに追加します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-157">In Visual Studio, add a new console application, using your preferred programming language, to the same solution that contains the Web service project.</span></span> <span data-ttu-id="b53a5-158">サンプル コードでは、プロジェクトに LaunchSSISPackageTest という名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-158">The sample code uses the name LaunchSSISPackageTest for the project.</span></span>  
  
2.  <span data-ttu-id="b53a5-159">新しいコンソール アプリケーションをソリューションのスタートアップ プロジェクトとして設定します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-159">Set the new console application as the startup project in the solution.</span></span>  
  
3.  <span data-ttu-id="b53a5-160">Web サービス プロジェクトの Web 参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-160">Add a Web reference for the Web service project.</span></span> <span data-ttu-id="b53a5-161">必要に応じて、Web サービス プロキシ オブジェクトに割り当てた名前に合わせて、サンプル コードの変数宣言を調整します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-161">If necessary, adjust the variable declaration in the sample code for the name that you assign to the Web service proxy object.</span></span>  
  
4.  <span data-ttu-id="b53a5-162">Main ルーチンとプライベート列挙のサンプル コードをコードに貼り付けます</span><span class="sxs-lookup"><span data-stu-id="b53a5-162">Paste the sample code for the Main routine and the private enumeration into the code.</span></span> <span data-ttu-id="b53a5-163">(このサンプルはコード ウィンドウの内容全体を表しています)。</span><span class="sxs-lookup"><span data-stu-id="b53a5-163">(The sample shows the whole contents of the code window.)</span></span>  
  
5.  <span data-ttu-id="b53a5-164">LaunchPackage メソッドを呼び出すコード行を編集し、入力引数に既存のパッケージを指し示す一連の有効な値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-164">Edit the line of code that calls the LaunchPackage method to provide a set of valid values for the input arguments that point to an existing package.</span></span> <span data-ttu-id="b53a5-165">たとえば、package1.dtsx がサーバーの C:\My Packages に格納されている場合、`sourceType` の値として "file"、`sourceLocation` の値として "C:\My Packages"、`packageName` の値として "package1" (拡張子なし) を渡します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-165">For example, if package1.dtsx is stored on the server in C:\My Packages, pass "file" as the value of `sourceType`, "C:\My Packages" as the value of `sourceLocation`, and "package1" (without the extension) as the value of `packageName`.</span></span>  
  
```vb  
Module LaunchSSISPackageTest  
  
  Sub Main()  
  
    Dim launchPackageService As New LaunchSSISPackageService.LaunchSSISPackageService  
    Dim packageResult As Integer  
  
    Try  
      packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage")  
    Catch ex As Exception  
      ' The type of exception returned by a Web service is:  
      '  System.Web.Services.Protocols.SoapException  
      Console.WriteLine("The following exception occurred: " & ex.Message)  
    End Try  
  
    Console.WriteLine(CType(packageResult, PackageExecutionResult).ToString)  
    Console.ReadKey()  
  
  End Sub  
  
  Private Enum PackageExecutionResult  
    PackageSucceeded  
    PackageFailed  
    PackageCompleted  
    PackageWasCancelled  
  End Enum  
  
End Module  
```  
  
```csharp  
using System;  
  
namespace LaunchSSISPackageSvcTestCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS launchPackageService = new LaunchSSISPackageServiceCS.LaunchSSISPackageServiceCS();  
      int packageResult = 0;  
  
      try  
      {  
        packageResult = launchPackageService.LaunchPackage("sql", String.Empty, "SimpleTestPackage");  
      }  
      catch (Exception ex)  
      {  
        // The type of exception returned by a Web service is:  
        //  System.Web.Services.Protocols.SoapException  
        Console.WriteLine("The following exception occurred: " + ex.Message);  
      }  
  
      Console.WriteLine(((PackageExecutionResult)packageResult).ToString());  
      Console.ReadKey();  
  
    }  
  
    private enum PackageExecutionResult  
    {  
      PackageSucceeded,  
      PackageFailed,  
      PackageCompleted,  
      PackageWasCancelled  
    };  
  
  }  
}  
```  
  

  
## <a name="external-resources"></a><span data-ttu-id="b53a5-166">外部リソース</span><span class="sxs-lookup"><span data-stu-id="b53a5-166">External Resources</span></span>  
  
-   <span data-ttu-id="b53a5-167">technet.microsoft.com のビデオ「[SQL Server エージェントを使用して SSIS パッケージ実行を自動化する方法 (SQL Server ビデオ)](https://technet.microsoft.com/sqlserver/ff686764.aspx)」</span><span class="sxs-lookup"><span data-stu-id="b53a5-167">Video, [How to: Automate SSIS Package Execution by Using the SQL Server Agent (SQL Server Video)](https://technet.microsoft.com/sqlserver/ff686764.aspx), on technet.microsoft.com</span></span>  
  
<span data-ttu-id="b53a5-168">![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  </span><span class="sxs-lookup"><span data-stu-id="b53a5-168">![Integration Services icon (small)](../media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="b53a5-169">マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b53a5-169">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="b53a5-170">MSDN の Integration Services のページを参照する</span><span class="sxs-lookup"><span data-stu-id="b53a5-170">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="b53a5-171">これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。</span><span class="sxs-lookup"><span data-stu-id="b53a5-171">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b53a5-172">参照</span><span class="sxs-lookup"><span data-stu-id="b53a5-172">See Also</span></span>  
 <span data-ttu-id="b53a5-173">[ローカル実行とリモート実行の違いについて](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span><span class="sxs-lookup"><span data-stu-id="b53a5-173">[Understanding the Differences between Local and Remote Execution](../run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md) </span></span>  
 <span data-ttu-id="b53a5-174">[プログラムによるローカルパッケージの読み込みと実行](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span><span class="sxs-lookup"><span data-stu-id="b53a5-174">[Loading and Running a Local Package Programmatically](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md) </span></span>  
 [<span data-ttu-id="b53a5-175">ローカル パッケージの出力の読み込み</span><span class="sxs-lookup"><span data-stu-id="b53a5-175">Loading the Output of a Local Package</span></span>](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
