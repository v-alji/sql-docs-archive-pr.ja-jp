---
title: Oracle パブリッシャーのトランザクションセットジョブの構成 (レプリケーション Transact-sql プログラミング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_publisherproperty
- Oracle publishing [SQL Server replication], configuring
ms.assetid: beea1a5c-0053-4971-a68f-0da53063fcbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 43a25ce755a505f0efd7c25243b8969a962ea701
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741890"
---
# <a name="configure-the-transaction-set-job-for-an-oracle-publisher-replication-transact-sql-programming"></a><span data-ttu-id="f8936-102">Oracle パブリッシャー用のトランザクション セット ジョブの構成 (レプリケーション Transact-SQL プログラミング)</span><span class="sxs-lookup"><span data-stu-id="f8936-102">Configure the Transaction Set Job for an Oracle Publisher (Replication Transact-SQL Programming)</span></span>
  <span data-ttu-id="f8936-103">**Xactset** ジョブは、Oracle パブリッシャーで実行されているレプリケーションがトランザクション セットを生成するために作成する Oracle データベース ジョブです。Oracle パブリッシャーにログ リーダー エージェントが接続されていない場合に使用されます。</span><span class="sxs-lookup"><span data-stu-id="f8936-103">The **Xactset** job is an Oracle database job created by replication that runs at an Oracle Publisher to create transaction sets when the Log Reader Agent is not connected to the Publisher.</span></span> <span data-ttu-id="f8936-104">このジョブは、レプリケーションのストアド プロシージャを使用し、ディストリビューターからプログラムによって有効化したり構成することができます。</span><span class="sxs-lookup"><span data-stu-id="f8936-104">You can enable and configure this job from the Distributor programmatically using replication stored procedures.</span></span> <span data-ttu-id="f8936-105">詳細については、「[Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md)」 (Oracle パブリッシャーのパフォーマンス チューニング) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8936-105">For more information, see [Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md).</span></span>  
  
### <a name="to-enable-the-transaction-set-job"></a><span data-ttu-id="f8936-106">トランザクション セット ジョブを有効にするには</span><span class="sxs-lookup"><span data-stu-id="f8936-106">To enable the transaction set job</span></span>  
  
1.  <span data-ttu-id="f8936-107">Oracle パブリッシャーで、 **job_queue_processes** 初期化パラメーターに、Xactset ジョブを実行できるだけの十分な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="f8936-107">At the Oracle Publisher, set the **job_queue_processes** initialization parameter to a sufficient value to allow the Xactset job run.</span></span> <span data-ttu-id="f8936-108">このパラメーターの詳細については、Oracle パブリッシャー用データベースのマニュアルを参照してください。</span><span class="sxs-lookup"><span data-stu-id="f8936-108">For more information about this parameter, see the database documentation for the Oracle Publisher.</span></span>  
  
2.  <span data-ttu-id="f8936-109">ディストリビューターで、[sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8936-109">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="f8936-110">\*\* \@ パブリッシャー\*\*に Oracle パブリッシャーの名前、propertyname には値、 `xactsetbatching` \*\* \@ \*\*propertyvalue には値を指定し `enabled` ます。 \*\* \@ \*\*</span><span class="sxs-lookup"><span data-stu-id="f8936-110">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetbatching` for **\@propertyname**, and a value of `enabled` for **\@propertyvalue**.</span></span>  
  
3.  <span data-ttu-id="f8936-111">ディストリビューターで、[sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8936-111">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="f8936-112">\*\* \@ パブリッシャー**に Oracle パブリッシャーの名前を、 `xactsetjobinterval` \*\* \@ propertyname**に値を、 \*\* \@ propertyvalue\*\*に対してジョブ間隔を分単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="f8936-112">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjobinterval` for **\@propertyname**, and the job interval, in minutes, for **\@propertyvalue**.</span></span>  
  
4.  <span data-ttu-id="f8936-113">ディストリビューターで、[sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8936-113">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="f8936-114">\*\* \@ パブリッシャー\*\*に Oracle パブリッシャーの名前、propertyname には値、 `xactsetjob` \*\* \@ \*\*propertyvalue には値を指定し `enabled` ます。 \*\* \@ \*\*</span><span class="sxs-lookup"><span data-stu-id="f8936-114">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjob` for **\@propertyname**, and a value of `enabled` for **\@propertyvalue**.</span></span>  
  
### <a name="to-configure-the-transaction-set-job"></a><span data-ttu-id="f8936-115">トランザクション セット ジョブを構成するには</span><span class="sxs-lookup"><span data-stu-id="f8936-115">To configure the transaction set job</span></span>  
  
1.  <span data-ttu-id="f8936-116">(省略可能) ディストリビューターで [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8936-116">(Optional) At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="f8936-117">**\@publisher** に Oracle パブリッシャーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8936-117">Specify the name of the Oracle Publisher for **\@publisher**.</span></span> <span data-ttu-id="f8936-118">これにより、パブリッシャーの **Xactset** ジョブのプロパティが返されます。</span><span class="sxs-lookup"><span data-stu-id="f8936-118">This returns properties of the **Xactset** job at the Publisher.</span></span>  
  
2.  <span data-ttu-id="f8936-119">ディストリビューターで、[sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8936-119">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="f8936-120">\*\* \@ パブリッシャー**の Oracle パブリッシャーの名前、 \*\* \@ propertyname**に対して設定する Xactset ジョブプロパティの名前、および\*\* \@ propertyvalue\*\*の新しい設定を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8936-120">Specify the name of the Oracle Publisher for **\@publisher**, the name of the Xactset job property being set for **\@propertyname**, and new setting for **\@propertyvalue**.</span></span>  
  
3.  <span data-ttu-id="f8936-121">(省略可) 設定対象の各 Xactset ジョブ プロパティについて、手順 2. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="f8936-121">(Optional) Repeat step 2 for each Xactset job property being set.</span></span> <span data-ttu-id="f8936-122">プロパティを変更するときは、 `xactsetjobinterval` 新しい間隔を有効にするために、Oracle パブリッシャーでジョブを再起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f8936-122">When changing the `xactsetjobinterval` property, you must restart the job on the Oracle Publisher for the new interval to take effect.</span></span>  
  
### <a name="to-view-properties-of-the-transaction-set-job"></a><span data-ttu-id="f8936-123">トランザクション セット ジョブのプロパティを表示するには</span><span class="sxs-lookup"><span data-stu-id="f8936-123">To view properties of the transaction set job</span></span>  
  
1.  <span data-ttu-id="f8936-124">ディストリビューターで [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8936-124">At the Distributor, execute [sp_helpxactsetjob](/sql/relational-databases/system-stored-procedures/sp-helpxactsetjob-transact-sql).</span></span> <span data-ttu-id="f8936-125">**\@publisher** に Oracle パブリッシャーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="f8936-125">Specify the name of the Oracle Publisher for **\@publisher**.</span></span>  
  
### <a name="to-disable-the-transaction-set-job"></a><span data-ttu-id="f8936-126">トランザクション セット ジョブを無効にするには</span><span class="sxs-lookup"><span data-stu-id="f8936-126">To disable the transaction set job</span></span>  
  
1.  <span data-ttu-id="f8936-127">ディストリビューターで、[sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql) を実行します。</span><span class="sxs-lookup"><span data-stu-id="f8936-127">At the Distributor, execute [sp_publisherproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-publisherproperty-transact-sql).</span></span> <span data-ttu-id="f8936-128">\*\* \@ パブリッシャー\*\*に Oracle パブリッシャーの名前、propertyname には値、 `xactsetjob` \*\* \@ \*\*propertyvalue には値を指定し `disabled` ます。 \*\* \@ \*\*</span><span class="sxs-lookup"><span data-stu-id="f8936-128">Specify the name of the Oracle Publisher for **\@publisher**, a value of `xactsetjob` for **\@propertyname**, and a value of `disabled` for **\@propertyvalue**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8936-129">例</span><span class="sxs-lookup"><span data-stu-id="f8936-129">Example</span></span>  
 <span data-ttu-id="f8936-130">次の例では、 `Xactset` ジョブを有効にし、実行間隔を 3 分に設定しています。</span><span class="sxs-lookup"><span data-stu-id="f8936-130">The following example enables the `Xactset` job and sets an interval of three minutes between runs.</span></span>  
  
 [!code-sql[HowTo#sp_enable_xactsetjob](../../../snippets/tsql/SQL15/replication/howto/tsql/enablexactsetjob.sql#sp_enable_xactsetjob)]  
  
## <a name="see-also"></a><span data-ttu-id="f8936-131">参照</span><span class="sxs-lookup"><span data-stu-id="f8936-131">See Also</span></span>  
 <span data-ttu-id="f8936-132">[Oracle パブリッシャーのパフォーマンスチューニング](../non-sql/performance-tuning-for-oracle-publishers.md) </span><span class="sxs-lookup"><span data-stu-id="f8936-132">[Performance Tuning for Oracle Publishers](../non-sql/performance-tuning-for-oracle-publishers.md) </span></span>  
 [<span data-ttu-id="f8936-133">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="f8936-133">Replication System Stored Procedures Concepts</span></span>](../concepts/replication-system-stored-procedures-concepts.md)  
  
  
