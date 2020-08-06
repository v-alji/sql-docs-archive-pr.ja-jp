---
title: データをインポートする方法を選択する (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.choosehowtoimpdata.f1
ms.assetid: 17dc6903-c239-46aa-a3b0-6e3156accacc
author: minewiskan
ms.author: owend
ms.openlocfilehash: fba1d5801f325400b228920fffa06512f4db8de2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634158"
---
# <a name="choose-how-to-import-the-data-ssas"></a><span data-ttu-id="9b3d5-102">[データのインポート方法の選択] (SSAS)</span><span class="sxs-lookup"><span data-stu-id="9b3d5-102">Choose How to Import the Data (SSAS)</span></span>
  <span data-ttu-id="9b3d5-103">**テーブルのインポート ウィザード** のこのページを使用すると、選択したデータ ソースからデータをインポートする方法を選択できます。</span><span class="sxs-lookup"><span data-stu-id="9b3d5-103">This page of the **Table Import Wizard** enables you to choose how to import data from the selected data source.</span></span> <span data-ttu-id="9b3d5-104">[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]からウィザードにアクセスするには、 **[モデル]** メニューの **[データ ソースからのインポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="9b3d5-104">To access the wizard from the [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], on the **Model** menu, click **Import from Data Source**.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="9b3d5-105">UI 要素の一覧</span><span class="sxs-lookup"><span data-stu-id="9b3d5-105">UI element list</span></span>  
 <span data-ttu-id="9b3d5-106">**[インポートするデータをテーブルとビューの一覧から選択する]**</span><span class="sxs-lookup"><span data-stu-id="9b3d5-106">**Select from a list of tables and views to choose the data to import**</span></span>  
 <span data-ttu-id="9b3d5-107">データを一覧から選択してインポートする場合に、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9b3d5-107">Select this option if you want to import data by selecting from a list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9b3d5-108">このオプションは、選択したデータ ソースが、 **テーブルのインポート ウィザード** でサポートされるスキーマ情報を公開している場合にのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="9b3d5-108">This option is available only when the selected data source exposes schema information that the **Table Import Wizard** supports.</span></span>  
  
 <span data-ttu-id="9b3d5-109">**[インポートするデータを指定するクエリを記述する]**</span><span class="sxs-lookup"><span data-stu-id="9b3d5-109">**Write a query to specify the data to import**</span></span>  
 <span data-ttu-id="9b3d5-110">SQL クエリを使用してデータをインポートする場合に、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="9b3d5-110">Select this option if you want to import data by using a SQL query.</span></span> <span data-ttu-id="9b3d5-111">SQL クエリでは、インポートするデータを操作できます。</span><span class="sxs-lookup"><span data-stu-id="9b3d5-111">The SQL query can manipulate the data that is imported.</span></span> <span data-ttu-id="9b3d5-112">たとえば、異なるテーブルからのデータを結合することも、特定の条件を満たす行だけを選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="9b3d5-112">For example, you could join data from different tables or select only rows that meet certain criteria.</span></span>  
  
  
