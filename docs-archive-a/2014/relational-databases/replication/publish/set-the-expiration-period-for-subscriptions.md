---
title: サブスクリプションの有効期限の設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [SQL Server replication], expiration
- expiration [SQL Server replication]
- retention periods [SQL Server replication]
- deactivating subscriptions
ms.assetid: 542f0613-5817-42d0-b841-fb2c94010665
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bc0ecb449af64b88cf3ded032c78c2e399dd4234
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641611"
---
# <a name="set-the-expiration-period-for-subscriptions"></a><span data-ttu-id="b07eb-102">サブスクリプションの有効期限の設定</span><span class="sxs-lookup"><span data-stu-id="b07eb-102">Set the Expiration Period for Subscriptions</span></span>
  <span data-ttu-id="b07eb-103">このトピックでは、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] で [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../../includes/tsql-md.md)]を使用して、サブスクリプションの有効期限を設定する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-103">This topic describes how to set the expiration period for subscriptions in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../../includes/tsql-md.md)].</span></span> <span data-ttu-id="b07eb-104">サブスクリプションの期限が切れて削除されるまでの時間は、サブスクリプションの有効期限によって決定されます。</span><span class="sxs-lookup"><span data-stu-id="b07eb-104">The expiration period for subscriptions determines the period of time before a subscription expires and is removed.</span></span> <span data-ttu-id="b07eb-105">詳細については、「 [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b07eb-105">For more information, see [Subscription Expiration and Deactivation](../subscription-expiration-and-deactivation.md).</span></span>  
  
 <span data-ttu-id="b07eb-106">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="b07eb-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="b07eb-107">**作業を開始する準備:**</span><span class="sxs-lookup"><span data-stu-id="b07eb-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="b07eb-108">Recommendations (推奨事項)</span><span class="sxs-lookup"><span data-stu-id="b07eb-108">Recommendations</span></span>](#Recommendations)  
  
-   <span data-ttu-id="b07eb-109">**サブスクリプションの有効期限を設定するために使用するもの:**</span><span class="sxs-lookup"><span data-stu-id="b07eb-109">**To set the expiration period for subscriptions, using:**</span></span>  
  
     [<span data-ttu-id="b07eb-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="b07eb-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="b07eb-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="b07eb-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="b07eb-112">はじめに</span><span class="sxs-lookup"><span data-stu-id="b07eb-112">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="b07eb-113">推奨事項</span><span class="sxs-lookup"><span data-stu-id="b07eb-113">Recommendations</span></span>  
  
-   <span data-ttu-id="b07eb-114">サブスクリプションの有効期限は、 *パブリケーション保有期間*とも呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="b07eb-114">The subscription expiration period is also referred to as the *publication retention period*.</span></span> <span data-ttu-id="b07eb-115">マージ レプリケーション メタデータのクリーンアップは、この設定に依存します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-115">Cleanup of merge replication metadata is dependent on this setting:</span></span>  
  
    -   <span data-ttu-id="b07eb-116">保有期間が終了するまで、パブリケーションおよびサブスクリプション データベースでメタデータをクリーンアップすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b07eb-116">Replication cannot clean up metadata in the publication and subscription databases until the retention period is reached.</span></span> <span data-ttu-id="b07eb-117">レプリケーション パフォーマンスを低下させる可能性があるため、保有期間に大きな値を指定する際は注意してください。</span><span class="sxs-lookup"><span data-stu-id="b07eb-117">Use caution in specifying a high value for the retention period, because it can negatively impact replication performance.</span></span> <span data-ttu-id="b07eb-118">すべてのサブスクライバーが保有期間内で定期的に同期されることを確実に予測できる場合は、小さい値を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b07eb-118">It is recommended that you use a lower setting if you can reliably predict that all Subscribers will synchronize regularly within that time period.</span></span>  
  
         <span data-ttu-id="b07eb-119">マージ パブリケーションの保有期間には、異なるタイム ゾーンのサブスクライバーに対応するため、24 時間の猶予期間があります。</span><span class="sxs-lookup"><span data-stu-id="b07eb-119">The retention period for merge publications has a 24-hour grace period to accommodate Subscribers in different time zones.</span></span> <span data-ttu-id="b07eb-120">たとえば、保有期間を 1 日に設定した場合、実際の保有期間は 48 時間となります。</span><span class="sxs-lookup"><span data-stu-id="b07eb-120">If, for example, you set a retention period of one day, the actual retention period is 48 hours.</span></span>  
  
    -   <span data-ttu-id="b07eb-121">サブスクリプションの期限が切れないように指定することは可能ですが、メタデータをクリーンアップできなくなるため、この値は使用しないことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b07eb-121">It is possible to specify that subscriptions never expire, but it is strongly recommended that you do not use this value, because metadata cannot be cleaned up.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="b07eb-122">SQL Server Management Studio の使用</span><span class="sxs-lookup"><span data-stu-id="b07eb-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="b07eb-123">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[全般]** ページで、サブスクリプションの有効期限を設定します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-123">Set the expiration period for subscriptions on the **General** page of the **Publication Properties - \<Publication>** dialog box.</span></span> <span data-ttu-id="b07eb-124">このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b07eb-124">For more information about accessing this dialog box, see [View and Modify Publication Properties](view-and-modify-publication-properties.md).</span></span>  
  
#### <a name="to-set-the-expiration-period-for-subscriptions"></a><span data-ttu-id="b07eb-125">サブスクリプションの有効期限を設定するには</span><span class="sxs-lookup"><span data-stu-id="b07eb-125">To set the expiration period for subscriptions</span></span>  
  
1.  <span data-ttu-id="b07eb-126">**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[全般]** ページで、 **[サブスクリプションの有効期限]** セクションに、サブスクリプションに有効期限を設定するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-126">In the **Subscription expiration** section on the **General** page of the **Publication Properties - \<Publication>** dialog box, specify whether subscriptions should expire.</span></span>  
  
2.  <span data-ttu-id="b07eb-127">有効期限を設定する場合、有効期限の期間を指定します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-127">If they should expire, specify an expiration time period.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="b07eb-128">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="b07eb-128">Using Transact-SQL</span></span>  
 <span data-ttu-id="b07eb-129">この値は、レプリケーションのストアド プロシージャを使用して、パブリケーションの作成時に設定することも、後で変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="b07eb-129">You can use replication stored procedures to either set this value when a publication is created or modify this value at a later time.</span></span>  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="b07eb-130">スナップショットまたはトランザクション パブリケーションのサブスクリプションに対して有効期限を設定するには</span><span class="sxs-lookup"><span data-stu-id="b07eb-130">To set the expiration period for a subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="b07eb-131">パブリッシャーで [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-131">At the Publisher, execute [sp_addpublication](/sql/relational-databases/system-stored-procedures/sp-addpublication-transact-sql).</span></span> <span data-ttu-id="b07eb-132">**\@retention** にサブスクリプションの有効期限を時間単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-132">Specify the desired subscription expiration period, in hours, for **\@retention**.</span></span> <span data-ttu-id="b07eb-133">既定の有効期限は 336 時間です。</span><span class="sxs-lookup"><span data-stu-id="b07eb-133">The default expiration period is 336 hours.</span></span> <span data-ttu-id="b07eb-134">詳しくは、「 [パブリケーションを作成](create-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b07eb-134">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-set-the-expiration-period-for-a-subscription-to-a-merge-publication"></a><span data-ttu-id="b07eb-135">マージ パブリケーションのサブスクリプションに対して有効期限を設定するには</span><span class="sxs-lookup"><span data-stu-id="b07eb-135">To set the expiration period for a subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="b07eb-136">パブリッシャーで [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-136">At the Publisher, execute [sp_addmergepublication](/sql/relational-databases/system-stored-procedures/sp-addmergepublication-transact-sql).</span></span> <span data-ttu-id="b07eb-137">**\@retention** にサブスクリプションの有効期限を指定します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-137">Specify the desired value for the subscription expiration period for **\@retention**.</span></span> <span data-ttu-id="b07eb-138">**\@retention_period_unit** に有効期限の単位を指定します。指定できる値は次のいずれかです。</span><span class="sxs-lookup"><span data-stu-id="b07eb-138">Specify the units in which the expiration period is expressed for **\@retention_period_unit**, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="b07eb-139">**1** = 週</span><span class="sxs-lookup"><span data-stu-id="b07eb-139">**1** = week</span></span>  
  
    -   <span data-ttu-id="b07eb-140">**2** = 月</span><span class="sxs-lookup"><span data-stu-id="b07eb-140">**2** = month</span></span>  
  
    -   <span data-ttu-id="b07eb-141">**3** = 年</span><span class="sxs-lookup"><span data-stu-id="b07eb-141">**3** = year</span></span>  
  
     <span data-ttu-id="b07eb-142">既定の有効期限は 14 日です。</span><span class="sxs-lookup"><span data-stu-id="b07eb-142">The default expiration period is 14 days.</span></span> <span data-ttu-id="b07eb-143">詳しくは、「 [パブリケーションを作成](create-a-publication.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b07eb-143">For more information, see [Create a Publication](create-a-publication.md).</span></span>  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-snapshot-or-transactional-publication"></a><span data-ttu-id="b07eb-144">スナップショットまたはトランザクション パブリケーションのサブスクリプションに対して有効期限を変更するには</span><span class="sxs-lookup"><span data-stu-id="b07eb-144">To change the expiration period for a subscription to a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="b07eb-145">パブリッシャーで [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-145">At the Publisher, execute [sp_changepublication](/sql/relational-databases/system-stored-procedures/sp-changepublication-transact-sql).</span></span> <span data-ttu-id="b07eb-146">**\@property** に **retention** を、 **\@value** にサブスクリプションの新しい有効期限を時間単位で指定します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-146">Specify **retention** for **\@property** and the new subscription expiration period, in hours, for **\@value**.</span></span>  
  
#### <a name="to-change-the-expiration-period-for-a-subscription-to-a-merge-publication"></a><span data-ttu-id="b07eb-147">マージ パブリケーションのサブスクリプションに対して有効期限を変更するには</span><span class="sxs-lookup"><span data-stu-id="b07eb-147">To change the expiration period for a subscription to a merge publication</span></span>  
  
1.  <span data-ttu-id="b07eb-148">パブリッシャーで [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql) を実行します。引数には **\@publication** と **\@publisher** を指定します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-148">At the Publisher, execute [sp_helpmergepublication](/sql/relational-databases/system-stored-procedures/sp-helpmergepublication-transact-sql), specifying **\@publication** and **\@publisher**.</span></span> <span data-ttu-id="b07eb-149">結果セットの **retention_period_unit** の値 (次のいずれか) を確認します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-149">Note the value of **retention_period_unit** in the result set, which can be one of the following:</span></span>  
  
    -   <span data-ttu-id="b07eb-150">**0** = 日</span><span class="sxs-lookup"><span data-stu-id="b07eb-150">**0** = day</span></span>  
  
    -   <span data-ttu-id="b07eb-151">**1** = 週</span><span class="sxs-lookup"><span data-stu-id="b07eb-151">**1** = week</span></span>  
  
    -   <span data-ttu-id="b07eb-152">**2** = 月</span><span class="sxs-lookup"><span data-stu-id="b07eb-152">**2** = month</span></span>  
  
    -   <span data-ttu-id="b07eb-153">**3** = 年</span><span class="sxs-lookup"><span data-stu-id="b07eb-153">**3** = year</span></span>  
  
2.  <span data-ttu-id="b07eb-154">パブリッシャーで [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-154">At the Publisher, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="b07eb-155">**\@property** に **retention** を指定します。また、 **\@value** には、手順 1 の保有期間の単位に基づいて、サブスクリプションの新しい有効期限をテキストで指定します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-155">Specify **retention** for **\@property** and the new subscription expiration period, as text based on the retention period unit from step 1, for **\@value**.</span></span>  
  
3.  <span data-ttu-id="b07eb-156">(省略可) パブリッシャーで [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql)を実行します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-156">(Optional) At the Publisher, execute [sp_changemergepublication](/sql/relational-databases/system-stored-procedures/sp-changemergepublication-transact-sql).</span></span> <span data-ttu-id="b07eb-157">**\@property** に **retention_period_unit** を、 **\@value** には、サブスクリプション有効期限に使用する新しい単位を指定します。</span><span class="sxs-lookup"><span data-stu-id="b07eb-157">Specify **retention_period_unit** for **\@property** and a new unit for the subscription expiration period for **\@value**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b07eb-158">参照</span><span class="sxs-lookup"><span data-stu-id="b07eb-158">See Also</span></span>  
 <span data-ttu-id="b07eb-159">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="b07eb-159">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="b07eb-160">サブスクリプションの有効期限と非アクティブ化</span><span class="sxs-lookup"><span data-stu-id="b07eb-160">Subscription Expiration and Deactivation</span></span>](../subscription-expiration-and-deactivation.md)  
  
  
