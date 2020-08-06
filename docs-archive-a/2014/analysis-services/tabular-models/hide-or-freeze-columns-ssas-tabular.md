---
title: 列の非表示または固定 (SSAS テーブル)Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.hideunhidecolumnsdb.f1
ms.assetid: 5407aee5-6a07-4559-a2ba-2ca00a242f02
author: minewiskan
ms.author: owend
ms.openlocfilehash: 71398eecbc342b4e3f9c2445fef3023132266dac
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712514"
---
# <a name="hide-or-freeze-columns-ssas-tabular"></a><span data-ttu-id="46457-102">列の非表示または固定 (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="46457-102">Hide or Freeze Columns (SSAS Tabular)</span></span>
  <span data-ttu-id="46457-103">モデル デザイナーで、テーブルに表示する必要のない列がある場合は、一時的に非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="46457-103">In the model designer, if there are columns that you don't want to display in a table, you can temporarily hide them.</span></span> <span data-ttu-id="46457-104">列を非表示にすると画面上のスペースが広くなり、新しい列の追加や、必要なデータ列のみを対象とした作業を行いやすくなります。</span><span class="sxs-lookup"><span data-stu-id="46457-104">Hiding a column gives you more room on the screen to add new columns or to work with only relevant columns of data.</span></span> <span data-ttu-id="46457-105">列の非表示と再表示は、モデル デザイナーの **[列]** メニューおよび各列見出しで使用できる右クリック メニューのどちらからでも行うことができます。</span><span class="sxs-lookup"><span data-stu-id="46457-105">You can hide and unhide columns from the **Column** menu in the model designer, and from the right-click menu available from each column header.</span></span> <span data-ttu-id="46457-106">モデルのある領域を表示したまま、別の領域にスクロールするには、表示しておく領域内の特定の列を固定します。</span><span class="sxs-lookup"><span data-stu-id="46457-106">To keep an area of a model visible while you scroll to another area of the model, you can lock specific columns in one area by freezing them.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="46457-107">列を非表示にする機能はデータ セキュリティを目的としたものではなく、モデル デザイナーまたはレポートの列の一覧を簡略化し、短縮して表示するだけのためのものでもありません。</span><span class="sxs-lookup"><span data-stu-id="46457-107">The ability to hide columns is not intended to be used for data security, only to simplify and shorten the list of columns visible in the model designer or reports.</span></span> <span data-ttu-id="46457-108">データを保護するには、セキュリティ ロールを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="46457-108">To secure data, you can define security roles.</span></span> <span data-ttu-id="46457-109">ロールは、表示することができるメタデータとデータを、ロールで定義されたオブジェクトのみに制限できます。</span><span class="sxs-lookup"><span data-stu-id="46457-109">Roles can limit viewable metadata and data to only those objects defined in the role.</span></span> <span data-ttu-id="46457-110">詳しくは、「 [ロール &#40;SSAS テーブル&#41;](roles-ssas-tabular.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="46457-110">For more information, see [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="46457-111">列を非表示にする場合、モデル デザイナーまたはレポートでの作業中に列を非表示にするかどうかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="46457-111">When you hide a column, you have the option to hide the column while you are working in the model designer or in reports.</span></span> <span data-ttu-id="46457-112">すべての列を非表示にすると、モデル デザイナーのテーブル全体が空白になります。</span><span class="sxs-lookup"><span data-stu-id="46457-112">If you hide all columns, the entire table appears blank in the model designer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="46457-113">非表示にする列が多い場合は、列の表示と非表示を切り替える代わりにパースペクティブを作成する方法もあります。</span><span class="sxs-lookup"><span data-stu-id="46457-113">If you have many columns to hide, you can create a perspective instead of hiding and unhiding columns.</span></span> <span data-ttu-id="46457-114">パースペクティブは、データのカスタム ビューです。関連するデータのサブセットを容易に扱うことができます。</span><span class="sxs-lookup"><span data-stu-id="46457-114">A perspective is a custom view of the data that makes it easier to work with subset of related data.</span></span> <span data-ttu-id="46457-115">詳細については、「[Create and Manage Perspectives (SSAS Tabular)](perspectives-ssas-tabular.md)」(パースペクティブの作成と管理 (SSAS テーブル)) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="46457-115">For more information, see [Create and Manage Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md)</span></span>  
  
