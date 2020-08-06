---
title: 外部アイテムへのパスの指定 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4fe513da-f3c5-479c-9fec-8662b91a0d6d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 097a3566f914e7810039ee07bc3d3bf3185d7f06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631522"
---
# <a name="specifying-paths-to-external-items-report-builder-and-ssrs"></a><span data-ttu-id="df274-102">外部アイテムへのパスの指定 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="df274-102">Specifying Paths to External Items (Report Builder and SSRS)</span></span>
  <span data-ttu-id="df274-103">詳細レポート、サブレポート、画像ファイルなど、レポート定義ファイルの外部にあり、レポート サーバーに保存されるアイテムを参照するには、レポート アイテム プロパティに目的のアイテムへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="df274-103">You specify paths in report item properties to reference items such as drillthrough reports, subreports, and image files that are external to the report definition file and are stored on a report server.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
> [!NOTE]  
>  <span data-ttu-id="df274-104">レポート ビルダーでは、レポート サーバー上のアイテムへのパスを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df274-104">In Report Builder, paths to items must specify items on a report server.</span></span> <span data-ttu-id="df274-105">ファイル システム上のアイテムへのパスはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="df274-105">Paths to items on a file system are not supported.</span></span> <span data-ttu-id="df274-106">これらのアイテムを使用するレポートは、アイテムが格納されているレポート サーバーに接続している場合にのみプレビューできます。</span><span class="sxs-lookup"><span data-stu-id="df274-106">You can preview a report that uses these items only if you are connected to the report server where the items are located.</span></span>  
  
 <span data-ttu-id="df274-107">アクション、サブレポート、または画像のダイアログ ボックスで外部アイテムへのパスを指定する場合は、レポート サーバーを直接参照してアイテムを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="df274-107">When you specify a path for an external item in a dialog box for actions, subreports, or images, you can browse directly to the report server and select the item.</span></span> <span data-ttu-id="df274-108">詳細レポートまたはサブレポートを指定する場合は、アイテムを直接参照して選択することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="df274-108">Browsing to an item and selecting it directly is the recommended way to specify a drillthrough report or subreport.</span></span> <span data-ttu-id="df274-109">そうすると、レポートまたはサブレポートのパラメーターを指定するときに、ドロップダウン リストから適切なパラメーター名を選択できるようになります。</span><span class="sxs-lookup"><span data-stu-id="df274-109">That way the correct parameter names will be available in a drop-down list when you specify report or subreport parameters.</span></span> <span data-ttu-id="df274-110">別のアイテムを指すようにアイテム パスを変更する場合は、必要に応じてパラメーターの名前と値を適切なものに手動で更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df274-110">When you change an item path to point to a different item, you must manually update the correct parameter names and values as needed.</span></span>  
  
 <span data-ttu-id="df274-111">ネイティブ モードで構成されているレポート サーバーでは、ファイル拡張子 .rdl を含まない詳細レポート名を指定します。</span><span class="sxs-lookup"><span data-stu-id="df274-111">On a report server configured in native mode, specify a drillthrough report name without the file extension .rdl.</span></span>  
  
 <span data-ttu-id="df274-112">SharePoint 統合モードで構成されているレポート サーバーでは、ファイル拡張子 .rdl を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="df274-112">On a report server configured in SharePoint integrated mode, you must include the file extension .rdl.</span></span> <span data-ttu-id="df274-113">次のいずれかのパスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="df274-113">The path can be one of the following:</span></span>  
  
-   <span data-ttu-id="df274-114">**メイン レポートからアイテムへの相対パス。**</span><span class="sxs-lookup"><span data-stu-id="df274-114">**A relative path to the item from the main report.**</span></span> <span data-ttu-id="df274-115">たとえば、../AllSubreports/Subreport1 のように指定します。</span><span class="sxs-lookup"><span data-stu-id="df274-115">For example, ../AllSubreports/Subreport1.</span></span> <span data-ttu-id="df274-116">この例で、 **..**</span><span class="sxs-lookup"><span data-stu-id="df274-116">In this example, the **..**</span></span> <span data-ttu-id="df274-117">は、メイン レポートが格納されているフォルダーの 1 つ上のフォルダーを示します。</span><span class="sxs-lookup"><span data-stu-id="df274-117">indicates the folder above the folder where the main report is located.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="df274-118">レポート ビルダーの内部でレポートを実行する場合、相対パスはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="df274-118">Relative paths are not supported when the report is run inside Report Builder.</span></span> <span data-ttu-id="df274-119">外部アイテムへの相対パスを使用するレポートを表示するには、レポート サーバーにレポートを保存し、そこからレポートを実行します。</span><span class="sxs-lookup"><span data-stu-id="df274-119">To view a report that uses relative paths to external items, save the report to the report server, and run the report from there</span></span>  
  
-   <span data-ttu-id="df274-120">**アイテムへの完全パス。**</span><span class="sxs-lookup"><span data-stu-id="df274-120">**A full path to the item.**</span></span>  
  
    -   <span data-ttu-id="df274-121">**レポート サーバーの場合** 、完全パスはホーム フォルダーである **/** から開始します。</span><span class="sxs-lookup"><span data-stu-id="df274-121">**On a report server:** The path starts from **/**, the Home folder.</span></span> <span data-ttu-id="df274-122">たとえば、/Reports/AllSubreports/Subreport1 のように指定します。</span><span class="sxs-lookup"><span data-stu-id="df274-122">For example, /Reports/AllSubreports/Subreport1.</span></span>  
  
    -   <span data-ttu-id="df274-123">**SharePoint サイトの場合** 、アイテムの完全な URL とファイル拡張子 .rdl を含めたレポート名を式で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="df274-123">**On a SharePoint site:** You must specify the report name in an expression, with the full URL of the item and the file extension .rdl.</span></span> <span data-ttu-id="df274-124">たとえば、「 `="http://server/site/library/folder/Report1.rdl"` 」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="df274-124">For example, `="http://server/site/library/folder/Report1.rdl"`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df274-125">参照</span><span class="sxs-lookup"><span data-stu-id="df274-125">See Also</span></span>  
 <span data-ttu-id="df274-126">[外部の画像の追加 &#40;レポート ビルダーおよび SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="df274-126">[Add an External Image &#40;Report Builder and SSRS&#41;](add-an-external-image-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="df274-127">[サブレポートおよびパラメーターの追加 &#40;レポート ビルダーおよび SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="df274-127">[Add a Subreport and Parameters &#40;Report Builder and SSRS&#41;](add-a-subreport-and-parameters-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="df274-128">レポートへのドリルスルー アクションの追加 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="df274-128">Add a Drillthrough Action on a Report &#40;Report Builder and SSRS&#41;</span></span>](add-a-drillthrough-action-on-a-report-report-builder-and-ssrs.md)  
  
  
