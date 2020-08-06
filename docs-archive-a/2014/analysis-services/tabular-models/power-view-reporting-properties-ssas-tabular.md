---
title: レポートのプロパティの Power View (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 51205c2d-b6ce-4b92-afd2-58e399a81691
author: minewiskan
ms.author: owend
ms.openlocfilehash: e85d91578e5c3f4b47f56eeb86aa738e37e8f59b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712454"
---
# <a name="power-view-reporting-properties-ssas-tabular"></a><span data-ttu-id="c6682-102">Power View レポート プロパティ (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="c6682-102">Power View Reporting Properties (SSAS Tabular)</span></span>
  [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="c6682-103">は、データ アナリスト、意思決定者、インフォメーション ワーカーなどのビジネス ユーザーのための、直感的なアドホック レポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="c6682-103">provides intuitive ad-hoc reporting for business users such as data analysts, business decision makers, and information workers.</span></span> <span data-ttu-id="c6682-104">これを使用すると、PowerPivot ギャラリーで発行される PowerPivot ブックに基づくテーブル モデル、または [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] を使用して作成されて [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis Services インスタンスに配置されるテーブル モデルから、データのビューを簡単に作成して対話できます。</span><span class="sxs-lookup"><span data-stu-id="c6682-104">They can easily create and interact with views of data from tabular models based on PowerPivot workbooks published in a PowerPivot Gallery, or tabular models authored by using [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and then deployed to [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Analysis Services instances.</span></span> [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] <span data-ttu-id="c6682-105">はブラウザー ベースの Silverlight アプリケーションであり、SharePoint Server 2010 以降から起動されます。</span><span class="sxs-lookup"><span data-stu-id="c6682-105">is a browser-based Silverlight application launched from SharePoint Server 2010 or later.</span></span>  
  
 <span data-ttu-id="c6682-106">テーブル モデル プロジェクトを [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]で作成するとき、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポートに固有のレポート プロパティを構成できます。</span><span class="sxs-lookup"><span data-stu-id="c6682-106">When authoring tabular model projects in [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], you can configure certain reporting properties unique to [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] reports.</span></span> <span data-ttu-id="c6682-107">このセクションのトピックでは、 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)]でレポートを作成しやすくするモデルの最適化方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="c6682-107">Topics in this section describe how to optimize a model to improve the reporting experience in [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)].</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="c6682-108">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="c6682-108">Related Tasks</span></span>  
  
|<span data-ttu-id="c6682-109">トピック</span><span class="sxs-lookup"><span data-stu-id="c6682-109">Topic</span></span>|<span data-ttu-id="c6682-110">説明</span><span class="sxs-lookup"><span data-stu-id="c6682-110">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="c6682-111">Power View レポートの既定のフィールド セットの構成 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="c6682-111">Configure Default Field Set for Power View Reports &#40;SSAS Tabular&#41;</span></span>](power-view-configure-default-field-set-for-reports.md)|<span data-ttu-id="c6682-112">既定のフィールド セットの構成方法を説明します。これは列とメジャーの定義済みリストであり、レポート フィールド リストでテーブルをクリックしたときに、自動的に [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポート キャンバスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="c6682-112">Describes how to configure a Default Field Set; a predefined list of columns and measures that are automatically added to a [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] report canvas when the table is selected in the report field list.</span></span>|  
|[<span data-ttu-id="c6682-113">Power View レポートのテーブル動作プロパティの構成 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="c6682-113">Configure Table Behavior Properties for Power View Reports &#40;SSAS Tabular&#41;</span></span>](power-view-configure-table-behavior-properties-for-reports.md)|<span data-ttu-id="c6682-114">詳細行をより細かなレベルで公開するテーブル動作プロパティの構成方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="c6682-114">Describes how to configure table behavior properties that expose detail rows at a more granular level.</span></span> <span data-ttu-id="c6682-115">テーブル動作プロパティの設定により、詳細行のグループ化動作を変更できます。また、タイル、カード、およびチャートのレイアウトを使用して、識別情報の適切な既定位置を設定できます。</span><span class="sxs-lookup"><span data-stu-id="c6682-115">Setting table behavior properties changes the grouping behavior of detail rows and produces a better default placement of identifying information in tile, card, and chart layouts.</span></span>|  
  
  