### <a name="to-hide-an-individual-column"></a><span data-ttu-id="46457-116">列を個別に非表示にするには</span><span class="sxs-lookup"><span data-stu-id="46457-116">To hide an individual column</span></span>  
  
1.  <span data-ttu-id="46457-117">モデル デザイナーで、非表示にする列が含まれるテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="46457-117">In the model designer, select the table that contains the column that you want to hide.</span></span>  
  
2.  <span data-ttu-id="46457-118">列を右クリックして **[列を表示しない]** をクリックし、 **[デザイナーとレポートから]**、 **[レポートから]**、 **[デザイナーから]** のいずれかをクリックします。</span><span class="sxs-lookup"><span data-stu-id="46457-118">Right-click the column, then click **Hide Columns**, and then click **From Designer and Reports**, **From Reports**, or **From Designer**.</span></span>  
  
### <a name="to-hide-multiple-columns"></a><span data-ttu-id="46457-119">複数の列を非表示にするには</span><span class="sxs-lookup"><span data-stu-id="46457-119">To hide multiple columns</span></span>  
  
1.  <span data-ttu-id="46457-120">モデル デザイナーで、非表示にする列が含まれるテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="46457-120">In the model designer, select the table that contains the columns that you want to hide.</span></span>  
  
2.  <span data-ttu-id="46457-121">**[列]** メニューをクリックし、 **[表示/非表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46457-121">Click on the **Columns** menu, and then click **Hide and Unhide**.</span></span>  
  
3.  <span data-ttu-id="46457-122">**[列の表示/非表示]** ダイアログ ボックスで、非表示にする各列を見つけ、 **[デザイナーで]** と **[レポートで]** の一方または両方の選択を解除します。</span><span class="sxs-lookup"><span data-stu-id="46457-122">In the **Hide and Unhide Columns** dialog box, locate each column that you want to hide, and then deselect one or both of **In Designer** and **In Reports**.</span></span>  
  
4.  <span data-ttu-id="46457-123">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46457-123">Click **OK**.</span></span>  
  
### <a name="to-freeze-columns"></a><span data-ttu-id="46457-124">列を固定するには</span><span class="sxs-lookup"><span data-stu-id="46457-124">To freeze columns</span></span>  
  
1.  <span data-ttu-id="46457-125">モデル デザイナーで、固定する列が含まれるテーブルを選択します。</span><span class="sxs-lookup"><span data-stu-id="46457-125">In the model designer, select the table that contains the columns that you want to freeze.</span></span>  
  
2.  <span data-ttu-id="46457-126">固定する 1 つ以上の列を選択します。</span><span class="sxs-lookup"><span data-stu-id="46457-126">Select one or more columns to freeze.</span></span>  
  
3.  <span data-ttu-id="46457-127">**[列]** メニューをクリックし、 **[固定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="46457-127">Click on the **Columns** menu, and then click **Freeze**..</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="46457-128">固定された列は、デザイナーのテーブルの左側 (前) に移動されます。</span><span class="sxs-lookup"><span data-stu-id="46457-128">When a column(s) is frozen, it is moved to left (or front) of the table in the designer.</span></span> <span data-ttu-id="46457-129">列の固定を解除しても、元の場所には戻りません。</span><span class="sxs-lookup"><span data-stu-id="46457-129">Unfreezing the column does not move it back to its original location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46457-130">参照</span><span class="sxs-lookup"><span data-stu-id="46457-130">See Also</span></span>  
 <span data-ttu-id="46457-131">[SSAS 表形式のテーブルと列 &#40;&#41;](tables-and-columns-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="46457-131">[Tables and Columns &#40;SSAS Tabular&#41;](tables-and-columns-ssas-tabular.md) </span></span>  
 <span data-ttu-id="46457-132">[SSAS テーブル&#41;&#40;パースペクティブ](perspectives-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="46457-132">[Perspectives &#40;SSAS Tabular&#41;](perspectives-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="46457-133">ロール (SSAS テーブル)</span><span class="sxs-lookup"><span data-stu-id="46457-133">Roles &#40;SSAS Tabular&#41;</span></span>](roles-ssas-tabular.md)  
  
  
