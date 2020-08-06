---
title: ファイルまたはアセンブリを読み込めませんでした &#39;Microsoft.analysisservices.sharepoint.integration.dll&#39; |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 6e350b67-5e18-4b90-8fb7-a0109cbb27b7
author: minewiskan
ms.author: owend
ms.openlocfilehash: b7ba75bdbd8e25f98d11d822c22fa7881352ad88
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643548"
---
# <a name="could-not-load-file-or-assembly-39microsoftanalysisservicessharepointintegration39"></a><span data-ttu-id="31b52-102">Microsoft.analysisservices.sharepoint.integration.dll&#39; &#39;ファイルまたはアセンブリを読み込めませんでした</span><span class="sxs-lookup"><span data-stu-id="31b52-102">Could not load file or assembly &#39;Microsoft.AnalysisServices.SharePoint.Integration&#39;</span></span>
  <span data-ttu-id="31b52-103">PowerPivot for SharePoint がある SharePoint 2010 環境で、PowerPivot のアプリケーション レベルのソリューションが正しく配置されていない場合にこのエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="31b52-103">In SharePoint 2010 environments that have PowerPivot for SharePoint, this error will occur if the application-level solution for PowerPivot did not deploy correctly.</span></span>  
  
## <a name="details"></a><span data-ttu-id="31b52-104">詳細</span><span class="sxs-lookup"><span data-stu-id="31b52-104">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="31b52-105">適用対象</span><span class="sxs-lookup"><span data-stu-id="31b52-105">Applies to</span></span>|<span data-ttu-id="31b52-106">PowerPivot for SharePoint</span><span class="sxs-lookup"><span data-stu-id="31b52-106">PowerPivot for SharePoint</span></span>|  
|<span data-ttu-id="31b52-107">製品バージョン</span><span class="sxs-lookup"><span data-stu-id="31b52-107">Product Version</span></span>|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]<span data-ttu-id="31b52-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31b52-108">, [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]</span></span>|  
|<span data-ttu-id="31b52-109">原因</span><span class="sxs-lookup"><span data-stu-id="31b52-109">Cause</span></span>|<span data-ttu-id="31b52-110">Powerpivotwebapp ソリューションが配置されていないか、配置が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="31b52-110">Powerpivotwebapp solution is not deployed or did not deploy correctly.</span></span>|  
|<span data-ttu-id="31b52-111">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="31b52-111">Message Text</span></span>|<span data-ttu-id="31b52-112">ファイルまたはアセンブリ 'Microsoft.AnalysisServices.SharePoint.Integration' を読み込めませんでした</span><span class="sxs-lookup"><span data-stu-id="31b52-112">Could not load file or assembly 'Microsoft.AnalysisServices.SharePoint.Integration'</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="31b52-113">説明</span><span class="sxs-lookup"><span data-stu-id="31b52-113">Explanation</span></span>  
 <span data-ttu-id="31b52-114">PowerPivot for SharePoint では、その機能を SharePoint サーバーに配置するためにソリューション パッケージを使用します。</span><span class="sxs-lookup"><span data-stu-id="31b52-114">PowerPivot for SharePoint uses solution packages to deploy its features on a SharePoint server.</span></span> <span data-ttu-id="31b52-115">ソリューションのいずれかが正しく配置されていません。</span><span class="sxs-lookup"><span data-stu-id="31b52-115">One of the solutions is not deployed correctly.</span></span> <span data-ttu-id="31b52-116">そのため、PowerPivot ギャラリーまたは SharePoint サイトのその他の PowerPivot アプリケーション ページを開こうとするたびに、このエラーが表示されます。</span><span class="sxs-lookup"><span data-stu-id="31b52-116">As a result, this error appears whenever you try to open PowerPivot Gallery or other PowerPivot application pages on a SharePoint site.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="31b52-117">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="31b52-117">User Action</span></span>  
 <span data-ttu-id="31b52-118">ソリューション パッケージを配置します。</span><span class="sxs-lookup"><span data-stu-id="31b52-118">Deploy the solution package.</span></span>  
  
1.  <span data-ttu-id="31b52-119">サーバーの全体管理で、[システム設定] の **[ファーム ソリューションの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31b52-119">In Central Administration, in System Settings, click **Manage farm solutions**.</span></span>  
  
2.  <span data-ttu-id="31b52-120">**[Powerpivotwebapp]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31b52-120">Click **Powerpivotwebapp**.</span></span>  
  
3.  <span data-ttu-id="31b52-121">**[ソリューションの配置]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31b52-121">Click **Deploy Solution**.</span></span>  
  
4.  <span data-ttu-id="31b52-122">このエラーが発生している Web アプリケーションを選択します。</span><span class="sxs-lookup"><span data-stu-id="31b52-122">Choose the web application for which this error is occurring.</span></span> <span data-ttu-id="31b52-123">複数の Web アプリケーションがある場合は、そのすべてについてソリューションを再配置します。</span><span class="sxs-lookup"><span data-stu-id="31b52-123">If there is more than one web application, redeploy the solution for all of hem.</span></span>  
  
5.  <span data-ttu-id="31b52-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="31b52-124">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b52-125">参照</span><span class="sxs-lookup"><span data-stu-id="31b52-125">See Also</span></span>  
 [<span data-ttu-id="31b52-126">SharePoint への PowerPivot ソリューションの配置</span><span class="sxs-lookup"><span data-stu-id="31b52-126">Deploy PowerPivot Solutions to SharePoint</span></span>](deploy-power-pivot-solutions-to-sharepoint.md)  
  
  
