---
title: 警告デザイナーでのデータ警告の編集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- editing, data alerts
- updating, data alerts
- editing, alerts
- updating, alerts
ms.assetid: dde3664d-90b5-4b12-969e-39152c86e58a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9906b33ae50d51733eaec1bf5c201c9f5b5d120e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87719641"
---
# <a name="edit-a-data-alert-in-alert-designer"></a><span data-ttu-id="2d5a2-102">警告デザイナーでのデータ警告の編集</span><span class="sxs-lookup"><span data-stu-id="2d5a2-102">Edit a Data Alert in Alert Designer</span></span>
  <span data-ttu-id="2d5a2-103">編集対象のデータ警告定義は、データ警告マネージャーから開きます。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-103">You open the data alert definition that you want to edit from Data Alert Manager.</span></span> <span data-ttu-id="2d5a2-104">警告の定義は、作成したユーザーのみが編集できます。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-104">Only the user that created the alert definition can edit it.</span></span> <span data-ttu-id="2d5a2-105">詳細については、「 [データ警告マネージャーでのデータ警告の管理](manage-my-data-alerts-in-data-alert-manager.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-105">For more information about opening Data Alert Manager, see [Manage My Data Alerts in Data Alert Manager](manage-my-data-alerts-in-data-alert-manager.md).</span></span>

 <span data-ttu-id="2d5a2-106">次の図は、データ警告マネージャーでの、データ警告のショートカット メニューを示しています。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-106">The following picture shows you the context menu on a data alert in Data Alert Manager.</span></span>

 <span data-ttu-id="2d5a2-107">![[編集] をクリックしてデータ警告デザイナーを開く](media/rs-alertmanageriwopendesigner.gif "[編集] をクリックしてデータ警告デザイナーを開く")</span><span class="sxs-lookup"><span data-stu-id="2d5a2-107">![Open Data Alert Designer by clicking Edit](media/rs-alertmanageriwopendesigner.gif "Open Data Alert Designer by clicking Edit")</span></span>

 <span data-ttu-id="2d5a2-108">次の手順には、データ警告デザイナーで編集するためにデータ警告マネージャーから警告定義を開く手順が含まれます。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-108">The following procedure includes the steps to open the alert definition for editing in Data Alert Designer from Data Alert Manager.</span></span>

### <a name="to-edit-a-data-alert-definition-in-data-alert-designer"></a><span data-ttu-id="2d5a2-109">データ警告デザイナーでデータ警告定義を編集するには</span><span class="sxs-lookup"><span data-stu-id="2d5a2-109">To edit a data alert definition in Data Alert Designer</span></span>

1.  <span data-ttu-id="2d5a2-110">データ警告マネージャーで、編集するデータ警告定義を右クリックし、 **[編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-110">In Data Alert Manager, right-click the data alert definition that you want to edit and click **Edit**.</span></span>

     <span data-ttu-id="2d5a2-111">データ警告デザイナーに警告定義が表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-111">The alert definition opens in Data Alert Designer.</span></span>

2.  <span data-ttu-id="2d5a2-112">ルール、スケジュール設定、および電子メールの設定を更新します。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-112">Update the rules, schedule settings, and email settings.</span></span> <span data-ttu-id="2d5a2-113">詳細については、「 [データ警告デザイナー](../../2014/reporting-services/data-alert-designer.md) 」および「 [警告デザイナーでのデータ警告の作成](create-a-data-alert-in-data-alert-designer.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-113">For more information, see [Data Alert Designer](../../2014/reporting-services/data-alert-designer.md) and [Create a Data Alert in Data Alert Designer](create-a-data-alert-in-data-alert-designer.md).</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2d5a2-114">別のデータ フィードを選択することはできません。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-114">You cannot choose a different data feed.</span></span> <span data-ttu-id="2d5a2-115">異なるデータ フィードを使用するには、新しいデータ警告定義を作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-115">To use a different data feed, you must create a new data alert definition.</span></span>

3.  <span data-ttu-id="2d5a2-116">**[保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-116">Click **Save**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="2d5a2-117">レポートが変更され、レポートから生成されたデータ フィードが変更されている場合、警告の定義が無効になっている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-117">If the report has changed and the data feeds generated from the report have changed the alert definition might no longer be valid.</span></span> <span data-ttu-id="2d5a2-118">この状況が生じるのは、警告定義のルールで参照される列がレポートから削除された場合、列のデータ型が変更された場合、またはレポートが削除または移動された場合です。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-118">This occurs when a column that the alert definition references in its rules is deleted from the report or changes data type or the report is deleted or moved.</span></span> <span data-ttu-id="2d5a2-119">無効な警告定義は開くことはできますが、基になるレポート データ フィードの現行バージョンに基づいて有効になるまでは再保存できません。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-119">You can open an alert definition that is not valid, but you cannot resave it until it is valid based on the current version of the report data feed that it is built upon.</span></span> <span data-ttu-id="2d5a2-120">レポートからデータ フィードが生成される方法の詳細については、「[複数のレポートからのデータ フィードの生成 &#40;レポート ビルダーおよび SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d5a2-120">To learn more about how data feeds are generated from reports, see [Generating Data Feeds from Reports &#40;Report Builder and SSRS&#41;](report-builder/generating-data-feeds-from-reports-report-builder-and-ssrs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2d5a2-121">参照</span><span class="sxs-lookup"><span data-stu-id="2d5a2-121">See Also</span></span>
 <span data-ttu-id="2d5a2-122">[警告管理者がデータ警告を Reporting Services するためのデータ警告マネージャー](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span><span class="sxs-lookup"><span data-stu-id="2d5a2-122">[Data Alert Manager for Alerting Administrators](../../2014/reporting-services/data-alert-manager-for-alerting-administrators.md) [Reporting Services Data Alerts](../ssms/agent/alerts.md)</span></span>


