---
title: データソース (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6908998b-9302-4a90-976e-770106b48d18
author: minewiskan
ms.author: owend
ms.openlocfilehash: d686d8100e30d7608e8d90f135022bdf46785723
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716961"
---
# <a name="data-sources-ssas-tabular"></a><span data-ttu-id="f4a45-102">データ ソース (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="f4a45-102">Data Sources (SSAS Tabular)</span></span>
  <span data-ttu-id="f4a45-103">データ ソースは、テーブル モデル ソリューションに含まれるデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="f4a45-103">Data sources provide the data to be included in a tabular model solution.</span></span> <span data-ttu-id="f4a45-104">モデルには、リレーショナル データベース、データ フィード、Analysis Services キューブなどの多次元データ ソース、Microsoft Excel ブックなどのテキスト ファイルなど、さまざまなソースからデータをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="f4a45-104">You can import data into your model from a wide variety of sources such as relational databases, data feeds, multidimensional data sources such as an Analysis Services cube, and from text files such as a Microsoft Excel workbook.</span></span> <span data-ttu-id="f4a45-105">このセクションのトピックでは、インポート元のデータ ソースの種類、インポートできるさまざまなデータ型、およびそれらのソースからデータをインポートする方法を記述するタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4a45-105">Topics in this section provide information about the types of data sources you can import from, the various data types you can import, and tasks describing how to import data from those sources.</span></span>  
  
## <a name="related-topics-and-tasks"></a><span data-ttu-id="f4a45-106">関連項目およびタスク</span><span class="sxs-lookup"><span data-stu-id="f4a45-106">Related Topics and Tasks</span></span>  
  
|<span data-ttu-id="f4a45-107">トピック</span><span class="sxs-lookup"><span data-stu-id="f4a45-107">Topic</span></span>|<span data-ttu-id="f4a45-108">説明</span><span class="sxs-lookup"><span data-stu-id="f4a45-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f4a45-109">サポートされているデータ ソース &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="f4a45-109">Data Sources Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-sources-supported-ssas-tabular.md)|<span data-ttu-id="f4a45-110">このトピックでは、データのインポート元となるさまざまなデータ ソースについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f4a45-110">This topic provides information about the different data sources that you can import data from.</span></span>|  
|[<span data-ttu-id="f4a45-111">サポートされているデータ型 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="f4a45-111">Data Types Supported &#40;SSAS Tabular&#41;</span></span>](tabular-models/data-types-supported-ssas-tabular.md)|<span data-ttu-id="f4a45-112">このトピックでは、テーブル モデルでサポートされるさまざまなデータ型について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4a45-112">This topic provides information about the various data types that are supported in a Tabular Model.</span></span>|  
|[<span data-ttu-id="f4a45-113">権限借用 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="f4a45-113">Impersonation &#40;SSAS Tabular&#41;</span></span>](tabular-models/impersonation-ssas-tabular.md)|<span data-ttu-id="f4a45-114">このトピックでは、データ ソースに接続してデータをインポートまたは更新する際に Analysis Services で使用するログオン資格情報を提供する権限借用について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4a45-114">This topic provides information about impersonation, which provides logon credentials that are used by Analysis Services when connecting to a data source to import and refresh data.</span></span>|  
|[<span data-ttu-id="f4a45-115">データのインポート &#40;SSAS テーブル&#41;</span><span class="sxs-lookup"><span data-stu-id="f4a45-115">Import Data &#40;SSAS Tabular&#41;</span></span>](import-data-ssas-tabular.md)|<span data-ttu-id="f4a45-116">このセクションのタスクでは、さまざまなデータ ソースからデータをインポートする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4a45-116">Tasks in this section describe how to import data from different data sources.</span></span>|  
|[<span data-ttu-id="f4a45-117">データの処理 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="f4a45-117">Process Data &#40;SSAS Tabular&#41;</span></span>](process-data-ssas-tabular.md)|<span data-ttu-id="f4a45-118">このセクションのタスクでは、モデルに既にインポートされているデータを処理 (更新) または変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4a45-118">Tasks in this section describe how to process (refresh) or change data that has already been imported into a model.</span></span>|  
|[<span data-ttu-id="f4a45-119">既存のデータ ソース接続の編集 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="f4a45-119">Edit an Existing Data Source Connection &#40;SSAS Tabular&#41;</span></span>](edit-an-existing-data-source-connection-ssas-tabular.md)|<span data-ttu-id="f4a45-120">ソースからデータをインポートするために使用された、作成済みのデータ ソース接続を編集する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f4a45-120">Describes how to edit a data source connection that has already been created and used to import data from a source.</span></span>|  
  
  
