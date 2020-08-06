---
title: 期限切れのバックアップ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 307a4ad0-675a-4f97-9a3c-cedd61bdfae5
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: c6a944b08b15d591a9bbce47a0c0c6a8de3eb54a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642735"
---
# <a name="outdated-backup"></a><span data-ttu-id="41804-102">期限切れのバックアップ</span><span class="sxs-lookup"><span data-stu-id="41804-102">Outdated Backup</span></span>
  <span data-ttu-id="41804-103">このルールでは、データベースに最新のバックアップがあることを確認します。</span><span class="sxs-lookup"><span data-stu-id="41804-103">This rule checks that a database has recent backups.</span></span> <span data-ttu-id="41804-104">定期的なバックアップをスケジュールすることは、さまざまなエラーによるデータの損失からデータベースを保護するために重要です。</span><span class="sxs-lookup"><span data-stu-id="41804-104">Scheduling regular backups is important for protecting your databases against data loss from many different failures.</span></span> <span data-ttu-id="41804-105">データをバックアップする適切な頻度は、データベースの復旧モデル、潜在的なデータの損失に関するビジネス要件、およびデータベースの更新頻度によって異なります。</span><span class="sxs-lookup"><span data-stu-id="41804-105">The appropriate frequency for backing up data depends on the recovery model of the database, on business requirements about potential data loss, and on how frequently the database is updated.</span></span> <span data-ttu-id="41804-106">頻繁に更新されるデータベースでは、バックアップ間で作業の損失の危険性が非常に早く高まります。</span><span class="sxs-lookup"><span data-stu-id="41804-106">In a frequently updated database, the work-loss exposure increases fairly quickly between backups.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="41804-107">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="41804-107">Best Practices Recommendations</span></span>  
 <span data-ttu-id="41804-108">データ損失からデータベースを保護するために、十分な頻度でバックアップを行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="41804-108">We recommend that you perform backups frequently enough to protect databases against data loss.</span></span>  
  
 <span data-ttu-id="41804-109">単純復旧モデルと完全復旧モデルの両方でデータのバックアップを行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="41804-109">The simple recovery model and full recovery model both require data backups.</span></span> <span data-ttu-id="41804-110">いずれの復旧モデルでも、完全バックアップを差分バックアップで補完すると、データ損失の危険性を効率的に低くすることができます。</span><span class="sxs-lookup"><span data-stu-id="41804-110">For either recovery model, you can supplement your full backups with differential backups to efficiently reduce the risk of data loss.</span></span>  
  
 <span data-ttu-id="41804-111">完全復旧モデルを使用するデータベースの場合は、ログのバックアップを頻繁に行うことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="41804-111">For a database that uses the full recovery model, we recommend that you take frequent log backups.</span></span> <span data-ttu-id="41804-112">非常に重要なデータが含まれている実稼働データベースの場合、ログのバックアップは通常 1 ～ 15 分ごとに行われます。</span><span class="sxs-lookup"><span data-stu-id="41804-112">For a production database that contains very important data, log backups would typically be taken every one to fifteen minutes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41804-113">バックアップのスケジュール方法として、データベース メンテナンス プランをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="41804-113">The recommended method for scheduling backups is a database maintenance plan.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="41804-114">詳細情報</span><span class="sxs-lookup"><span data-stu-id="41804-114">For More Information</span></span>  
 [<span data-ttu-id="41804-115">システム データベースのバックアップと復元 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41804-115">Back Up and Restore of System Databases &#40;SQL Server&#41;</span></span>](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)  
  
 [<span data-ttu-id="41804-116">復旧モデル &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41804-116">Recovery Models &#40;SQL Server&#41;</span></span>](../backup-restore/recovery-models-sql-server.md)  
  
 [<span data-ttu-id="41804-117">データベースの差分バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41804-117">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 [<span data-ttu-id="41804-118">データベースの完全バックアップの作成 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41804-118">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](../backup-restore/create-a-full-database-backup-sql-server.md)  
  
 [<span data-ttu-id="41804-119">メンテナンス プラン</span><span class="sxs-lookup"><span data-stu-id="41804-119">Maintenance Plans</span></span>](../maintenance-plans/maintenance-plans.md)  
  
 [<span data-ttu-id="41804-120">トランザクション ログのバックアップ &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="41804-120">Transaction Log Backups &#40;SQL Server&#41;</span></span>](../backup-restore/transaction-log-backups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="41804-121">参照</span><span class="sxs-lookup"><span data-stu-id="41804-121">See Also</span></span>  
 [<span data-ttu-id="41804-122">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="41804-122">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
