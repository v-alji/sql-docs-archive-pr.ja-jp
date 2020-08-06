---
title: レポートビルダー (SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 32be8fcc-e87d-4c45-a644-dff45776a981
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: dae43dd86cd6b02c81f0fc90a05292458eb87200
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716013"
---
# <a name="report-builder-ssrs"></a><span data-ttu-id="10741-102">レポート ビルダー (SSRS)</span><span class="sxs-lookup"><span data-stu-id="10741-102">Report Builder (SSRS)</span></span>
  <span data-ttu-id="10741-103">レポートビルダーは、Office 環境での作業を好むビジネスユーザー向けのレポート作成環境 [!INCLUDE[msCoName](../../includes/msconame-md.md)] です。</span><span class="sxs-lookup"><span data-stu-id="10741-103">Report Builder is a report authoring environment for business users who prefer to work in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Office environment.</span></span> <span data-ttu-id="10741-104">レポートをデザインする際には、データの取得場所、取得するデータ、およびデータの表示方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="10741-104">When you design a report, you specify where to get the data, which data to get, and how to display the data.</span></span> <span data-ttu-id="10741-105">レポートを実行すると、指定した情報がすべてレポート プロセッサに渡されます。レポート プロセッサは、データを取得し、それをレポート レイアウトに結合して、レポートを生成します。</span><span class="sxs-lookup"><span data-stu-id="10741-105">When you run the report, the report processor takes all the information you have specified, retrieves the data, and combines it with the report layout to generate the report.</span></span>  
  
## <a name="benefits-of-report-builder"></a><span data-ttu-id="10741-106">レポート ビルダーの利点</span><span class="sxs-lookup"><span data-stu-id="10741-106">Benefits of Report Builder</span></span>  
 <span data-ttu-id="10741-107">レポート ビルダーでは、次の操作が可能です。</span><span class="sxs-lookup"><span data-stu-id="10741-107">Report Builder enables you to:</span></span>  
  
-   <span data-ttu-id="10741-108">レポート ビルダーのリボンを使用して、レポートへのアイテムの追加、テーブル、グラフ、マップの各種ウィザードの起動、およびレポート データの書式設定をすばやく実行します。</span><span class="sxs-lookup"><span data-stu-id="10741-108">Use the Report Builder ribbon to quickly add items your reports, launch table, chart, and map wizards, and format report data.</span></span>  
  
-   <span data-ttu-id="10741-109">レポートに含めるデータを指定できるクエリ デザイナーを使用して、組み込みのデータ プロバイダーからデータを追加します。</span><span class="sxs-lookup"><span data-stu-id="10741-109">Add data from built-in data providers by using query designers that help you specify which data to include in your report.</span></span>  
  
-   <span data-ttu-id="10741-110">レポート パラメーターとその他の対話機能を作成して、レポートを使用するユーザーがデータをカスタマイズし、レポートの表示方法を変更できるようにします。</span><span class="sxs-lookup"><span data-stu-id="10741-110">Create and use report parameters and other interactive features that enable your report readers to customize data and vary report presentation.</span></span>  
  
-   <span data-ttu-id="10741-111">組み込みフィールド、コレクション、演算子、および関数から式を作成します。</span><span class="sxs-lookup"><span data-stu-id="10741-111">Create expressions from built-in fields, collections, operators, and functions.</span></span>  
  
-   <span data-ttu-id="10741-112">レポート サーバーから直接レポートを開きます。</span><span class="sxs-lookup"><span data-stu-id="10741-112">Open reports directly from a report server.</span></span>  
  
-   <span data-ttu-id="10741-113">ローカルまたはパブリッシュ済みの共有データ ソースおよび共有データセットを使用するレポートをプレビューします。</span><span class="sxs-lookup"><span data-stu-id="10741-113">Preview reports that use local or published shared data sources and shared datasets.</span></span>  
  
-   <span data-ttu-id="10741-114">レポートを HTML 形式または印刷形式でプレビューします。</span><span class="sxs-lookup"><span data-stu-id="10741-114">Preview reports in HTML or print format.</span></span>  
  
-   <span data-ttu-id="10741-115">レポートを他のファイル形式 ( [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)]など) にエクスポートします。</span><span class="sxs-lookup"><span data-stu-id="10741-115">Export reports to other file formats such as [!INCLUDE[ofprexcel](../../includes/ofprexcel-md.md)].</span></span>  
  
-   <span data-ttu-id="10741-116">レポートおよび関連アイテムを SharePoint ライブラリ、レポート サーバー、またはローカル コンピューターに保存します。</span><span class="sxs-lookup"><span data-stu-id="10741-116">Save your report and related items s to a SharePoint library, a report server, or your local computer.</span></span>  
  
 <span data-ttu-id="10741-117">レポート ビルダーとレポート デザイナーは、多くの機能を共有します。</span><span class="sxs-lookup"><span data-stu-id="10741-117">Report Builder and Report Designer share many features.</span></span> <span data-ttu-id="10741-118">レポートビルダーの詳細については、msdn.microsoft.com の[レポートビルダードキュメント](https://go.microsoft.com/fwlink/?LinkId=154494)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10741-118">For more information about Report Builder, see [Report Builder documentation](https://go.microsoft.com/fwlink/?LinkId=154494) on msdn.microsoft.com.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10741-119">参照</span><span class="sxs-lookup"><span data-stu-id="10741-119">See Also</span></span>  
 <span data-ttu-id="10741-120">[レポートビルダーアクセスの構成](../report-server/configure-report-builder-access.md) </span><span class="sxs-lookup"><span data-stu-id="10741-120">[Configure Report Builder Access](../report-server/configure-report-builder-access.md) </span></span>  
 <span data-ttu-id="10741-121">[Reporting Services ツール](reporting-services-tools.md) </span><span class="sxs-lookup"><span data-stu-id="10741-121">[Reporting Services Tools](reporting-services-tools.md) </span></span>  
 [<span data-ttu-id="10741-122">レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="10741-122">Design Reports with Report Designer &#40;SSRS&#41;</span></span>](design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  
