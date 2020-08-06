---
title: インポート (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.importing.f1
ms.assetid: f1681be4-c543-4e77-875d-b13eeb75cf77
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95ea60385014e5ca8b998b986a66c384f7151081
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644682"
---
# <a name="importing-ssas"></a><span data-ttu-id="9e5b9-102">[インポートしています] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="9e5b9-102">Importing (SSAS)</span></span>
  <span data-ttu-id="9e5b9-103">**テーブルのインポート ウィザード** のこのページを使用すると、インポート操作の進行状況を表示できます。</span><span class="sxs-lookup"><span data-stu-id="9e5b9-103">This page of the **Table Import Wizard** enables you to view the progress of the import operation.</span></span> <span data-ttu-id="9e5b9-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9e5b9-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="9e5b9-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="9e5b9-105">UI element list</span></span>  
 <span data-ttu-id="9e5b9-106">**詳細**</span><span class="sxs-lookup"><span data-stu-id="9e5b9-106">**Details**</span></span>  
 <span data-ttu-id="9e5b9-107">データのインポート操作ごとに以下の情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="9e5b9-107">Displays the following information for each data import operation.</span></span>  
  
|<span data-ttu-id="9e5b9-108">列</span><span class="sxs-lookup"><span data-stu-id="9e5b9-108">Column</span></span>|<span data-ttu-id="9e5b9-109">説明</span><span class="sxs-lookup"><span data-stu-id="9e5b9-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9e5b9-110">**作業項目**</span><span class="sxs-lookup"><span data-stu-id="9e5b9-110">**Work Item**</span></span>|<span data-ttu-id="9e5b9-111">インポートするテーブルまたはビューの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="9e5b9-111">Displays the name of the table or view that is being imported.</span></span>|  
|<span data-ttu-id="9e5b9-112">**状態**</span><span class="sxs-lookup"><span data-stu-id="9e5b9-112">**Status**</span></span>|<span data-ttu-id="9e5b9-113">テーブルやビューのインポートに成功したかどうかと、インポートされた行数を示します。</span><span class="sxs-lookup"><span data-stu-id="9e5b9-113">Indicates whether the table or view was successfully imported and the number of rows that were imported.</span></span>|  
|<span data-ttu-id="9e5b9-114">**Message**</span><span class="sxs-lookup"><span data-stu-id="9e5b9-114">**Message**</span></span>|<span data-ttu-id="9e5b9-115">テーブルまたはビューのインポートに失敗した場合は、詳細情報へのリンクが表示されます。</span><span class="sxs-lookup"><span data-stu-id="9e5b9-115">If the table or view import failed, displays a link to more information.</span></span> <span data-ttu-id="9e5b9-116">この情報は、[詳細] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9e5b9-116">This information is displayed in the Details window.</span></span><br /><br /> <span data-ttu-id="9e5b9-117">テーブルまたはビューのインポートを再試行するには、ウィザードを終了し、もう一度実行します。</span><span class="sxs-lookup"><span data-stu-id="9e5b9-117">To try again to import the table or view, exit the wizard and run it again.</span></span>|  
  
 <span data-ttu-id="9e5b9-118">**[インポートの停止]**</span><span class="sxs-lookup"><span data-stu-id="9e5b9-118">**Stop Import**</span></span>  
 <span data-ttu-id="9e5b9-119">クリックすると、インポート操作が完了前に停止します。</span><span class="sxs-lookup"><span data-stu-id="9e5b9-119">Click to stop the import operation before it is finished.</span></span> <span data-ttu-id="9e5b9-120">既にインポートされたテーブルとビューは [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] デザイナーに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9e5b9-120">Tables and views that have already been imported will be displayed in the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] designer.</span></span> <span data-ttu-id="9e5b9-121">インポートされなかったテーブルとビューのインポートは行われません。</span><span class="sxs-lookup"><span data-stu-id="9e5b9-121">Tables and views that have not been imported yet will not be imported.</span></span>  
  
  
