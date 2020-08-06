---
title: SQL Server フェールオーバー クラスターでのレポート サーバー データベースのホスト | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7bd5f019-2857-452f-a023-cc3b9e93aec4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 921ce03fd08e7820266b828d5848f64db1e257ee
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716114"
---
# <a name="host-a-report-server-database-in-a-sql-server-failover-cluster"></a><span data-ttu-id="a717f-102">SQL Server フェールオーバー クラスターでのレポート サーバー データベースのホスト</span><span class="sxs-lookup"><span data-stu-id="a717f-102">Host a Report Server Database in a SQL Server Failover Cluster</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a717f-103">インスタンスに対して複数のディスクを使用できるように、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、フェールオーバー クラスタリングをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="a717f-103">provides failover clustering support so that you can use multiple disks for one or more [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instances.</span></span> <span data-ttu-id="a717f-104">フェールオーバー クラスタリングは、レポート サーバー データベースでのみサポートされています。つまり、フェールオーバー クラスターの一部としてレポート サーバー サービスを実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="a717f-104">Failover clustering is supported only for the report server database; you cannot run the Report Server service as part of a failover cluster.</span></span>  
  
 <span data-ttu-id="a717f-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー クラスターでレポート サーバー データベースをホストするには、クラスターを事前にインストールして構成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="a717f-105">To host a report server database on a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster, the cluster must already be installed and configured.</span></span> <span data-ttu-id="a717f-106">その後、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 構成ツールの [データベースのセットアップ] ページでレポート サーバー データベースを作成するときに、そのフェールオーバー クラスターをサーバー名として選択できます。</span><span class="sxs-lookup"><span data-stu-id="a717f-106">You can then select the failover cluster as the server name when you create the report server database in the Database Setup page of the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool.</span></span>  
  
 <span data-ttu-id="a717f-107">レポート サーバー サービスはフェールオーバー クラスターに参加できませんが、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] フェールオーバー クラスターをインストールしたコンピューターに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] をインストールできます。</span><span class="sxs-lookup"><span data-stu-id="a717f-107">Although the Report Server service cannot participate in a failover cluster, you can install [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on a computer that has a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover cluster installed.</span></span> <span data-ttu-id="a717f-108">レポート サーバーは、フェールオーバー クラスターとは別に実行されます。</span><span class="sxs-lookup"><span data-stu-id="a717f-108">The report server runs independently of the failover cluster.</span></span> <span data-ttu-id="a717f-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] フェールオーバー インスタンスの一部であるコンピューターにレポート サーバーをインストールした場合、レポート サーバー データベースにフェールオーバー クラスターを使用する必要はありません。別の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスを使用してデータベースをホストできます。</span><span class="sxs-lookup"><span data-stu-id="a717f-109">If you install a report server on a computer that is part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] failover instance, you are not required to use the failover cluster for the report server database; you can use a different [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance to host the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a717f-110">参照</span><span class="sxs-lookup"><span data-stu-id="a717f-110">See Also</span></span>  
 <span data-ttu-id="a717f-111">[レポート サーバー データベース &#40;SSRS ネイティブ モード&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="a717f-111">[Report Server Database &#40;SSRS Native Mode&#41;](../report-server/report-server-database-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="a717f-112">レポート サーバー データベースの作成 &#40;SSRS構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="a717f-112">Create a Report Server Database  &#40;SSRS Configuration Manager&#41;</span></span>](../../sql-server/install/create-a-report-server-database-ssrs-configuration-manager.md)  
  
  
