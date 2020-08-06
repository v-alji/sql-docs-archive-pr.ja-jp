---
title: '[テーブルのプロパティ] ダイアログボックス (SSAS-テーブル) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.ssmsimbi.TableProperties.f1
ms.assetid: 77571ccd-bdba-4e07-af55-465509dc6a33
author: minewiskan
ms.author: owend
ms.openlocfilehash: e3ca6d787616821532b30af0fe3591f79d6dbea6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639680"
---
# <a name="table-properties-dialog-box-ssas---tabular"></a><span data-ttu-id="4d5d2-102">[テーブルのプロパティ] ダイアログ ボックス (SSAS - テーブル)</span><span class="sxs-lookup"><span data-stu-id="4d5d2-102">Table Properties Dialog Box (SSAS - Tabular)</span></span>
  <span data-ttu-id="4d5d2-103">テーブル モデル データベースでテーブルのプロパティを表示するには、 **の** [テーブルのプロパティ] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ダイアログ ボックスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-103">Use the **Table Properties** dialog box in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to view the properties of a table in a tabular model database.</span></span> <span data-ttu-id="4d5d2-104">すべてのプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-104">All properties are read-only.</span></span>  
  
 <span data-ttu-id="4d5d2-105">**[テーブルのプロパティ]** ダイアログ ボックスを表示するには、オブジェクト エクスプローラーでテーブルを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-105">You can display the **Table Properties** dialog box by right-clicking a table in Object Explorer and selecting **Properties**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4d5d2-106">Options</span><span class="sxs-lookup"><span data-stu-id="4d5d2-106">Options</span></span>  
  
|<span data-ttu-id="4d5d2-107">期間</span><span class="sxs-lookup"><span data-stu-id="4d5d2-107">Term</span></span>|<span data-ttu-id="4d5d2-108">定義</span><span class="sxs-lookup"><span data-stu-id="4d5d2-108">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="4d5d2-109">**名前**</span><span class="sxs-lookup"><span data-stu-id="4d5d2-109">**Name**</span></span>|<span data-ttu-id="4d5d2-110">テーブルの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-110">Displays the name of the table.</span></span>|  
|<span data-ttu-id="4d5d2-111">**ID**</span><span class="sxs-lookup"><span data-stu-id="4d5d2-111">**ID**</span></span>|<span data-ttu-id="4d5d2-112">テーブルの識別子を表示します。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-112">Displays the identifier of the table.</span></span>|  
|<span data-ttu-id="4d5d2-113">**説明**</span><span class="sxs-lookup"><span data-stu-id="4d5d2-113">**Description**</span></span>|<span data-ttu-id="4d5d2-114">テーブルの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-114">Displays the description of the table.</span></span>|  
|<span data-ttu-id="4d5d2-115">**[タイムスタンプの作成]**</span><span class="sxs-lookup"><span data-stu-id="4d5d2-115">**Create Timestamp**</span></span>|<span data-ttu-id="4d5d2-116">テーブルが作成された日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-116">Displays the date and time the table was created.</span></span>|  
|<span data-ttu-id="4d5d2-117">**[スキーマの最終更新]**</span><span class="sxs-lookup"><span data-stu-id="4d5d2-117">**Last Schema Update**</span></span>|<span data-ttu-id="4d5d2-118">テーブルのメタデータが最後に更新された日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-118">Displays the date and time the metadata for the table was last updated.</span></span>|  
|<span data-ttu-id="4d5d2-119">**State**</span><span class="sxs-lookup"><span data-stu-id="4d5d2-119">**State**</span></span>|<span data-ttu-id="4d5d2-120">テーブルの処理状態を表示します。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-120">Displays the processing state of the table.</span></span> <span data-ttu-id="4d5d2-121">このプロパティの値の詳細については、「<xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-121">For more information about the values for this property, see <xref:Microsoft.AnalysisServices.ProcessableMajorObject.State%2A>.</span></span>|  
|<span data-ttu-id="4d5d2-122">**[最終処理]**</span><span class="sxs-lookup"><span data-stu-id="4d5d2-122">**Last Processed**</span></span>|<span data-ttu-id="4d5d2-123">テーブルが最後に処理された日時を表示します。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-123">Displays the date and time the table was last processed.</span></span>|  
|<span data-ttu-id="4d5d2-124">**[現在のストレージ モード]**</span><span class="sxs-lookup"><span data-stu-id="4d5d2-124">**Current Storage Mode**</span></span>|<span data-ttu-id="4d5d2-125">テーブルの現在のストレージ モードを表示します。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-125">Displays the current storage mode for the table.</span></span> <span data-ttu-id="4d5d2-126">ストレージ モードはデータベース レベルで設定され、すべてのテーブルで継承されます。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-126">Storage mode is set at the database level and inherited by all tables.</span></span> <span data-ttu-id="4d5d2-127">テーブル レベルで異なるストレージ モードを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-127">You cannot use different storage modes at the table level.</span></span> <span data-ttu-id="4d5d2-128">有効な値は、InMemory (既定値)、InMemoryWithDirectQuery、DirectQuery、DirectQueryWithinMemory です。</span><span class="sxs-lookup"><span data-stu-id="4d5d2-128">Valid values are InMemory (default), InMemoryWithDirectQuery, DirectQuery, DirectQueryWithinMemory.</span></span>|  
  
  
