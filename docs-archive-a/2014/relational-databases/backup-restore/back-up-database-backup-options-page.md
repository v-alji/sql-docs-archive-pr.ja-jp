---
title: '[データベースのバックアップ] ([バックアップ オプション] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.backupdatabase.options.f1
- swb.backupdatabase.options.f1
ms.assetid: df0ddcdb-c94e-472b-b786-469ae8117b93
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: ffd527ba4334244c7fd4c5d4a73099093cb8520b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645696"
---
# <a name="back-up-database-backup-options-page"></a><span data-ttu-id="02b67-102">[データベースのバックアップ] ([バックアップ オプション] ページ)</span><span class="sxs-lookup"><span data-stu-id="02b67-102">Back Up Database (Backup Options Page)</span></span>
  <span data-ttu-id="02b67-103">**[データベースのバックアップ]** ダイアログ ボックスの **[バックアップ オプション]** ページを使用すると、データベースのバックアップのオプションを表示または変更できます。</span><span class="sxs-lookup"><span data-stu-id="02b67-103">Use the  **Backup Options** page of the **Back Up Database** dialog box to view or modify database backup options.</span></span>  
  
 <span data-ttu-id="02b67-104">**SQL Server Management Studio を使用してバックアップを作成するには**</span><span class="sxs-lookup"><span data-stu-id="02b67-104">**To create a backup by using SQL Server Management Studio**</span></span>  
  
-   [<span data-ttu-id="02b67-105">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="02b67-105">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="02b67-106">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="02b67-106">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="02b67-107">データベース メンテナンス プランを定義して、データベース バックアップを作成できます。</span><span class="sxs-lookup"><span data-stu-id="02b67-107">You can define a database maintenance plan to create database backups.</span></span> <span data-ttu-id="02b67-108">詳細については、「 [メンテナンス プラン](../maintenance-plans/maintenance-plans.md) 」および「 [メンテナンス プラン ウィザードの使用](../maintenance-plans/use-the-maintenance-plan-wizard.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02b67-108">For more information, see [Maintenance Plans](../maintenance-plans/maintenance-plans.md) and [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02b67-109">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]を使用してバックアップ タスクを指定する場合、 [!INCLUDE[tsql](../../includes/tsql-md.md)][[スクリプト]](/sql/t-sql/statements/backup-transact-sql) ボタンをクリックしてスクリプトの保存先を選択することにより、対応する **BACKUP** スクリプトを生成できます。</span><span class="sxs-lookup"><span data-stu-id="02b67-109">When you specify a backup task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate the corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)][BACKUP](/sql/t-sql/statements/backup-transact-sql) script by clicking the **Script** button and then selecting a destination for the script.</span></span>  
  
## <a name="options"></a><span data-ttu-id="02b67-110">Options</span><span class="sxs-lookup"><span data-stu-id="02b67-110">Options</span></span>  
  
