---
title: レポートの全般プロパティの構成 (レポートマネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- reports [Reporting Services], properties
- properties [Reporting Services], general
ms.assetid: 10b941b2-28e6-4408-9ee4-acebc63c8496
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f30900158591afcd5997053dbb61cc22b495ed10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739553"
---
# <a name="configure-general-properties-for-a-report-report-manager"></a><span data-ttu-id="a60d5-102">レポートの全般プロパティを構成する (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="a60d5-102">Configure General Properties for a Report (Report Manager)</span></span>
  
### <a name="to-configure-general-report-properties"></a><span data-ttu-id="a60d5-103">全般レポート プロパティを構成するには</span><span class="sxs-lookup"><span data-stu-id="a60d5-103">To configure general report properties</span></span>

1.  <span data-ttu-id="a60d5-104">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) を開始します。</span><span class="sxs-lookup"><span data-stu-id="a60d5-104">Start [Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md).</span></span>

2.  <span data-ttu-id="a60d5-105">レポート マネージャーで **[コンテンツ]** ページに移動します。</span><span class="sxs-lookup"><span data-stu-id="a60d5-105">In Report Manager, navigate to the **Contents** page.</span></span> <span data-ttu-id="a60d5-106">全般プロパティを構成するレポートに移動し、そのレポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="a60d5-106">Navigate to the report that you want to configure general properties for and open it.</span></span>

3.  <span data-ttu-id="a60d5-107">**[プロパティ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a60d5-107">Click the **Properties** tab.</span></span>

     <span data-ttu-id="a60d5-108">または、[**コンテンツ**] ページが詳細ビューに表示されている場合は、[プロパティページ] アイコンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a60d5-108">Or, if the **Contents** page is in Details view, click the property page icon:</span></span>

     <span data-ttu-id="a60d5-109">![プロパティ ページのアイコン](media/prop.gif "プロパティ ページのアイコン")</span><span class="sxs-lookup"><span data-stu-id="a60d5-109">![Property page icon](media/prop.gif "Property page icon")</span></span>

4.  <span data-ttu-id="a60d5-110">**[全般**] プロパティページが表示され、次のようにプロパティを構成できます。</span><span class="sxs-lookup"><span data-stu-id="a60d5-110">The **General** properties page is displayed, and you can configure properties as follows:</span></span>

    -   <span data-ttu-id="a60d5-111">[**プロパティ**] セクションでは、レポートの名前と説明を変更できます。</span><span class="sxs-lookup"><span data-stu-id="a60d5-111">In the **Properties** section, you can modify the report name and description.</span></span>

    -   <span data-ttu-id="a60d5-112">[**リストビューで非表示**にする] チェックボックスをオンにすると、既定のページレイアウト (リストビュー) でページを開いたときにアイテムを非表示にすることができます。このページでは、アイテムがページの上下に配置されます。</span><span class="sxs-lookup"><span data-stu-id="a60d5-112">You can select the **Hide in list view** checkbox to hide the item when the page is opened in the default page layout (list view) which arranges items across and down the page.</span></span>

    -   <span data-ttu-id="a60d5-113">[**レポート定義**] セクションで、[**編集**] をクリックして、レポート定義のコピーを抽出します。</span><span class="sxs-lookup"><span data-stu-id="a60d5-113">In the **Report Definition** section, click **Edit** to extract a copy of the report definition.</span></span> <span data-ttu-id="a60d5-114">ローカルでレポート定義に加えた変更は、レポート サーバーに保存されません。</span><span class="sxs-lookup"><span data-stu-id="a60d5-114">Modifications that you make locally to the report definition are not saved on the report server.</span></span>

         <span data-ttu-id="a60d5-115">または、.rdl ファイルからレポート定義を更新するには、[**更新**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a60d5-115">Or, to update the report definition from an .rdl file, click **Update**.</span></span>

        > [!NOTE]
        >  <span data-ttu-id="a60d5-116">レポート定義を更新する場合、更新の完了後にデータ ソースの設定を再設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a60d5-116">If you update a report definition, you must reset the data source settings after the update is completed.</span></span>

    -   <span data-ttu-id="a60d5-117">レポートを削除または移動するには、[**削除**] または [**移動**] ボタンを使用します。</span><span class="sxs-lookup"><span data-stu-id="a60d5-117">Use the **Delete** or **Move** buttons to delete or move the report.</span></span>

    -   <span data-ttu-id="a60d5-118">また、リンク レポートを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a60d5-118">You can also create a linked report.</span></span>

5.  <span data-ttu-id="a60d5-119">レポートの全般プロパティの構成が完了したら、[**適用**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a60d5-119">When you have finished configuring general properties for the report, click **Apply**.</span></span>

## <a name="see-also"></a><span data-ttu-id="a60d5-120">参照</span><span class="sxs-lookup"><span data-stu-id="a60d5-120">See Also</span></span>
 <span data-ttu-id="a60d5-121">[アイテムの移動または削除 &#40;レポートマネージャー&#41;](report-server/move-or-delete-an-item-report-manager.md) [コンテンツ] ページ &#40;](../../2014/reporting-services/contents-page-report-manager.md)レポートマネージャー&#41;[レポートの検索、表示、および管理 &#40;レポートビルダーと SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) [全般プロパティページ、レポート &#40;レポートマネージャー](../../2014/reporting-services/general-properties-page-reports-report-manager.md)&#41;</span><span class="sxs-lookup"><span data-stu-id="a60d5-121">[Move or Delete an Item &#40;Report Manager&#41;](report-server/move-or-delete-an-item-report-manager.md) [Contents Page &#40;Report Manager&#41;](../../2014/reporting-services/contents-page-report-manager.md) [Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) [General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md)</span></span>


