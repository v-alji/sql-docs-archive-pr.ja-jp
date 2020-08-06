---
title: バックアップファイルは、データベースファイルとは別のデバイスに配置する必要があります。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 7039bebb-1f25-4cf3-81f1-393dfb78da12
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d5eff9cb3139e1e1043f99ba63d11160b1010c27
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716821"
---
# <a name="backup-files-must-be-on-separate-devices-from-the-database-files"></a><span data-ttu-id="1f3a7-102">バックアップ ファイルはデータベース ファイルとは別のデバイスに配置する</span><span class="sxs-lookup"><span data-stu-id="1f3a7-102">Backup Files Must Be on Separate Devices from the Database Files</span></span>
  <span data-ttu-id="1f3a7-103">このルールでは、データベース ファイルがバックアップ ファイルとは異なるデバイス上にあるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="1f3a7-103">This rule checks whether database files are on devices separate from the backup files.</span></span> <span data-ttu-id="1f3a7-104">データベース ファイルとバックアップ ファイルが同じデバイスにある場合、デバイスに障害が発生すると、データベースとバックアップの両方が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="1f3a7-104">If database files and backup files are on the same device and the device fails, the database and backups will be unavailable.</span></span> <span data-ttu-id="1f3a7-105">また、データベースとバックアップ ファイルを異なるデバイスに置くと、データベースの運用でもバックアップの書き込みでも I/O パフォーマンスが最適化されます。</span><span class="sxs-lookup"><span data-stu-id="1f3a7-105">Also, putting the database and backup files on the separate devices optimizes the I/O performance for both the production use of the database and the writing of backups.</span></span>  
  
## <a name="best-practices-recommendations"></a><span data-ttu-id="1f3a7-106">ベスト プラクティスと推奨事項</span><span class="sxs-lookup"><span data-stu-id="1f3a7-106">Best Practices Recommendations</span></span>  
 <span data-ttu-id="1f3a7-107">データベースとバックアップは異なるデバイスに置くことを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="1f3a7-107">We strongly recommend that you put the database and backups on separate backup devices.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1f3a7-108">このポリシーでは、マウント ポイントを介して別個の物理デバイスを検出することはできません。</span><span class="sxs-lookup"><span data-stu-id="1f3a7-108">This policy cannot detect separate physical devices through mount points.</span></span>  
  
## <a name="for-more-information"></a><span data-ttu-id="1f3a7-109">詳細情報</span><span class="sxs-lookup"><span data-stu-id="1f3a7-109">For More Information</span></span>  
 [<span data-ttu-id="1f3a7-110">バックアップ デバイス &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1f3a7-110">Backup Devices &#40;SQL Server&#41;</span></span>](../relational-databases/backup-restore/backup-devices-sql-server.md)  
  
 [<span data-ttu-id="1f3a7-111">SQL Server データベースのバックアップと復元</span><span class="sxs-lookup"><span data-stu-id="1f3a7-111">Back Up and Restore of SQL Server Databases</span></span>](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)  
  
## <a name="see-also"></a><span data-ttu-id="1f3a7-112">参照</span><span class="sxs-lookup"><span data-stu-id="1f3a7-112">See Also</span></span>  
 [<span data-ttu-id="1f3a7-113">ポリシーベースの管理を使用したベスト プラクティスの監視と実行</span><span class="sxs-lookup"><span data-stu-id="1f3a7-113">Monitor and Enforce Best Practices by Using Policy-Based Management</span></span>](../relational-databases/policy-based-management/monitor-and-enforce-best-practices-by-using-policy-based-management.md)  
  
  
