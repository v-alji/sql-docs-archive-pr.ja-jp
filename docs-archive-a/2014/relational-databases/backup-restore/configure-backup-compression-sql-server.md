---
title: バックアップの圧縮の構成 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
ms.assetid: 430905eb-d218-458c-bd48-aeee6fbb7446
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f70994eb64cb6a50b538fd87f03ce7ea2fafe857
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645680"
---
# <a name="configure-backup-compression-sql-server"></a><span data-ttu-id="37f81-102">バックアップの圧縮の構成 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="37f81-102">Configure Backup Compression (SQL Server)</span></span>
  <span data-ttu-id="37f81-103">インストール時には、既定でバックアップ圧縮が無効になっています。</span><span class="sxs-lookup"><span data-stu-id="37f81-103">At installation, backup compression is off by default.</span></span> <span data-ttu-id="37f81-104">バックアップ圧縮の既定の動作は、 **backup compression default** サーバー レベル構成オプションで定義されています。</span><span class="sxs-lookup"><span data-stu-id="37f81-104">The default behavior for backup compression is defined by the **backup compression default** Option server-level configuration option.</span></span> <span data-ttu-id="37f81-105">ただし、単一バックアップの作成時や、一連の定期的バックアップのスケジュール設定時には、サーバー レベルの既定値をオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="37f81-105">However, you can override the server-level default when creating a single backup or scheduling a series of routine backups.</span></span> <span data-ttu-id="37f81-106">サーバー レベルの既定値を変更する方法については、「 [backup compression default サーバー構成オプションの表示または構成](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37f81-106">To change the server-level default, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>  
  
## <a name="override-the-backup-compression-default"></a><span data-ttu-id="37f81-107">backup compression default のオーバーライド</span><span class="sxs-lookup"><span data-stu-id="37f81-107">Override the Backup Compression Default</span></span>  
 <span data-ttu-id="37f81-108">バックアップ、バックアップ ジョブ、またはログ配布構成ごとにバックアップ圧縮動作を変更できます。</span><span class="sxs-lookup"><span data-stu-id="37f81-108">You can change the backup compression behavior for an individual backup, backup job, or log shipping configuration.</span></span>  
  
-   **[!INCLUDE[tsql](../../includes/tsql-md.md)]**  
  
     <span data-ttu-id="37f81-109">バックアップの作成時に、サーバーの backup compression default をオーバーライドするには、[BACKUP](/sql/t-sql/statements/backup-transact-sql) ステートメントで WITH NO_COMPRESSION または WITH COMPRESSION を使用します。</span><span class="sxs-lookup"><span data-stu-id="37f81-109">To override the server backup-compression default when creating a backup, use either WITH NO_COMPRESSION or WITH COMPRESSION in you [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
     <span data-ttu-id="37f81-110">ログ配布構成の場合は、[sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)[sp_change_log_shipping_primary_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql) を使用して、ログ バックアップのバックアップ圧縮動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="37f81-110">For a log shipping configuration, you can control the backup compression behavior of log backups by using [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql)[sp_change_log_shipping_primary_database &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-change-log-shipping-primary-database-transact-sql).</span></span>  
  
-   **[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]**  
  
     <span data-ttu-id="37f81-111">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスのバックアップ圧縮の既定オプションを表示または構成する方法については、「[backup compression default サーバー構成オプションの表示または構成](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37f81-111">For information about how to view or configure the backup compression default option for an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>  
  
     <span data-ttu-id="37f81-112">サーバーのバックアップ圧縮に対する既定の動作は、バックアップの作成時、次のダイアログ ボックスのいずれかで **[バックアップを圧縮する]** または **[バックアップを圧縮しない]** を指定してオーバーライドできます。</span><span class="sxs-lookup"><span data-stu-id="37f81-112">You can override the server backup-compression default when creating a backup by specifying **Compress backup** or **Do not compress backup** in any of the following dialog boxes:</span></span>  
  
    -   <span data-ttu-id="37f81-113">[[データベースのバックアップ] ([オプション] ページ)](back-up-database-backup-options-page.md)</span><span class="sxs-lookup"><span data-stu-id="37f81-113">[Back Up Database (Options Page)](back-up-database-backup-options-page.md)</span></span>  
  
         <span data-ttu-id="37f81-114">データベースをバックアップすると、個別のデータベース、ファイル、またはログのバックアップについて、圧縮を制御できます。</span><span class="sxs-lookup"><span data-stu-id="37f81-114">When backing up a database, you can control backup compression for an individual database, file, or log backup.</span></span>  
  
    -   [<span data-ttu-id="37f81-115">メンテナンス プラン ウィザードの使用</span><span class="sxs-lookup"><span data-stu-id="37f81-115">Use the Maintenance Plan Wizard</span></span>](../maintenance-plans/use-the-maintenance-plan-wizard.md)  
  
         <span data-ttu-id="37f81-116">メンテナンス プラン ウィザードを使用すると、スケジュール設定対象の完全データベース バックアップ、差分データベース バックアップ、またはログ バックアップについて、圧縮を制御できます。</span><span class="sxs-lookup"><span data-stu-id="37f81-116">The Maintenance Plan Wizard enables you to control backup compression for each set full or differential database backups or log backups that you schedule.</span></span>  
  
    -   <span data-ttu-id="37f81-117">Integration Services (SSIS) の [データベースのバックアップ タスク](../../integration-services/control-flow/back-up-database-task.md)</span><span class="sxs-lookup"><span data-stu-id="37f81-117">Integration Services (SSIS) [Back Up Database task](../../integration-services/control-flow/back-up-database-task.md)</span></span>  
  
         <span data-ttu-id="37f81-118">単一データベースまたは複数データベースをバックアップするパッケージの作成時に、バックアップ圧縮動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="37f81-118">You can control the backup compression behavior when creating a package for backing up a single database or multiple databases.</span></span>  
  
    -   <span data-ttu-id="37f81-119">[[トランザクション ログのバックアップの設定]](../databases/log-shipping-transaction-log-backup-settings.md)</span><span class="sxs-lookup"><span data-stu-id="37f81-119">[Log Shipping Transaction Log Backup Settings](../databases/log-shipping-transaction-log-backup-settings.md)</span></span>  
  
         <span data-ttu-id="37f81-120">ログのバックアップのバックアップ圧縮動作を制御できます。</span><span class="sxs-lookup"><span data-stu-id="37f81-120">You can control the backup compression behavior of log backups.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="37f81-121">参照</span><span class="sxs-lookup"><span data-stu-id="37f81-121">See Also</span></span>  
 [<span data-ttu-id="37f81-122">バックアップの圧縮 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="37f81-122">Backup Compression &#40;SQL Server&#41;</span></span>](backup-compression-sql-server.md)  
  
  
