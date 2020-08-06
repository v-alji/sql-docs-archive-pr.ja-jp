---
title: Oracle パブリッシャーのパフォーマンス チューニング | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Oracle publishing [SQL Server replication], performance tuning
ms.assetid: 32c0b4ec-c166-45a3-b41e-38a30fd56813
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 83d660eee839d525fa0bdabf88a313da0ed44244
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630901"
---
# <a name="performance-tuning-for-oracle-publishers"></a><span data-ttu-id="00935-102">Oracle パブリッシャーのパフォーマンス チューニング</span><span class="sxs-lookup"><span data-stu-id="00935-102">Performance Tuning for Oracle Publishers</span></span>
  <span data-ttu-id="00935-103">Oracle のパブリッシング アーキテクチャは、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] のパブリッシング アーキテクチャに似ています。したがって、「 [Enhance General Replication Performance](../administration/enhance-general-replication-performance.md)」で紹介されているチューニング全般の推奨事項に従うことが、Oracle レプリケーションのパフォーマンスをチューニングするための第一歩となります。</span><span class="sxs-lookup"><span data-stu-id="00935-103">The Oracle publishing architecture is similar to the [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] publishing architecture; therefore the first step in tuning Oracle replication for performance requires following the general tuning recommendations found in [Enhance General Replication Performance](../administration/enhance-general-replication-performance.md).</span></span>  
  
 <span data-ttu-id="00935-104">それに加えて、Oracle パブリッシャーには、パフォーマンスに関連するオプションが 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="00935-104">In addition there are two options for Oracle Publishers that are performance related:</span></span>  
  
-   <span data-ttu-id="00935-105">パブリッシング オプションとして、[Oracle (完全)] または [Oracle (ゲートウェイ)] のいずれか適切な方を指定します。</span><span class="sxs-lookup"><span data-stu-id="00935-105">Specifying the appropriate publishing option: Oracle or Oracle Gateway.</span></span>  
  
-   <span data-ttu-id="00935-106">パブリッシャーの変更を適切な間隔で処理するようにトランザクション セット ジョブを構成します。</span><span class="sxs-lookup"><span data-stu-id="00935-106">Configuring the transaction set job to process changes on the Publisher at an appropriate interval.</span></span>  
  
