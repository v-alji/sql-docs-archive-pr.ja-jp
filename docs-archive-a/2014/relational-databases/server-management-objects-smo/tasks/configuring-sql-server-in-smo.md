---
title: SMO で SQL Server を構成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- SQL Server, configuring
- configuration options [SMO]
ms.assetid: 0a372643-15cb-45a7-8665-04f1215df8ed
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6da1bca0aec650c01553b42bc2f3628b0bf7282e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739673"
---
# <a name="configuring-sql-server-in-smo"></a><span data-ttu-id="de4cc-102">SMO での SQL Server の構成</span><span class="sxs-lookup"><span data-stu-id="de4cc-102">Configuring SQL Server in SMO</span></span>
  <span data-ttu-id="de4cc-103">SMO では、オブジェクト、オブジェクト、オブジェクト、 <xref:Microsoft.SqlServer.Management.Smo.Information> <xref:Microsoft.SqlServer.Management.Smo.Settings> およびオブジェクトに、 <xref:Microsoft.SqlServer.Management.Smo.UserOptions> <xref:Microsoft.SqlServer.Management.Smo.Configuration> のインスタンスの設定と情報が含まれて [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] います。</span><span class="sxs-lookup"><span data-stu-id="de4cc-103">In SMO, the <xref:Microsoft.SqlServer.Management.Smo.Information> object, the <xref:Microsoft.SqlServer.Management.Smo.Settings> object, the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object, and the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object contain settings and information for the instance of [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="de4cc-104">には、インストールされたインスタンスの動作を記述する複数のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="de4cc-104">has numerous properties that describe the behavior of the installed instance.</span></span> <span data-ttu-id="de4cc-105">これらのプロパティでは、スタートアップ オプション、サーバーの既定、ファイルとディレクトリ、システムとプロセッサの情報、製品とバージョン、接続情報、メモリ オプション、言語と照合順序の選択、および認証モードについて記述します。</span><span class="sxs-lookup"><span data-stu-id="de4cc-105">The properties describe the startup options, the server defaults, files and directories, system and processor information, product and versions, connection information, memory options, language and collation selections, and the authentication mode.</span></span>  
  
## <a name="sql-server-configuration"></a><span data-ttu-id="de4cc-106">SQL Server 構成</span><span class="sxs-lookup"><span data-stu-id="de4cc-106">SQL Server Configuration</span></span>  
 <span data-ttu-id="de4cc-107"><xref:Microsoft.SqlServer.Management.Smo.Information> オブジェクト プロパティには、プロセッサやプラットフォームなど、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="de4cc-107">The <xref:Microsoft.SqlServer.Management.Smo.Information> object properties contain information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], such as processor and platform.</span></span>  
  
 <span data-ttu-id="de4cc-108"><xref:Microsoft.SqlServer.Management.Smo.Settings> オブジェクト プロパティには、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスに関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="de4cc-108">The <xref:Microsoft.SqlServer.Management.Smo.Settings> object properties contain information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="de4cc-109">Mail Profile および Server Account に加え、既定のデータベース ファイルおよびディレクトリも変更することができます。</span><span class="sxs-lookup"><span data-stu-id="de4cc-109">The default database file and directory can be modified in addition to the Mail Profile and the Server Account.</span></span> <span data-ttu-id="de4cc-110">これらのプロパティは、接続が続いている間は保持されます。</span><span class="sxs-lookup"><span data-stu-id="de4cc-110">These properties remain for the duration of the connection.</span></span>  
  
 <span data-ttu-id="de4cc-111"><xref:Microsoft.SqlServer.Management.Smo.UserOptions> オブジェクト プロパティには、算術、ANSI 規格、およびトランザクションに関連する現在の接続の動作に関する情報が含まれています。</span><span class="sxs-lookup"><span data-stu-id="de4cc-111">The <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object properties contain information about the current connections behavior relating to arithmetic, ANSI standards, and transactions.</span></span>  
  
 <span data-ttu-id="de4cc-112">また、<xref:Microsoft.SqlServer.Management.Smo.Configuration> オブジェクトで表現される構成オプションのセットもあります。</span><span class="sxs-lookup"><span data-stu-id="de4cc-112">There is also a set of configuration options that is represented by the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object.</span></span> <span data-ttu-id="de4cc-113">これには、`sp_configure` ストアド プロシージャによって変更可能なオプションを表すプロパティのセットが含まれています。</span><span class="sxs-lookup"><span data-stu-id="de4cc-113">It contains a set of properties that represent the options that can be modified by the `sp_configure` stored procedure.</span></span> <span data-ttu-id="de4cc-114">**優先度ブースト**、 **Recovery Interval** 、 **Network Packet Size**などのオプションは、のインスタンスのパフォーマンスを制御し [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="de4cc-114">Options such as **Priority Boost**, **Recovery Interval** and **Network Packet Size**control the performance of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="de4cc-115">これらのオプションの多くは動的に変更できますが、場合によっては、構成した値が [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスの再起動時に変更されることもあります。</span><span class="sxs-lookup"><span data-stu-id="de4cc-115">Many of these options can be changed dynamically, but in some cases the value is first configured and then changed when the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="de4cc-116">構成オプションごとに <xref:Microsoft.SqlServer.Management.Smo.Configuration> オブジェクト プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="de4cc-116">There is a <xref:Microsoft.SqlServer.Management.Smo.Configuration> object property for every configuration option.</span></span> <span data-ttu-id="de4cc-117"><xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> オブジェクトを使用すると、グローバル構成設定を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="de4cc-117">Using the <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> object you can modify the global configuration setting.</span></span> <span data-ttu-id="de4cc-118">多くのプロパティには、最大値および最小値が設定されており、これらも <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> プロパティとして格納されます。</span><span class="sxs-lookup"><span data-stu-id="de4cc-118">Many properties have maximum and minimum values that are also stored as <xref:Microsoft.SqlServer.Management.Smo.ConfigProperty> properties.</span></span> <span data-ttu-id="de4cc-119">これらのプロパティには、 <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> のインスタンスに変更をコミットするメソッドが必要 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="de4cc-119">These properties require the <xref:Microsoft.SqlServer.Management.Smo.ConfigurationBase.Alter%2A> method to commit the change to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="de4cc-120"><xref:Microsoft.SqlServer.Management.Smo.Configuration> オブジェクトの構成オプションの変更はすべて、システム管理者が行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="de4cc-120">All of the configuration options in the <xref:Microsoft.SqlServer.Management.Smo.Configuration> object must be changed by the system administrator.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="de4cc-121">例</span><span class="sxs-lookup"><span data-stu-id="de4cc-121">Examples</span></span>  
 <span data-ttu-id="de4cc-122">次のコード例では、アプリケーションを作成するプログラミング環境、プログラミング テンプレート、およびプログラミング言語を選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="de4cc-122">For the following code examples, you will have to select the programming environment, programming template and the programming language to create your application.</span></span> <span data-ttu-id="de4cc-123">詳細については、「 [Visual studio .net での VISUAL BASIC Smo プロジェクトの作成](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)」および「visual [Studio .Net で VISUAL C&#35; Smo プロジェクトを作成](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de4cc-123">For more information, see [Create a Visual Basic SMO Project in Visual Studio .NET](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md) and [Create a Visual C&#35; SMO Project in Visual Studio .NET](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md).</span></span>  
  
## <a name="modifying-sql-server-configuration-options-in-visual-basic"></a><span data-ttu-id="de4cc-124">Visual Basic での SQL Server 構成オプションの変更</span><span class="sxs-lookup"><span data-stu-id="de4cc-124">Modifying SQL Server Configuration Options in Visual Basic</span></span>  
 <span data-ttu-id="de4cc-125">このコード例は、Visual Basic .NET で構成オプションを更新する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="de4cc-125">The code example shows how to update a configuration option in Visual Basic .NET.</span></span> <span data-ttu-id="de4cc-126">また、指定された構成オプションの最大値と最小値についての情報を取得および表示しています。</span><span class="sxs-lookup"><span data-stu-id="de4cc-126">It also retrieves and displays information about maximum and minimum values for the specified configuration option.</span></span> <span data-ttu-id="de4cc-127">最後に、変更が動的に行われたのか、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスが再起動されるまで変更が格納されるのかを、ユーザーに通知しています。</span><span class="sxs-lookup"><span data-stu-id="de4cc-127">Finally, the program informs the user if the change has been made dynamically, or if it is stored until the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure2](SMO How to#SMO_VBConfigure2)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-basic"></a><span data-ttu-id="de4cc-128">Visual Basic での SQL Server 設定の変更</span><span class="sxs-lookup"><span data-stu-id="de4cc-128">Modifying SQL Server Settings in Visual Basic</span></span>  
 <span data-ttu-id="de4cc-129">このコード例では、およびでのインスタンスに関する情報を表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> し、 <xref:Microsoft.SqlServer.Management.Smo.Settings> およびオブジェクトのプロパティの設定を変更し <xref:Microsoft.SqlServer.Management.Smo.Settings> <xref:Microsoft.SqlServer.Management.Smo.UserOptions> ます。</span><span class="sxs-lookup"><span data-stu-id="de4cc-129">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="de4cc-130">この例では、<xref:Microsoft.SqlServer.Management.Smo.UserOptions> オブジェクトと <xref:Microsoft.SqlServer.Management.Smo.Settings> オブジェクトの両方に <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="de4cc-130">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="de4cc-131"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> メソッドは、これらのオブジェクトに対して個別に実行できます。</span><span class="sxs-lookup"><span data-stu-id="de4cc-131">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBConfigure1](SMO How to#SMO_VBConfigure1)]  -->  
  
## <a name="modifying-sql-server-settings-in-visual-c"></a><span data-ttu-id="de4cc-132">Visual C# での SQL Server 設定の変更</span><span class="sxs-lookup"><span data-stu-id="de4cc-132">Modifying SQL Server Settings in Visual C#</span></span>  
 <span data-ttu-id="de4cc-133">このコード例では、およびでのインスタンスに関する情報を表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> し、 <xref:Microsoft.SqlServer.Management.Smo.Settings> およびオブジェクトのプロパティの設定を変更し <xref:Microsoft.SqlServer.Management.Smo.Settings> <xref:Microsoft.SqlServer.Management.Smo.UserOptions> ます。</span><span class="sxs-lookup"><span data-stu-id="de4cc-133">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="de4cc-134">この例では、<xref:Microsoft.SqlServer.Management.Smo.UserOptions> オブジェクトと <xref:Microsoft.SqlServer.Management.Smo.Settings> オブジェクトの両方に <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="de4cc-134">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="de4cc-135"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> メソッドは、これらのオブジェクトに対して個別に実行できます。</span><span class="sxs-lookup"><span data-stu-id="de4cc-135">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
 `//Connect to the local, default instance of SQL Server.`  
  
```csharp
{  
            Server srv = new Server();  
            //Display all the configuration options.   
  
            foreach (ConfigProperty p in srv.Configuration.Properties)  
            {  
                Console.WriteLine(p.DisplayName);  
            }  
            Console.WriteLine("There are " + srv.Configuration.Properties.Count.ToString() + " configuration options.");  
            //Display the maximum and minimum values for ShowAdvancedOptions.   
            int min = 0;  
            int max = 0;  
            min = srv.Configuration.ShowAdvancedOptions.Minimum;  
            max = srv.Configuration.ShowAdvancedOptions.Maximum;  
            Console.WriteLine("Minimum and Maximum values are " + min + " and " + max + ".");  
            //Modify the value of ShowAdvancedOptions and run the Alter method.   
            srv.Configuration.ShowAdvancedOptions.ConfigValue = 0;  
            srv.Configuration.Alter();  
            //Display when the change takes place according to the IsDynamic property.   
            if (srv.Configuration.ShowAdvancedOptions.IsDynamic == true)  
            {  
                Console.WriteLine("Configuration option has been updated.");  
            }  
            else  
            {  
                Console.WriteLine("Configuration option will be updated when SQL Server is restarted.");  
            }  
        }  
```  
  
## <a name="modifying-sql-server-settings-in-powershell"></a><span data-ttu-id="de4cc-136">PowerShell での SQL Server 設定の変更</span><span class="sxs-lookup"><span data-stu-id="de4cc-136">Modifying SQL Server Settings in PowerShell</span></span>  
 <span data-ttu-id="de4cc-137">このコード例では、およびでのインスタンスに関する情報を表示 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <xref:Microsoft.SqlServer.Management.Smo.Information> し、 <xref:Microsoft.SqlServer.Management.Smo.Settings> およびオブジェクトのプロパティの設定を変更し <xref:Microsoft.SqlServer.Management.Smo.Settings> <xref:Microsoft.SqlServer.Management.Smo.UserOptions> ます。</span><span class="sxs-lookup"><span data-stu-id="de4cc-137">The code example displays information about the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] in <xref:Microsoft.SqlServer.Management.Smo.Information> and <xref:Microsoft.SqlServer.Management.Smo.Settings>, and modifies settings in <xref:Microsoft.SqlServer.Management.Smo.Settings> and <xref:Microsoft.SqlServer.Management.Smo.UserOptions>object properties.</span></span>  
  
 <span data-ttu-id="de4cc-138">この例では、<xref:Microsoft.SqlServer.Management.Smo.UserOptions> オブジェクトと <xref:Microsoft.SqlServer.Management.Smo.Settings> オブジェクトの両方に <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> メソッドがあります。</span><span class="sxs-lookup"><span data-stu-id="de4cc-138">In the example the <xref:Microsoft.SqlServer.Management.Smo.UserOptions> object and the <xref:Microsoft.SqlServer.Management.Smo.Settings> object both have an <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> method.</span></span> <span data-ttu-id="de4cc-139"><xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> メソッドは、これらのオブジェクトに対して個別に実行できます。</span><span class="sxs-lookup"><span data-stu-id="de4cc-139">You can run the <xref:Microsoft.SqlServer.Management.Smo.DefaultRuleBase.Alter%2A> methods for these individually.</span></span>  
  
```powershell
# Set the path context to the local, default instance of SQL Server.  
CD \sql\localhost\  
$srv = Get-Item default  
  
#Display information about the instance of SQL Server in Information and Settings.  
"OS Version = " + $srv.Information.OSVersion  
"State = "+ $srv.Settings.State.ToString()  
  
#Display information specific to the current user in UserOptions.  
"Quoted Identifier support = " + $srv.UserOptions.QuotedIdentifier  
  
#Modify server settings in Settings.  
$srv.Settings.LoginMode = [Microsoft.SqlServer.Management.SMO.ServerLoginMode]::Integrated  
  
#Modify settings specific to the current connection in UserOptions.  
$srv.UserOptions.AbortOnArithmeticErrors = $true  
  
#Run the Alter method to make the changes on the instance of SQL Server.  
$srv.Alter()  
```  
  
## <a name="modifying-sql-server-configuration-options-in-powershell"></a><span data-ttu-id="de4cc-140">PowerShell での SQL Server 構成オプションの変更</span><span class="sxs-lookup"><span data-stu-id="de4cc-140">Modifying SQL Server Configuration Options in PowerShell</span></span>  
 <span data-ttu-id="de4cc-141">このコード例は、Visual Basic .NET で構成オプションを更新する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="de4cc-141">The code example shows how to update a configuration option in Visual Basic .NET.</span></span> <span data-ttu-id="de4cc-142">また、指定された構成オプションの最大値と最小値についての情報を取得および表示しています。</span><span class="sxs-lookup"><span data-stu-id="de4cc-142">It also retrieves and displays information about maximum and minimum values for the specified configuration option.</span></span> <span data-ttu-id="de4cc-143">最後に、変更が動的に行われたのか、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のインスタンスが再起動されるまで変更が格納されるのかを、ユーザーに通知しています。</span><span class="sxs-lookup"><span data-stu-id="de4cc-143">Finally, the program informs the user if the change has been made dynamically, or if it is stored until the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
```powershell
#Get a server object which corresponds to the default instance replace LocalMachine with the physical server  
cd \sql\LocalMachine  
$svr = Get-Item default  
  
#enumerate its properties  
foreach ($Item in $Svr.Configuration.Properties)   
{  
 $Item.DisplayName  
}  
  
"There are " + $svr.Configuration.Properties.Count.ToString() + " configuration options."  
  
#Display the maximum and minimum values for ShowAdvancedOptions.  
$min = $svr.Configuration.ShowAdvancedOptions.Minimum  
$max = $svr.Configuration.ShowAdvancedOptions.Maximum  
"Minimum and Maximum values are " + $min.ToString() + " and " + $max.ToString() + "."  
  
#Modify the value of ShowAdvancedOptions and run the Alter method.  
$svr.Configuration.ShowAdvancedOptions.ConfigValue = 0  
$svr.Configuration.Alter()  
  
#Display when the change takes place according to the IsDynamic property.  
If ($svr.Configuration.ShowAdvancedOptions.IsDynamic -eq $true)  
 {
   "Configuration option has been updated."  
 }  
Else  
 {  
    "Configuration option will be updated when SQL Server is restarted."  
 }  
```  
