---
title: ビジネスロジックハンドラーをデバッグする |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- merge replication business logic handlers [SQL Server replication]
- business logic handlers [SQL Server replication]
- BusinessLogicModule class
ms.assetid: edd0d17a-0e9c-4c28-8395-a7d47e8ce3d6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7b255407783b1e52a376e562ec910f8b123e42c1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632398"
---
# <a name="debug-a-business-logic-handler-replication-programming"></a><span data-ttu-id="d2c0c-102">ビジネス ロジック ハンドラーのデバッグ (レプリケーション プログラミング)</span><span class="sxs-lookup"><span data-stu-id="d2c0c-102">Debug a Business Logic Handler (Replication Programming)</span></span>
  <span data-ttu-id="d2c0c-103">マージ サブスクリプションの同期時にカスタム ビジネス ロジックを呼び出すには、ビジネス ロジック ハンドラーを使用します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-103">Use a business logic handler to invoke custom business logic when a merge subscription is synchronized.</span></span> <span data-ttu-id="d2c0c-104">詳細については、「[Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md)」(マージ同期中のビジネス ロジックの実行) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-104">For more information, see [Execute Business Logic During Merge Synchronization](merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
 <span data-ttu-id="d2c0c-105">マージ レプリケーション競合回避モジュール (replrec.dll) は、ビジネス ロジックを含むマネージド コード アセンブリを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-105">The Merge Replication Reconciler (replrec.dll) calls the managed code assembly containing the business logic.</span></span> <span data-ttu-id="d2c0c-106">ほとんどの場合、replrec.dll とカスタム ビジネス ロジックは、マージ エージェントが実行されるコンピューター (プル サブスクリプションの場合はサブスクライバー、プッシュ サブスクリプションの場合はディストリビューター) で実行されます。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-106">In most cases, replrec.dll and the custom business logic is executed on the computer where the Merge Agent runs (at the Subscriber for a pull subscription or at the Distributor for a push subscription).</span></span> <span data-ttu-id="d2c0c-107">Web 同期の場合、または [!INCLUDE[ssEW](../../includes/ssew-md.md)] サブスクライバーの場合、競合回避モジュールとカスタム ビジネス ロジックは Web サーバーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-107">In the case of Web synchronization, or in the case of a [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscriber, the reconciler and the custom business logic is executed on the Web server.</span></span>  
  
### <a name="to-debug-a-business-logic-handler-on-a-local-computer"></a><span data-ttu-id="d2c0c-108">ローカル コンピューターでビジネス ロジック ハンドラーをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="d2c0c-108">To debug a business logic handler on a local computer</span></span>  
  
1.  <span data-ttu-id="d2c0c-109">パブリッシングとディストリビューションを構成し、パブリケーションを作成し、パブリケーションへのサブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-109">Configure publishing and distribution, create a publication, and create a subscription to the publication.</span></span> <span data-ttu-id="d2c0c-110">詳細については、「[パブリッシングおよびディストリビューションの構成](configure-publishing-and-distribution.md)」と「[パブリケーションの作成](publish/create-a-publication.md)」をご参照ください。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-110">For more information, see [Configure Publishing and Distribution](configure-publishing-and-distribution.md) and [Create a Publication](publish/create-a-publication.md).</span></span>  
  
2.  <span data-ttu-id="d2c0c-111">ビジネス ロジック ハンドラーを作成して登録します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-111">Create and register a business logic handler.</span></span> <span data-ttu-id="d2c0c-112">詳細については、「 [マージ アーティクルのビジネス ロジック ハンドラーの実装](implement-a-business-logic-handler-for-a-merge-article.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-112">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="d2c0c-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio で、マージ エージェントをプログラムで同期的に起動するレプリケーション管理オブジェクト (RMO) プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-113">Create a Replication Management Objects (RMO) project in [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Studio that programmatically starts the Merge Agent synchronously.</span></span> <span data-ttu-id="d2c0c-114">詳細については、「 [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-114">For more information, see [Synchronize a Pull Subscription](synchronize-a-pull-subscription.md).</span></span>  
  
4.  <span data-ttu-id="d2c0c-115">ビジネス ロジック ハンドラー コードのデバッグ対象のメソッドまたはクラス コンストラクター内にブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-115">Set a breakpoint in the business logic handler code, either in the method being debugged or in the class constructor.</span></span> <span data-ttu-id="d2c0c-116">ビジネス ロジック ハンドラーで実装可能なメソッドに詳細については、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> メソッドのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-116">For more information about the methods that can be implemented in a business logic handler, see the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> methods topic.</span></span>  
  
5.  <span data-ttu-id="d2c0c-117">ビジネス ロジック ハンドラーをデバッグ モードでビルドし、手順 1. で登録した場所にアセンブリとデバッグ シンボル ファイル (.pdb) を配置します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-117">Build the business logic handler in debug mode and deploy the assembly and debugging symbol file (.pdb) in the location registered in step 1.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d2c0c-118">デバッグを簡素化するには、ビジネス ロジック ハンドラー プロジェクトとサブスクリプションを同期するプロジェクトの両方を含む単一の Visual Studio .NET ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-118">To simplify debugging, create a single Visual Studio .NET solution that contains both the business logic handler project and the project that synchronizes the subscription.</span></span> <span data-ttu-id="d2c0c-119">その場合は、同期プロジェクトをスタートアップ プロジェクトとして設定し、デバッグ時に手順 1. で登録した場所にビジネス ロジック アセンブリを配置するようにビルド環境を構成します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-119">In this case, set the synchronization project as the startup project, and configure the build environment to deploy the business logic assembly to the location registered in step 1 during debugging.</span></span>  
  
6.  <span data-ttu-id="d2c0c-120">サブスクリプションまたはパブリケーション データベースに対して、挿入、更新、削除のいずれかのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-120">Execute insert, update, or delete commands against the subscription or publication database.</span></span> <span data-ttu-id="d2c0c-121">コマンドと実行場所は、デバッグ対象のメソッドによって異なります。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-121">The command and execution location depends on the method being debugged.</span></span>  
  
7.  <span data-ttu-id="d2c0c-122">手順 3. のプロジェクトをデバッグ モードで起動し、サブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-122">Start the project from step 3 in debug mode to synchronize the subscription.</span></span>  
  
8.  <span data-ttu-id="d2c0c-123">他のブレークポイントを設定しておらず、適切なコマンドがレプリケートされたと仮定すると、ビジネス ロジック ハンドラー内のブレークポイントに達したときに実行が停止します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-123">Assuming that no other breakpoints are set and the proper commands are replicated, the execution stops when it reaches the breakpoint in the business logic handler.</span></span>  
  
### <a name="to-debug-a-business-logic-handler-on-a-web-server-using-web-synchronization-or-for-a-sql-server-compact-subscriber"></a><span data-ttu-id="d2c0c-124">Web 同期を使用する Web サーバーまたは SQL Server Compact サブスクライバーに対してビジネス ロジック ハンドラーをデバッグするには</span><span class="sxs-lookup"><span data-stu-id="d2c0c-124">To debug a business logic handler on a Web server using Web synchronization, or for a SQL Server Compact Subscriber</span></span>  
  
1.  <span data-ttu-id="d2c0c-125">パブリッシングとディストリビューションを構成し、パブリケーションを作成し、パブリケーションへのプル サブスクリプションを作成します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-125">Configure publishing and distribution, create a publication, and create a pull subscription to the publication.</span></span> <span data-ttu-id="d2c0c-126">パブリケーションでは、Web 同期または [!INCLUDE[ssEW](../../includes/ssew-md.md)] サブスクライバーをサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-126">The publication must support Web synchronization or [!INCLUDE[ssEW](../../includes/ssew-md.md)] Subscribers.</span></span>  
  
2.  <span data-ttu-id="d2c0c-127">ビジネス ロジック ハンドラーを作成して登録します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-127">Create and register a business logic handler.</span></span> <span data-ttu-id="d2c0c-128">詳細については、「 [マージ アーティクルのビジネス ロジック ハンドラーの実装](implement-a-business-logic-handler-for-a-merge-article.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-128">For more information, see [Implement a Business Logic Handler for a Merge Article](implement-a-business-logic-handler-for-a-merge-article.md).</span></span>  
  
3.  <span data-ttu-id="d2c0c-129">ビジネス ロジック ハンドラー コードのデバッグ対象のメソッドまたはクラス コンストラクター内にブレークポイントを設定します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-129">Set a breakpoint in the business logic handler code, either in the method being debugged or in the class constructor.</span></span> <span data-ttu-id="d2c0c-130">ビジネス ロジック ハンドラーで実装可能なメソッドに詳細については、 <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> メソッドのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-130">For more information about the methods that can be implemented in a business logic handler, see the <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule> methods topic.</span></span>  
  
4.  <span data-ttu-id="d2c0c-131">ビジネス ロジック ハンドラーをデバッグ モードでビルドし、手順 1. で登録した場所にある Web サーバーにアセンブリとデバッグ シンボル ファイル (.pdb) を配置します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-131">Build the business logic handler in debug mode and deploy the assembly and debugging symbol file (.pdb) at the Web server in the location registered in step 1.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d2c0c-132">アセンブリが使用中であるためにビジネス ロジック ハンドラーのビルドに失敗した場合は、Web サーバーでコマンド プロンプトからコマンド `iisreset` を入力し、Web サーバーをリセットします。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-132">If the business logic handler fails to build because the assembly is in use, type the command `iisreset` on the Web server at the command prompt to reset the Web server.</span></span>  
  
5.  <span data-ttu-id="d2c0c-133">Web 同期を有効にしてサブスクリプションを同期します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-133">Synchronize the subscription with Web synchronization enabled.</span></span> <span data-ttu-id="d2c0c-134">同期中に、Web サーバーは登録されたアセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-134">During synchronization, the Web server loads the registered assembly.</span></span>  
  
6.  <span data-ttu-id="d2c0c-135">Visual Studio .NET デバッガーを使用し、Web サーバー上の以下のプロセスのいずれかにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-135">Using the Visual Studio .NET debugger, attach to the one of the following processes on the Web server:</span></span>  
  
    -   <span data-ttu-id="d2c0c-136">w3wp.exe - Windows Server 2003。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-136">w3wp.exe - Windows Server 2003.</span></span>  
  
    -   <span data-ttu-id="d2c0c-137">inetinfo.exe - Windows 2000 および Windows XP。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-137">inetinfo.exe - Windows 2000 and Windows XP.</span></span>  
  
7.  <span data-ttu-id="d2c0c-138">**[出力]** ウィンドウで、デバッグ出力を確認し、登録されたアセンブリのシンボルが正しく読み込まれたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-138">In the **Output** window, check the debug output to verify that the symbols for the registered assembly loaded properly.</span></span> <span data-ttu-id="d2c0c-139">シンボルが読み込まれていない場合は、適切な .pdb ファイルが手順 4. でコピーされたことを確認し、手順 5. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-139">If the symbols were not loaded, ensure that the correct .pdb file was copied in step 4, and repeat step 5.</span></span>  
  
8.  <span data-ttu-id="d2c0c-140">サブスクリプションまたはパブリケーション データベースに対して、挿入、更新、削除のいずれかのコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-140">Execute insert, update, or delete commands against the subscription or publication database.</span></span> <span data-ttu-id="d2c0c-141">コマンドと実行場所は、デバッグ対象のメソッドによって異なります。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-141">The command and execution location depends on the method being debugged.</span></span>  
  
9. <span data-ttu-id="d2c0c-142">Visual Studio デバッガーを使用し、w3wp.exe プロセスにアタッチします。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-142">Using the Visual Studio debugger, attach to the w3wp.exe process.</span></span>  
  
10. <span data-ttu-id="d2c0c-143">Web 同期を使用して、サブスクリプションを再び同期します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-143">Synchronize the subscription again, using Web synchronization.</span></span>  
  
11. <span data-ttu-id="d2c0c-144">他のブレークポイントを設定しておらず、適切なコマンドがレプリケートされたと仮定すると、ビジネス ロジック ハンドラー内のブレークポイントに達したときに実行が停止します。</span><span class="sxs-lookup"><span data-stu-id="d2c0c-144">Assuming that no other breakpoints are set and the proper commands are replicated, the execution stops when it reaches the breakpoint in the business logic handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c0c-145">参照</span><span class="sxs-lookup"><span data-stu-id="d2c0c-145">See Also</span></span>  
 [<span data-ttu-id="d2c0c-146">マージ アーティクルのビジネス ロジック ハンドラーの実装</span><span class="sxs-lookup"><span data-stu-id="d2c0c-146">Implement a Business Logic Handler for a Merge Article</span></span>](implement-a-business-logic-handler-for-a-merge-article.md)  
  
  
