---
title: AlwaysOn 可用性グループを使用した暗号化されたデータベース (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Transparent Data Encryption, AlwaysOn Availability Groups
- TDE, AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 09eb6ebc-3051-4fff-86a5-93524507b1fc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91e717a896634a7df5a96253c51207831f142cff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632705"
---
# <a name="encrypted-databases-with-alwayson-availability-groups-sql-server"></a><span data-ttu-id="052f7-102">暗号化されたデータベースと AlwaysOn 可用性グループ (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="052f7-102">Encrypted Databases with AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="052f7-103">このトピックでは、 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] で現在暗号化されているデータベースまたは最近暗号化解除されたデータベースと [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="052f7-103">This topic contains information about the using currently encrypted or recently decrypted databases with [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
 <span data-ttu-id="052f7-104">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="052f7-104">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="052f7-105">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="052f7-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
-   [<span data-ttu-id="052f7-106">関連タスク</span><span class="sxs-lookup"><span data-stu-id="052f7-106">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="052f7-107">制限事項と制約事項</span><span class="sxs-lookup"><span data-stu-id="052f7-107">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="052f7-108">データベースが暗号化されているか、データベース暗号化キー (DEK) を含んでいる場合、 [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] または [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] を使用してそのデータベースを可用性グループに追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="052f7-108">If a database is encrypted or even contains a Database Encryption Key (DEK), you cannot use the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)] or [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)] to add the database to an availability group.</span></span> <span data-ttu-id="052f7-109">暗号化されたデータベースの暗号化を解除した場合でも、そのログ バックアップには暗号化されたデータが含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="052f7-109">Even if an encrypted database has been decrypted, its log backups might contain encrypted data.</span></span> <span data-ttu-id="052f7-110">この場合、データベースに対する初期データの完全同期が失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="052f7-110">In this case, full initial data synchronization could fail on the database.</span></span> <span data-ttu-id="052f7-111">これは、ログの復元操作にはデータベース暗号化キー (DEK) で使用された証明書が必要なことがあり、その証明書を使用できないことがあるためです。</span><span class="sxs-lookup"><span data-stu-id="052f7-111">This is because the restore log operation might require the certificate that was used by the database encryption keys (DEKs), and that certificate might be unavailable.</span></span>  
  
     <span data-ttu-id="052f7-112">暗号化解除されたデータベースを、ウィザードを使用して可用性グループに追加できるようにするには、次の操作を行います。</span><span class="sxs-lookup"><span data-stu-id="052f7-112">To make a decrypted database eligible to add to an availability group using the wizard:</span></span>  
  
    1.  <span data-ttu-id="052f7-113">プライマリ データベースのログ バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="052f7-113">Create a log backup of the primary database.</span></span>  
  
    2.  <span data-ttu-id="052f7-114">プライマリ データベースの完全バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="052f7-114">Create a full database backup of the primary database.</span></span>  
  
    3.  <span data-ttu-id="052f7-115">セカンダリ レプリカをホストするサーバー インスタンスでデータベース バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="052f7-115">Restore the database backup on the server instance that hosts the secondary replica.</span></span>  
  
    4.  <span data-ttu-id="052f7-116">プライマリ データベースから新しいログ バックアップを作成します。</span><span class="sxs-lookup"><span data-stu-id="052f7-116">Create a new log backup from primary database.</span></span>  
  
    5.  <span data-ttu-id="052f7-117">セカンダリ データベースでこのログ バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="052f7-117">Restore this log backup on the secondary database.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="052f7-118">関連タスク</span><span class="sxs-lookup"><span data-stu-id="052f7-118">Related Tasks</span></span>  
  
-   [<span data-ttu-id="052f7-119">可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="052f7-119">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="052f7-120">可用性グループ ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="052f7-120">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="052f7-121">可用性グループへのデータベース追加ウィザードの使用 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="052f7-121">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="052f7-122">参照</span><span class="sxs-lookup"><span data-stu-id="052f7-122">See Also</span></span>  
 <span data-ttu-id="052f7-123">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="052f7-123">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="052f7-124">透過的なデータ暗号化 &#40;TDE&#41;</span><span class="sxs-lookup"><span data-stu-id="052f7-124">Transparent Data Encryption &#40;TDE&#41;</span></span>](../../../relational-databases/security/encryption/transparent-data-encryption.md)  
  
  
