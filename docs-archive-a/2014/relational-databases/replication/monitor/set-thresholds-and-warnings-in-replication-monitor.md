---
title: レプリケーション モニターのしきい値と警告の設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- alerts [SQL Server replication]
- Merge Agent, thresholds and warnings
- Distribution Agent, thresholds and warnings
- thresholds [SQL Server replication]
- Replication Monitor, thresholds and warnings
- monitoring performance [SQL Server replication], thresholds and warnings
ms.assetid: 3a409c2c-b77e-4001-b81a-1dcd918618ec
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f34878a6398df34e55e6dd3783f2da736bee0959
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741829"
---
# <a name="set-thresholds-and-warnings-in-replication-monitor"></a><span data-ttu-id="39e7a-102">レプリケーション モニターのしきい値と警告の設定</span><span class="sxs-lookup"><span data-stu-id="39e7a-102">Set Thresholds and Warnings in Replication Monitor</span></span>
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="39e7a-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] レプリケーション モニターには、パブリケーションおよびサブスクリプションの状態情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Replication Monitor displays status information for publications and subscriptions.</span></span> <span data-ttu-id="39e7a-104">既定で表示される警告は、初期化されていないサブスクリプションに対する警告だけですが、その他の条件に対する警告を有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-104">By default, Replication Monitor displays warnings only for uninitialized subscriptions, but you can enable warnings for other conditions.</span></span> <span data-ttu-id="39e7a-105">トポロジに対する警告を有効にすることをお勧めします。この警告を有効にすると、状態やパフォーマンスに関する情報をタイムリーに受け取ることができます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-105">It is recommended that you enable warnings for your topology, so that you are informed about status and performance in a timely manner.</span></span>  
  
 <span data-ttu-id="39e7a-106">警告を有効にする際には、しきい値を指定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-106">When you enable a warning, you specify a threshold.</span></span> <span data-ttu-id="39e7a-107">指定したしきい値に達したり、それを超えると、警告が表示されます (それより優先度の高い問題がない場合)。</span><span class="sxs-lookup"><span data-stu-id="39e7a-107">When that threshold is met or exceeded, a warning is displayed (unless an issue with a higher priority needs to be displayed).</span></span> <span data-ttu-id="39e7a-108">しきい値に到達した場合は、レプリケーション モニターに警告を表示でき、さらに通知を発行することができます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-108">In addition to displaying a warning in Replication Monitor, reaching a threshold can also trigger an alert.</span></span> <span data-ttu-id="39e7a-109">以下のような条件について、警告を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-109">You can enable warnings for the following conditions:</span></span>  
  
-   <span data-ttu-id="39e7a-110">サブスクリプションの有効期限の残り時間</span><span class="sxs-lookup"><span data-stu-id="39e7a-110">Imminent subscription expiration</span></span>  
  
     <span data-ttu-id="39e7a-111">すべての種類のレプリケーションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-111">This applies to all types of replication.</span></span> <span data-ttu-id="39e7a-112">指定したしきい値に達したり、それを超えたりすると、サブスクリプションの状態が " **まもなく期限切れ/期限切れ**" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-112">If the specified threshold is met or exceeded, the subscription status is displayed as **Expiring soon/Expired**.</span></span>  
  
-   <span data-ttu-id="39e7a-113">指定した待機時間 (パブリッシャーでトランザクションがコミットされてから、対応するトランザクションがサブスクライバーでコミットされるまでの経過時間) の超過</span><span class="sxs-lookup"><span data-stu-id="39e7a-113">Exceeding the specified latency (the amount of time that elapses between a transaction being committed at the Publisher and the corresponding transaction being committed at the Subscriber).</span></span>  
  
     <span data-ttu-id="39e7a-114">トランザクション レプリケーションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-114">This applies to transactional replication.</span></span> <span data-ttu-id="39e7a-115">指定したしきい値に達したり、それを超えたりすると、サブスクリプションの状態が " **パフォーマンス クリティカル**" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-115">If the specified threshold is met or exceeded, the subscription status is displayed as **Performance critical**.</span></span>  
  
-   <span data-ttu-id="39e7a-116">指定した同期時刻を超えた場合。</span><span class="sxs-lookup"><span data-stu-id="39e7a-116">Exceeding the specified synchronization time.</span></span>  
  
     <span data-ttu-id="39e7a-117">マージ レプリケーションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-117">This applies to merge replication.</span></span> <span data-ttu-id="39e7a-118">指定したしきい値に達したり、それを超えたりすると、状態が " **長期マージ**" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-118">If the specified threshold is met or exceeded, the status is displayed as **Long-running merge**.</span></span> <span data-ttu-id="39e7a-119">ダイヤルアップ接続とローカル エリア ネットワーク (LAN) 接続にそれぞれ別のしきい値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-119">You can specify different thresholds for dialup and Local Area Network (LAN) connections.</span></span>  
  
