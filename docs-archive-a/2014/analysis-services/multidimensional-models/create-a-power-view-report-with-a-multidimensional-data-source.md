---
title: 多次元データソースを使用して Power View レポートを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b9b6f4c9-7e1f-4f61-b657-8986e39a6af2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 179bb9eed94cd0dbb579bdb06d630b213339d12f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737051"
---
# <a name="create-a-power-view-report-with-a-multidimensional-data-source"></a><span data-ttu-id="890a6-102">多次元データ ソースを使用した Power View レポートの作成</span><span class="sxs-lookup"><span data-stu-id="890a6-102">Create a Power View Report with a Multidimensional Data Source</span></span>
  <span data-ttu-id="890a6-103">多次元モデルに基づく Power View レポートを作成するのは、PowerPivot ブックまたは Analysis Services テーブル モデルに基づくレポートを作成するのと同じです。</span><span class="sxs-lookup"><span data-stu-id="890a6-103">Creating a Power View report based on a multidimensional model is no different than creating a report based on a PowerPivot workbook or an Analysis Services Tabular model.</span></span> <span data-ttu-id="890a6-104">Power View レポートは、SharePoint ライブラリのレポート データ ソース接続ファイル (.rsds) から作成されます。</span><span class="sxs-lookup"><span data-stu-id="890a6-104">Power View reports are created from a Report Data Source connection file (.rsds) in a SharePoint library.</span></span> <span data-ttu-id="890a6-105">.rsds ファイルの作成方法については、「 [レポート データ ソースの作成](create-a-report-data-source.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="890a6-105">For more information about how to create an .rsds, see [Create a Report Data Source](create-a-report-data-source.md).</span></span>  
  
 <span data-ttu-id="890a6-106">開始する前に以下を調べます。</span><span class="sxs-lookup"><span data-stu-id="890a6-106">Before you begin, you need to know:</span></span>  
  
-   <span data-ttu-id="890a6-107">多次元モデルへの共有レポート データ ソース接続 (.rsds) を含む SharePoint ライブラリの名前と場所。</span><span class="sxs-lookup"><span data-stu-id="890a6-107">The name and location of the SharePoint library that contains a shared report data source connection (.rsds) to a multidimensional model.</span></span>  
  
#### <a name="create-a-new-blank-power-view-report"></a><span data-ttu-id="890a6-108">空の Power View レポートの新規作成</span><span class="sxs-lookup"><span data-stu-id="890a6-108">Create a new, blank Power View report</span></span>  
  
-   <span data-ttu-id="890a6-109">SharePoint ライブラリで、.rsds 共有レポートのデータ ソース接続 (多次元モデルに接続する .rsds ファイル) の横の矢印をクリックし、 **[Power View レポートの作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="890a6-109">In the SharePoint library, click the arrow next to the .rsds shared report data source connection (the .rsds that connects to the multidimensional model), and then click **Create Power View Report**.</span></span>  
  
  
