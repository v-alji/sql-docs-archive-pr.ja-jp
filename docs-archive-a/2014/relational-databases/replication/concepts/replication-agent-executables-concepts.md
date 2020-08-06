---
title: レプリケーション エージェント実行可能ファイルの概念 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- programming interfaces [SQL Server replication]
- programming [SQL Server replication], agents
- replication [SQL Server], agents and profiles
- agents [SQL Server replication], executables
- command prompt [SQL Server replication]
ms.assetid: cba476df-d4ea-44c9-bb86-81488971e328
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73f9fe0d1a98fa1afc813cd113dcced685b4f98a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741854"
---
# <a name="replication-agent-executables-concepts"></a><span data-ttu-id="7d3c4-102">レプリケーション エージェント実行可能ファイルの概念</span><span class="sxs-lookup"><span data-stu-id="7d3c4-102">Replication Agent Executables Concepts</span></span>
  <span data-ttu-id="7d3c4-103">レプリケーション エージェントは、次のような方法でプログラムから制御できます。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-103">Replication agents can be controlled programmatically in the following ways:</span></span>  
  
-   <span data-ttu-id="7d3c4-104"><xref:Microsoft.SqlServer.Replication> 名前空間のマネージド エージェント プログラミング インターフェイスを使用する。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-104">Using the managed agent programming interfaces in the <xref:Microsoft.SqlServer.Replication> Namespace.</span></span>  
  
-   <span data-ttu-id="7d3c4-105">エージェントの実行可能ファイルを一連のパラメーターを指定してコマンド プロンプトから呼び出す。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-105">Invoking agent executable files from the command prompt with a supplied set of parameters.</span></span>  
  
 <span data-ttu-id="7d3c4-106">レプリケーション エージェントはコマンド プロンプトから直接呼び出すことができるため、コマンド ライン スクリプトをバッチ ファイル化することで、プログラムからエージェントにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-106">Directly invoking replication agents from the command prompt enables agents to be programmatically accessed from command-line scripting in batch files.</span></span> <span data-ttu-id="7d3c4-107">エージェントをコマンド プロンプトから呼び出した場合、そのエージェントは、エージェントを呼び出したユーザーまたはバッチ ファイルを実行したユーザーの [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows セキュリティ アカウント下で実行されます。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-107">When an agent is invoked from the command prompt, it runs under the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Windows security account of the user that invoked the agent or started the batch file.</span></span>  
  
 <span data-ttu-id="7d3c4-108">次のレプリケーション エージェントのインスタンスは、実行可能ファイルを使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-108">Instances of the following replication agents can be run using executable files.</span></span>  
  
-   [<span data-ttu-id="7d3c4-109">Replication Distribution Agent</span><span class="sxs-lookup"><span data-stu-id="7d3c4-109">Replication Distribution Agent</span></span>](../agents/replication-distribution-agent.md)  
  
-   [<span data-ttu-id="7d3c4-110">レプリケーション ログ リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="7d3c4-110">Replication Log Reader Agent</span></span>](../agents/replication-log-reader-agent.md)  
  
-   [<span data-ttu-id="7d3c4-111">Replication Merge Agent</span><span class="sxs-lookup"><span data-stu-id="7d3c4-111">Replication Merge Agent</span></span>](../agents/replication-merge-agent.md)  
  
-   [<span data-ttu-id="7d3c4-112">レプリケーション キュー リーダー エージェント</span><span class="sxs-lookup"><span data-stu-id="7d3c4-112">Replication Queue Reader Agent</span></span>](../agents/replication-queue-reader-agent.md)  
  