## <a name="specifying-the-appropriate-publishing-option"></a><span data-ttu-id="00935-107">適切なパブリッシング オプションの指定</span><span class="sxs-lookup"><span data-stu-id="00935-107">Specifying the Appropriate Publishing Option</span></span>  
 <span data-ttu-id="00935-108">[Oracle (ゲートウェイ)] を選択すると、[Oracle (完全)] より高いパフォーマンスが得られますが、このオプションは、複数のトランザクション パブリケーションで同じテーブルをパブリッシュする場合は使用できません。</span><span class="sxs-lookup"><span data-stu-id="00935-108">The Oracle Gateway option provides improved performance over the Oracle Complete option; however, this option cannot be used to publish the same table in multiple transactional publications.</span></span> <span data-ttu-id="00935-109">テーブルを表示できるのは、最大で 1 つのトランザクション パブリケーションと、任意の数のスナップショット パブリケーションになります。</span><span class="sxs-lookup"><span data-stu-id="00935-109">A table can appear in at most one transactional publication and any number of snapshot publications.</span></span> <span data-ttu-id="00935-110">複数のトランザクション パブリケーションで同じテーブルをパブリッシュする必要がある場合は、[Oracle (完全)] を選択します。</span><span class="sxs-lookup"><span data-stu-id="00935-110">If you need to publish the same table in multiple transactional publications, choose the Oracle Complete option.</span></span> <span data-ttu-id="00935-111">このオプションは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターで Oracle パブリッシャーを識別する際に指定します。</span><span class="sxs-lookup"><span data-stu-id="00935-111">Specify this option when identifying the Oracle Publisher at the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor.</span></span> <span data-ttu-id="00935-112">詳細については、「 [Create a Publication from an Oracle Database](../publish/create-a-publication-from-an-oracle-database.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00935-112">For more information, see [Create a Publication from an Oracle Database](../publish/create-a-publication-from-an-oracle-database.md).</span></span>  
  
## <a name="configuring-the-transaction-set-job"></a><span data-ttu-id="00935-113">トランザクション セット ジョブの構成</span><span class="sxs-lookup"><span data-stu-id="00935-113">Configuring the Transaction Set Job</span></span>  
 <span data-ttu-id="00935-114">パブリッシュされた Oracle テーブルに対する変更は、トランザクション セットと呼ばれるグループで処理されます。</span><span class="sxs-lookup"><span data-stu-id="00935-114">Changes to published Oracle tables are processed in groups called transaction sets.</span></span> <span data-ttu-id="00935-115">トランザクションの一貫性を確保するために、各トランザクション セットはディストリビューション データベースで 1 つのトランザクションとしてコミットされます。</span><span class="sxs-lookup"><span data-stu-id="00935-115">To ensure transactional consistency, each transaction set is committed as a single transaction at the distribution database.</span></span> <span data-ttu-id="00935-116">トランザクション セットが大きくなりすぎると、1 つのトランザクションとして効率的に処理できなくなります。</span><span class="sxs-lookup"><span data-stu-id="00935-116">If the transaction set becomes too large, it cannot be processed efficiently as a single transaction.</span></span>  
  
 <span data-ttu-id="00935-117">既定では、トランザクション セットはログ リーダー エージェントによってのみ作成されます。</span><span class="sxs-lookup"><span data-stu-id="00935-117">By default, transaction sets are created only by the Log Reader Agent.</span></span> <span data-ttu-id="00935-118">変更が頻繁に行われているときにログ リーダー エージェントが実行されていなかったり、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ディストリビューターから Oracle パブリッシャーに接続できなかったりすると、トランザクション セットが極端に大きくなる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="00935-118">If, during periods of high change activity, the Log Reader Agent does not run or cannot connect from the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Distributor to the Oracle Publisher, transaction sets can become unmanageably large.</span></span> <span data-ttu-id="00935-119">この問題を防ぐには、ログ リーダー エージェントが実行されていなかったり Oracle パブリッシャーに接続できなかったりしてもトランザクション セットが定期的に作成されるようにします。</span><span class="sxs-lookup"><span data-stu-id="00935-119">To prevent this problem, ensure that transaction sets are created at regular intervals, even if the Log Reader Agent does not run or cannot connect to the Oracle Publisher.</span></span>  
  
 <span data-ttu-id="00935-120">トランザクション セットは、Xactset ジョブ (レプリケーションによってインストールされる Oracle データベース ジョブ) で作成できます。Xactset ジョブは、ログ リーダー エージェントと同じメカニズムを使ってトランザクション セットを作成します。</span><span class="sxs-lookup"><span data-stu-id="00935-120">Transaction sets can be created with the Xactset job (an Oracle database job installed by replication), which uses the same mechanism that the Log Reader Agent does to create sets.</span></span> <span data-ttu-id="00935-121">このジョブが実行されるたびに、新しいトランザクション セットが作成されます。</span><span class="sxs-lookup"><span data-stu-id="00935-121">Each time the job runs, a new transaction set is created.</span></span> <span data-ttu-id="00935-122">次にログ リーダー エージェントが実行されたときに、それまでに作成されたトランザクション セットが処理されます。</span><span class="sxs-lookup"><span data-stu-id="00935-122">The next time that the Log Reader Agent runs, the agent processes any sets that have been created.</span></span> <span data-ttu-id="00935-123">既存のトランザクション セットがすべて処理された後にまだ保留中の変更がある場合は、ログ リーダー エージェントが 1 つ以上のトランザクション セットを追加で作成して処理します。</span><span class="sxs-lookup"><span data-stu-id="00935-123">If there are still pending changes after all existing transaction sets have been processed, the Log Reader Agent creates and processes one or more additional transaction sets.</span></span>  
  
 <span data-ttu-id="00935-124">トランザクション セット ジョブを構成するには、「[Configure the Transaction Set Job for an Oracle Publisher](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md)」 (Oracle パブリッシャー用にトランザクション セット ジョブを構成する方法 (レプリケーション Transact-SQL プログラミング)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="00935-124">To configure the transaction set job, see [Configure the Transaction Set Job for an Oracle Publisher &#40;Replication Transact-SQL Programming&#41;](../administration/configure-the-transaction-set-job-for-an-oracle-publisher.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00935-125">参照</span><span class="sxs-lookup"><span data-stu-id="00935-125">See Also</span></span>  
 <span data-ttu-id="00935-126">[Configure an Oracle Publisher (Oracle パブリッシャーの構成)](configure-an-oracle-publisher.md) </span><span class="sxs-lookup"><span data-stu-id="00935-126">[Configure an Oracle Publisher](configure-an-oracle-publisher.md) </span></span>  
 [<span data-ttu-id="00935-127">Oracle パブリッシングの概要</span><span class="sxs-lookup"><span data-stu-id="00935-127">Oracle Publishing Overview</span></span>](oracle-publishing-overview.md)  
  
  
