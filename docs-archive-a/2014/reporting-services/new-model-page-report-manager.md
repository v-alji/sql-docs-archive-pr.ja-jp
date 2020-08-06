---
title: '[新しいモデル] ページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 27d5bf66-b0e7-489e-a830-ffe2ec8e5350
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ed591108585b494ebb4498c1a0ab3e782693a45b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643200"
---
# <a name="new-model-page-report-manager"></a><span data-ttu-id="96cf5-102">[新しいモデル] ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="96cf5-102">New Model Page (Report Manager)</span></span>
  <span data-ttu-id="96cf5-103">このページでは、共有データ ソースから既定のレポート モデルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="96cf5-103">Use this page to generate a default report model from a shared data source.</span></span> <span data-ttu-id="96cf5-104">レポート モデルを生成できるのは、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多次元データ ソース、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] リレーショナル データ ソース、および Oracle リレーショナル データ ソースだけです。</span><span class="sxs-lookup"><span data-stu-id="96cf5-104">You can only generate report models from [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional data sources, [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] relational data sources, and Oracle relational data sources.</span></span>  
  
 <span data-ttu-id="96cf5-105">レポート マネージャーで生成されるモデルは、共有データ ソースのスキーマに基づいています。</span><span class="sxs-lookup"><span data-stu-id="96cf5-105">Models that you generate in Report Manager are based on the schema of the shared data source.</span></span> <span data-ttu-id="96cf5-106">データ ソース内のすべてのテーブルと列に対して、エンティティ、フォルダー、およびフィールドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="96cf5-106">Entities, folders, and fields are created for all tables and columns in the data source.</span></span> <span data-ttu-id="96cf5-107">アイテムを除外したり、モデルの生成方法を決定するオプションを設定することはできません。</span><span class="sxs-lookup"><span data-stu-id="96cf5-107">You cannot exclude items, nor can you set options that determine how the model is generated.</span></span> <span data-ttu-id="96cf5-108">モデルをカスタマイズまたは調整する場合は、モデル デザイナーを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="96cf5-108">If you want to customize or refine a model, you must use Model Designer instead.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="96cf5-109">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="96cf5-109">Navigation</span></span>  
 <span data-ttu-id="96cf5-110">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="96cf5-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-model-page"></a><span data-ttu-id="96cf5-111">[新しいモデル] ページを開くには</span><span class="sxs-lookup"><span data-stu-id="96cf5-111">To open the New Model page</span></span>  
  
1.  <span data-ttu-id="96cf5-112">レポート マネージャーを開き、モデルの生成元の共有データ ソースを探します。</span><span class="sxs-lookup"><span data-stu-id="96cf5-112">Open Report Manager, and locate the shared data source from which you want to generate a model.</span></span>  
  
2.  <span data-ttu-id="96cf5-113">データ ソースの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="96cf5-113">Hover over the data source, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="96cf5-114">ドロップダウン メニューで次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="96cf5-114">In the drop-down menu, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="96cf5-115">**[レポート モデルの生成]** をクリックし、[新しいモデル] ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="96cf5-115">Click **Generate Report Model** to open the New Model page.</span></span>  
  
    -   <span data-ttu-id="96cf5-116">**[管理]** をクリックし、レポートの [全般] プロパティ ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="96cf5-116">Click **Manage** to open the General properties page for the report.</span></span> <span data-ttu-id="96cf5-117">次に、 **[モデルの生成]** をクリックし、[新しいモデル] ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="96cf5-117">Then click **Generate Model** to open the New Model page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="96cf5-118">Options</span><span class="sxs-lookup"><span data-stu-id="96cf5-118">Options</span></span>  
 <span data-ttu-id="96cf5-119">**名前**</span><span class="sxs-lookup"><span data-stu-id="96cf5-119">**Name**</span></span>  
 <span data-ttu-id="96cf5-120">モデルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="96cf5-120">Specifies the name of the model.</span></span> <span data-ttu-id="96cf5-121">名前には、少なくとも 1 つの英数字が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="96cf5-121">A name must contain at least one alphanumeric character.</span></span> <span data-ttu-id="96cf5-122">また、スペースおよびいくつかの記号を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="96cf5-122">It can also include spaces and some symbols.</span></span> <span data-ttu-id="96cf5-123">名前を指定するときに使用できない記号は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="96cf5-123">Do not use the following characters when specifying a name:</span></span>  
  
 <span data-ttu-id="96cf5-124">; ?</span><span class="sxs-lookup"><span data-stu-id="96cf5-124">; ?</span></span> <span data-ttu-id="96cf5-125">: \@ & = +、$/\* \< > |" /</span><span class="sxs-lookup"><span data-stu-id="96cf5-125">: \@ & = + , $ / \* \< > | " /</span></span>  
  
 <span data-ttu-id="96cf5-126">**説明**</span><span class="sxs-lookup"><span data-stu-id="96cf5-126">**Description**</span></span>  
 <span data-ttu-id="96cf5-127">モデルの説明を表示します。</span><span class="sxs-lookup"><span data-stu-id="96cf5-127">Shows a description of the model.</span></span> <span data-ttu-id="96cf5-128">レポート マネージャーを使用してこのアイテムを表示すると、フォルダー階層を参照しているときにこの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="96cf5-128">Users who view this item through Report Manager see this description when browsing the folder hierarchy.</span></span>  
  
 <span data-ttu-id="96cf5-129">**[場所の変更]**</span><span class="sxs-lookup"><span data-stu-id="96cf5-129">**Change Location**</span></span>  
 <span data-ttu-id="96cf5-130">新しいモデルのフォルダーの場所を表示します。</span><span class="sxs-lookup"><span data-stu-id="96cf5-130">Shows the folder location for the new model.</span></span> <span data-ttu-id="96cf5-131">**[場所の変更]** ボタンをクリックすると、別の場所を選択できます。</span><span class="sxs-lookup"><span data-stu-id="96cf5-131">You can click the **Change Location** button to select a different location.</span></span>  
  
  
