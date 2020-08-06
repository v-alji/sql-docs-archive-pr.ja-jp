---
title: 個人用サブスクリプションを使用する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- subscriptions [Reporting Services], My Subscriptions page
- My Subscriptions page [Reporting Services]
ms.assetid: e96623ba-677e-4748-8787-f32bed3b5c12
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f3378a65637ad04151cc517fd9047363af954c31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739096"
---
# <a name="use-my-subscriptions"></a><span data-ttu-id="f999c-102">個人用サブスクリプションを使用する</span><span class="sxs-lookup"><span data-stu-id="f999c-102">Use My Subscriptions</span></span>
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="f999c-103">レポートマネージャーには、すべてのサブスクリプションを1か所にまとめた **[個人用サブスクリプション**] ページが含まれています。</span><span class="sxs-lookup"><span data-stu-id="f999c-103">Report Manager includes a **My Subscriptions** page that organizes all of your subscriptions into one place.</span></span> <span data-ttu-id="f999c-104">[個人用サブスクリプション] を使用して、既存のサブスクリプションを表示、変更、および削除できます。</span><span class="sxs-lookup"><span data-stu-id="f999c-104">You can use My Subscriptions to view, modify, and delete existing subscriptions.</span></span> <span data-ttu-id="f999c-105">ただし、このページは、サブスクリプションの作成には使用できません。</span><span class="sxs-lookup"><span data-stu-id="f999c-105">However, you cannot use it to create subscriptions.</span></span>  
  
||  
|-|  
|<span data-ttu-id="f999c-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] ネイティブ モード</span><span class="sxs-lookup"><span data-stu-id="f999c-106">**[!INCLUDE[applies](../../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] Native mode</span></span>|  
  
 <span data-ttu-id="f999c-107">[個人用サブスクリプション] 内では、フォルダー、レポート、説明、トリガー、最後に実行された日時、状態によるサブスクリプションの並べ替えが可能です。</span><span class="sxs-lookup"><span data-stu-id="f999c-107">Within My Subscriptions, you can sort subscriptions by folder, report, description, trigger, last run, or status.</span></span> <span data-ttu-id="f999c-108">日時順に並べ替えられる [最終実行] を除いて、すべての値はアルファベット順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="f999c-108">All values are sorted alphabetically except for Last Run, which is in chronological order.</span></span>  
  
 <span data-ttu-id="f999c-109">[個人用サブスクリプション] では、自分で作成したサブスクリプションだけが表示されます。</span><span class="sxs-lookup"><span data-stu-id="f999c-109">My Subscriptions shows only the subscriptions that you create.</span></span> <span data-ttu-id="f999c-110">他のユーザーが所有しているサブスクリプションにサブスクライバーとして自分が追加されていても、そのサブスクリプションは一覧表示されません。データ ドリブン サブスクリプションも表示されません。</span><span class="sxs-lookup"><span data-stu-id="f999c-110">It does not list subscriptions that are owned by other users, even if you are added as a subscriber to those subscriptions, nor does it show data-driven subscriptions.</span></span>  
  
 <span data-ttu-id="f999c-111">サブスクリプションを名前で検索することはできません。また、トリガー情報、状態情報などを基にサブスクリプションを検索することもできません。</span><span class="sxs-lookup"><span data-stu-id="f999c-111">You cannot search for subscriptions by name, nor can you search for subscriptions based on trigger information, status information, and so forth.</span></span> <span data-ttu-id="f999c-112">詳細については、「[ネイティブモード&#41;での標準サブスクリプション &#40;Reporting Services の作成、変更、および削除](create-and-manage-subscriptions-for-native-mode-report-servers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f999c-112">For more information, see [Create, Modify, and Delete Standard Subscriptions &#40;Reporting Services in Native Mode&#41;](create-and-manage-subscriptions-for-native-mode-report-servers.md).</span></span>  
  
## <a name="how-to-use-my-subscriptions"></a><span data-ttu-id="f999c-113">個人用サブスクリプションを使用する方法</span><span class="sxs-lookup"><span data-stu-id="f999c-113">How to Use My Subscriptions</span></span>  
 <span data-ttu-id="f999c-114">個人用サブスクリプションはレポート マネージャーから利用できます。</span><span class="sxs-lookup"><span data-stu-id="f999c-114">My Subscriptions is available through Report Manager.</span></span> <span data-ttu-id="f999c-115">個人用サブスクリプションにアクセスするには、レポートマネージャーグローバルツールバーの [**個人用サブスクリプション**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="f999c-115">To access My Subscriptions, click **My Subscriptions** on the Report Manager global toolbar.</span></span>  
  
## <a name="use-windows-powershell-to-list-mysubscriptions"></a><span data-ttu-id="f999c-116">Windows PowerShell を使用した個人用サブスクリプションの一覧表示</span><span class="sxs-lookup"><span data-stu-id="f999c-116">Use Windows PowerShell to list MySubscriptions</span></span>  
 <span data-ttu-id="f999c-117">![PowerShell 関連コンテンツ](../media/rs-powershellicon.jpg "PowerShell 関連コンテンツ")</span><span class="sxs-lookup"><span data-stu-id="f999c-117">![PowerShell related content](../media/rs-powershellicon.jpg "PowerShell related content")</span></span>  
  
 <span data-ttu-id="f999c-118">次の PowerShell スクリプトは、現在のユーザーのサブスクリプションとサブスクリプションのプロパティの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="f999c-118">The following PowerShell script will return the list of subscriptions and subscription properties for the current user.</span></span> <span data-ttu-id="f999c-119">詳細については、「 [ReportingService2010.ListMySubscriptions メソッド](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f999c-119">For more information, see [ReportingService2010.ListMySubscriptions Method](https://technet.microsoft.com/library/reportservice2010.reportingservice2010.listmysubscriptions.aspx).</span></span>  
  
```powershell
#server -  all subscriptions of the current user at the given server or site  
$server="[server name]/reportserver"  
$rs2010 = New-WebServiceProxy -Uri "http://$server/ReportService2010.asmx" -Namespace SSRS.ReportingService2010 -UseDefaultCredential ;  
  
$subscriptions=ListMySubscriptions(ItemPathOrSiteURL)  
$subscriptions | select Path, report, Description, Owner, SubscriptionID, lastexecuted,Status  
#uncomment the following to list all the subscription properties  
#$subscriptions
```  
  
## <a name="see-also"></a><span data-ttu-id="f999c-120">参照</span><span class="sxs-lookup"><span data-stu-id="f999c-120">See Also</span></span>  
 <span data-ttu-id="f999c-121">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span><span class="sxs-lookup"><span data-stu-id="f999c-121">[Data-Driven Subscriptions](data-driven-subscriptions.md) </span></span>  
 <span data-ttu-id="f999c-122">[サブスクリプションと配信 &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="f999c-122">[Subscriptions and Delivery &#40;Reporting Services&#41;](subscriptions-and-delivery-reporting-services.md) </span></span>  
 [<span data-ttu-id="f999c-123">ネイティブ モード レポート サーバーのサブスクリプションの作成と管理</span><span class="sxs-lookup"><span data-stu-id="f999c-123">Create and Manage Subscriptions for Native Mode Report Servers</span></span>](../create-manage-subscriptions-native-mode-report-servers.md)  
