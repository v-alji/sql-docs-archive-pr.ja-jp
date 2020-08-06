---
title: SQL Server Service Broker | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- SQL12.SWB.SSBQUEUEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBREMSVCBINDPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBMSGTYPEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBROUTEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBCONTRACTPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBSERVICEPROPERTIES.GENERAL.F1
- SQL12.SWB.SSBPRIORITYPROPERTIES.GENERAL.F1
helpviewer_keywords:
- Broker See Service Broker
- SQL Server Service Broker
- Service Broker
ms.assetid: 8b8b3b57-fd46-44de-9a4e-e3a8e3999c1e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3d3877dd8311e0fe5b65bd4b1e7f9c40fbd84751
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740386"
---
# <a name="sql-server-service-broker"></a><span data-ttu-id="1c1c9-102">SQL Server Service Broker</span><span class="sxs-lookup"><span data-stu-id="1c1c9-102">SQL Server Service Broker</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]<span data-ttu-id="1c1c9-103">[!INCLUDE[ssSB](../../includes/sssb-md.md)]では、のメッセージングアプリケーションとキューアプリケーションがネイティブにサポートされて [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] います。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-103">[!INCLUDE[ssSB](../../includes/sssb-md.md)] provides native support for messaging and queuing applications in the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="1c1c9-104">これにより、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] コンポーネントを使用して異種データベース間の通信を行う高度なアプリケーションを簡単に作成できるようになるため、</span><span class="sxs-lookup"><span data-stu-id="1c1c9-104">This makes it easier for developers to create sophisticated applications that use the [!INCLUDE[ssDE](../../includes/ssde-md.md)] components to communicate between disparate databases.</span></span> <span data-ttu-id="1c1c9-105">[!INCLUDE[ssSB](../../includes/sssb-md.md)] を使用すれば、信頼性の高い分散アプリケーションを簡単に開発できます。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-105">Developers can use [!INCLUDE[ssSB](../../includes/sssb-md.md)] to easily build distributed and reliable applications.</span></span>  
  
 <span data-ttu-id="1c1c9-106">アプリケーション開発者は、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] を使用すれば、通信やメッセージングの複雑な内部のプログラミングを行わなくても、データ ワークロードを複数のデータベースに分散できます。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-106">Application developers who use [!INCLUDE[ssSB](../../includes/sssb-md.md)] can distribute data workloads across several databases without programming complex communication and messaging internals.</span></span> <span data-ttu-id="1c1c9-107">[!INCLUDE[ssSB](../../includes/sssb-md.md)] によってメッセージ交換のコンテキスト内で通信パスが処理されるので、開発やテストの作業を削減できます。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-107">This reduces development and test work because [!INCLUDE[ssSB](../../includes/sssb-md.md)] handles the communication paths in the context of a conversation.</span></span> <span data-ttu-id="1c1c9-108">また、パフォーマンスも向上します。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-108">It also improves performance.</span></span> <span data-ttu-id="1c1c9-109">たとえば、Web サイトをサポートするフロントエンド データベースで情報の記録を行い、処理負荷の高いタスクはバックエンド データベースのキューに送信できます。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-109">For example, front-end databases supporting Web sites can record information and send process intensive tasks to queue in back-end databases.</span></span> [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="1c1c9-110">では、すべてのタスクがトランザクションのコンテキストで管理されるため、信頼性と技術的な一貫性を確保できます。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-110">ensures that all tasks are managed in the context of transactions to assure reliability and technical consistency.</span></span>  
  
## <a name="where-is-the-documentation-for-service-broker"></a><span data-ttu-id="1c1c9-111">Service Broker のドキュメントの格納場所</span><span class="sxs-lookup"><span data-stu-id="1c1c9-111">Where is the documentation for Service Broker?</span></span>  
 <span data-ttu-id="1c1c9-112">[!INCLUDE[ssSB](../../includes/sssb-md.md)] のリファレンス ドキュメントは [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] のドキュメントに含まれています。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-112">The reference documentation for [!INCLUDE[ssSB](../../includes/sssb-md.md)] is included in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] documentation.</span></span> <span data-ttu-id="1c1c9-113">リファレンス ドキュメントには次のセクションがあります。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-113">This reference documentation includes the following sections:</span></span>  
  
-   <span data-ttu-id="1c1c9-114">CREATE、ALTER、および DROP ステートメントの[データ定義言語 &#40;DDL&#41; ステートメント &#40;Transact-SQL&#41;](/sql/odbc/reference/develop-app/ddl-statements)</span><span class="sxs-lookup"><span data-stu-id="1c1c9-114">[Data Definition Language &#40;DDL&#41; Statements &#40;Transact-SQL&#41;](/sql/odbc/reference/develop-app/ddl-statements) for CREATE, ALTER, and DROP statements</span></span>  
  
-   [<span data-ttu-id="1c1c9-115">Service Broker カタログ ビュー &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1c1c9-115">Service Broker Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/service-broker-catalog-views-transact-sql)  
  
-   [<span data-ttu-id="1c1c9-116">Service Broker 関連の動的管理ビュー &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="1c1c9-116">Service Broker Related Dynamic Management Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql)  
  
-   [<span data-ttu-id="1c1c9-117">ssbdiagnose ユーティリティ &#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="1c1c9-117">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](../../tools/ssbdiagnose/ssbdiagnose-utility-service-broker.md)  
  
 <span data-ttu-id="1c1c9-118">[の概念、開発作業、および管理作業については、](https://go.microsoft.com/fwlink/?LinkId=231312) 以前に公開されたドキュメント [!INCLUDE[ssSB](../../includes/sssb-md.md)] を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-118">See the [previously published documentation](https://go.microsoft.com/fwlink/?LinkId=231312) for [!INCLUDE[ssSB](../../includes/sssb-md.md)] concepts and for development and management tasks.</span></span> <span data-ttu-id="1c1c9-119">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] は [!INCLUDE[ssSB](../../includes/sssb-md.md)] においてわずかな変更しか加えられていないため、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]用のドキュメントは作成されていません。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-119">This documentation is not reproduced in the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] documentation due to the small number of changes in [!INCLUDE[ssSB](../../includes/sssb-md.md)] in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="whats-new-in-service-broker"></a><span data-ttu-id="1c1c9-120">Service Broker の新機能</span><span class="sxs-lookup"><span data-stu-id="1c1c9-120">What's new in Service Broker</span></span>  
 <span data-ttu-id="1c1c9-121">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]で導入された大きな変更はありません。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-121">No significant changes are introduced in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  <span data-ttu-id="1c1c9-122">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]では、以下の変更が導入されました。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-122">The following changes were introduced in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)].</span></span>  
  
### <a name="messages-can-be-sent-to-multiple-target-services-multicast"></a><span data-ttu-id="1c1c9-123">メッセージを複数の対象サービスに送信可能 (マルチキャスト)</span><span class="sxs-lookup"><span data-stu-id="1c1c9-123">Messages can be sent to multiple target services (multicast)</span></span>  
 <span data-ttu-id="1c1c9-124">[SEND &#40;Transact-SQL&#41;](/sql/t-sql/statements/send-transact-sql) ステートメントの構文が拡張され、複数のメッセージ交換ハンドルをサポートすることにより、マルチキャストが有効になりました。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-124">The syntax of the [SEND &#40;Transact-SQL&#41;](/sql/t-sql/statements/send-transact-sql) statement has been extended to enable multicast by supporting multiple conversation handles.</span></span>  
  
### <a name="queues-expose-the-message-enqueued-time"></a><span data-ttu-id="1c1c9-125">メッセージがエンキューされている時間の公開</span><span class="sxs-lookup"><span data-stu-id="1c1c9-125">Queues expose the message enqueued time</span></span>  
 <span data-ttu-id="1c1c9-126">メッセージがキューに格納されている時間を示す新しい列 **message_enqueue_time**がキューに追加されました。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-126">Queues have a new column, **message_enqueue_time**, that shows how long a message has been in the queue.</span></span>  
  
### <a name="poison-message-handling-can-be-disabled"></a><span data-ttu-id="1c1c9-127">有害メッセージの処理の無効化が可能</span><span class="sxs-lookup"><span data-stu-id="1c1c9-127">Poison message handling can be disabled</span></span>  
 <span data-ttu-id="1c1c9-128">[CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) ステートメントおよび [ALTER QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-queue-transact-sql) ステートメントでは、`POISON_MESSAGE_HANDLING (STATUS = ON | OFF)` 句を追加することによって有害メッセージの処理を無効化できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-128">The [CREATE QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-queue-transact-sql) and [ALTER QUEUE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-queue-transact-sql) statements now have the ability to enable or disable poison message handling by adding the clause, `POISON_MESSAGE_HANDLING (STATUS = ON | OFF)`.</span></span> <span data-ttu-id="1c1c9-129">カタログ ビュー **sys.service_queues** に、有害メッセージの処理が有効であるか無効であるかを示す **is_poison_message_handling_enabled** 列が追加されました。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-129">The catalog view **sys.service_queues** now has the column **is_poison_message_handling_enabled** to indicate whether poison message is enabled or disabled.</span></span>  
  
### <a name="alwayson-support-in-service-broker"></a><span data-ttu-id="1c1c9-130">Service Broker での AlwaysOn のサポート</span><span class="sxs-lookup"><span data-stu-id="1c1c9-130">AlwaysOn support in Service Broker</span></span>  
 <span data-ttu-id="1c1c9-131">詳細については、「[Service Broker と Always On 可用性グループ  &#40;SQL Server&#41;](../availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1c1c9-131">For more information, see [Service Broker with AlwaysOn Availability Groups &#40;SQL Server&#41;](../availability-groups/windows/service-broker-with-always-on-availability-groups-sql-server.md).</span></span>  
  
  
