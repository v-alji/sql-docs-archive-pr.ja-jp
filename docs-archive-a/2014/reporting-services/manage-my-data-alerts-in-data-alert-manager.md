---
title: データ警告マネージャーでのデータ警告の管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- managing, alerts
- managing, data alerts
ms.assetid: e0e4ffdf-bd4c-4ebd-872b-07486cbb47c2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 371c62c2f97334e20280a659c8039ab20852ccfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721224"
---
# <a name="manage-my-data-alerts-in-data-alert-manager"></a><span data-ttu-id="e0097-102">データ警告マネージャーでのデータ警告の管理</span><span class="sxs-lookup"><span data-stu-id="e0097-102">Manage My Data Alerts in Data Alert Manager</span></span>
  <span data-ttu-id="e0097-103">SharePoint ユーザーは、自分が作成したデータ警告と、それらの警告に関する情報を一覧表示できます。</span><span class="sxs-lookup"><span data-stu-id="e0097-103">SharePoint users can view a list of the data alerts that they created and information about the alerts.</span></span> <span data-ttu-id="e0097-104">また、警告を削除したり、データ警告デザイナーで警告定義を開いて編集したり、それらの警告を実行することもできます。</span><span class="sxs-lookup"><span data-stu-id="e0097-104">Users can also delete their alerts, open alert definitions for edit in Data Alert Designer, and run their alerts.</span></span> <span data-ttu-id="e0097-105">次の図に、データ警告マネージャーでユーザーが使用できる機能を示します。</span><span class="sxs-lookup"><span data-stu-id="e0097-105">The following picture shows the features available to users in Data Alert Manager.</span></span>  
  
 <span data-ttu-id="e0097-106">![SharePoint ユーザー用の警告マネージャー機能](media/rs-alertmanageriw.gif "SharePoint ユーザー用の警告マネージャー機能")</span><span class="sxs-lookup"><span data-stu-id="e0097-106">![Alert Manager features for SharePoint users](media/rs-alertmanageriw.gif "Alert Manager features for SharePoint users")</span></span>  
  
### <a name="to-view-a-list-of-your-alerts"></a><span data-ttu-id="e0097-107">警告の一覧を表示するには</span><span class="sxs-lookup"><span data-stu-id="e0097-107">To view a list of your alerts</span></span>  
  
1.  <span data-ttu-id="e0097-108">データ警告の作成対象のレポートが保存されている SharePoint ライブラリに移動します。</span><span class="sxs-lookup"><span data-stu-id="e0097-108">Go to the SharePoint library where you saved the reports on which you created data alerts.</span></span>  
  
