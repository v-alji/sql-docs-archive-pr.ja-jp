---
title: レポートへのドリルスルー アクションの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 153729c4-d01e-4629-b78f-0cfd5a7f83da
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a429380f677a309e4e1437a2e3c5036bb4e8a455
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634263"
---
# <a name="add-a-drillthrough-action-on-a-report-report-builder-and-ssrs"></a><span data-ttu-id="c2258-102">レポートへのドリルスルー アクションの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="c2258-102">Add a Drillthrough Action on a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="c2258-103">メイン レポートのリンクをクリックすると開くレポートが *詳細レポート*です。</span><span class="sxs-lookup"><span data-stu-id="c2258-103">The report that opens when you click the link in the main report is known as a *drillthrough report*.</span></span> <span data-ttu-id="c2258-104">このドリルスルー リンクを使用すると、ドリルスルー アクションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="c2258-104">This drillthrough link enables a drillthrough action.</span></span>  
  
 <span data-ttu-id="c2258-105">詳細レポートはメイン レポートと同じレポート サーバーにパブリッシュする必要がありますが、別のフォルダーでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="c2258-105">Drillthrough reports must be published to the same report server as the main report, but they can be in different folders.</span></span> <span data-ttu-id="c2258-106">テキスト ボックス、画像、グラフ上のデータ ポイントなど、 **Action** プロパティがあるアイテムにドリルスルー リンクを追加できます。</span><span class="sxs-lookup"><span data-stu-id="c2258-106">You can add a drillthrough link to any item that has an **Action** property, such as a text box, an image, or data points on a chart.</span></span>  
  
 <span data-ttu-id="c2258-107">レポートにドリルスルー リンクを追加するには、まず、メイン レポートからリンクする詳細レポートを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2258-107">To add a drillthrough link to a report, you must first create the drillthrough report that the main report will link to.</span></span> <span data-ttu-id="c2258-108">詳細レポートには、通常、元の要約レポートに含まれるアイテムについての詳細が含まれています。また、多くの場合、メイン レポートから渡されるパラメーターに基づいて詳細レポートをフィルターするパラメーターも含まれます。</span><span class="sxs-lookup"><span data-stu-id="c2258-108">A drillthrough report commonly contains details about an item that is contained in the original summary report, and often contains parameters that filter the drillthrough report based on parameters passed to it from the main report.</span></span> <span data-ttu-id="c2258-109">詳細レポートの作成方法については、「[詳細レポート (レポート ビルダーおよび SSRS)](drillthrough-reports-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2258-109">For more information on creating the drillthrough report, see [Drillthrough Reports &#40;Report Builder and SSRS&#41;](drillthrough-reports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-drillthrough-action"></a><span data-ttu-id="c2258-110">ドリルスルー アクションを追加するには</span><span class="sxs-lookup"><span data-stu-id="c2258-110">To add a drillthrough action</span></span>  
  
1.  <span data-ttu-id="c2258-111">デザイン ビューで、リンクを追加するテキスト ボックス、画像、またはグラフを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2258-111">In Design view, right-click the text box, image, or chart to which you want to add a link and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="c2258-112">アイテムの **[プロパティ]** ダイアログ ボックスで **[アクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2258-112">In the item's **Properties** dialog box, click **Action**.</span></span>  
  
3.  <span data-ttu-id="c2258-113">**[レポートに移動する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="c2258-113">Select **Go to report**.</span></span> <span data-ttu-id="c2258-114">このオプションのダイアログ ボックスに追加のセクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c2258-114">Additional sections appear in the dialog box for this option.</span></span>  
  
4.  <span data-ttu-id="c2258-115">**[レポートの指定]** で、 **[参照]** をクリックして移動先レポートを指定するか、移動先レポートの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c2258-115">In **Specify a report**, click **Browse** to locate the report that you want to jump to, or type the name of the report.</span></span> <span data-ttu-id="c2258-116">または、式 ( **[fx]** ) ボタンをクリックしてレポート名の式を作成します。</span><span class="sxs-lookup"><span data-stu-id="c2258-116">Alternatively, click the expression (**fx**) button to create an expression for the report name.</span></span>  
  
     <span data-ttu-id="c2258-117">詳細レポートのパスの形式は、ネイティブ モードと SharePoint 統合モードとで異なります。</span><span class="sxs-lookup"><span data-stu-id="c2258-117">The format of the path to the drillthrough report differs for native and SharePoint integrated mode.</span></span> <span data-ttu-id="c2258-118">参照によってレポートを指定した場合は、パスが正しい形式で指定されます。</span><span class="sxs-lookup"><span data-stu-id="c2258-118">If you browse to the report, a path of the correct format is provided.</span></span> <span data-ttu-id="c2258-119">詳細については、「[外部アイテムへのパスの指定 &#40;レポート ビルダーおよび SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2258-119">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
     <span data-ttu-id="c2258-120">詳細レポートのパラメーターを指定する必要がある場合は、次の手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="c2258-120">If you have to specify parameters for the drillthrough report, follow the next step.</span></span>  
  
5.  <span data-ttu-id="c2258-121">**[レポートの実行に以下のパラメーターを使用]** で、 **[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2258-121">In **Use these parameters to run the report**, click **Add**.</span></span> <span data-ttu-id="c2258-122">パラメーター グリッドに、新しい行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="c2258-122">A new row is added to the parameter grid.</span></span>  
  
    -   <span data-ttu-id="c2258-123">**[名前]** ボックスで、詳細レポートのレポート パラメーターの名前を一覧から選択するか入力します。</span><span class="sxs-lookup"><span data-stu-id="c2258-123">In the **Name** text box, click the drop-down list or type the name of the report parameter in the drillthrough report.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c2258-124">パラメーターの一覧にある名前は、対象となるレポートで予測されるパラメーターと完全に一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2258-124">The names in the parameter list must match the expected parameters in the target report exactly.</span></span> <span data-ttu-id="c2258-125">たとえば、パラメーター名の大文字と小文字の違いも一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c2258-125">For example, parameter names must match by case.</span></span> <span data-ttu-id="c2258-126">これらの名前が一致しない場合、または予測されるパラメーターが一覧にない場合は、詳細レポートは失敗します。</span><span class="sxs-lookup"><span data-stu-id="c2258-126">If the names do not match, or if an expected parameter is not listed, the drillthrough report fails.</span></span>  
  
    -   <span data-ttu-id="c2258-127">**[値]** に、詳細レポートのパラメーターに渡す値を入力するか、選択します。</span><span class="sxs-lookup"><span data-stu-id="c2258-127">In **Value**, type or select the value to pass to the parameter in the drillthrough report.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="c2258-128">レポート パラメーターに渡す値には、結果が値になる式を指定できます。</span><span class="sxs-lookup"><span data-stu-id="c2258-128">Values can contain an expression that evaluates to a value to pass to the report parameter.</span></span> <span data-ttu-id="c2258-129">値の一覧にある式には、現在のレポートのフィールドの一覧が含まれています。</span><span class="sxs-lookup"><span data-stu-id="c2258-129">The expressions in the value list include the field list for the current report.</span></span>  
  
     <span data-ttu-id="c2258-130">レポートのパラメーターを非表示にする方法については、「[レポート パラメーターの追加、変更、または削除 (レポート ビルダーおよび SSRS)](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c2258-130">For information on how to hide parameters in reports, see [Add, Change, or Delete a Report Parameter &#40;Report Builder and SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="c2258-131">(省略可) テキスト ボックスの場合、リボンの **[ホーム]** タブでテキストの色と効果を変更してそのテキストがリンクであることをユーザーに示すと便利です。</span><span class="sxs-lookup"><span data-stu-id="c2258-131">(Optional) For text boxes, it is helpful to indicate to the user that the text is a link by changing the color and effect of the text on the **Home** tab of the Ribbon.</span></span>  
  
7.  <span data-ttu-id="c2258-132">リンクをテストするには、レポートを実行し、このリンクを設定したレポート アイテムをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c2258-132">To test the link, run the report and click the report item that you set this link on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2258-133">参照</span><span class="sxs-lookup"><span data-stu-id="c2258-133">See Also</span></span>  
 <span data-ttu-id="c2258-134">[アクション プロパティ ダイアログ ボックス (レポート ビルダーおよび SSRS)](../action-properties-dialog-box-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2258-134">[Action Properties Dialog Box &#40;Report Builder and SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="c2258-135">[グラフでのデータ ポイントの書式設定 (レポート ビルダーおよび SSRS)](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="c2258-135">[Formatting Data Points on a Chart &#40;Report Builder and SSRS&#41;](formatting-data-points-on-a-chart-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="c2258-136">系列へのツールヒントの表示 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="c2258-136">Show ToolTips on a Series &#40;Report Builder and SSRS&#41;</span></span>](show-tooltips-on-a-series-report-builder-and-ssrs.md)  
  
  
