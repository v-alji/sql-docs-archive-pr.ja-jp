---
title: テーブルのプロパティ (SSAS テーブル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.tableprop.f1
ms.assetid: 16d3347b-7e43-4a6b-9956-fdd6ede092e6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9613609c42de8fd3a4aab7aec3208dfe3d31be4a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738815"
---
# <a name="table-properties-ssas-tabular"></a><span data-ttu-id="36210-102">Table Properties (SSAS Tabular)</span><span class="sxs-lookup"><span data-stu-id="36210-102">Table Properties (SSAS Tabular)</span></span>
  <span data-ttu-id="36210-103">このトピックでは、テーブル モデルのテーブルのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="36210-103">This topic describes tabular model table properties.</span></span> <span data-ttu-id="36210-104">ここで説明するプロパティは、ソースのどの列をインポートするかを定義する [テーブルのプロパティの編集] ダイアログ ボックスのプロパティとは異なります。</span><span class="sxs-lookup"><span data-stu-id="36210-104">The properties described here are different from those in the Edit Table Properties dialog box, which define which columns from the source are imported.</span></span>  
  
 <span data-ttu-id="36210-105">このトピックのセクション:</span><span class="sxs-lookup"><span data-stu-id="36210-105">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="36210-106">テーブルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="36210-106">Table Properties</span></span>](#bkmk_properties)  
  
-   [<span data-ttu-id="36210-107">テーブル プロパティの設定を構成するには</span><span class="sxs-lookup"><span data-stu-id="36210-107">To configure table property settings</span></span>](#bkmk_config_prop)  
  
##  <a name="table-properties"></a><a name="bkmk_properties"></a><span data-ttu-id="36210-108">テーブルのプロパティ</span><span class="sxs-lookup"><span data-stu-id="36210-108">Table Properties</span></span>  
 <span data-ttu-id="36210-109">**Basic**</span><span class="sxs-lookup"><span data-stu-id="36210-109">**Basic**</span></span>  
  
|<span data-ttu-id="36210-110">プロパティ</span><span class="sxs-lookup"><span data-stu-id="36210-110">Property</span></span>|<span data-ttu-id="36210-111">既定の設定</span><span class="sxs-lookup"><span data-stu-id="36210-111">Default Setting</span></span>|<span data-ttu-id="36210-112">説明</span><span class="sxs-lookup"><span data-stu-id="36210-112">Description</span></span>|  
|--------------|---------------------|-----------------|  
|<span data-ttu-id="36210-113">**Connection Name**</span><span class="sxs-lookup"><span data-stu-id="36210-113">**Connection Name**</span></span>|\<connection name>|<span data-ttu-id="36210-114">テーブルのデータソースへの接続の名前。</span><span class="sxs-lookup"><span data-stu-id="36210-114">The name of the connection to the table's data source.</span></span><br /><br /> <span data-ttu-id="36210-115">接続を編集するには、ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36210-115">To edit the connection, click the button.</span></span>|  
|<span data-ttu-id="36210-116">**[非表示]**</span><span class="sxs-lookup"><span data-stu-id="36210-116">**Hidden**</span></span>|<span data-ttu-id="36210-117">誤り</span><span class="sxs-lookup"><span data-stu-id="36210-117">False</span></span>|<span data-ttu-id="36210-118">レポート クライアント フィールドの一覧で、テーブルを非表示にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="36210-118">Specifies whether the table is hidden from reporting client field lists.</span></span>|  
|<span data-ttu-id="36210-119">**パーティション**</span><span class="sxs-lookup"><span data-stu-id="36210-119">**Partitions**</span></span>||<span data-ttu-id="36210-120">テーブルのパーティションは、 **[プロパティ]** ウィンドウに表示できません。</span><span class="sxs-lookup"><span data-stu-id="36210-120">Partitions for the table cannot be displayed in the **Properties** window.</span></span> <span data-ttu-id="36210-121">パーティションを表示、作成、または編集するには、ボタンをクリックしてパーティション マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="36210-121">To view, create, or edit partitions, click the button to open the Partition Manager.</span></span>|  
|<span data-ttu-id="36210-122">**ソースデータ**</span><span class="sxs-lookup"><span data-stu-id="36210-122">**Source Data**</span></span>||<span data-ttu-id="36210-123">テーブルのソース データは、 **[プロパティ]** ウィンドウに表示できません。</span><span class="sxs-lookup"><span data-stu-id="36210-123">Source data for the table cannot be displayed in the **Properties** window.</span></span> <span data-ttu-id="36210-124">ソース データを表示または編集するには、ボタンをクリックして [テーブルのプロパティの編集] ダイアログ ボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="36210-124">To view or edit the source data, click the button to open the Edit Table Properties dialog box.</span></span>|  
|<span data-ttu-id="36210-125">**テーブルの説明**</span><span class="sxs-lookup"><span data-stu-id="36210-125">**Table Description**</span></span>||<span data-ttu-id="36210-126">テーブルの説明文です。</span><span class="sxs-lookup"><span data-stu-id="36210-126">A text description for the table.</span></span><br /><br /> <span data-ttu-id="36210-127">[!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)]では、フィールド一覧のこのテーブルにエンド ユーザーがカーソルを重ねると、ツールヒントとしてこの説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="36210-127">In [!INCLUDE[ssGeminiClient](../../includes/ssgeminiclient-md.md)], if an end-user places the cursor over this table in the field list, the description appears as a tooltip.</span></span>|  
|<span data-ttu-id="36210-128">**テーブル名**</span><span class="sxs-lookup"><span data-stu-id="36210-128">**Table Name**</span></span>|\<friendly name>|<span data-ttu-id="36210-129">テーブルのフレンドリ名を指定します。</span><span class="sxs-lookup"><span data-stu-id="36210-129">Specifies the table's friendly name.</span></span> <span data-ttu-id="36210-130">テーブルのインポート ウィザードを使用してテーブルをインポートするとき、またはインポート後の任意の時点で、テーブル名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="36210-130">The table name can be specified when a table is imported using the Table Import Wizard or at any time after import.</span></span> <span data-ttu-id="36210-131">モデル内のテーブル名は、ソースに関連付けられているテーブルとは異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="36210-131">The table name in the model can be different from the associated table at the source.</span></span> <span data-ttu-id="36210-132">テーブル表示名は、レポート クライアント アプリケーション フィールドのリストおよび [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]のモデル データベース内に表示されます。</span><span class="sxs-lookup"><span data-stu-id="36210-132">The table friendly name appears in the reporting client application field list as well as in the model database in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>|  
  
 <span data-ttu-id="36210-133">**レポートのプロパティ**</span><span class="sxs-lookup"><span data-stu-id="36210-133">**Reporting Properties**</span></span>  
  
 <span data-ttu-id="36210-134">レポートのプロパティの詳細な説明と構成に関する情報については、「[Power View レポート プロパティ (SSAS テーブル)](properties-ssas-tabular.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36210-134">For detailed descriptions and configuration information for reporting properties, see [Power View Reporting Properties &#40;SSAS Tabular&#41;](properties-ssas-tabular.md).</span></span>  
  
|<span data-ttu-id="36210-135">プロパティ</span><span class="sxs-lookup"><span data-stu-id="36210-135">Property</span></span>|<span data-ttu-id="36210-136">既定の設定</span><span class="sxs-lookup"><span data-stu-id="36210-136">Default Setting</span></span>|<span data-ttu-id="36210-137">説明</span><span class="sxs-lookup"><span data-stu-id="36210-137">Description</span></span>|  
|--------------|---------------------|-----------------|  
|<span data-ttu-id="36210-138">**既定のフィールド セット**</span><span class="sxs-lookup"><span data-stu-id="36210-138">**Default Field Set**</span></span>|||  
|<span data-ttu-id="36210-139">テーブルの動作</span><span class="sxs-lookup"><span data-stu-id="36210-139">Table Behavior</span></span>|||  
  
###  <a name="to-configure-table-property-settings"></a><a name="bkmk_config_prop"></a><span data-ttu-id="36210-140">テーブルプロパティの設定を構成するには</span><span class="sxs-lookup"><span data-stu-id="36210-140">To configure table property settings</span></span>  
  
1.  <span data-ttu-id="36210-141">モデル デザイナーのデータ ビューでテーブル (タブ) をクリックするか、ダイアグラム ビューでテーブルのヘッダーをクリックします。</span><span class="sxs-lookup"><span data-stu-id="36210-141">In the model designer, in Data View, click a table (tab), or, in Diagram View, click a table header.</span></span>  
  
2.  <span data-ttu-id="36210-142">**[プロパティ]** ウィンドウで、プロパティをクリックして値を入力するか、ボタンをクリックして追加の構成オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="36210-142">In the **Properties** window, click on a property, and then type a value or click the button for additional configuration options.</span></span>  
  
  
