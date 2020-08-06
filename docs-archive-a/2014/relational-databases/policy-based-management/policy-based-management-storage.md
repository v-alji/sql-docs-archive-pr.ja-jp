---
title: ポリシー ベースの管理のストレージ | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Policy-Based Management, storage
ms.assetid: d0cbf214-fc2e-4917-8d31-1d71c9ffa61d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 0e775d038c5bb4f7a467f2691e374296f1389d84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715193"
---
# <a name="policy-based-management-storage"></a><span data-ttu-id="befa3-102">ポリシー ベースの管理のストレージ</span><span class="sxs-lookup"><span data-stu-id="befa3-102">Policy-Based Management Storage</span></span>
  <span data-ttu-id="befa3-103">ポリシーは msdb データベースに格納されます。</span><span class="sxs-lookup"><span data-stu-id="befa3-103">Policies are stored in the msdb database.</span></span> <span data-ttu-id="befa3-104">ポリシーまたは条件を変更した後、msdb をバックアップする必要があります。</span><span class="sxs-lookup"><span data-stu-id="befa3-104">After a policy or condition is changed, msdb should be backed up.</span></span> <span data-ttu-id="befa3-105">詳細については、「[システム データベースのバックアップと復元 &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="befa3-105">For more information, see [Back Up and Restore of System Databases &#40;SQL Server&#41;](../backup-restore/back-up-and-restore-of-system-databases-sql-server.md).</span></span>  
  
## <a name="storing-policies"></a><span data-ttu-id="befa3-106">ポリシーの保存</span><span class="sxs-lookup"><span data-stu-id="befa3-106">Storing Policies</span></span>  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="befa3-107">には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスの監視に使用できるポリシーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="befa3-107">includes policies that can be used to monitor an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="befa3-108">既定では、これらのポリシーはにインストールされませんが、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 既定のインストール場所である C:\Program files (x86) \MICROSOFT SQL server\120\tools\policies\databaseengine\1033 からインポートできます。</span><span class="sxs-lookup"><span data-stu-id="befa3-108">By default, these policies are not installed on the [!INCLUDE[ssDE](../../includes/ssde-md.md)]; however, they can be imported from the default installation location of C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Policies\DatabaseEngine\1033.</span></span>  
  
 <span data-ttu-id="befa3-109">ポリシーを直接作成するには、 **[ファイル] メニューの [新規作成]** を使用して、ポリシーをファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="befa3-109">You can directly create policies by using the **File/New** menu, and then saving them to a file.</span></span> <span data-ttu-id="befa3-110">これにより、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]インスタンスに接続していないときにポリシーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="befa3-110">This enables you to create policies when you are not connected to an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
 <span data-ttu-id="befa3-111">[!INCLUDE[ssDE](../../includes/ssde-md.md)] の現在のインスタンスで評価されたポリシーのポリシー履歴は、msdb システム テーブルに格納されます。</span><span class="sxs-lookup"><span data-stu-id="befa3-111">Policy history for policies evaluated in the current instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] is maintained in msdb system tables.</span></span> <span data-ttu-id="befa3-112">[!INCLUDE[ssDE](../../includes/ssde-md.md)] のその他のインスタンスに適用されたポリシーまたは [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] や [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] に適用されたポリシーのポリシー履歴は保持されません。</span><span class="sxs-lookup"><span data-stu-id="befa3-112">Policy history for policies applied to other instances of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] or applied to [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] or [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] is not retained.</span></span>  
  
  
