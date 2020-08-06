---
title: レポート内のテキスト、数値、または日付の検索 (SharePoint 統合モードでの Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- searching reports
ms.assetid: 309dffe5-00f5-404f-bb63-9e6046253ae0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9b11f01e700ff6a7449c47dfb79d8e48086d90d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716082"
---
# <a name="find-text-numbers-or-dates-in-a-report-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="2ec98-102">レポート内のテキスト、数値、または日付を検索する (Reporting Services の SharePoint 統合モード)</span><span class="sxs-lookup"><span data-stu-id="2ec98-102">Find Text, Numbers, or Dates in a Report (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="2ec98-103">レポートのコンテンツは、単語や語句を入力して検索できます (検索用語の最大文字数は 256 文字です)。</span><span class="sxs-lookup"><span data-stu-id="2ec98-103">You can search for content in a report by typing a word or phrase that you want to find (the maximum value of a search term is 256 characters).</span></span> <span data-ttu-id="2ec98-104">検索は、レポート内にある一致する値を検出し、その値の位置にカーソルを移動するナビゲーション技法です。</span><span class="sxs-lookup"><span data-stu-id="2ec98-104">Search is a navigation technique that finds a matching value in the report and puts focus on the part of the report that contains that value.</span></span>  
  
 <span data-ttu-id="2ec98-105">検索は大文字と小文字を区別せず、現在選択されているページまたはセクションから開始されます。</span><span class="sxs-lookup"><span data-stu-id="2ec98-105">Search is case-insensitive and begins at the page or section that is currently selected.</span></span> <span data-ttu-id="2ec98-106">レポートで表示されているコンテンツのみが、検索の対象になります。</span><span class="sxs-lookup"><span data-stu-id="2ec98-106">Only content that is visible in the report is included in the search operation.</span></span> <span data-ttu-id="2ec98-107">展開したり折りたたんだりできる領域がレポートに含まれている場合、その領域に含まれている値は検索対象外となります。</span><span class="sxs-lookup"><span data-stu-id="2ec98-107">If the report contains areas that you expand or collapse, values that are in a collapsed area are skipped during the search.</span></span> <span data-ttu-id="2ec98-108">検索できるのは、現在のレポート内のテキスト、数値、または日付だけです。</span><span class="sxs-lookup"><span data-stu-id="2ec98-108">You can only search for text, numbers, or dates that are in the current report.</span></span> <span data-ttu-id="2ec98-109">自動生成されたクリックスルー レポートを使用してデータを検索している場合、以前に生成されたレポートに含まれる用語を検索することはできません。また、データ パスに含まれる用語を検索することもできません。</span><span class="sxs-lookup"><span data-stu-id="2ec98-109">If you are using an autogenerated clickthrough report to explore data, you cannot search for a term that you saw on a previously generated report, nor can you use search to find a term that might appear in a report further down the data path.</span></span>  
  
 <span data-ttu-id="2ec98-110">検索する値を入力する際には、レポートで実際に使用されていることが予想される値を入力します。</span><span class="sxs-lookup"><span data-stu-id="2ec98-110">When entering a value to search on, type the value as you expect it to appear in the report.</span></span> <span data-ttu-id="2ec98-111">「今月の平均利益は」のような質問は、この文字列がレポートに含まれていると予想できる場合を除いて不適切です。</span><span class="sxs-lookup"><span data-stu-id="2ec98-111">Do not pose a question, such as "what is the average profit for this month," unless you expect every word in the sentence to be in the report.</span></span>  
  
 <span data-ttu-id="2ec98-112">一度に検索できる用語または値は 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="2ec98-112">You can only search for one term or value at a time.</span></span> <span data-ttu-id="2ec98-113">検索演算子 (AND や OR など)、記号、およびワイルドカードは使用できません。</span><span class="sxs-lookup"><span data-stu-id="2ec98-113">You cannot use search operators (such as AND or OR), or symbols and wildcards.</span></span> <span data-ttu-id="2ec98-114">複数のセクションにわたったデータは検索できません (たとえば、特定の製品のある月の純売上高を検索することはできません)。</span><span class="sxs-lookup"><span data-stu-id="2ec98-114">You cannot perform a search on a cross-section of the data (for example, searching for net sales for specific month for a particular product).</span></span> <span data-ttu-id="2ec98-115">このような分析には、レポート ビルダーを使用してクリックスルー レポートを作成するか、作成したクリックスルー レポートを使用します。</span><span class="sxs-lookup"><span data-stu-id="2ec98-115">For that kind of analysis, use Report Builder to create or use clickthrough reports.</span></span>  
  
 <span data-ttu-id="2ec98-116">レポート データへのアクセスを制限するデータベースとモデルのセキュリティ設定は、検索操作にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="2ec98-116">Database and model security settings that restrict access to report data apply to search operations.</span></span> <span data-ttu-id="2ec98-117">データ ソースにモデルを使用しているクリックスルー レポートで値を検索する場合に、そのモデルの一部にアクセス権限がないと、その部分に含まれるデータは検索対象外になります。</span><span class="sxs-lookup"><span data-stu-id="2ec98-117">If you are searching for a value in a clickthrough report that uses a model as a data source, and you do not have access to part of the model, data that is represented by the part of the model will be excluded from the search.</span></span>  
  
### <a name="to-find-data-in-a-report"></a><span data-ttu-id="2ec98-118">レポートでデータを検索するには</span><span class="sxs-lookup"><span data-stu-id="2ec98-118">To find data in a report</span></span>  
  
1.  <span data-ttu-id="2ec98-119">レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="2ec98-119">Open the report.</span></span>  
  
2.  <span data-ttu-id="2ec98-120">レポート ツール バーで、検索するテキスト、数値、または日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="2ec98-120">In the report toolbar, enter the text, number, or date that you want to find.</span></span>  
  
     <span data-ttu-id="2ec98-121">レポート ツール バーが表示されない場合は、意図的に非表示に設定されているため、レポート ツール バーの機能を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="2ec98-121">If the report toolbar is not visible, it has been hidden on purpose and you cannot use the functionality it provides.</span></span> <span data-ttu-id="2ec98-122">このツール バーが表示されるかどうかは、レポート ビューアー Web パーツのプロパティで指定されます。</span><span class="sxs-lookup"><span data-stu-id="2ec98-122">Properties on the Report Viewer Web Part determine whether the toolbar is visible.</span></span>  
  
3.  <span data-ttu-id="2ec98-123">**[検索]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ec98-123">Click **Find**.</span></span>  
  
4.  <span data-ttu-id="2ec98-124">同じ値で引き続き検索を続ける場合は、 **[次へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2ec98-124">To search for subsequent occurrences of the same value, click **Next**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec98-125">参照</span><span class="sxs-lookup"><span data-stu-id="2ec98-125">See Also</span></span>  
 [<span data-ttu-id="2ec98-126">レポート ビューアー Web パーツを Web ページに追加する (Reporting Services の SharePoint 統合モード)</span><span class="sxs-lookup"><span data-stu-id="2ec98-126">Add the Report Viewer Web Part to a Web Page &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](../report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)  
  
  