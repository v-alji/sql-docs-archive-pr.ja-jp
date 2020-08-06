---
title: インターネット経由のレプリケーション | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- Web publishing [SQL Server replication], about Web publishing
- Web publishing [SQL Server replication]
- Internet [SQL Server replication]
- Internet [SQL Server replication], publishing
ms.assetid: 04e7f4ed-e244-4bbe-ba12-09c33abea09e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 46c61f8a5383c87d46fa0dbda18876b43ffb7739
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631783"
---
# <a name="replication-over-the-internet"></a><span data-ttu-id="2d6a1-102">インターネット経由のレプリケーション</span><span class="sxs-lookup"><span data-stu-id="2d6a1-102">Replication over the Internet</span></span>
  <span data-ttu-id="2d6a1-103">インターネット経由でデータをレプリケートすると、リモートおよび未接続のユーザーが必要に応じて、インターネット接続を使用してデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="2d6a1-103">Replicating data over the Internet allows remote, disconnected users to access data when they need it using a connection to the Internet.</span></span> <span data-ttu-id="2d6a1-104">インターネット経由のデータのレプリケーションでは、以下を使用します。</span><span class="sxs-lookup"><span data-stu-id="2d6a1-104">Replicate data over the Internet using:</span></span>  
  
-   <span data-ttu-id="2d6a1-105">仮想プライベート ネットワーク (VPN)。</span><span class="sxs-lookup"><span data-stu-id="2d6a1-105">A Virtual Private Network (VPN).</span></span> <span data-ttu-id="2d6a1-106">詳細については、「[Publish Data over the Internet Using VPN](publish-data-over-the-internet-using-vpn.md)」 (VPN を使用したインターネット経由のデータのパブリッシュ) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d6a1-106">For more information, see [Publish Data over the Internet Using VPN](publish-data-over-the-internet-using-vpn.md).</span></span>  
  
-   <span data-ttu-id="2d6a1-107">マージ レプリケーション用の Web 同期オプション。</span><span class="sxs-lookup"><span data-stu-id="2d6a1-107">The Web synchronization option for merge replication.</span></span> <span data-ttu-id="2d6a1-108">詳細については、「 [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d6a1-108">For more information, see [Web Synchronization for Merge Replication](web-synchronization-for-merge-replication.md).</span></span>  
  
 <span data-ttu-id="2d6a1-109">すべての種類の [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] レプリケーションは、VPN 経由でデータをレプリケートできますが、マージ レプリケーションを使用している場合は Web 同期を検討してください。</span><span class="sxs-lookup"><span data-stu-id="2d6a1-109">All types of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] replication can replicate data over a VPN, but you should consider Web synchronization if you are using merge replication.</span></span>  
  
  