2.  <span data-ttu-id="e0097-109">レポートの展開ドロップダウン メニューのアイコンをクリックし、 **[データ警告の管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0097-109">Click the icon for the expand drop-down menu on a report and click **Manage Data Alerts**.</span></span> <span data-ttu-id="e0097-110">ドロップダウン メニューを次の図に示します。</span><span class="sxs-lookup"><span data-stu-id="e0097-110">The following picture shows the drop-down menu.</span></span>  
  
     <span data-ttu-id="e0097-111">![レポート コンテキスト メニューから警告マネージャーを開く](media/rs-openalertmanager.gif "レポート コンテキスト メニューから警告マネージャーを開く")</span><span class="sxs-lookup"><span data-stu-id="e0097-111">![Open Alert Manager from report context menu](media/rs-openalertmanager.gif "Open Alert Manager from report context menu")</span></span>  
  
     <span data-ttu-id="e0097-112">データ警告マネージャーが開きます。</span><span class="sxs-lookup"><span data-stu-id="e0097-112">Data Alert Manager opens.</span></span> <span data-ttu-id="e0097-113">既定では、ライブラリで選択したレポートに対する警告が一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0097-113">By default, it lists the alerts for the report that you selected in the library.</span></span>  
  
3.  <span data-ttu-id="e0097-114">**[レポート用の警告の表示]** の一覧の横にある下矢印をクリックして、警告を表示するレポートを選択するか、 **[すべて表示]** をクリックして警告をすべて表示します。</span><span class="sxs-lookup"><span data-stu-id="e0097-114">Click the down arrow next to the **View alerts for report** list and select a report to view its alerts, or click **Show All** to list all alerts.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e0097-115">選択したレポートに警告が存在しない場合、SharePoint ライブラリに戻って警告があるレポートを検索および選択する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="e0097-115">If the report that you selected does not have any alerts, you do not have to return to the SharePoint library to locate and select a report that hasalerts.</span></span> <span data-ttu-id="e0097-116">代わりに、 **[すべて表示]** をクリックしてすべての警告を一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="e0097-116">Instead, click **Show All** to see a list of all your alerts.</span></span>  
  
     <span data-ttu-id="e0097-117">警告名、レポート名、警告の作成者としての自分の名前、送信された警告の数、最後に警告定義が変更された日時、および警告の状態が表に一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0097-117">A table lists the alert name, report name, your name as the creator of the alert, the number the alert was sent, the last time the alert definition was modified, and the status of the alert.</span></span> <span data-ttu-id="e0097-118">警告の生成や送信ができない場合は、エラーに関する情報が状態列に含まれているので、これを利用して問題のトラブルシューティングを行います。</span><span class="sxs-lookup"><span data-stu-id="e0097-118">If the alert cannot be generated or sent, the status column contains information about the error and helps you troubleshoot the problem.</span></span>  
  
### <a name="to-edit-an-alert-definition"></a><span data-ttu-id="e0097-119">警告定義を編集するには</span><span class="sxs-lookup"><span data-stu-id="e0097-119">To edit an alert definition</span></span>  
  
-   <span data-ttu-id="e0097-120">警告定義を編集するデータ警告を右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0097-120">Right-click the data alert for which you want to edit the alert definition and click **Edit**.</span></span>  
  
     <span data-ttu-id="e0097-121">データ警告デザイナーに警告定義が表示されます。</span><span class="sxs-lookup"><span data-stu-id="e0097-121">The alert definition opens in Data Alert Designer.</span></span> <span data-ttu-id="e0097-122">詳しくは、「 [警告デザイナーでのデータ警告の編集](edit-a-data-alert-in-alert-designer.md) 」および「 [データ警告デザイナー](../../2014/reporting-services/data-alert-designer.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="e0097-122">For more information, see [Edit a Data Alert in Alert Designer](edit-a-data-alert-in-alert-designer.md) and [Data Alert Designer](../../2014/reporting-services/data-alert-designer.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e0097-123">データ警告定義は、作成したユーザーのみが編集できます。</span><span class="sxs-lookup"><span data-stu-id="e0097-123">Only the user that created the data alert definition can edit it.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e0097-124">レポートが変更され、レポートから生成されたデータ フィードが変更されている場合、警告の定義が無効になっている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="e0097-124">If the report has changed and the data feeds generated from the report have changed the alert definition might no longer be valid.</span></span> <span data-ttu-id="e0097-125">この状況が生じるのは、警告のルールで参照される列がレポートから削除された場合、列のデータ型が変更された場合、列が別のデータ フィードに含まれている場合、またはレポートが削除または移動された場合です。</span><span class="sxs-lookup"><span data-stu-id="e0097-125">This occurs when a column that the alert references in its rules is deleted from the report, changes data type, or is included in a different data feed or the report is deleted or moved.</span></span> <span data-ttu-id="e0097-126">無効な警告定義は開くことはできますが、基になるレポート データ フィードの現行バージョンに基づいて有効になるまでは再保存できません。</span><span class="sxs-lookup"><span data-stu-id="e0097-126">You can open an alert definition that is not valid, but you cannot resave it until it is valid based on the current version of the report data feed that it is built upon.</span></span> <span data-ttu-id="e0097-127">レポートからデータ フィードが生成される方法の詳細については、「[複数のレポートからのデータ フィードの生成 &#40;レポート ビルダーおよび SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e0097-127">To learn more about how data feeds are generated from reports, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>  
  
### <a name="to-delete-an-alert-definition"></a><span data-ttu-id="e0097-128">警告の定義を削除するには</span><span class="sxs-lookup"><span data-stu-id="e0097-128">To delete an alert definition</span></span>  
  
-   <span data-ttu-id="e0097-129">削除するデータ警告を右クリックして、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0097-129">Right-click the data alert that you want to delete and click **Delete**.</span></span>  
  
     <span data-ttu-id="e0097-130">警告を削除すると、それ以降、警告メッセージは送信されません。</span><span class="sxs-lookup"><span data-stu-id="e0097-130">When you delete the alert, no further alert messages are sent.</span></span>  
  
### <a name="to-run-an-alert"></a><span data-ttu-id="e0097-131">警告を実行するには</span><span class="sxs-lookup"><span data-stu-id="e0097-131">To run an alert</span></span>  
  
-   <span data-ttu-id="e0097-132">実行するデータ警告を右クリックして、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e0097-132">Right-click the data alert that you want to run and click **Run**.</span></span>  
  
     <span data-ttu-id="e0097-133">警告インスタンスが作成され、データ警告メッセージが直ちに送信されます。これは、データ警告デザイナーで指定したスケジュール オプションの内容にかかわらず実行されます。</span><span class="sxs-lookup"><span data-stu-id="e0097-133">The alert instance is created and the data alert message is immediately sent, regardless of the schedule options you specified in Data Alert Designer.</span></span> <span data-ttu-id="e0097-134">たとえば、結果が変更された場合にのみ、週単位で送信されるよう構成された警告も同様です。</span><span class="sxs-lookup"><span data-stu-id="e0097-134">For example, an alert configured to be sent weekly and then only if the results change is sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0097-135">参照</span><span class="sxs-lookup"><span data-stu-id="e0097-135">See Also</span></span>  
 <span data-ttu-id="e0097-136">[警告管理者用のデータ警告マネージャー](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span><span class="sxs-lookup"><span data-stu-id="e0097-136">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) </span></span>  
 [<span data-ttu-id="e0097-137">Reporting Services のデータ警告</span><span class="sxs-lookup"><span data-stu-id="e0097-137">Reporting Services Data Alerts</span></span>](../ssms/agent/alerts.md)  
  
  