-   [<span data-ttu-id="7d3c4-113">Replication Snapshot Agent</span><span class="sxs-lookup"><span data-stu-id="7d3c4-113">Replication Snapshot Agent</span></span>](../agents/replication-snapshot-agent.md)  
  
 <span data-ttu-id="7d3c4-114">レプリケーション エージェントを呼び出す際、パフォーマンス プロファイルを使用することで、あらかじめ定義された一連のパラメーターを自動的にエージェント実行可能ファイルに渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-114">When invoking replication agents, you can use performance profiles to automatically pass a defined set of parameters to the agent executable.</span></span> <span data-ttu-id="7d3c4-115">詳しくは、「 [レプリケーション エージェント プロファイル](../agents/replication-agent-profiles.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-115">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7d3c4-116">例</span><span class="sxs-lookup"><span data-stu-id="7d3c4-116">Examples</span></span>  
 <span data-ttu-id="7d3c4-117">次の例は、レプリケーション エージェントをコマンド プロンプトから呼び出す方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-117">The following examples show how to invoke replication agents from the command prompt.</span></span> <span data-ttu-id="7d3c4-118">レプリケーション エージェントは、レプリケーション管理オブジェクト (RMO) を使用して呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-118">Replication agents can also be invoked using Replication Management Objects (RMO).</span></span> <span data-ttu-id="7d3c4-119">詳細については、「[サブスクリプションの同期 &#40;レプリケーション&#41;](../synchronize-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-119">For more information, see [Synchronize Subscriptions &#40;Replication&#41;](../synchronize-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7d3c4-120">これらの例では、読みやすくするために、改行が追加されています。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-120">Line breaks in these examples were added to improve readability.</span></span> <span data-ttu-id="7d3c4-121">バッチ ファイルの場合、コマンドは 1 行で入力する必要があります。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-121">In a batch file, commands must be made in a single line.</span></span>  
  
### <a name="running-the-snapshot-agent"></a><span data-ttu-id="7d3c4-122">スナップショット エージェントの実行</span><span class="sxs-lookup"><span data-stu-id="7d3c4-122">Running the Snapshot Agent</span></span>  
 <span data-ttu-id="7d3c4-123">次の例では、バッチ ファイルを使って、スナップショット エージェントをコマンド プロンプトから呼び出し、**AdvWorksSalesOrdersMerge** パブリケーションのスナップショットを生成しています。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-123">This example batch file invokes the Snapshot Agent from the command prompt to generate a snapshot for the **AdvWorksSalesOrdersMerge** publication.</span></span>  
  
```  
REM -- Declare variables  
SET Publisher=%InstanceName%;  
SET PublicationDB=AdventureWorks2012;   
SET Publication=AdvWorksSalesOrdersMerge;   
  
REM --Start the Snapshot Agent to generate the snapshot for AdvWorksSalesOrdersMerge.  
"C:\Program Files\Microsoft SQL Server\120\COM\SNAPSHOT.EXE" -Publication %Publication%   
-Publisher %Publisher% -Distributor %Publisher% -PublisherDB %PublicationDB%   
-ReplicationType 2 -OutputVerboseLevel 1 -DistributorSecurityMode 1 ;  
  
```  
  
### <a name="running-the-distribution-agent"></a><span data-ttu-id="7d3c4-124">ディストリビューション エージェントの実行</span><span class="sxs-lookup"><span data-stu-id="7d3c4-124">Running the Distribution Agent</span></span>  
 <span data-ttu-id="7d3c4-125">この例では、バッチ ファイルを使って、ディストリビューション エージェントをコマンド プロンプトから呼び出し、**AdvWorksProductTran** パブリケーションからの変更を、プッシュ サブスクライバーに連続してレプリケートしています。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-125">This example batch file invokes the Distribution Agent from the command prompt to continuously replicate changes from the **AdvWorksProductTran** publication to a push subscriber.</span></span>  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksProductsTran;  
  
REM -- Start the Distribution Agent with four subscription streams.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\DISTRIB.EXE" -Subscriber %Subscriber%   
-SubscriberDB %SubscriptionDB% -SubscriberSecurityMode 1 -Publication %Publication%   
-Publisher %Publisher% -PublisherDB %PublicationDB% -Distributor %Publisher%   
-DistributorSecurityMode 1 -Continuous -SubscriptionType 0 -SubscriptionStreams 4 ;  
  
```  
  
### <a name="running-the-merge-agent"></a><span data-ttu-id="7d3c4-126">マージ エージェントの実行</span><span class="sxs-lookup"><span data-stu-id="7d3c4-126">Running the Merge Agent</span></span>  
 <span data-ttu-id="7d3c4-127">この例では、バッチ ファイルを使って、マージ エージェントをコマンド プロンプトから呼び出し、**AdvWorksSalesOrdersMerge** パブリケーションにプル サブスクリプションを同期しています。</span><span class="sxs-lookup"><span data-stu-id="7d3c4-127">This example batch file invokes the Merge Agent from the command prompt to synchronize a pull subscription to the **AdvWorksSalesOrdersMerge** publication.</span></span>  
  
```  
REM -- Declare the variables.  
SET Publisher=%instancename%;  
SET Subscriber=%instancename%;  
SET PublicationDB=AdventureWorks2012;  
SET SubscriptionDB=AdventureWorks2012Replica;   
SET Publication=AdvWorksSalesOrdersMerge;  
  
REM --Start the Merge Agent with concurrent upload and download processes.  
REM -- The following command must be supplied without line breaks.  
"C:\Program Files\Microsoft SQL Server\120\COM\REPLMERG.EXE" -Publication %Publication%    
-Publisher %Publisher%  -Subscriber  %Subscriber%  -Distributor %Publisher%    
-PublisherDB %PublicationDB%  -SubscriberDB %SubscriptionDB% -PublisherSecurityMode 1    
-OutputVerboseLevel 2  -SubscriberSecurityMode 1  -SubscriptionType 1 -DistributorSecurityMode 1    
-Validate 3  -ParallelUploadDownload 1 ;  
  
```  
  
  
