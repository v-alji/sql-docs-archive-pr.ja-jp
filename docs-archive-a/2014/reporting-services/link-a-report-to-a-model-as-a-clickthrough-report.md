---
title: レポートをクリックスルーレポートとしてモデルにリンクする |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- customizing clickthrough reports
- clickthrough reports, customizing
- clickthrough reports, templates
ms.assetid: 3af42de3-67ef-41c2-bc8a-7045baec6f63
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cb84f8036dbe5a1694628144f0b948452261ca75
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632959"
---
# <a name="link-a-report-to-a-model-as-a-clickthrough-report"></a><span data-ttu-id="d06a5-102">レポートをクリックスルー レポートとしてモデルにリンクする</span><span class="sxs-lookup"><span data-stu-id="d06a5-102">Link a Report to a Model as a Clickthrough Report</span></span>
  <span data-ttu-id="d06a5-103">クリックスルー レポートの既定のテンプレートを使用する代わりに、レポート ビルダーのレポートを作成し、それをレポート モデルの特定のエンティティにリンクすることができます。</span><span class="sxs-lookup"><span data-stu-id="d06a5-103">Instead of using the default clickthrough report templates, you can create a Report Builder report and then link it to a specific entity in the report model.</span></span> <span data-ttu-id="d06a5-104">レポートを閲覧しているユーザーがメイン レポート内の対話型データをクリックすると、このレポートがクリックスルー レポートとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="d06a5-104">When the person viewing the report clicks the interactive data in the main report, this report is displayed as a clickthrough report.</span></span> <span data-ttu-id="d06a5-105">レポートをエンティティにリンクするには、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] レポート マネージャーを使用します。</span><span class="sxs-lookup"><span data-stu-id="d06a5-105">To link a report to an entity, use [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] Report Manager.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="d06a5-106">レポートで使用されるプライマリ (基本) エンティティは、レポートのリンク先と同じエンティティである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d06a5-106">The primary, or base, entity that is used in the report must to be the same entity to which the report is linked.</span></span>  
  
### <a name="to-start-report-manager-from-a-browser"></a><span data-ttu-id="d06a5-107">ブラウザーからレポート マネージャーを起動するには</span><span class="sxs-lookup"><span data-stu-id="d06a5-107">To start Report Manager from a browser</span></span>  
  
1.  <span data-ttu-id="d06a5-108">[!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 以降を開きます。</span><span class="sxs-lookup"><span data-stu-id="d06a5-108">Open [!INCLUDE[msCoName](../includes/msconame-md.md)] Internet Explorer 6.0 or later.</span></span>  
  
2.  <span data-ttu-id="d06a5-109">Web ブラウザーのアドレス バーに、レポート マネージャーの URL を入力します。</span><span class="sxs-lookup"><span data-stu-id="d06a5-109">In the address bar of the Web browser, type the Report Manager URL.</span></span> <span data-ttu-id="d06a5-110">既定では、URL は http:// \<*ComputerName*> /レポートです。</span><span class="sxs-lookup"><span data-stu-id="d06a5-110">By default, the URL is http://\<*ComputerName*>/reports.</span></span>  
  
### <a name="to-create-a-customized-clickthrough-report"></a><span data-ttu-id="d06a5-111">カスタマイズされたクリックスルー レポートを作成するには</span><span class="sxs-lookup"><span data-stu-id="d06a5-111">To create a customized clickthrough report</span></span>  
  
1.  <span data-ttu-id="d06a5-112">カスタマイズされたクリックスルー レポートを追加するレポート モデルに移動します。</span><span class="sxs-lookup"><span data-stu-id="d06a5-112">Navigate to the report model to which you want to add the customized clickthrough report.</span></span>  
  
2.  <span data-ttu-id="d06a5-113">レポート モデルをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="d06a5-113">Double-click the report model.</span></span>  
  
3.  <span data-ttu-id="d06a5-114">**[クリックスルー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d06a5-114">Click **Clickthrough**.</span></span>  
  
4.  <span data-ttu-id="d06a5-115">カスタマイズされたクリックスルー レポートをアタッチするエンティティを選択します。</span><span class="sxs-lookup"><span data-stu-id="d06a5-115">Select the entity to which you want to attach the customized clickthrough report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d06a5-116">このエンティティは、カスタマイズされたクリックスルー レポートの基本エンティティと同じものである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d06a5-116">This entity must be the same as the base entity of the customized clickthrough report.</span></span>  
  
5.  <span data-ttu-id="d06a5-117">選択したエンティティの単一のインスタンスがクリックされたときに、カスタマイズされたレポートを表示するには、単一インスタンス レポートの **[参照]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d06a5-117">To display the customized report when a single instance of the selected entity is clicked, click the Single instance report **Browse** button.</span></span>  
  
     <span data-ttu-id="d06a5-118">または</span><span class="sxs-lookup"><span data-stu-id="d06a5-118">-or-</span></span>  
  
     <span data-ttu-id="d06a5-119">選択したエンティティの複数のインスタンスがクリックされたときに、カスタマイズされたレポートを表示するには、複数インスタンス レポートの **[参照]** ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="d06a5-119">To display the customized report when a multiple instance of the selected entity is clicked, click the Multiple instance report **Browse** button.</span></span>  
  
6.  <span data-ttu-id="d06a5-120">レポートを選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d06a5-120">Select the report and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="d06a5-121">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d06a5-121">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d06a5-122">参照</span><span class="sxs-lookup"><span data-stu-id="d06a5-122">See Also</span></span>  
 [<span data-ttu-id="d06a5-123">クリックスルーレポート &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="d06a5-123">Clickthrough Reports &#40;SSRS&#41;</span></span>](reports/clickthrough-reports-ssrs.md)  
  
  
