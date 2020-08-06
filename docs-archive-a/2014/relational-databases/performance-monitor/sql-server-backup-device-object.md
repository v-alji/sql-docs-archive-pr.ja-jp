---
title: 'SQL Server: Backup Device オブジェクト | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e3126310ad31dcc153fc79508dbfaccf86f5da78
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639465"
---
# <a name="sql-server-backup-device-object"></a><span data-ttu-id="dfdf0-102">SQL Server: Backup Device オブジェクト</span><span class="sxs-lookup"><span data-stu-id="dfdf0-102">SQL Server, Backup Device Object</span></span>
  <span data-ttu-id="dfdf0-103">**Backup Device** オブジェクトには、バックアップ操作と復元操作に使用する Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ デバイスを監視するためのカウンターがあります。</span><span class="sxs-lookup"><span data-stu-id="dfdf0-103">The **Backup Device** object provides counters to monitor Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup devices used for backup and restore operations.</span></span> <span data-ttu-id="dfdf0-104">バックアップ デバイスを監視するのは、バックアップ操作と復元操作のスループット、または進行状況やパフォーマンスをデバイスごとに調べる場合です。</span><span class="sxs-lookup"><span data-stu-id="dfdf0-104">Monitor backup devices when you want to determine the throughput or the progress and performance of your backup and restore operations on a per device basis.</span></span> <span data-ttu-id="dfdf0-105">データベースのバックアップ操作または復元操作全体のスループットを監視するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** オブジェクトの **Backup/Restore Throughput/sec** カウンターを使用します。</span><span class="sxs-lookup"><span data-stu-id="dfdf0-105">To monitor the throughput of the entire database backup or restore operation, use the **Backup/Restore Throughput/sec** counter of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** object.</span></span> <span data-ttu-id="dfdf0-106">詳しくは、「 [SQL Server, Databases Object](sql-server-databases-object.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="dfdf0-106">For more information, see [SQL Server, Databases Object](sql-server-databases-object.md).</span></span>  
  
 <span data-ttu-id="dfdf0-107">次の表では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** カウンターについて説明します。</span><span class="sxs-lookup"><span data-stu-id="dfdf0-107">This table describes the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** counter.</span></span>  
  
|<span data-ttu-id="dfdf0-108">SQL Server Backup Device カウンター</span><span class="sxs-lookup"><span data-stu-id="dfdf0-108">SQL Server Backup Device counters</span></span>|<span data-ttu-id="dfdf0-109">説明</span><span class="sxs-lookup"><span data-stu-id="dfdf0-109">Description</span></span>|  
|---------------------------------------|-----------------|  
|<span data-ttu-id="dfdf0-110">**Device Throughput Bytes/sec**</span><span class="sxs-lookup"><span data-stu-id="dfdf0-110">**Device Throughput Bytes/sec**</span></span>|<span data-ttu-id="dfdf0-111">データベースをバックアップまたは復元するときに使用するバックアップ デバイスの読み取りおよび書き込み操作のスループット (1 秒あたりのバイト数)。</span><span class="sxs-lookup"><span data-stu-id="dfdf0-111">Throughput of read and write operations (in bytes per second) for a backup device used when backing up or restoring databases.</span></span> <span data-ttu-id="dfdf0-112">このカウンターは、バックアップ操作または復元操作の実行中のみ存在します。</span><span class="sxs-lookup"><span data-stu-id="dfdf0-112">This counter exists only while the backup or restore operation is executing.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dfdf0-113">参照</span><span class="sxs-lookup"><span data-stu-id="dfdf0-113">See Also</span></span>  
 <span data-ttu-id="dfdf0-114">[バックアップ デバイス &#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="dfdf0-114">[Backup Devices &#40;SQL Server&#41;](../backup-restore/backup-devices-sql-server.md) </span></span>  
 [<span data-ttu-id="dfdf0-115">リソースの利用状況の監視 &#40;システム モニター&#41;</span><span class="sxs-lookup"><span data-stu-id="dfdf0-115">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
