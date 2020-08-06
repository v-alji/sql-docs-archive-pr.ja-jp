---
title: マージ同期中のビジネス ロジックの実行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- custom error resolution [SQL Server replication]
- custom change handling [SQL Server replication]
- errors [SQL Server replication], business logic handlers
- merge replication business logic handlers [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
- business logic handlers [SQL Server replication]
ms.assetid: 9d4da2ef-c17f-4a31-a1f6-5c3b7ca85f71
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1e082cbbb46ceae712cd39925c28fe89988a3793
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630962"
---
# <a name="execute-business-logic-during-merge-synchronization"></a><span data-ttu-id="ad7af-102">マージ同期中のビジネス ロジックの実行</span><span class="sxs-lookup"><span data-stu-id="ad7af-102">Execute Business Logic During Merge Synchronization</span></span>
  <span data-ttu-id="ad7af-103">ビジネス ロジック ハンドラー フレームワークを使用すると、マネージド コードのアセンブリを記述して、マージ同期処理中に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-103">The business logic handler framework allows you to write a managed code assembly that is called during the merge synchronization process.</span></span> <span data-ttu-id="ad7af-104">このアセンブリには、データの変更、競合、およびエラーなど、同期中に発生するさまざまな状況に対処するためのビジネス ロジックを記述できます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-104">The assembly includes business logic that can respond to a number of conditions during synchronization: data changes, conflicts, and errors.</span></span> <span data-ttu-id="ad7af-105">ビジネス ロジック ハンドラー フレームワークには単純なプログラミング モデルが用意されており、マージ処理によってアセンブリに提供されるデータは ADO.NET データセットの形式になっています。このため、専用インターフェイスについての知識ではなく ADO.NET についての知識を活用できます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-105">The business logic handler framework provides a simple programming model, and the data that the merge process provides to your assembly is in the form of an ADO.NET data set, so you can leverage knowledge of ADO.NET rather than learning a proprietary interface.</span></span> <span data-ttu-id="ad7af-106">ビジネス ロジック ハンドラーのプログラミングの詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad7af-106">For more information on programming business logic handlers, see:</span></span>  
  
-   <span data-ttu-id="ad7af-107">アプリケーション プログラミング インターフェイス (API) リファレンス : <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport></span><span class="sxs-lookup"><span data-stu-id="ad7af-107">The application programming interface (API) reference: <xref:Microsoft.SqlServer.Replication.BusinessLogicSupport></span></span>  
  
-   <span data-ttu-id="ad7af-108">ビジネス ロジック ハンドラーの実装方法についての説明: [マージ アーティクルのビジネス ロジック ハンドラーの実装](../implement-a-business-logic-handler-for-a-merge-article.md)</span><span class="sxs-lookup"><span data-stu-id="ad7af-108">Instructions on how to implement a business logic handler: [Implement a Business Logic Handler for a Merge Article](../implement-a-business-logic-handler-for-a-merge-article.md)</span></span>  
  
## <a name="uses-for-business-logic-handlers"></a><span data-ttu-id="ad7af-109">ビジネス ロジック ハンドラーの用途</span><span class="sxs-lookup"><span data-stu-id="ad7af-109">Uses for Business Logic Handlers</span></span>  
 <span data-ttu-id="ad7af-110">マージ同期処理では、ビジネス ロジック ハンドラーを呼び出して、以下の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-110">The merge synchronization process can invoke business logic handlers to perform:</span></span>  
  
-   <span data-ttu-id="ad7af-111">カスタム変更処理</span><span class="sxs-lookup"><span data-stu-id="ad7af-111">Custom change handling</span></span>  
  
-   <span data-ttu-id="ad7af-112">カスタム競合解決</span><span class="sxs-lookup"><span data-stu-id="ad7af-112">Custom conflict resolution</span></span>  
  
-   <span data-ttu-id="ad7af-113">カスタム エラー解決</span><span class="sxs-lookup"><span data-stu-id="ad7af-113">Custom error resolution</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ad7af-114">指定するビジネス ロジック ハンドラーは、同期されるすべての行に対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-114">The business logic handler you specify is executed for every row that is synchronized.</span></span> <span data-ttu-id="ad7af-115">その他のアプリケーションまたはネットワーク サービスに対する複雑なロジックおよび呼び出しは、パフォーマンスに影響を与える可能性があります。</span><span class="sxs-lookup"><span data-stu-id="ad7af-115">Complex logic and calls to other applications or network services can impact performance.</span></span>  
  
### <a name="custom-change-handling"></a><span data-ttu-id="ad7af-116">カスタム変更処理</span><span class="sxs-lookup"><span data-stu-id="ad7af-116">Custom Change Handling</span></span>  
 <span data-ttu-id="ad7af-117">ビジネス ロジック ハンドラーは、競合していないデータの変更処理中に呼び出すことができ、次の 3 つの操作のいずれかを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-117">The business logic handler can be invoked during the processing of non-conflicting data changes and can perform one of three actions:</span></span>  
  
-   <span data-ttu-id="ad7af-118">データの拒否</span><span class="sxs-lookup"><span data-stu-id="ad7af-118">Reject the data</span></span>  
  
     <span data-ttu-id="ad7af-119">特定のサブスクライバーからの変更または特定のサブスクライバーへの変更を反映したくないアプリケーションに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-119">This is useful for applications that do not want changes propagated to or from a given Subscriber.</span></span> <span data-ttu-id="ad7af-120">たとえば、管理者は、サブスクライバーのパーティション内に属さない挿入をフィルター処理によって拒否したり、場合によってはサブスクライバーで実行された削除を拒否することができます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-120">For example, an administrator could filter out inserts that do not belong in the Subscriber's partition, or possibly reject deletes performed at a Subscriber.</span></span> <span data-ttu-id="ad7af-121">別の例としては、在庫が不足している場合に、サブスクライバーで入力された注文をアプリケーションが拒否できます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-121">As another example, an application could reject an order entered at a Subscriber because the inventory is no longer available.</span></span>  
  
-   <span data-ttu-id="ad7af-122">データの受け入れ</span><span class="sxs-lookup"><span data-stu-id="ad7af-122">Accept the data</span></span>  
  
     <span data-ttu-id="ad7af-123">これは、パブリッシャーまたはサブスクライバーで行われたデータの変更を反映する前に確認を行う必要があるアプリケーションに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-123">This is useful for applications in which it is necessary to review data changes made at either the Publisher or Subscriber before allowing them to be propagated.</span></span> <span data-ttu-id="ad7af-124">たとえば、中間層アプリケーションでは、フィールドから送られてきた新しい注文を検証し、中間層で調達ワークフロー プロセスと統合することができます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-124">For example, a mid-tier application could examine new orders coming in from the field and integrate with a procurement workflow process in the mid-tier.</span></span>  
  
-   <span data-ttu-id="ad7af-125">カスタム データの適用</span><span class="sxs-lookup"><span data-stu-id="ad7af-125">Apply custom data</span></span>  
  
     <span data-ttu-id="ad7af-126">これは、特定のデータの値または操作をオーバーライドする必要があるアプリケーションに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-126">This is useful for applications that need to override specific data values or operations.</span></span> <span data-ttu-id="ad7af-127">たとえば、アプリケーションでは、行の削除を、その行の **status** 列を "削除" の値に設定するという特殊な更新方法に変更して、その削除を実行するクライアントの ID を追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-127">For example, an application could transform a row delete into a special update that sets a **status** column in the row to a value of "deleted" and then tracks the identity of the client performing the delete.</span></span> <span data-ttu-id="ad7af-128">これは、監査やワークフローにも役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-128">This might be useful for auditing or workflow purposes.</span></span>  
  
### <a name="custom-conflict-resolution"></a><span data-ttu-id="ad7af-129">カスタム競合解決</span><span class="sxs-lookup"><span data-stu-id="ad7af-129">Custom Conflict Resolution</span></span>  
 <span data-ttu-id="ad7af-130">マージ レプリケーションには、競合の検出機能と解決機能が用意されており、既定の解決方法を受け入れるか、競合に対するカスタム解決方法を選択することができます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-130">Merge replication provides conflict detection and resolution, allowing you to accept a default resolution strategy or choose custom resolution for conflicts.</span></span> <span data-ttu-id="ad7af-131">詳細については、「 [マージ レプリケーションの競合検出および解決の詳細](advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ad7af-131">For more information, see [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span> <span data-ttu-id="ad7af-132">ビジネス ロジック ハンドラーは、競合しているデータの変更処理中に呼び出すことができ、次の 2 つの操作のいずれかを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-132">The business logic handler can be invoked during the processing of conflicting data changes and can perform one of two actions:</span></span>  
  
-   <span data-ttu-id="ad7af-133">既定の解決の受け入れ</span><span class="sxs-lookup"><span data-stu-id="ad7af-133">Accept default resolution</span></span>  
  
     <span data-ttu-id="ad7af-134">これは、競合の確認や追加アクションの実行、場合によってはカスタム競合ログ メッセージのログ記録などを行う必要があるアプリケーションに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-134">This is useful for applications that might need to review the conflict, perform additional actions, and possibly log a custom conflict log message.</span></span>  
  
-   <span data-ttu-id="ad7af-135">カスタム解決の実行</span><span class="sxs-lookup"><span data-stu-id="ad7af-135">Perform custom resolution</span></span>  
  
     <span data-ttu-id="ad7af-136">これは、ビジネス ロジックに固有のデータ値を選択し、このカスタム データセットを使用した同期処理を提供する必要があるアプリケーションに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-136">This is useful for applications that might need to select data values that are specific to their business logic and supply the synchronization process with this custom dataset.</span></span> <span data-ttu-id="ad7af-137">たとえば、アプリケーションで、パブリッシャーとサブスクライバーのデータセットの値を組み合わせることにより、優先される行の新しいバージョンを提供することができます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-137">For example, an application could provide a new version of the winning row by combining values from the Publisher and Subscriber data sets.</span></span>  
  
### <a name="custom-error-resolution"></a><span data-ttu-id="ad7af-138">カスタム エラー解決</span><span class="sxs-lookup"><span data-stu-id="ad7af-138">Custom Error Resolution</span></span>  
 <span data-ttu-id="ad7af-139">カスタム ロジックは、結果的にエラーが発生する変更の反映中に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-139">Custom logic can be invoked during the propagation of changes that result in errors.</span></span> <span data-ttu-id="ad7af-140">このロジックは、次の 2 つの操作のいずれかを実行できます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-140">The logic can perform one of two actions:</span></span>  
  
-   <span data-ttu-id="ad7af-141">既定のエラー解決の受け入れ</span><span class="sxs-lookup"><span data-stu-id="ad7af-141">Accept default error resolution</span></span>  
  
     <span data-ttu-id="ad7af-142">これは、エラーの確認や追加アクションの実行、場合によってはカスタム エラー ログ メッセージのログ記録などを行う必要があるアプリケーションに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-142">This is useful for applications that might need to review the error and perform additional action and possibly log a custom error log message.</span></span>  
  
-   <span data-ttu-id="ad7af-143">カスタム エラー解決の受け入れ</span><span class="sxs-lookup"><span data-stu-id="ad7af-143">Accept custom error resolution</span></span>  
  
     <span data-ttu-id="ad7af-144">これは、ビジネス ロジックに固有のデータ値を選択し、このカスタム データセットを使用した同期処理を提供する必要があるアプリケーションに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-144">This is useful for applications that might need to select data values that are specific to their business logic and supply the synchronization process with this custom dataset.</span></span> <span data-ttu-id="ad7af-145">たとえば、レプリケーション処理で重複キー違反が発生した場合、ビジネス ロジック ハンドラーによって、キーの競合がなくなる新しいバージョンのデータ変更を提供することができます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-145">For example, if the replication process encounters a duplicate key violation, the business logic handler could provide a new version of the data change in which the key will no longer conflict.</span></span> <span data-ttu-id="ad7af-146">パブリッシャーとサブスクライバーで行われた変更は、データベースで保持することができます。レプリケーション プロセスは、失敗した挿入に対して削除による補正を行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ad7af-146">Changes made at the Publisher and Subscriber can then persist in the database, and the replication process doesn't have to compensate for the failed insert with a delete.</span></span>  
  
## <a name="deployment-scenarios-for-business-logic-handlers"></a><span data-ttu-id="ad7af-147">ビジネス ロジック ハンドラーの配置シナリオ</span><span class="sxs-lookup"><span data-stu-id="ad7af-147">Deployment Scenarios for Business Logic Handlers</span></span>  
 <span data-ttu-id="ad7af-148">ビジネス ロジック ハンドラーは、以下の場所に配置できます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-148">Business logic handlers can be deployed at:</span></span>  
  
-   <span data-ttu-id="ad7af-149">ディストリビューター。</span><span class="sxs-lookup"><span data-stu-id="ad7af-149">The Distributor.</span></span> <span data-ttu-id="ad7af-150">ディストリビューターでビジネス ロジックが実行されるように、プッシュ サブスクリプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad7af-150">Use a push subscription so that business logic is executed at the Distributor.</span></span>  
  
-   <span data-ttu-id="ad7af-151">サブスクライバー。</span><span class="sxs-lookup"><span data-stu-id="ad7af-151">The Subscriber.</span></span> <span data-ttu-id="ad7af-152">サブスクライバーでビジネス ロジックが実行されるように、プル サブスクリプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="ad7af-152">Use a pull subscription so that business logic is executed at the Subscriber.</span></span>  
  
-   <span data-ttu-id="ad7af-153">インターネット インフォメーション サービス (IIS) サーバー (Web 同期を使用する場合)。</span><span class="sxs-lookup"><span data-stu-id="ad7af-153">An Internet Information Services (IIS) server if Web synchronization is used.</span></span> <span data-ttu-id="ad7af-154">Web 同期を使用して同期されたプル サブスクリプションを使用します。ビジネス ロジック ハンドラーが IIS サーバーで実行されます。</span><span class="sxs-lookup"><span data-stu-id="ad7af-154">Use a pull subscription synchronized with Web synchronization, and the business logic handler will execute at the IIS Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad7af-155">参照</span><span class="sxs-lookup"><span data-stu-id="ad7af-155">See Also</span></span>  
 <span data-ttu-id="ad7af-156">[マージ レプリケーション](merge-replication.md) </span><span class="sxs-lookup"><span data-stu-id="ad7af-156">[Merge Replication](merge-replication.md) </span></span>  
 <span data-ttu-id="ad7af-157">[Subscribe to Publications](../subscribe-to-publications.md) </span><span class="sxs-lookup"><span data-stu-id="ad7af-157">[Subscribe to Publications](../subscribe-to-publications.md) </span></span>  
 <span data-ttu-id="ad7af-158">[データの同期](../synchronize-data.md) </span><span class="sxs-lookup"><span data-stu-id="ad7af-158">[Synchronize Data](../synchronize-data.md) </span></span>  
 [<span data-ttu-id="ad7af-159">マージ レプリケーションの Web 同期</span><span class="sxs-lookup"><span data-stu-id="ad7af-159">Web Synchronization for Merge Replication</span></span>](../web-synchronization-for-merge-replication.md)  
  
  
