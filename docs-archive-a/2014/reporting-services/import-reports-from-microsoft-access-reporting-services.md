---
title: Microsoft Access からレポートをインポートする (Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Access reports [Reporting Services]
- importing reports
ms.assetid: 4f29d5b8-b77d-4714-a84a-05523df55646
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 862d8b90f3c91dffda35971677db7fdc231c1b63
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643715"
---
# <a name="import-reports-from-microsoft-access-reporting-services"></a><span data-ttu-id="e68ff-102">Microsoft Access からレポートをインポートする (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="e68ff-102">Import Reports from Microsoft Access (Reporting Services)</span></span>
  <span data-ttu-id="e68ff-103">レポートデザイナーで [!INCLUDE[msCoName](../includes/msconame-md.md)] は、Access データベースまたはプロジェクトからレポートをインポートできます。</span><span class="sxs-lookup"><span data-stu-id="e68ff-103">In Report Designer, you can import reports from a [!INCLUDE[msCoName](../includes/msconame-md.md)] Access database or project.</span></span> <span data-ttu-id="e68ff-104">レポート デザイナーがインストールされているコンピューターに、Access 2002 以降のバージョンがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e68ff-104">Access 2002 or a later version must be installed on the same computer on which Report Designer is installed.</span></span>  
  
 <span data-ttu-id="e68ff-105">インポート機能を使用すると、Access データベースまたはプロジェクト ファイルのすべてのレポートがインポートされます。</span><span class="sxs-lookup"><span data-stu-id="e68ff-105">When you use the import feature, all reports in the database or project file are imported.</span></span> <span data-ttu-id="e68ff-106">Access ファイルに多数のレポートが含まれている場合は、レポートのインポート先に別のレポート プロジェクトを作成し、その後各 RDL ファイルをメインのレポート プロジェクトで開くことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e68ff-106">If your Access file contains many reports, you may want to create a separate report project into which to import the reports, and then open the individual RDL files in your main report project.</span></span> <span data-ttu-id="e68ff-107">レポートは、レポート デザイナーにインポートした後に、編集できます。</span><span class="sxs-lookup"><span data-stu-id="e68ff-107">You can edit the reports after they are imported into Report Designer.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="e68ff-108">では、Access のレポート オブジェクトがすべてサポートされているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e68ff-108">does not support all Access report objects.</span></span> <span data-ttu-id="e68ff-109">変換されていない項目は、[**タスク一覧**] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e68ff-109">Items that are not converted are displayed in the **Task List** window.</span></span> <span data-ttu-id="e68ff-110">詳細については、「[サポートされているアクセスレポート機能 &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e68ff-110">For more information, see [Supported Access Report Features &#40;SSRS&#41;](../../2014/reporting-services/supported-access-report-features-ssrs.md).</span></span>  
  
### <a name="to-import-reports-from-microsoft-access"></a><span data-ttu-id="e68ff-111">Microsoft Access からレポートをインポートするには</span><span class="sxs-lookup"><span data-stu-id="e68ff-111">To import reports from Microsoft Access</span></span>  
  
1.  <span data-ttu-id="e68ff-112">レポートをインポートするプロジェクトを開くか、作成します。</span><span class="sxs-lookup"><span data-stu-id="e68ff-112">Open or create a project into which to import the reports.</span></span>  
  
2.  <span data-ttu-id="e68ff-113">[**プロジェクト**] メニューの [**レポートのインポート**] をポイントし、[ **Microsoft access**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e68ff-113">On the **Project** menu, point to **Import Reports**, and then click **Microsoft Access**.</span></span> <span data-ttu-id="e68ff-114">または、ソリューションエクスプローラーでプロジェクトを右クリックして [**レポートのインポート**] をポイントし、[ **Microsoft access**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e68ff-114">Alternatively, right-click the project in Solution Explorer, point to **Import Reports**, and then click **Microsoft Access**.</span></span>  
  
3.  <span data-ttu-id="e68ff-115">[**開く**] ダイアログボックスで、レポートが格納されている Access データベース (.mdb、.accdb) またはプロジェクト (.adp) を選択し、[**開く**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e68ff-115">In the **Open** dialog box, select the Access database (.mdb, .accdb) or project (.adp) that contains the reports, and then click **Open**.</span></span> <span data-ttu-id="e68ff-116">データベースまたはプロジェクト ファイルのすべてのレポートがインポートされて、ソリューション エクスプローラーの [レポート] フォルダーに一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="e68ff-116">All the reports in the database or project file are imported and listed in the Reports folder in Solution Explorer.</span></span>  
  
4.  <span data-ttu-id="e68ff-117">[**タスク一覧**] ウィンドウでビルドエラーを確認します。</span><span class="sxs-lookup"><span data-stu-id="e68ff-117">Check the **Task List** window for build errors.</span></span> <span data-ttu-id="e68ff-118">**タスク一覧**ウィンドウを表示するには、[**表示**] メニューの [**その他のウィンドウ**] をポイントし、[**タスク一覧**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e68ff-118">To view the **Task List** window, open the **View** menu, point to **Other Windows**, and then click **Task List**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e68ff-119">参照</span><span class="sxs-lookup"><span data-stu-id="e68ff-119">See Also</span></span>  
 [<span data-ttu-id="e68ff-120">レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e68ff-120">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
