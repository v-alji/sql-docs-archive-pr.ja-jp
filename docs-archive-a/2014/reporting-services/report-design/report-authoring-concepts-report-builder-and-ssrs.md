---
title: レポート作成の概念 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- concepts
- terminology
ms.assetid: 99311b36-5dc5-4039-ac93-4d2826701327
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d6d6293de87aba33a4cc6ee1ac094fe83041ca55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640691"
---
# <a name="report-authoring-concepts-report-builder-and-ssrs"></a><span data-ttu-id="698f0-102">レポート作成の概念 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="698f0-102">Report Authoring Concepts (Report Builder and SSRS)</span></span>
  <span data-ttu-id="698f0-103">ここでは、レポート ビルダーとレポート デザイナーのドキュメントで使用する主要な概念について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="698f0-103">This section briefly defines key concepts used in the Report Builder and Report Designer documentation.</span></span> <span data-ttu-id="698f0-104">特定の用語の定義については、「[用語集 &#40;レポート ビルダー&#41;](../report-builder/glossary-report-builder.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="698f0-104">For definitions of specific words or terms, see the [Glossary &#40;Report Builder&#41;](../report-builder/glossary-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="in-this-section"></a><span data-ttu-id="698f0-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="698f0-105">In This Section</span></span>  
 [<span data-ttu-id="698f0-106">レポート、レポート パーツ、およびレポート定義 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="698f0-106">Reports, Report Parts, and Report Definitions &#40;Report Builder and SSRS&#41;</span></span>](reports-report-parts-and-report-definitions-report-builder-and-ssrs.md)  
 <span data-ttu-id="698f0-107">初期定義、パブリッシュされたレポート、ユーザーに表示される表示レポートなど、レポートの異なる状態を示すさまざまな用語について説明します。</span><span class="sxs-lookup"><span data-stu-id="698f0-107">Describes the variety of terms used to describe a report in different states, including the initial definition, the published report, and the viewed report as it appears to the user.</span></span>  
  
 [<span data-ttu-id="698f0-108">埋め込みおよび共有のデータ接続またはデータ ソース (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="698f0-108">Embedded and Shared Data Connections or Data Sources &#40;Report Builder and SSRS&#41;</span></span>](../embedded-and-shared-data-connections-or-data-sources-report-builder-and-ssrs.md)  
 <span data-ttu-id="698f0-109">レポート、レポート モデル、およびデータ ドリブン サブスクリプションで使用されるデータ ソースへの接続を定義する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="698f0-109">Describes the ways to define connections to the data sources used in reports, report models, and data-driven subscriptions.</span></span>  
  
 [<span data-ttu-id="698f0-110">埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="698f0-110">Embedded and Shared Datasets &#40;Report Builder and SSRS&#41;</span></span>](../report-data/embedded-and-shared-datasets-report-builder-and-ssrs.md)  
 <span data-ttu-id="698f0-111">埋め込みデータセットと共有データセットの作成、格納、および管理の違いについて説明します。</span><span class="sxs-lookup"><span data-stu-id="698f0-111">Explains the differences in creating, storing, and managing embedded and shared datasets.</span></span>  
  
 [<span data-ttu-id="698f0-112">データ領域とマップ &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="698f0-112">Data Regions and Maps &#40;Report Builder and SSRS&#41;</span></span>](maps-report-builder-and-ssrs.md)  
 <span data-ttu-id="698f0-113">レポート レイアウトに追加できるデータ領域の種類について説明します。</span><span class="sxs-lookup"><span data-stu-id="698f0-113">Describes the types of data regions that can be added to a report layout.</span></span> <span data-ttu-id="698f0-114">レポートの外観 (テーブル、マトリックス、一覧、グラフ) は、データ領域によって決まります。</span><span class="sxs-lookup"><span data-stu-id="698f0-114">Data regions determine the appearance of a report: tabular, matrix, list, or chart.</span></span>  
  
 [<span data-ttu-id="698f0-115">レポートパラメーターの概念 &#40;レポートビルダーと SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="698f0-115">Report Parameters Concept &#40;Report Builder and SSRS&#41;</span></span>](report-parameters-concepts-report-builder-and-ssrs.md)  
 <span data-ttu-id="698f0-116">レポート パラメーターを定義および使用する方法と、それらをレポート サーバー上でレポート定義とは別に管理する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="698f0-116">Describes the ways to define and use report parameters, and how they are independently managed from the report definition on the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="698f0-117">参照</span><span class="sxs-lookup"><span data-stu-id="698f0-117">See Also</span></span>  
 [<span data-ttu-id="698f0-118">SQL Server 2014 のレポート ビルダー</span><span class="sxs-lookup"><span data-stu-id="698f0-118">Report Builder in SQL Server 2014</span></span>](../report-builder/report-builder-in-sql-server-2016.md)  
  
  
