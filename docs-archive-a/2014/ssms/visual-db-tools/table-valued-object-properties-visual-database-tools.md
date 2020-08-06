---
title: テーブル値オブジェクトのプロパティ (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.designers.properties.TVO
ms.assetid: eaf06cbf-8242-4483-894f-80ae02a4840e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 6f1c1e6414d0059dfd1d43bbbb40eabdfc9470b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720685"
---
# <a name="table-valued-object-properties-visual-database-tools"></a><span data-ttu-id="575db-102">テーブル値オブジェクトのプロパティ (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="575db-102">Table-Valued Object Properties (Visual Database Tools)</span></span>
  <span data-ttu-id="575db-103">これらのプロパティは、 **クエリおよびビュー デザイナー**でテーブル値オブジェクトを選択したときに、[プロパティ] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="575db-103">These properties appear in the Properties window when you select a table-valued object in **Query and View Designer**.</span></span> <span data-ttu-id="575db-104">テーブル値オブジェクトは、ビュー、シノニム、派生テーブル、またはテーブル値関数です。</span><span class="sxs-lookup"><span data-stu-id="575db-104">The table-valued object could be a view, synonym, derived table, or table-valued function.</span></span> <span data-ttu-id="575db-105">特に指定しない限り、 **[プロパティ]** ウィンドウのこれらのプロパティは読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="575db-105">Unless otherwise noted, these properties are read-only in the **Properties** window.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="575db-106">このトピックでは、プロパティを五十音順ではなくカテゴリ別に示しています。</span><span class="sxs-lookup"><span data-stu-id="575db-106">The properties in this topic are ordered by category rather than alphabet.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="575db-107">使用中の設定やエディションに応じて、表示されるダイアログ ボックスとメニュー コマンドがヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="575db-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="575db-108">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** を選択してください。</span><span class="sxs-lookup"><span data-stu-id="575db-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span>  
  
 <span data-ttu-id="575db-109">**[IDENTITY] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="575db-109">**Identity Category**</span></span>  
 <span data-ttu-id="575db-110">展開すると、 **[オブジェクト名]** プロパティと **[TVO 型]** プロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="575db-110">Expands to show the **Name** and **TVO Type** properties.</span></span>  
  
 <span data-ttu-id="575db-111">**Name**</span><span class="sxs-lookup"><span data-stu-id="575db-111">**Name**</span></span>  
 <span data-ttu-id="575db-112">選択されたテーブル値オブジェクトの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="575db-112">Shows the name of the selected table-valued object.</span></span>  
  
 <span data-ttu-id="575db-113">**[TVO 型]**</span><span class="sxs-lookup"><span data-stu-id="575db-113">**TVO Type**</span></span>  
 <span data-ttu-id="575db-114">テーブル値オブジェクトの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="575db-114">Shows which type of table-valued object.</span></span> <span data-ttu-id="575db-115">ベース テーブル、ビュー、テーブル値関数、または派生テーブルです。</span><span class="sxs-lookup"><span data-stu-id="575db-115">It can be either a base table, view, table-valued function, or a derived table.</span></span>  
  
 <span data-ttu-id="575db-116">**クエリ デザイナー カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="575db-116">**Query DesignerCategory**</span></span>  
 <span data-ttu-id="575db-117">展開すると、 **[エイリアス]** 、 **[列一覧]** 、 **[名前]** 、および **[パラメーター リスト]** のプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="575db-117">Expands to show properties for **Alias**, **Column List**, **Full Name**, and **Parameter List**.</span></span>  
  
 <span data-ttu-id="575db-118">**エイリアス**</span><span class="sxs-lookup"><span data-stu-id="575db-118">**Alias**</span></span>  
 <span data-ttu-id="575db-119">選択されたテーブル値オブジェクトの別名を表示します。</span><span class="sxs-lookup"><span data-stu-id="575db-119">Shows the alias for the selected table-valued object.</span></span> <span data-ttu-id="575db-120">別名を追加または変更するには、フィールドに入力します。</span><span class="sxs-lookup"><span data-stu-id="575db-120">To add or change an alias, type it into the field.</span></span>  
  
 <span data-ttu-id="575db-121">**[列一覧]**</span><span class="sxs-lookup"><span data-stu-id="575db-121">**Column List**</span></span>  
 <span data-ttu-id="575db-122">選択されたテーブル値オブジェクトに含まれている列を表示します。</span><span class="sxs-lookup"><span data-stu-id="575db-122">Shows the columns included in the selected table-valued object.</span></span> <span data-ttu-id="575db-123">別のウィンドウに表示する場合は、[列一覧] をクリックしてから、プロパティの右の [...] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="575db-123">To see them in a separate window, click Column List and then click the ellipses (...) to the right of the property.</span></span>  
  
 <span data-ttu-id="575db-124">**[名前]**</span><span class="sxs-lookup"><span data-stu-id="575db-124">**Full Name**</span></span>  
 <span data-ttu-id="575db-125">選択したテーブル値オブジェクトの名前を表示します。オブジェクトのスキーマまたはデータ ソースなどの追加情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="575db-125">Shows the name of the selected table-valued object, including additional information such as the schema or data source of the object.</span></span>  
  
 <span data-ttu-id="575db-126">**[パラメーター リスト]**</span><span class="sxs-lookup"><span data-stu-id="575db-126">**Parameter List**</span></span>  
 <span data-ttu-id="575db-127">選択したテーブル値関数用に定義されたパラメーターを表示します。</span><span class="sxs-lookup"><span data-stu-id="575db-127">Shows the parameters defined for selected table-valued function.</span></span> <span data-ttu-id="575db-128">パラメーターの値を定義する場合は、[パラメーター リスト] をクリックしてから、プロパティの右の [...] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="575db-128">To define a value for the parameters, click Parameter List and then click the ellipses (...) to the right of the property.</span></span> <span data-ttu-id="575db-129">[関数パラメーター] ダイアログ ボックスで、値を入力します。</span><span class="sxs-lookup"><span data-stu-id="575db-129">In the Function Parameters dialog box, type in values.</span></span> <span data-ttu-id="575db-130">このプロパティは、テーブル値関数が選択された場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="575db-130">This property is only available when a table-valued function is selected.</span></span>  
  
  
