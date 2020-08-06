---
title: 失敗したファイルの追加操作のトラブルシューティング (AlwaysOn 可用性グループ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary databases [SQL Server], Availability Groups
- Availability Groups [SQL Server], troubleshooting
ms.assetid: 31ceaebf-864b-4dd0-9112-0d047b0316ad
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2551080c214f18473caa71a3e17797c34fcc943a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741270"
---
# <a name="troubleshoot-a-failed-add-file-operation-alwayson-availability-groups"></a><span data-ttu-id="b04b5-102">失敗したファイルの追加操作のトラブルシューティング (AlwaysOn 可用性グループ)</span><span class="sxs-lookup"><span data-stu-id="b04b5-102">Troubleshoot a Failed Add-File Operation (AlwaysOn Availability Groups)</span></span>
  <span data-ttu-id="b04b5-103">一部の AlwaysOn 可用性グループの配置では、プライマリ レプリカをホストするシステムとセカンダリ レプリカをホストするシステムのファイル パスが異なります。</span><span class="sxs-lookup"><span data-stu-id="b04b5-103">In some AlwaysOn availability group deployments, file paths differ between the system that hosts the primary replica and systems that host a secondary replica.</span></span> <span data-ttu-id="b04b5-104">ファイルの追加操作のファイル パスがセカンダリ レプリカ上に存在しない場合でも、プライマリ データベース上でのファイルの追加操作は成功します。</span><span class="sxs-lookup"><span data-stu-id="b04b5-104">If the file path of an add-file operation does not exist on a secondary replica, the add-file operation will succeed on the primary database.</span></span> <span data-ttu-id="b04b5-105">ただし、そのようなファイルの追加操作を行うと、セカンダリ データベースが中断します。</span><span class="sxs-lookup"><span data-stu-id="b04b5-105">But the add-file operation will cause the secondary database to be suspended.</span></span> <span data-ttu-id="b04b5-106">セカンダリ データベースが中断すると、セカンダリ レプリカが NOT SYNCHRONIZING 状態になります。</span><span class="sxs-lookup"><span data-stu-id="b04b5-106">This, in turn, causes the secondary replica to enter the NOT SYNCHRONIZING state.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b04b5-107">可能であれば、特定のセカンダリ データベースのファイル パス (ドライブ文字を含む) は、対応するプライマリ データベースのパスと一致させることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b04b5-107">We recommend that, if possible, the file path (including the drive letter) of a given secondary database be identical to the path of the corresponding primary database.</span></span>  
  
## <a name="problem-resolution"></a><span data-ttu-id="b04b5-108">問題解決</span><span class="sxs-lookup"><span data-stu-id="b04b5-108">Problem Resolution</span></span>  
 <span data-ttu-id="b04b5-109">この問題を解決するには、データベース所有者が次の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b04b5-109">To resolve this problem the database owner must complete the following steps:</span></span>  
  
1.  <span data-ttu-id="b04b5-110">セカンダリ データベースを可用性グループから削除します。</span><span class="sxs-lookup"><span data-stu-id="b04b5-110">Remove the secondary database from the availability group.</span></span> <span data-ttu-id="b04b5-111">詳細については、「[可用性グループからのセカンダリ データベースの削除 &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b04b5-111">For more information, see [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="b04b5-112">既存のセカンダリ データベースで、WITH NORECOVERY と WITH MOVE (セカンダリ レプリカをホストするサーバー インスタンス上のファイル パスを指定) を使用して、セカンダリ データベースに追加されたファイルを含むファイル グループの完全バックアップを復元します。</span><span class="sxs-lookup"><span data-stu-id="b04b5-112">On the existing secondary database, restore a full backup of the filegroup that contains the added file to the secondary database, using WITH NORECOVERY and WITH MOVE (specifying the file path on the server instance that hosts the secondary replica).</span></span> <span data-ttu-id="b04b5-113">詳細については、「[データベースを新しい場所に復元する &#40;SQL Server&#41;](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b04b5-113">For more information, see [Restore a Database to a New Location &#40;SQL Server&#41;](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="b04b5-114">ファイルの追加操作を含むトランザクション ログをプライマリ データベースでバックアップし、WITH NORECOVERY と WITH MOVE を使用して、そのログ バックアップをセカンダリ データベースに手動で復元します。</span><span class="sxs-lookup"><span data-stu-id="b04b5-114">Back up the transaction log that contains the add-file operation on the primary database, and manually restore the log backup on the secondary database using WITH NORECOVERY and WITH MOVE.</span></span>  
  
4.  <span data-ttu-id="b04b5-115">可用性グループに再度参加させるセカンダリ データベースを準備します。これは、プライマリ データベースでバックアップした他の未処理のログを、WITH NO RECOVERY で復元することによって行います。</span><span class="sxs-lookup"><span data-stu-id="b04b5-115">Prepare the secondary database for re-joining the availability group, by restoring, WITH NO RECOVERY, any other outstanding log backups from the primary database.</span></span>  
  
5.  <span data-ttu-id="b04b5-116">セカンダリ データベースを可用性グループに再度参加させます。</span><span class="sxs-lookup"><span data-stu-id="b04b5-116">Rejoin the secondary database to the availability group.</span></span> <span data-ttu-id="b04b5-117">詳細については、「 [可用性グループへのセカンダリ データベースの参加 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)のインスタンスに AlwaysOn 可用性グループを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b04b5-117">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b04b5-118">参照</span><span class="sxs-lookup"><span data-stu-id="b04b5-118">See Also</span></span>  
 <span data-ttu-id="b04b5-119">[AlwaysOn 可用性グループ &#40;SQL Server の概要&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b04b5-119">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="b04b5-120">[可用性グループに対するセカンダリ データベースの手動準備 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b04b5-120">[Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="b04b5-121">[孤立ユーザーのトラブルシューティング &#40;SQL Server&#41;](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b04b5-121">[Troubleshoot Orphaned Users &#40;SQL Server&#41;](../../../sql-server/failover-clusters/troubleshoot-orphaned-users-sql-server.md) </span></span>  
 [<span data-ttu-id="b04b5-122">SQL Server&#41;削除された AlwaysOn 可用性グループ構成 &#40;のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="b04b5-122">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
  
