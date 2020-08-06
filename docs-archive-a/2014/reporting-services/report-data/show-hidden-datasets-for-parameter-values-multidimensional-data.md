---
title: 多次元データのパラメーター値の非表示データセットの表示 (レポートビルダーおよび SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: eb01c4ca-4fd6-4629-b595-f0d2565915df
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f9c005b6e7c8927316c19a3302e32f4407f9885
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742854"
---
# <a name="show-hidden-datasets-for-parameter-values-for-multidimensional-data-report-builder-and-ssrs"></a><span data-ttu-id="b0b87-102">多次元データのパラメーター値の非表示データセットの表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="b0b87-102">Show Hidden Datasets for Parameter Values for Multidimensional Data (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b0b87-103">既定ではレポート データ ペインに表示されない、自動的に生成されたデータセット (非表示のデータセット) がレポートに含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b0b87-103">Your report might include automatically-generated datasets (also known as hidden datasets) that do not appear by default in the Report Data pane.</span></span> <span data-ttu-id="b0b87-104">これらのデータセットは次のような場合に作成されます。</span><span class="sxs-lookup"><span data-stu-id="b0b87-104">These datasets are created in the following ways:</span></span>  
  
-   <span data-ttu-id="b0b87-105">多次元データベース用のクエリ デザイナーの中には、フィルターを適用するフィールドをクエリ ペインのフィルター領域で指定して、そのフィルターのクエリ パラメーターを作成するかどうかを選択できるものがあります。</span><span class="sxs-lookup"><span data-stu-id="b0b87-105">In some query designers for multidimensional databases, you can specify fields to filter on in the filter area of the query pane, and select whether to create a query parameter for the filter.</span></span> <span data-ttu-id="b0b87-106">そのような場合にパラメーターを作成するように選択すると、そのレポート パラメーターの有効な値を提供するレポート データセットが自動的に作成されます。</span><span class="sxs-lookup"><span data-stu-id="b0b87-106">If you select the parameter option, report datasets are automatically created to provide valid values for the report parameter.</span></span>  
  
-   <span data-ttu-id="b0b87-107">多次元データベースに基づくクエリをインポートすると、非表示のデータセットもレポートに含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="b0b87-107">If you import a query based on multidimensional databases, you might also include hidden datasets in your report.</span></span>  
  
 <span data-ttu-id="b0b87-108">非表示のデータセットはウィザードからは使用できません。</span><span class="sxs-lookup"><span data-stu-id="b0b87-108">Hidden datasets are not available to use from a wizard.</span></span>  
  
 <span data-ttu-id="b0b87-109">レポート データ ペインで、レポートのすべてのデータセットを表示するビューを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="b0b87-109">You can change the view in the Report Data pane to display all datasets in the report.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-hidden-datasets"></a><span data-ttu-id="b0b87-110">非表示のデータセットを表示するには</span><span class="sxs-lookup"><span data-stu-id="b0b87-110">To display hidden datasets</span></span>  
  
-   <span data-ttu-id="b0b87-111">レポート データ ペインで、[データセット] フォルダーを右クリックし、 **[非表示データセットの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b0b87-111">In the Report Data pane, right-click the Datasets folder, and then click **Show Hidden Datasets**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0b87-112">参照</span><span class="sxs-lookup"><span data-stu-id="b0b87-112">See Also</span></span>  
 <span data-ttu-id="b0b87-113">[クエリデザイナー &#40;レポートビルダー&#41;](../query-designers-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="b0b87-113">[Query Designers &#40;Report Builder&#41;](../query-designers-report-builder.md) </span></span>  
 <span data-ttu-id="b0b87-114">[Reporting Services クエリ デザイナー](../reporting-services-query-designers.md) </span><span class="sxs-lookup"><span data-stu-id="b0b87-114">[Reporting Services Query Designers](../reporting-services-query-designers.md) </span></span>  
 <span data-ttu-id="b0b87-115">[レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b0b87-115">[Report Embedded Datasets and Shared Datasets &#40;Report Builder and SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b0b87-116">レポート &#40;レポートビルダーおよび SSRS&#41;にデータを追加する</span><span class="sxs-lookup"><span data-stu-id="b0b87-116">Add Data to a Report &#40;Report Builder and SSRS&#41;</span></span>](report-datasets-ssrs.md)  
  
  
