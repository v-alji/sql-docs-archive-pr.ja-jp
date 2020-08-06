---
title: データ警告マネージャーで SharePoint サイトのすべてのデータ警告を管理する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: 9c70b0f4-2db8-4c2e-acbf-96e2a55ddc48
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b41fdbd18a0b1b4a7a69a3ca202de1c555c070de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721219"
---
# <a name="manage-all-data-alerts-on-a-sharepoint-site-in-data-alert-manager"></a><span data-ttu-id="48a41-102">データ警告マネージャーで SharePoint サイトのすべてのデータ警告を管理する</span><span class="sxs-lookup"><span data-stu-id="48a41-102">Manage All Data Alerts on a SharePoint Site in Data Alert Manager</span></span>
  <span data-ttu-id="48a41-103">SharePoint 警告管理者は、サイト ユーザーによって作成されたデータ警告の一覧と、警告に関する情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="48a41-103">SharePoint alerting administrators can view a list of the data alerts that were created by any site user and information about the alerts.</span></span> <span data-ttu-id="48a41-104">また、警告管理者は警告を削除することもできます。</span><span class="sxs-lookup"><span data-stu-id="48a41-104">Alerting administrators can also delete alerts.</span></span> <span data-ttu-id="48a41-105">次の図に、警告管理者がデータ警告マネージャー内で使用できる機能を示します。</span><span class="sxs-lookup"><span data-stu-id="48a41-105">The following picture shows the features available to alerting administrators in Data Alert Manager.</span></span>  
  
 <span data-ttu-id="48a41-106">![SharePoint サイト管理者用の警告マネージャー](media/rs-alertmanagersite.gif "SharePoint サイト管理者用の警告マネージャー")</span><span class="sxs-lookup"><span data-stu-id="48a41-106">![Alert Manager for SharePoin tsite administrators](media/rs-alertmanagersite.gif "Alert Manager for SharePoin tsite administrators")</span></span>  
  
### <a name="to-view-a-list-of-alerts-created-by-a-site-user"></a><span data-ttu-id="48a41-107">サイト ユーザーが作成した警告の一覧を表示するには</span><span class="sxs-lookup"><span data-stu-id="48a41-107">To view a list of alerts created by a site user</span></span>  
  
1.  <span data-ttu-id="48a41-108">データ警告定義が保存されている SharePoint サイトに移動します。</span><span class="sxs-lookup"><span data-stu-id="48a41-108">Go to the SharePoint site where data alerts definitions are saved.</span></span>  
  
2.  <span data-ttu-id="48a41-109">ホーム ページで、 **[サイトの操作]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48a41-109">On the Home page, click **Site Actions**.</span></span>  
  
3.  <span data-ttu-id="48a41-110">一覧の一番下までスクロールし、 **[サイトの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48a41-110">Scroll to the bottom of the list and click **Site Settings**.</span></span>  
  
4.  <span data-ttu-id="48a41-111">**[Reporting Services]** で、 **[データ警告の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48a41-111">Under **Reporting Services**, click **Manage Data Alerts**.</span></span>  
  
5.  <span data-ttu-id="48a41-112">**[ユーザー用の警告の表示]** の一覧で下矢印をクリックし、警告を表示するユーザーを選択します。</span><span class="sxs-lookup"><span data-stu-id="48a41-112">Click the down arrow by the **View alerts for user** list and select the user whose alerts you want to view.</span></span>  
  
6.  <span data-ttu-id="48a41-113">**[レポート用の警告の表示]** の一覧の横にある下矢印をクリックして、表示する特定の警告を選択するか、 **[すべて表示]** をクリックして、選択したユーザーによって作成されたすべての警告を表示します。</span><span class="sxs-lookup"><span data-stu-id="48a41-113">Click the down arrow next to the **View alerts for report** list and select a specific alert to view, or click **Show All** to list all alerts created by the selected user.</span></span>  
  
     <span data-ttu-id="48a41-114">テーブルに、名前、レポート名、データ警告の作成者の名前、データ警告が送信された回数、データ警告定義が最後に変更された時刻、およびデータ警告の状態が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="48a41-114">A table lists the name, report name, name of the person who created the data alert, the number times the data alert was sent, the last time the data alert definition was modified, and the status of the data alert.</span></span> <span data-ttu-id="48a41-115">データ警告の生成や送信ができない場合は、エラーに関する情報が状態列に含まれているので、これを利用して問題のトラブルシューティングを行います。</span><span class="sxs-lookup"><span data-stu-id="48a41-115">If the data alert cannot be generated or sent, the status column contains information about the error and helps you troubleshoot the problem.</span></span>  
  
### <a name="to-delete-an-alert-definition"></a><span data-ttu-id="48a41-116">警告の定義を削除するには</span><span class="sxs-lookup"><span data-stu-id="48a41-116">To delete an alert definition</span></span>  
  
-   <span data-ttu-id="48a41-117">削除するデータ警告を右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="48a41-117">Right-click the data alert that you want to delete and click **Delete**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="48a41-118">警告を削除すると、それ以降、警告メッセージは送信されません。</span><span class="sxs-lookup"><span data-stu-id="48a41-118">After you delete the alert, no further alert messages are sent.</span></span> <span data-ttu-id="48a41-119">ただし、警告データベースを照会すると、警告の定義がまだ存在している場合があります。</span><span class="sxs-lookup"><span data-stu-id="48a41-119">However, if you query the alerting database you might find that the alert definition still exists.</span></span> <span data-ttu-id="48a41-120">警告サービスではスケジュールに基づいてクリーンアップが実行され、警告の定義は次回のクリーンアップで完全に削除されます。</span><span class="sxs-lookup"><span data-stu-id="48a41-120">The alerting service performs clean up on a schedule and the alert definition is deleted permanently in the next cleanup.</span></span> <span data-ttu-id="48a41-121">既定のクリーンアップ間隔は 20 分です。</span><span class="sxs-lookup"><span data-stu-id="48a41-121">The default cleanup interval is 20 minutes.</span></span> <span data-ttu-id="48a41-122">クリーンアップ間隔は設定可能です。</span><span class="sxs-lookup"><span data-stu-id="48a41-122">This and other cleanup intervals are configurable.</span></span> <span data-ttu-id="48a41-123">詳細については、「 [Reporting Services のデータ警告](../ssms/agent/alerts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="48a41-123">For more information, see [Reporting Services Data Alerts](../ssms/agent/alerts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a41-124">参照</span><span class="sxs-lookup"><span data-stu-id="48a41-124">See Also</span></span>  
 <span data-ttu-id="48a41-125">[警告管理者用のデータ警告マネージャー](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="48a41-125">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span></span>  
 [<span data-ttu-id="48a41-126">Reporting Services のデータ警告</span><span class="sxs-lookup"><span data-stu-id="48a41-126">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
