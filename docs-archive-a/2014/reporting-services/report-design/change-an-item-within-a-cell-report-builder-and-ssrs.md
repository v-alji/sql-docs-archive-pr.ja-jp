---
title: セル内のアイテムの変更 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 91a54778-8929-41f9-bb4c-826cec636be4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 80ef171713e6505867e00e343ce17b70cab9045a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742837"
---
# <a name="change-an-item-within-a-cell-report-builder-and-ssrs"></a><span data-ttu-id="37d0f-102">セル内のアイテムの変更 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="37d0f-102">Change an Item Within a Cell (Report Builder and SSRS)</span></span>
  <span data-ttu-id="37d0f-103">新しいレポート アイテムで置き換えることができるのは、テキスト ボックスや線、画像などの非コンテナー アイテムに限られています。</span><span class="sxs-lookup"><span data-stu-id="37d0f-103">Only a non-container item, such as a text box, line, or image, can be replaced by a new report item.</span></span> <span data-ttu-id="37d0f-104">たとえば、テーブルをテキスト ボックス内にドラッグすると、テキスト ボックスをテーブルで置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="37d0f-104">For example, you can drag a table into a text box to replace the text box with a table.</span></span>  
  
 <span data-ttu-id="37d0f-105">四角形、一覧、テーブル、マトリックスなどのコンテナー アイテムがセルに含まれている場合、新しいアイテムはコンテナー アイテムに置き換わるのではなく、コンテナー アイテムに追加されます。</span><span class="sxs-lookup"><span data-stu-id="37d0f-105">If the cell contains a container item such as a rectangle, list, table, or matrix, the new item is added to the containing item instead of replacing it.</span></span> <span data-ttu-id="37d0f-106">コンテナー アイテムを新しいアイテムで置き換えるには、コンテナーを削除します。</span><span class="sxs-lookup"><span data-stu-id="37d0f-106">To replace a container item with a new item, delete the container.</span></span> <span data-ttu-id="37d0f-107">コンテナー アイテムを削除すると、コンテナー アイテムはテキスト ボックスで置き換えられます。その後、テキスト ボックスを別のアイテムで置換できます。</span><span class="sxs-lookup"><span data-stu-id="37d0f-107">Deleting the container item replaces it with a text box, which you can then replace with another item.</span></span>  
  
 <span data-ttu-id="37d0f-108">既定では、テーブル、マトリックス、または一覧のデータ領域内にあるすべてのセルにテキスト ボックスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="37d0f-108">By default, all cells in a table, matrix, or list data region contain a text box.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-an-item-within-a-cell"></a><span data-ttu-id="37d0f-109">セル内のアイテムを変更するには</span><span class="sxs-lookup"><span data-stu-id="37d0f-109">To change an item within a cell</span></span>  
  
-   <span data-ttu-id="37d0f-110">**[挿入]** タブの **[データ領域]** または **[レポート アイテム]** グループでレポートに追加するアイテムをクリックし、レポートをクリックします。</span><span class="sxs-lookup"><span data-stu-id="37d0f-110">On the **Insert** tab, in the **Data Regions** or **Report Items** group, click the item that you want to add to the report, and then click the report.</span></span> <span data-ttu-id="37d0f-111">アイテムがレポートに追加されます。</span><span class="sxs-lookup"><span data-stu-id="37d0f-111">The item is added to the report.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="37d0f-112">画像レポート アイテムをセルにドラッグすると、 **[画像のプロパティ]** ダイアログ ボックスが開きます。このダイアログ ボックスでは、画像をセルに追加する前に画像のソースなどのプロパティを設定できます。</span><span class="sxs-lookup"><span data-stu-id="37d0f-112">The **Image Properties** dialog box opens when you drag an image report item to a cell, where you can set properties such as the source of the image before the image is added to the cell.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37d0f-113">参照</span><span class="sxs-lookup"><span data-stu-id="37d0f-113">See Also</span></span>  
 <span data-ttu-id="37d0f-114">[画像、テキスト ボックス、四角形、および罫線 &#40;レポート ビルダーおよび SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="37d0f-114">[Images, Text Boxes, Rectangles, and Lines &#40;Report Builder and SSRS&#41;](rectangles-and-lines-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="37d0f-115">一覧 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="37d0f-115">Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
