---
title: SQL Server のリソース正常性のトラブルシューティング (SQL Server ユーティリティ) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: 614f07b5-f221-4013-9f8d-22964cf42270
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 182225dd618dd1e9e058c549bdc07818813ba764
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633142"
---
# <a name="troubleshoot-sql-server-resource-health-sql-server-utility"></a><span data-ttu-id="e60e5-102">SQL Server のリソース正常性のトラブルシューティング (SQL Server ユーティリティ)</span><span class="sxs-lookup"><span data-stu-id="e60e5-102">Troubleshoot SQL Server Resource Health (SQL Server Utility)</span></span>
  <span data-ttu-id="e60e5-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP によって特定されるリソース正常性の問題のトラブルシューティングでは、コンピューターや [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスでの CPU の過大使用を緩和したり、データ層アプリケーションの CPU の過大使用を緩和したりします。</span><span class="sxs-lookup"><span data-stu-id="e60e5-103">Troubleshooting resource health issues identified by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP might include mitigating overutilized CPU on a computer or on an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], or mitigating overutilized CPU for a data-tier application.</span></span> <span data-ttu-id="e60e5-104">この他にも、データベース ファイルのファイル領域の過大使用や記憶域ボリュームに割り当てられたディスク領域の過大使用の解決も行われます。</span><span class="sxs-lookup"><span data-stu-id="e60e5-104">Other issues might include resolving overutilized file space for database files or resolving overutilization of allocated disk space on a storage volume.</span></span>  
  
 <span data-ttu-id="e60e5-105">データベースが "緊急" 状態になっている場合、正常性状態は過大使用になっているログ ファイル領域を示します。</span><span class="sxs-lookup"><span data-stu-id="e60e5-105">Note that if a database is in "emergency" state, the health state will display overutilized log file space.</span></span>  
  
 <span data-ttu-id="e60e5-106">データ収集の失敗 (UCP のマネージド インスタンスのリスト ビューに灰色の状態アイコンで示されます) の詳細については、「 [SQL Server ユーティリティのトラブルシューティング](../../database-engine/troubleshoot-the-sql-server-utility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e60e5-106">For more information about failed data collection resulting in gray status icons in the managed instance list view on a UCP, see [Troubleshoot the SQL Server Utility](../../database-engine/troubleshoot-the-sql-server-utility.md).</span></span> <span data-ttu-id="e60e5-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーティリティの概要の詳細については、「 [SQL Server ユーティリティの機能とタスク](sql-server-utility-features-and-tasks.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e60e5-107">For more information about getting started with [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Utility, see [SQL Server Utility Features and Tasks](sql-server-utility-features-and-tasks.md).</span></span>  
  
 <span data-ttu-id="e60e5-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP で検出された特定のリソースの正常性に関する問題を緩和する方法の詳細については、以下のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e60e5-108">For more information about mitigating specific resource health issues identified by a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] UCP, see the following topics:</span></span>  
  
-   [<span data-ttu-id="e60e5-109">SQL Server のバージョンとエディションを識別する方法</span><span class="sxs-lookup"><span data-stu-id="e60e5-109">How to identify your SQL Server version and edition</span></span>](https://go.microsoft.com/fwlink/?LinkID=178504)  
  
-   [<span data-ttu-id="e60e5-110">SQL Server 2008 のパフォーマンスに関する問題のトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="e60e5-110">Troubleshooting Performance Problems in SQL Server 2008</span></span>](https://go.microsoft.com/fwlink/?LinkId=151354)  
  
  
