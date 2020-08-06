---
title: URL へのハイパーリンクの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d3392c0b-7b62-4d27-bc04-2bd0c5487d08
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d3db3fc75feca1393e73e698f44db633f09e8dc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87713866"
---
# <a name="add-a-hyperlink-to-a-url-report-builder-and-ssrs"></a><span data-ttu-id="32f71-102">URL へのハイパーリンクの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="32f71-102">Add a Hyperlink to a URL (Report Builder and SSRS)</span></span>
  <span data-ttu-id="32f71-103">ユーザーがレポート内のリンクをクリックするとブラウザーが開かれ、指定した URL にアクセスできるようにするために、レポート アイテムへのハイパーリンクを追加できます。</span><span class="sxs-lookup"><span data-stu-id="32f71-103">You can add a hyperlink to a report item when you want your users to be able to click a link in a report and open a browser to the URL that you specify.</span></span> <span data-ttu-id="32f71-104">ハイパーリンクには、静的な URL または URL を評価する式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="32f71-104">A hyperlink can be a static URL or an expression that evaluates to a URL.</span></span> <span data-ttu-id="32f71-105">URL を保持しているデータベースのフィールドがある場合は、式にそのフィールドを指定し、レポートにハイパーリンクの動的な一覧を渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="32f71-105">If you have a field in a database that contains URLs, the expression can contain that field, resulting in a dynamic list of hyperlinks in the report.</span></span> <span data-ttu-id="32f71-106">ハイパーリンクは、テキスト ボックス、画像、グラフ、およびゲージに追加できます。</span><span class="sxs-lookup"><span data-stu-id="32f71-106">You can add hyperlinks to text boxes, images, charts, and gauges.</span></span> <span data-ttu-id="32f71-107">ただし、ユーザーがその URL にアクセスできることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="32f71-107">You must ensure that the user has access to the URL that you provide.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 <span data-ttu-id="32f71-108">表示アクセス権のあるレポート サーバーへの URL 要求を使用して、レポート サーバー上のレポートへの URL を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="32f71-108">You can also specify URLs to reports on any report server that you and your users have permission to view using URL requests to the report server.</span></span> <span data-ttu-id="32f71-109">たとえば、レポートを指定して、レポートがユーザーに最初に表示されたときにドキュメント マップを非表示にすることができます。</span><span class="sxs-lookup"><span data-stu-id="32f71-109">For example, you can specify a report and hide the document map for the user when they first view the report.</span></span> <span data-ttu-id="32f71-110">詳細については、[Reporting Services のドキュメント](https://go.microsoft.com/fwlink/?linkid=121312) ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブック) の「[URL アクセス &#40;SSRS&#41;](../url-access-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32f71-110">For more information, see [URL Access &#40;SSRS&#41;](../url-access-ssrs.md) in the [Reporting Services documentation](https://go.microsoft.com/fwlink/?linkid=121312) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="32f71-111">URL へのハイパーリンクは、グラフ内のテキスト ボックス、画像、計算系列などの **Action** プロパティがあるアイテムに追加できます。</span><span class="sxs-lookup"><span data-stu-id="32f71-111">You can add a hyperlink to a URL to any item that has an **Action** property, for example, a text box, an image, or a calculated series in a chart.</span></span> <span data-ttu-id="32f71-112">ユーザーがそのレポート アイテムをクリックすると、定義されたアクションが実行されます。</span><span class="sxs-lookup"><span data-stu-id="32f71-112">When the user clicks that report item, the action that you define takes place.</span></span> <span data-ttu-id="32f71-113">詳細については、「[[アクション プロパティ] ダイアログ ボックス &#40;レポート ビルダーおよび SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md)」と「[外部アイテムへのパスの指定 &#40;レポート ビルダーおよび SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32f71-113">For more information, see the [Action Properties Dialog Box &#40;Report Builder and SSRS&#41;](../action-properties-dialog-box-report-builder-and-ssrs.md) and [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="32f71-114">すぐに使用するには、「[チュートリアル: テキストの書式設定 &#40;レポート ビルダー&#41;](../tutorial-format-text-report-builder.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="32f71-114">To quickly get started, see [Tutorial: Format Text &#40;Report Builder&#41;](../tutorial-format-text-report-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="32f71-115">データセット フィールドにバインドされているリンクは、悪意的な改ざんに対して脆弱である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="32f71-115">Links that are bound to dataset fields can be vulnerable to tampering for malicious purposes.</span></span> <span data-ttu-id="32f71-116">詳細については、msdn.microsoft.com で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][オンライン ブック](https://go.microsoft.com/fwlink/?LinkId=154888)の「[レポートとリソースの保護](../security/secure-reports-and-resources.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32f71-116">For more information, see [Secure Reports and Resources](../security/secure-reports-and-resources.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][Books Online](https://go.microsoft.com/fwlink/?LinkId=154888) on msdn.microsoft.com.</span></span>  
  
### <a name="to-add-a-hyperlink"></a><span data-ttu-id="32f71-117">ハイパーリンクを追加するには</span><span class="sxs-lookup"><span data-stu-id="32f71-117">To add a hyperlink</span></span>  
  
1.  <span data-ttu-id="32f71-118">レポート デザイン ビューで、リンクを追加するテキスト ボックス、画像、またはグラフを右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32f71-118">In report design view, right-click the text box, image, or chart to which you want to add a link and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="32f71-119">[プロパティ] ダイアログ ボックスで **[アクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32f71-119">In the Properties dialog box, click **Action**.</span></span>  
  
3.  <span data-ttu-id="32f71-120">**[URL に移動する]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="32f71-120">Select **Go to URL**.</span></span> <span data-ttu-id="32f71-121">このオプションのダイアログ ボックスに追加のセクションが表示されます。</span><span class="sxs-lookup"><span data-stu-id="32f71-121">An additional section appears in the dialog box for this option.</span></span>  
  
4.  <span data-ttu-id="32f71-122">**[Select URL]** ボックスで、URL または URL に評価される式を入力または選択するか、下矢印をクリックして URL が格納されているフィールドの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="32f71-122">In **Select URL**, type or select a URL or an expression that evaluates to a URL, or click the drop-down arrow and click the name of a field that contains a URL.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
6.  <span data-ttu-id="32f71-123">(省略可) テキストがリンクとして自動的に書式設定されることはありません。</span><span class="sxs-lookup"><span data-stu-id="32f71-123">(Optional) The text is not automatically formatted as a link.</span></span> <span data-ttu-id="32f71-124">テキストでは、テキストの色と効果を変更してそのテキストがリンクであることを示すと便利です。</span><span class="sxs-lookup"><span data-stu-id="32f71-124">For text, it is helpful to change the color and effect of the text to indicate that the text is a link.</span></span> <span data-ttu-id="32f71-125">たとえば、リボンの [ホーム] タブの **[フォント]** セクションで、色を青に変更し、効果を下線に変更します。</span><span class="sxs-lookup"><span data-stu-id="32f71-125">For example, change the color to blue and the effect to underline in the **Font** section in the Home tab of the Ribbon.</span></span>  
  
7.  <span data-ttu-id="32f71-126">リンクをテストするには、 **[実行]** をクリックしてレポートをプレビューし、リンクを設定したレポート アイテムをクリックします。</span><span class="sxs-lookup"><span data-stu-id="32f71-126">To test the link, click **Run** to preview the report, and then click the report item that you set this link on.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32f71-127">参照</span><span class="sxs-lookup"><span data-stu-id="32f71-127">See Also</span></span>  
 <span data-ttu-id="32f71-128">[対話的な並べ替え、ドキュメントマップ、およびリンク &#40;レポートビルダーと SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="32f71-128">[Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="32f71-129">ドキュメント マップの作成 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="32f71-129">Create a Document Map &#40;Report Builder and SSRS&#41;</span></span>](create-a-document-map-report-builder-and-ssrs.md)  
  
  