-   <span data-ttu-id="39e7a-120">指定した数の行を特定の時間内で処理できない場合。</span><span class="sxs-lookup"><span data-stu-id="39e7a-120">Falling short of processing the specified number of rows in a given amount of time.</span></span>  
  
     <span data-ttu-id="39e7a-121">マージ レプリケーションに適用できます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-121">This applies to merge replication.</span></span> <span data-ttu-id="39e7a-122">指定したしきい値に達したり、それを超えたりすると、状態が " **パフォーマンス クリティカル**" と表示されます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-122">If the specified threshold is met or exceeded, the status is displayed as **Performance critical**.</span></span> <span data-ttu-id="39e7a-123">ダイヤルアップ接続と LAN 接続にそれぞれ別のしきい値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-123">You can specify different thresholds for dialup and LAN connections.</span></span>  
  
 <span data-ttu-id="39e7a-124">**パフォーマンス クリティカル**と**長期マージ**の警告の詳細については、「[レプリケーション モニターを使用したパフォーマンスの監視](monitor-performance-with-replication-monitor.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39e7a-124">For more information on the warnings **Performance critical** and **Long-running merge**, see [Monitor Performance with Replication Monitor](monitor-performance-with-replication-monitor.md).</span></span>  
  
 <span data-ttu-id="39e7a-125">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="39e7a-125">**In This Topic**</span></span>  
  
-   [<span data-ttu-id="39e7a-126">トランザクション パブリケーションのしきい値と警告を設定する</span><span class="sxs-lookup"><span data-stu-id="39e7a-126">Set thresholds and warnings for a transactional publication</span></span>](#Transactional)  
  
-   [<span data-ttu-id="39e7a-127">マージ パプリケーションのしきい値および警告を設定する</span><span class="sxs-lookup"><span data-stu-id="39e7a-127">Set thresholds and warnings for a merge publication</span></span>](#Merge)  
  
-   [<span data-ttu-id="39e7a-128">スナップショット パプリケーションのしきい値および警告を設定する</span><span class="sxs-lookup"><span data-stu-id="39e7a-128">Set thresholds and warnings for a snapshot publication</span></span>](#Snapshot)  
  
##  <a name="to-set-thresholds-and-warnings-for-a-transactional-publication"></a><a name="Transactional"></a> <span data-ttu-id="39e7a-129">トランザクション パブリケーションのしきい値と警告を設定するには</span><span class="sxs-lookup"><span data-stu-id="39e7a-129">To set thresholds and warnings for a transactional publication</span></span>  
  
1.  <span data-ttu-id="39e7a-130">左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-130">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="39e7a-131">**[警告]** タブをクリックします。このタブの各オプションに関する情報を表示するには、メニュー バーの **[ヘルプ]** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="39e7a-131">Click the **Warnings** tab. To view more information about the options on this tab click **Help** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="39e7a-132">適切なチェック ボックスをオンにして警告を有効にします。 **[サブスクリプションの有効期限がしきい値内で切れる場合に警告します]** または **[待機時間がしきい値を超えた場合に警告します]** 。</span><span class="sxs-lookup"><span data-stu-id="39e7a-132">Enable a warning by selecting the appropriate check box: **Warn if a subscription will expire within the threshold** or **Warn if latency exceeds the threshold**.</span></span>  
  
4.  <span data-ttu-id="39e7a-133">**[しきい値]** 列で警告のしきい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-133">Set a threshold for the warnings in the **Threshold** column.</span></span> <span data-ttu-id="39e7a-134">たとえば、手順 3. で **[待機時間がしきい値を超えた場合に警告します]** チェック ボックスをオンにした場合、 **[しきい値]** 列で **60 秒** の待機時間を選択します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-134">For example, if you selected **Warn if latency exceeds the threshold** in step 3, you could select a latency of **60 seconds** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="39e7a-135">**[変更を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-135">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="39e7a-136">しきい値の警告を構成するには</span><span class="sxs-lookup"><span data-stu-id="39e7a-136">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="39e7a-137">**[警告の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-137">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="39e7a-138">**[レプリケーションの警告の構成]** ダイアログ ボックスで警告を選択し、 **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-138">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="39e7a-139">このダイアログ ボックスには、監視しきい値に関連していない警告を含め、すべての種類のパブリケーションに対する警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-139">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span> <span data-ttu-id="39e7a-140">詳細については、「[レプリケーション エージェント イベントに対する警告の使用](../agents/use-alerts-for-replication-agent-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39e7a-140">For more information, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
3.  <span data-ttu-id="39e7a-141">**[\<AlertName> 警告のプロパティ]** ダイアログ ボックスでオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-141">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="39e7a-142">**[全般]** ページで **[有効化]** をクリックし、警告を適用するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-142">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="39e7a-143">**[応答]** ページで、電子メールを送信するかどうか、または、ジョブを実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-143">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="39e7a-144">**[オプション]** ページで、応答のテキストをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-144">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="39e7a-145">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-145">Click **Close**.</span></span>  
  
##  <a name="set-thresholds-and-warnings-for-a-merge-publication"></a><a name="Merge"></a> <span data-ttu-id="39e7a-146">マージ パプリケーションのしきい値および警告を設定する</span><span class="sxs-lookup"><span data-stu-id="39e7a-146">Set thresholds and warnings for a merge publication</span></span>  
  
1.  <span data-ttu-id="39e7a-147">左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-147">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="39e7a-148">**[警告]** タブをクリックします。このタブの各オプションに関する情報を表示するには、メニュー バーの **[ヘルプ]** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="39e7a-148">Click the **Warnings** tab. To view more information about the options on this tab, click **Help** on the menu bar.</span></span>  
  
3.  <span data-ttu-id="39e7a-149">適切なチェック ボックスをオンにして警告を有効にします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-149">Enable a warning by selecting the appropriate check box:</span></span>  
  
    -   <span data-ttu-id="39e7a-150">**[サブスクリプションの有効期限がしきい値内で切れる場合に警告します]**</span><span class="sxs-lookup"><span data-stu-id="39e7a-150">**Warn if a subscription will expire within the threshold**</span></span>  
  
    -   <span data-ttu-id="39e7a-151">**[ダイヤルアップ接続のマージ長がしきい値を超えた場合に警告します]**</span><span class="sxs-lookup"><span data-stu-id="39e7a-151">**Warn if a merge length for dialup connections exceeds the threshold**</span></span>  
  
    -   <span data-ttu-id="39e7a-152">**[LAN 接続のマージ長がしきい値を超えた場合に警告します]**</span><span class="sxs-lookup"><span data-stu-id="39e7a-152">**Warn if a merge length for LAN connections exceeds the threshold**</span></span>  
  
    -   <span data-ttu-id="39e7a-153">**[LAN 接続で 1 秒あたりにマージされる行数がしきい値未満の場合に警告します]**</span><span class="sxs-lookup"><span data-stu-id="39e7a-153">**Warn if rows merged per second for LAN connections is less than the threshold**</span></span>  
  
    -   <span data-ttu-id="39e7a-154">**[ダイヤルアップ接続で 1 秒あたりにマージされる行数がしきい値未満の場合に警告します]**</span><span class="sxs-lookup"><span data-stu-id="39e7a-154">**Warn if rows merged per second for dialup connections is less than the threshold**</span></span>  
  
4.  <span data-ttu-id="39e7a-155">**[しきい値]** 列で警告のしきい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-155">Set thresholds for the warnings in the **Threshold** column.</span></span> <span data-ttu-id="39e7a-156">たとえば、手順 3. で **[ダイヤルアップ接続のマージ長がしきい値を超えた場合に警告します]** を選択した場合、 **[しきい値]** 列では **[10 分]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-156">For example, if you selected **Warn if a merge length for dialup connections exceeds the threshold** in step 3, you could select a time of **10 minutes** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="39e7a-157">**[変更を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-157">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="39e7a-158">しきい値の警告を構成するには</span><span class="sxs-lookup"><span data-stu-id="39e7a-158">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="39e7a-159">**[警告の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-159">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="39e7a-160">**[レプリケーションの警告の構成]** ダイアログ ボックスで警告を選択し、 **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-160">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="39e7a-161">このダイアログ ボックスには、監視しきい値に関連していない警告を含め、すべての種類のパブリケーションに対する警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-161">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span>  
  
3.  <span data-ttu-id="39e7a-162">**[\<AlertName> 警告のプロパティ]** ダイアログ ボックスでオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-162">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="39e7a-163">**[全般]** ページで **[有効化]** をクリックし、警告を適用するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-163">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="39e7a-164">**[応答]** ページで、電子メールを送信するかどうか、または、ジョブを実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-164">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="39e7a-165">**[オプション]** ページで、応答のテキストをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-165">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="39e7a-166">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-166">Click **Close**.</span></span>  
  
##  <a name="set-thresholds-and-warnings-for-a-snapshot-publication"></a><a name="Snapshot"></a> <span data-ttu-id="39e7a-167">スナップショット パプリケーションのしきい値および警告を設定する</span><span class="sxs-lookup"><span data-stu-id="39e7a-167">Set thresholds and warnings for a snapshot publication</span></span>  
  
1.  <span data-ttu-id="39e7a-168">左ペインでパブリッシャー グループを展開し、パブリッシャーを展開して、パブリケーションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-168">Expand a Publisher group in the left pane, expand a Publisher, and then click a publication.</span></span>  
  
2.  <span data-ttu-id="39e7a-169">**[警告]** タブをクリックします。このタブの各オプションに関する情報を表示するには、トップ メニューの **[ヘルプ]** をクリックしてください。</span><span class="sxs-lookup"><span data-stu-id="39e7a-169">Click the **Warnings** tab. To view more information about the options on this tab click **Help** on the top menu.</span></span>  
  
3.  <span data-ttu-id="39e7a-170">**[サブスクリプションの有効期限がしきい値内で切れる場合に警告します。]** チェック ボックスをオンにし、警告を有効にします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-170">Enable a warning by selecting the check box **Warn if a subscription will expire within the threshold**.</span></span>  
  
4.  <span data-ttu-id="39e7a-171">**[しきい値]** 列で警告のしきい値を設定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-171">Set a threshold for the warning in the **Threshold** column.</span></span> <span data-ttu-id="39e7a-172">たとえば、 **[しきい値]** 列で **[70%]** の値を選択できます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-172">For example, you could select a value of **70%** in the **Threshold** column.</span></span>  
  
5.  <span data-ttu-id="39e7a-173">**[変更を保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-173">Click **Save Changes**.</span></span>  
  
#### <a name="to-configure-an-alert-for-a-threshold"></a><span data-ttu-id="39e7a-174">しきい値の警告を構成するには</span><span class="sxs-lookup"><span data-stu-id="39e7a-174">To configure an alert for a threshold</span></span>  
  
1.  <span data-ttu-id="39e7a-175">**[警告の構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-175">Click **Configure Alerts**.</span></span>  
  
2.  <span data-ttu-id="39e7a-176">**[レプリケーションの警告の構成]** ダイアログ ボックスで警告を選択し、 **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-176">In the **Configure Replication Alerts** dialog box, select an alert, and then click **Configure**.</span></span>  
  
     <span data-ttu-id="39e7a-177">このダイアログ ボックスには、監視しきい値に関連していない警告を含め、すべての種類のパブリケーションに対する警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39e7a-177">This dialog box displays alerts for all publication types, including alerts that are not related to monitoring thresholds.</span></span> <span data-ttu-id="39e7a-178">詳細については、「[レプリケーション エージェント イベントに対する警告の使用](../agents/use-alerts-for-replication-agent-events.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39e7a-178">For more information, see [Use Alerts for Replication Agent Events](../agents/use-alerts-for-replication-agent-events.md).</span></span>  
  
3.  <span data-ttu-id="39e7a-179">**[\<AlertName> 警告のプロパティ]** ダイアログ ボックスでオプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-179">Set options in the **\<AlertName> alert properties** dialog box:</span></span>  
  
    -   <span data-ttu-id="39e7a-180">**[全般]** ページで **[有効化]** をクリックし、警告を適用するデータベースを指定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-180">On the **General** page, click **Enable**; specify which database the alert should apply to.</span></span>  
  
    -   <span data-ttu-id="39e7a-181">**[応答]** ページで、電子メールを送信するかどうか、または、ジョブを実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="39e7a-181">On the **Response** page, specify whether an e-mail should be sent and/or a job should be executed.</span></span>  
  
    -   <span data-ttu-id="39e7a-182">**[オプション]** ページで、応答のテキストをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-182">On the **Options** page, customize the text of the response.</span></span>  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  <span data-ttu-id="39e7a-183">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e7a-183">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39e7a-184">参照</span><span class="sxs-lookup"><span data-stu-id="39e7a-184">See Also</span></span>  
 [<span data-ttu-id="39e7a-185">レプリケーションの監視</span><span class="sxs-lookup"><span data-stu-id="39e7a-185">Monitoring Replication</span></span>](../monitoring-replication.md)  
  
  
