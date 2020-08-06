---
title: '[スケジュールのプロパティ] ([レポート] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.scheduleproperties.reports.f1
ms.assetid: 7db728bd-4b08-43ef-a49a-e8dcdd37cf89
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: da0b5255e73522572fa22da8668329a28f108104
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634820"
---
# <a name="schedule-properties-reports-page"></a><span data-ttu-id="55933-102">[スケジュールのプロパティ] ([レポート] ページ)</span><span class="sxs-lookup"><span data-stu-id="55933-102">Schedule Properties (Reports Page)</span></span>
  <span data-ttu-id="55933-103">このページを使用すると、共有データ ソースを使用するすべてのレポートの一覧を表示できます。</span><span class="sxs-lookup"><span data-stu-id="55933-103">Use this page to view a list of all reports that use this shared schedule.</span></span> <span data-ttu-id="55933-104">スケジュールを使用して、レポート スナップショットの更新、レポート履歴の生成、サブスクリプションのトリガー、またはレポートのキャッシュされたコピーの期限の終了を実行できます。</span><span class="sxs-lookup"><span data-stu-id="55933-104">Schedules can be used to refresh report snapshots, generate report history, trigger a subscription, or expire a cached copy of the report.</span></span> <span data-ttu-id="55933-105">スケジュールがどのように使用されているかを確認するには、レポートのプロパティおよびサブスクリプション情報を参照します。</span><span class="sxs-lookup"><span data-stu-id="55933-105">To find out how the schedule is used, view the property and subscription information of the report.</span></span>  
  
 <span data-ttu-id="55933-106">このページには共有スケジュールを使用する各レポートが表示されますが、1 つのレポート内で共有スケジュールが何回使用されるかについては示されません。</span><span class="sxs-lookup"><span data-stu-id="55933-106">Although this page shows each report that uses the shared schedule, it does not indicate how many times the shared schedule is used within that single report.</span></span> <span data-ttu-id="55933-107">たとえば、Company Sales レポートの 20 の異なるサブスクライバーがすべて同じ共有スケジュールを使用してサブスクリプション処理を開始するとします。</span><span class="sxs-lookup"><span data-stu-id="55933-107">For example, suppose 20 different subscribers to the Company Sales report all use the same shared schedule to trigger subscription processing.</span></span> <span data-ttu-id="55933-108">この場合、Company Sales レポートでは共有スケジュールの参照が 20 回行われますが、この一覧には 1 回しか表示されません。</span><span class="sxs-lookup"><span data-stu-id="55933-108">In this case, the Company Sales report will only appear once in this list, even though the report has 20 references to the shared schedule.</span></span>  
  
 <span data-ttu-id="55933-109">このページを開くには、を起動し [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] てレポートサーバーに接続し、[**共有スケジュール**] フォルダーを開きます。共有スケジュールを右クリックし、[**プロパティ**] を選択し、[**レポート**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="55933-109">To open this page, start [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], connect to a report server, open the **Shared Schedules** folder, right-click a shared schedule, select **Properties**, and then click **Reports**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="55933-110">この機能は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="55933-110">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="55933-111">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2012 の各エディションがサポートする機能](https://go.microsoft.com/fwlink/?linkid=232473)」 (を参照してください https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="55933-111">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
## <a name="options"></a><span data-ttu-id="55933-112">Options</span><span class="sxs-lookup"><span data-stu-id="55933-112">Options</span></span>  
 <span data-ttu-id="55933-113">**フォルダー**</span><span class="sxs-lookup"><span data-stu-id="55933-113">**Folder**</span></span>  
 <span data-ttu-id="55933-114">レポートのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="55933-114">Specifies the path of the report.</span></span>  
  
 <span data-ttu-id="55933-115">**Report**</span><span class="sxs-lookup"><span data-stu-id="55933-115">**Report**</span></span>  
 <span data-ttu-id="55933-116">スケジュールを使用するレポートの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="55933-116">Specifies the name of the report that uses the schedule.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55933-117">参照</span><span class="sxs-lookup"><span data-stu-id="55933-117">See Also</span></span>  
 <span data-ttu-id="55933-118">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="55933-118">[Create, Modify, and Delete Schedules](../subscriptions/create-modify-and-delete-schedules.md) </span></span>  
 <span data-ttu-id="55933-119">[[スケジュール]](../subscriptions/schedules.md) </span><span class="sxs-lookup"><span data-stu-id="55933-119">[Schedules](../subscriptions/schedules.md) </span></span>  
 <span data-ttu-id="55933-120">[Management Studio F1 ヘルプのレポートサーバー](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="55933-120">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="55933-121">[Management Studio でレポートサーバーに接続する](connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="55933-121">[Connect to a Report Server in Management Studio](connect-to-a-report-server-in-management-studio.md) </span></span>  
 [<span data-ttu-id="55933-122">レポート &#40;レポートマネージャーの全般プロパティの構成&#41;</span><span class="sxs-lookup"><span data-stu-id="55933-122">Configure General Properties for a Report &#40;Report Manager&#41;</span></span>](../configure-general-properties-for-a-report-report-manager.md)  
  
  
