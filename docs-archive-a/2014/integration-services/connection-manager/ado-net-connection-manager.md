---
title: ADO.NET 接続マネージャー | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- connection managers [Integration Services], ADO.NET
- ADO.NET connection manager [Integration Services]
- connections [Integration Services], ADO.NET
ms.assetid: fc5daa2f-0159-4bda-9402-c87f1035a96f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9bdc25eeeae93fe0bd85deb55bfc86c55ab91ee5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641193"
---
# <a name="adonet-connection-manager"></a><span data-ttu-id="d0328-102">ADO.NET 接続マネージャー</span><span class="sxs-lookup"><span data-stu-id="d0328-102">ADO.NET Connection Manager</span></span>
  <span data-ttu-id="d0328-103">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーを使用すると、パッケージは .NET プロバイダーを使用してデータ ソースにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="d0328-103">An [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager enables a package to access data sources by using a .NET provider.</span></span> <span data-ttu-id="d0328-104">この接続マネージャーは通常、などのデータソースにアクセスするために使用され [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。また、C# などの言語を使用してマネージコードで記述されたカスタムタスクで、OLE DB と XML を介して公開されるデータソースにもアクセスします。</span><span class="sxs-lookup"><span data-stu-id="d0328-104">This connection manager is typically used to access data sources such as [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and also data sources exposed through OLE DB and XML in custom tasks that are written in managed code by using a language such C#.</span></span>  
  
 <span data-ttu-id="d0328-105">[!INCLUDE[vstecado](../../includes/vstecado-md.md)]接続マネージャーをパッケージに追加すると、は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 実行時に接続として解決される接続マネージャーを作成し、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーのプロパティを設定して、接続マネージャーをパッケージのコレクションに追加し `Connections` ます。</span><span class="sxs-lookup"><span data-stu-id="d0328-105">When you add an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager to a package, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] creates a connection manager that is resolved as an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection at run time, sets the connection manager properties, and adds the connection manager to the `Connections` collection on the package.</span></span>  
  
 <span data-ttu-id="d0328-106">接続マネージャーの `ConnectionManagerType` プロパティは、`ADO.NET` に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d0328-106">The `ConnectionManagerType` property of the connection manager is set to `ADO.NET`.</span></span> <span data-ttu-id="d0328-107">`ConnectionManagerType` の値には、接続マネージャーが使用する .NET プロバイダーの名前を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d0328-107">The value of `ConnectionManagerType` is qualified to include the name of the .NET provider that the connection manager uses.</span></span>  
  
## <a name="adonet-connection-manager-troubleshooting"></a><span data-ttu-id="d0328-108">ADO.NET 接続マネージャーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="d0328-108">ADO.NET Connection Manager Troubleshooting</span></span>  
 <span data-ttu-id="d0328-109">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーによる外部データ プロバイダーの呼び出しをログに記録できます。</span><span class="sxs-lookup"><span data-stu-id="d0328-109">You can log the calls that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data providers.</span></span> <span data-ttu-id="d0328-110">このログ機能を使用すると、 [!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーによる外部データ ソースへの接続に関するトラブルシューティングを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="d0328-110">You can use this logging capability to troubleshoot the connections that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data sources.</span></span> <span data-ttu-id="d0328-111">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーによる外部データ プロバイダーの呼び出しのログを記録するには、パッケージ ログ記録を有効にして、パッケージ レベルで **Diagnostic** イベントを選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0328-111">To log the calls that the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager makes to external data providers, enable package logging and select the **Diagnostic** event at the package level.</span></span> <span data-ttu-id="d0328-112">詳細については、「 [パッケージ実行のトラブルシューティング ツール](../troubleshooting/troubleshooting-tools-for-package-execution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0328-112">For more information, see [Troubleshooting Tools for Package Execution](../troubleshooting/troubleshooting-tools-for-package-execution.md).</span></span>  
  
 <span data-ttu-id="d0328-113">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーに読み込まれると、特定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日付データ型のデータは次の表に示す結果を生成します。</span><span class="sxs-lookup"><span data-stu-id="d0328-113">When being read by an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager, data of certain [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date data types will generate the results shown in the following table.</span></span>  
  
|<span data-ttu-id="d0328-114">SQL Server のデータ型</span><span class="sxs-lookup"><span data-stu-id="d0328-114">SQL Server data type</span></span>|<span data-ttu-id="d0328-115">結果</span><span class="sxs-lookup"><span data-stu-id="d0328-115">Result</span></span>|  
|--------------------------|------------|  
|<span data-ttu-id="d0328-116">`time`, `datetimeoffset`</span><span class="sxs-lookup"><span data-stu-id="d0328-116">`time`, `datetimeoffset`</span></span>|<span data-ttu-id="d0328-117">パッケージがパラメーター化 SQL コマンドを使用していない場合、パッケージは失敗します。</span><span class="sxs-lookup"><span data-stu-id="d0328-117">The package fails unless the package uses parameterized SQL commands.</span></span> <span data-ttu-id="d0328-118">パラメーター化 SQL コマンドを使用するには、パッケージで SQL 実行タスクを使用します。</span><span class="sxs-lookup"><span data-stu-id="d0328-118">To use parameterized SQL commands, use the Execute SQL Task in your package.</span></span> <span data-ttu-id="d0328-119">詳細については、「 [SQL 実行タスク](../control-flow/execute-sql-task.md) 」と「 [SQL 実行タスクのパラメーターとリターン コード](../parameters-and-return-codes-in-the-execute-sql-task.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0328-119">For more information, see [Execute SQL Task](../control-flow/execute-sql-task.md) and [Parameters and Return Codes in the Execute SQL Task](../parameters-and-return-codes-in-the-execute-sql-task.md).</span></span>|  
|`datetime2`|<span data-ttu-id="d0328-120">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーは、ミリ秒の値を切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="d0328-120">The [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager truncates the millisecond value.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="d0328-121">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型の詳細とそれを [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] データ型にマッピングする方法については、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」と「[Integration Services のデータ型](../data-flow/integration-services-data-types.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0328-121">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types and how they map to [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] data types, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql) and [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="adonet-connection-manager-configuration"></a><span data-ttu-id="d0328-122">ADO.NET 接続マネージャーの構成</span><span class="sxs-lookup"><span data-stu-id="d0328-122">ADO.NET Connection Manager Configuration</span></span>  
 <span data-ttu-id="d0328-123">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーは、次の方法で構成できます。</span><span class="sxs-lookup"><span data-stu-id="d0328-123">You can configure an [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager in the following ways:</span></span>  
  
 <span data-ttu-id="d0328-124">プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。</span><span class="sxs-lookup"><span data-stu-id="d0328-124">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
-   <span data-ttu-id="d0328-125">選択した .NET プロバイダーの要件を満たすように構成された、特定の接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="d0328-125">Provide a specific connection string configured to meet the requirements of the selected .NET provider.</span></span>  
  
-   <span data-ttu-id="d0328-126">プロパイダによっては、接続先のデータ ソースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="d0328-126">Depending on the provider, include the name of the data source to connect to.</span></span>  
  
-   <span data-ttu-id="d0328-127">選択したプロバイダーに適したセキュリティ資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="d0328-127">Provide security credentials as appropriate for the selected provider.</span></span>  
  
-   <span data-ttu-id="d0328-128">接続マネージャーから作成される接続を、実行時に保持するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0328-128">Indicate whether the connection that is created from the connection manager is retained at run time.</span></span>  
  
 <span data-ttu-id="d0328-129">[!INCLUDE[vstecado](../../includes/vstecado-md.md)] 接続マネージャーの多くの構成オプションは、接続マネージャーが使用する .NET プロバイダーによって異なります。</span><span class="sxs-lookup"><span data-stu-id="d0328-129">Many of configuration options of the [!INCLUDE[vstecado](../../includes/vstecado-md.md)] connection manager depend on the .NET provider that the connection manager uses.</span></span>  
  
 <span data-ttu-id="d0328-130">[!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0328-130">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topic:</span></span>  
  
-   <span data-ttu-id="d0328-131">[[ADO.NET の接続マネージャーの構成]](../configure-ado-net-connection-manager.md)</span><span class="sxs-lookup"><span data-stu-id="d0328-131">[Configure ADO.NET Connection Manager](../configure-ado-net-connection-manager.md)</span></span>  
  
 <span data-ttu-id="d0328-132">プログラムによる接続マネージャーの構成については、「 <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> 」と「 [プログラムによる接続の追加](../building-packages-programmatically/adding-connections-programmatically.md)に設定されます。</span><span class="sxs-lookup"><span data-stu-id="d0328-132">For information about configuring a connection manager programmatically, see <xref:Microsoft.SqlServer.Dts.Runtime.ConnectionManager> and [Adding Connections Programmatically](../building-packages-programmatically/adding-connections-programmatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0328-133">参照</span><span class="sxs-lookup"><span data-stu-id="d0328-133">See Also</span></span>  
 [<span data-ttu-id="d0328-134">Integration Services &#40;SSIS&#41; の接続</span><span class="sxs-lookup"><span data-stu-id="d0328-134">Integration Services &#40;SSIS&#41; Connections</span></span>](integration-services-ssis-connections.md)  
  
  
