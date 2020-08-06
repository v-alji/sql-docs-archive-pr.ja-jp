---
title: プロアクティブキャッシュ (ディメンション) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
author: minewiskan
ms.author: owend
ms.openlocfilehash: 50c723d46b6c51fae0ccc227b5e58cf96f72c7b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632764"
---
# <a name="proactive-caching-dimensions"></a><span data-ttu-id="6ebec-102">プロアクティブ キャッシュ (ディメンション)</span><span class="sxs-lookup"><span data-stu-id="6ebec-102">Proactive Caching (Dimensions)</span></span>
  <span data-ttu-id="6ebec-103">プロアクティブ キャッシュでは、自動 MOLAP キャッシュの作成と、OLAP オブジェクトの管理が可能です。</span><span class="sxs-lookup"><span data-stu-id="6ebec-103">Proactive caching provides automatic MOLAP cache creation and management for OLAP objects.</span></span> <span data-ttu-id="6ebec-104">データベース内のデータに加えられた変更は、データベースからの通知に基づき、すぐにキューブに反映されます。</span><span class="sxs-lookup"><span data-stu-id="6ebec-104">The cubes immediately incorporate changes that are made to the data in the database, based upon notifications received from the database.</span></span> <span data-ttu-id="6ebec-105">プロアクティブ キャッシュの目標は、従来の MOLAP のパフォーマンスを提供しながら、ROLAP の即時性と管理のしやすさを保つことです。</span><span class="sxs-lookup"><span data-stu-id="6ebec-105">The goal of proactive caching is to provide the performance of traditional MOLAP, while retaining the immediacy and ease of management offered by ROLAP.</span></span>  
  
 <span data-ttu-id="6ebec-106">簡単な <xref:Microsoft.AnalysisServices.ProactiveCaching> オブジェクトは、タイミングの指定およびテーブル通知で構成されます。</span><span class="sxs-lookup"><span data-stu-id="6ebec-106">A simple <xref:Microsoft.AnalysisServices.ProactiveCaching> object is composed of: timing specification, and table notification.</span></span> <span data-ttu-id="6ebec-107">タイミングの指定は、変更通知を受信してからキャッシュが更新されるまでのタイムフレームを定義します。</span><span class="sxs-lookup"><span data-stu-id="6ebec-107">The timing specification defines the timeframe for updating the cache after a change notification has been received.</span></span> <span data-ttu-id="6ebec-108">テーブル通知は、データ テーブルと <xref:Microsoft.AnalysisServices.ProactiveCaching> オブジェクトとの間の通知スキーマを定義します。</span><span class="sxs-lookup"><span data-stu-id="6ebec-108">The table notification defines the notification schema between the data table and the <xref:Microsoft.AnalysisServices.ProactiveCaching> object.</span></span>  
  
  
