---
title: Developer&#39;s ガイド (レプリケーション) |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: reference
helpviewer_keywords:
- developer's guide [SQL Server replication]
- programming [SQL Server replication]
- replication [SQL Server], development
ms.assetid: 7ee134ae-1cab-4a35-8017-8ac6d8fc64b6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d9651aec1f02d19ea3494abf242f75049a4f33f8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736241"
---
# <a name="developer39s-guide-replication"></a><span data-ttu-id="9ef93-102">Developer&#39;s ガイド (レプリケーション)</span><span class="sxs-lookup"><span data-stu-id="9ef93-102">Developer&#39;s Guide (Replication)</span></span>
  <span data-ttu-id="9ef93-103">レプリケーション トポロジをプログラムから構成、保守、監視できれば、繰り返し行うレプリケーション タスクを効率化できるという開発者側のメリットに加え、レプリケーション ベースのアプリケーションを快適に使用できるというユーザー側のメリットも生まれます。</span><span class="sxs-lookup"><span data-stu-id="9ef93-103">The ability to programmatically configure, maintain, and monitor a replication topology enables you to both simplify repeated replication tasks and improve the user experience for your replication-based applications.</span></span> <span data-ttu-id="9ef93-104">レプリケーションをプログラミングすることにより、レプリケーションのストアド プロシージャやレプリケーション エージェントの実行可能ファイルに関する知識がないエンド ユーザーに、[!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] に実装されているレプリケーション ユーザー インターフェイスの使用を強要することなく、カスタマイズされたレプリケーション機能を提供できます。</span><span class="sxs-lookup"><span data-stu-id="9ef93-104">By programming replication, your end-users can be provided with customized replication functionalities without having to be familiar with replication stored procedures and replication agent executables or having to using the replication user interface implemented by [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="9ef93-105">プログラムからレプリケーション サービスにアクセスすることによって効果が期待できるアプリケーション開発のシナリオを次に示します。</span><span class="sxs-lookup"><span data-stu-id="9ef93-105">The following are scenarios in which your applications might benefit from programmatic access to replication services:</span></span>  
  
-   <span data-ttu-id="9ef93-106">既存のエンド ユーザー アプリケーションにレプリケーション機能を追加する (ユーザーがボタンをクリックするとプル サブスクリプションが同期されるなど)。</span><span class="sxs-lookup"><span data-stu-id="9ef93-106">Adding replication functionalities to an existing end-user application, such as synchronizing a pull subscription when the user clicks a button.</span></span>   
-   <span data-ttu-id="9ef93-107">レプリケーションをリモートから管理するための Web ベースのユーザー インターフェイスを作成する。</span><span class="sxs-lookup"><span data-stu-id="9ef93-107">Creating a Web-based user interface for remotely administering replication.</span></span>    
-   <span data-ttu-id="9ef93-108">カスタム ユーザー インターフェイスを作成する (一部の管理機能だけを公開する、複数のレプリケーション トポロジをリモートから一元管理できるようにする、管理機能と同期機能を組み合わせるなど)。</span><span class="sxs-lookup"><span data-stu-id="9ef93-108">Creating a custom user interface that exposes only a subset of administration functionality, can be used to remotely administer multiple replication topologies from a single location, or that combine administration and synchronization functionalities.</span></span>    
-   <span data-ttu-id="9ef93-109">既存の監視ツールを強化する (パブリケーションやサブスクリプションの状態をディストリビューター側で監視する機能を追加するなど)。</span><span class="sxs-lookup"><span data-stu-id="9ef93-109">Improving an existing monitoring tool by adding the ability to monitor the status of a publication, subscription, or at the Distributor.</span></span>    
-   <span data-ttu-id="9ef93-110">Oracle パブリッシャーのサブスクリプションを管理または同期するカスタム アプリケーションを作成する。</span><span class="sxs-lookup"><span data-stu-id="9ef93-110">Creating a custom application to administer or synchronize subscriptions to an Oracle publisher.</span></span>    
-   <span data-ttu-id="9ef93-111">マージ サブスクリプションの同期時に実行されるビジネス ルールを独自に作成する。</span><span class="sxs-lookup"><span data-stu-id="9ef93-111">Writing customized business rules that are executed when a merge subscription is synchronized.</span></span>    
-   <span data-ttu-id="9ef93-112">新しいサブスクライバーを構成する際に繰り返し実行することのできる [!INCLUDE[tsql](../../../includes/tsql-md.md)] スクリプトを生成する。</span><span class="sxs-lookup"><span data-stu-id="9ef93-112">Generating [!INCLUDE[tsql](../../../includes/tsql-md.md)] scripts that can be run repeated when configuring new Subscribers.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="9ef93-113">では、レプリケーション エージェントを制御したり、レプリケーション トポロジを管理、監視する作業をプログラムから行うことができます。</span><span class="sxs-lookup"><span data-stu-id="9ef93-113">enables you to programmatically control replication agents and to programmatically administer and monitor a replication topology.</span></span> <span data-ttu-id="9ef93-114">レプリケーションのプログラミングの詳細については、「[レプリケーションのプログラミング概念](replication-programming-concepts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9ef93-114">To learn more about programming replication, see [Replication Programming Concepts](replication-programming-concepts.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ef93-115">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9ef93-115">In This Section</span></span>  
 [<span data-ttu-id="9ef93-116">レプリケーションのプログラミング概念</span><span class="sxs-lookup"><span data-stu-id="9ef93-116">Replication Programming Concepts</span></span>](replication-programming-concepts.md)  
 <span data-ttu-id="9ef93-117">レプリケーションを使ったアプリケーション開発の計画手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ef93-117">Describes the planning steps to develop an application that uses replication.</span></span>  
  
 [<span data-ttu-id="9ef93-118">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="9ef93-118">Replication System Stored Procedures Concepts</span></span>](replication-system-stored-procedures-concepts.md)  
 <span data-ttu-id="9ef93-119">システム ストアド プロシージャを使用した、レプリケーション トポロジのプログラム アクセスの方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="9ef93-119">Describes how system stored procedures can be used to proivide programmatic access in a replication topology.</span></span>  
  
 [<span data-ttu-id="9ef93-120">レプリケーション管理オブジェクトの概念</span><span class="sxs-lookup"><span data-stu-id="9ef93-120">Replication Management Objects Concepts</span></span>](replication-management-objects-concepts.md)  
 <span data-ttu-id="9ef93-121">レプリケーション管理オブジェクト (RMO) を使用するための概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ef93-121">Explains the concepts for using Replication Management Objects (RMO).</span></span> <span data-ttu-id="9ef93-122">これは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のレプリケーション機能をカプセル化するマネージド コード アセンブリです。</span><span class="sxs-lookup"><span data-stu-id="9ef93-122">This is a managed code assembly that encapsulates replication functionalities for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="9ef93-123">Replication Agent Executables Concepts</span><span class="sxs-lookup"><span data-stu-id="9ef93-123">Replication Agent Executables Concepts</span></span>](replication-agent-executables-concepts.md)  
 <span data-ttu-id="9ef93-124">レプリケーション エージェントの実行可能ファイルの使用について説明します。</span><span class="sxs-lookup"><span data-stu-id="9ef93-124">Describes the use of Replication Agent Executable files.</span></span>  

  
  
