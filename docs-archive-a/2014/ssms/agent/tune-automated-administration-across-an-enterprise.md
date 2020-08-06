---
title: 企業全体の自動管理のチューニング | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52fef95cd13beafef89701196a445a90e6fc1eb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642494"
---
# <a name="tune-automated-administration-across-an-enterprise"></a><span data-ttu-id="808a3-102">企業全体の自動管理のチューニング</span><span class="sxs-lookup"><span data-stu-id="808a3-102">Tune Automated Administration Across an Enterprise</span></span>
  <span data-ttu-id="808a3-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントによるマルチサーバー管理では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の自己チューニング機能を活用しています。</span><span class="sxs-lookup"><span data-stu-id="808a3-103">Multiserver administration with Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent takes advantage of the self-tuning features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="808a3-104">したがって、通常の条件下では、新たにジョブのチューニングを行う必要はありません。</span><span class="sxs-lookup"><span data-stu-id="808a3-104">Therefore, under normal conditions, additional job tuning is not necessary.</span></span> <span data-ttu-id="808a3-105">ただし、ジョブの実行、警告の生成、オペレーターへの通知などを行うと、ネットワークの負荷が増加します。</span><span class="sxs-lookup"><span data-stu-id="808a3-105">However, network loads increase when you run jobs, generate alerts, and notify operators.</span></span> <span data-ttu-id="808a3-106">これらの動作によって生じるネットワーク トラフィックを最小限に抑えるために、企業全体の自動管理をチューニングできます。</span><span class="sxs-lookup"><span data-stu-id="808a3-106">You can tune automated administration across an enterprise to minimize the network traffic these activities cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="808a3-107">参照</span><span class="sxs-lookup"><span data-stu-id="808a3-107">See Also</span></span>  
 [<span data-ttu-id="808a3-108">パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="808a3-108">Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