### <a name="backup-set"></a><span data-ttu-id="02b67-111">バックアップ セット</span><span class="sxs-lookup"><span data-stu-id="02b67-111">Backup set</span></span>  
 <span data-ttu-id="02b67-112">**[バックアップ セット]** パネルのオプションでは、バックアップ操作で作成されるバックアップ セットに関する情報を指定できます。</span><span class="sxs-lookup"><span data-stu-id="02b67-112">The options of the **Backup set** panel allow for you to specify optional information about the backup set created by the back up operation.</span></span>  
  
 <span data-ttu-id="02b67-113">**名前**</span><span class="sxs-lookup"><span data-stu-id="02b67-113">**Name**</span></span>  
 <span data-ttu-id="02b67-114">バックアップ セット名を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b67-114">Specify the backup set name.</span></span> <span data-ttu-id="02b67-115">データベース名とバックアップの種類に基づいて、既定の名前が自動的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="02b67-115">The system automatically suggests a default name based on the database name and the backup type.</span></span>  
  
 <span data-ttu-id="02b67-116">バックアップ セットの詳細については、「[メディア セット、メディア ファミリ、およびバックアップ セット &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02b67-116">For information about backup sets, see [Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md).</span></span>  
  
 <span data-ttu-id="02b67-117">**説明**</span><span class="sxs-lookup"><span data-stu-id="02b67-117">**Description**</span></span>  
 <span data-ttu-id="02b67-118">バックアップ セットの説明を入力します。</span><span class="sxs-lookup"><span data-stu-id="02b67-118">Enter a description of the backup set.</span></span>  
  
 <span data-ttu-id="02b67-119">**[バックアップ セットの有効期限]**</span><span class="sxs-lookup"><span data-stu-id="02b67-119">**Backup set will expire**</span></span>  
 <span data-ttu-id="02b67-120">次の有効期限オプションの 1 つを選択します。</span><span class="sxs-lookup"><span data-stu-id="02b67-120">Choose one of the following expiration options.</span></span> <span data-ttu-id="02b67-121">**[URL]** がバックアップ先として選択された場合、このオプションは無効です。</span><span class="sxs-lookup"><span data-stu-id="02b67-121">This option is disabled if **URL** is chosen as the backup destination.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02b67-122">**変更後**</span><span class="sxs-lookup"><span data-stu-id="02b67-122">**After**</span></span>|<span data-ttu-id="02b67-123">このバックアップ セットが失効して上書きできるようになるまでの経過日数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b67-123">Specify the number of days that must elapse before this backup set expires and can be overwritten.</span></span> <span data-ttu-id="02b67-124">0 ～ 99,999 日の値を指定できます。0 日を指定すると、バックアップ セットの有効期限は無期限になります。</span><span class="sxs-lookup"><span data-stu-id="02b67-124">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span><br /><br /> <span data-ttu-id="02b67-125">バックアップの有効期限の既定値は、 **[バックアップ メディアの既定の保有期間 (日)]** オプションの値のセットです。</span><span class="sxs-lookup"><span data-stu-id="02b67-125">The default value for backup expiration is the value set in the **Default backup media retention (in days)** option.</span></span> <span data-ttu-id="02b67-126">このオプションを表示するには、オブジェクト エクスプローラーでサーバー名を右クリックし、 **[プロパティ]** を選択した後、 **[サーバーのプロパティ]** ダイアログ ボックスの **[データベースの設定]** ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="02b67-126">To access this, right-click the server name in Object Explorer and select **Properties**; then click the **Database Settings** page of the **Server Properties** dialog box.</span></span>|  
|<span data-ttu-id="02b67-127">**基準**</span><span class="sxs-lookup"><span data-stu-id="02b67-127">**On**</span></span>|<span data-ttu-id="02b67-128">バックアップ セットが失効して上書きできるようになる特定の日を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b67-128">Specify a specific date when the backup set expires and can be overwritten.</span></span>|  
  
### <a name="compression"></a><span data-ttu-id="02b67-129">圧縮</span><span class="sxs-lookup"><span data-stu-id="02b67-129">Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="02b67-130">(またはそれ以降のバージョン) では、 [バックアップの圧縮](backup-compression-sql-server.md)がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="02b67-130">(or a later version) supports [backup compression](backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="02b67-131">**[バックアップの圧縮の設定]**</span><span class="sxs-lookup"><span data-stu-id="02b67-131">**Set backup compression**</span></span>  
 <span data-ttu-id="02b67-132">[!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] (またはそれ以降のバージョン) で、バックアップの圧縮の値を次の中から 1 つ選択します。</span><span class="sxs-lookup"><span data-stu-id="02b67-132">In [!INCLUDE[ssEnterpriseEd10](../../../includes/ssenterpriseed10-md.md)] (or a later version), select one of the following backup compression values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="02b67-133">**[既定のサーバー設定を使用する]**</span><span class="sxs-lookup"><span data-stu-id="02b67-133">**Use the default server setting**</span></span>|<span data-ttu-id="02b67-134">オンにすると、サーバー レベルの既定値が使用されます。</span><span class="sxs-lookup"><span data-stu-id="02b67-134">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="02b67-135">この既定値は、 **backup compression default** サーバー構成オプションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b67-135">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="02b67-136">このオプションの現在の設定を表示する方法については、「 [backup compression default サーバー構成オプションの表示または構成](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02b67-136">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="02b67-137">**[バックアップを圧縮する]**</span><span class="sxs-lookup"><span data-stu-id="02b67-137">**Compress backup**</span></span>|<span data-ttu-id="02b67-138">オンにすると、サーバー レベルの既定値に関係なく、バックアップが圧縮されます。</span><span class="sxs-lookup"><span data-stu-id="02b67-138">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="02b67-139">**\*\* 重要 \*\*** 既定の設定では、圧縮によって CPU 使用率が著しく増加し、圧縮処理によって CPU がさらに消費されるために、同時に実行される操作が悪影響を受ける場合があります。</span><span class="sxs-lookup"><span data-stu-id="02b67-139">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="02b67-140">このため、 [リソース ガバナー](../resource-governor/resource-governor.md)によって CPU 使用率が制限されるセッションでは、優先度の低い圧縮バックアップを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="02b67-140">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="02b67-141">詳細については、「 [リソース ガバナーを使用してバックアップの圧縮による CPU 使用率を制限する方法 &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02b67-141">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="02b67-142">**[バックアップを圧縮しない]**</span><span class="sxs-lookup"><span data-stu-id="02b67-142">**Do not compress backup**</span></span>|<span data-ttu-id="02b67-143">オンにすると、サーバー レベルの既定値に関係なく、圧縮されていないバックアップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="02b67-143">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
### <a name="encryption"></a><span data-ttu-id="02b67-144">暗号化</span><span class="sxs-lookup"><span data-stu-id="02b67-144">Encryption</span></span>  
 <span data-ttu-id="02b67-145">暗号化されたバックアップを作成するには、 **[バックアップ ファイルを暗号化する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="02b67-145">To create an encrypted backup, check the **Encrypt backup** check box.</span></span> <span data-ttu-id="02b67-146">暗号化手順に使用する暗号化アルゴリズムを選択し、既存の証明書または非対称キーの一覧から証明書または非対称キーを指定します。</span><span class="sxs-lookup"><span data-stu-id="02b67-146">Select an encryption algorithm to use for the encryption step, and provide a Certificate or Asymmetric key from a list of existing certificates or asymmetric keys.</span></span> <span data-ttu-id="02b67-147">暗号化に使用できるアルゴリズムは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="02b67-147">The available algorithms for encryption are:</span></span>  
  
-   <span data-ttu-id="02b67-148">AES 128</span><span class="sxs-lookup"><span data-stu-id="02b67-148">AES 128</span></span>  
  
-   <span data-ttu-id="02b67-149">AES 192</span><span class="sxs-lookup"><span data-stu-id="02b67-149">AES 192</span></span>  
  
-   <span data-ttu-id="02b67-150">AES 256</span><span class="sxs-lookup"><span data-stu-id="02b67-150">AES 256</span></span>  
  
-   <span data-ttu-id="02b67-151">Triple DES</span><span class="sxs-lookup"><span data-stu-id="02b67-151">Triple DES</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="02b67-152">既存のバックアップ セットに追加することを選択した場合、暗号化オプションは無効になります。</span><span class="sxs-lookup"><span data-stu-id="02b67-152">The encryption option is disabled if you selected to append to existing backup set.</span></span>  
>   
>  <span data-ttu-id="02b67-153">証明書またはキーをバックアップし、暗号化されたバックアップとは別の場所に保管することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="02b67-153">It is recommended practice to back up your certificate or keys and store them in a different location than the backup you encrypted.</span></span>  
>   
>  <span data-ttu-id="02b67-154">拡張キー管理 (EKM) に存在するキーのみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="02b67-154">Only keys residing in the Extensible Key Management (EKM) are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02b67-155">参照</span><span class="sxs-lookup"><span data-stu-id="02b67-155">See Also</span></span>  
 <span data-ttu-id="02b67-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="02b67-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="02b67-157">[トランザクション ログのバックアップ &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="02b67-157">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="02b67-158">[ファイルおよびファイル グループのバックアップ &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="02b67-158">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 [<span data-ttu-id="02b67-159">データベースが破損したときのトランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="02b67-159">Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;</span></span>](back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md)  
  
  
