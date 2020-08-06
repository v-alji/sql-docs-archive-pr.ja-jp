---
title: レポートとサブスクリプションの処理を一時停止する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- pausing schedules
- subscriptions [Reporting Services], pausing
- report processing [Reporting Services], pausing
- shared data sources [Reporting Services]
- pausing subscription processing
- pausing report processing
- temporarily stopping report processing
- disabling shared data sources
- roles [Reporting Services], modifying
- shared schedules [Reporting Services], pausing
ms.assetid: 3cf9a240-24cc-46d4-bec6-976f82d8f830
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1607637630c507588602dd7e566917ce1eeb6080
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87721051"
---
# <a name="pause-report-and-subscription-processing"></a><span data-ttu-id="f165f-102">レポートとサブスクリプションの処理を一時停止する</span><span class="sxs-lookup"><span data-stu-id="f165f-102">Pause Report and Subscription Processing</span></span>
  <span data-ttu-id="f165f-103">レポートまたはサブスクリプションを直接一時停止することはできません。</span><span class="sxs-lookup"><span data-stu-id="f165f-103">You cannot pause a report or subscription directly.</span></span> <span data-ttu-id="f165f-104">ただし、処理の開始前、またはデータ ソースへの接続時に、レポートおよびサブスクリプションの処理を中断できます。</span><span class="sxs-lookup"><span data-stu-id="f165f-104">However, you can interrupt report and subscription processing prior to the process starting or when a data source connection is made.</span></span> <span data-ttu-id="f165f-105">また、レポートやサブスクリプションにユーザーがアクセスできないようにして、レポートやサブスクリプションが処理されないようにすることもできます。</span><span class="sxs-lookup"><span data-stu-id="f165f-105">You can also prevent a report or subscription from processing by making it inaccessible to users.</span></span>  
  
 <span data-ttu-id="f165f-106">以下の操作は、一時的な処理の中断に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f165f-106">The following strategies can be used to temporarily prevent a process from occurring.</span></span>  
  
## <a name="modify-role-assignments-to-prevent-access"></a><span data-ttu-id="f165f-107">アクセス防止のためのロールの割り当ての変更</span><span class="sxs-lookup"><span data-stu-id="f165f-107">Modify Role Assignments to Prevent Access</span></span>  
 <span data-ttu-id="f165f-108">レポートを使用できないようにする最善の方法は、レポートにアクセスするためのロールの割り当てを一時的に削除することです。</span><span class="sxs-lookup"><span data-stu-id="f165f-108">The best way to make a report unavailable is to temporarily remove the role assignment that provides access to the report.</span></span> <span data-ttu-id="f165f-109">この方法は、データ ソースへの接続方法に関係なくすべてのレポートに使用できます。</span><span class="sxs-lookup"><span data-stu-id="f165f-109">This approach can be used on all reports regardless of how the data source connection is made.</span></span> <span data-ttu-id="f165f-110">この方法は、ロールの割り当てを一時的に削除したレポートのみに有効で、他のレポートやアイテムの操作には影響しません。</span><span class="sxs-lookup"><span data-stu-id="f165f-110">This approach targets only the report, without affecting the operation of other reports or items.</span></span>  
  
 <span data-ttu-id="f165f-111">ロールの割り当てを削除するには、レポート マネージャーでレポートの [セキュリティ] プロパティ ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="f165f-111">To remove the role assignment, open the Security Properties page of the report in Report Manager.</span></span> <span data-ttu-id="f165f-112">そのレポートが親レポートからセキュリティを継承している場合は、 **[アイテムのセキュリティを編集]** をクリックして、広範囲なアクセスを提供するロールの割り当てを削除する、制限付きのセキュリティ ポリシーを作成できます。たとえば、Everyone にアクセスを提供するロールの割り当てを削除し、Administrators など小さなユーザー グループにアクセスを提供するロールの割り当てを保持できます。</span><span class="sxs-lookup"><span data-stu-id="f165f-112">If the report inherits security from a parent, you can click **Edit Item Security** to create a restrictive security policy that omits role assignments that provide widespread access (for example, you can remove a role assignment that provides access to Everyone, and keep the role assignment that provides access to a small group of users, such as Administrators).</span></span>  
  
## <a name="disable-a-shared-data-source"></a><span data-ttu-id="f165f-113">共有データソースを無効にする</span><span class="sxs-lookup"><span data-stu-id="f165f-113">Disable a Shared Data Source</span></span>  
 <span data-ttu-id="f165f-114">共有データ ソースを使用する利点の 1 つは、共有データ ソースを無効にして、レポートまたはデータ ドリブン サブスクリプションの実行を中止できることです。</span><span class="sxs-lookup"><span data-stu-id="f165f-114">One advantage to using shared data sources is that you can disable it to prevent a report or data-driven subscription from running.</span></span> <span data-ttu-id="f165f-115">共有データ ソースを無効にすると、レポートは外部ソースから切断されます。</span><span class="sxs-lookup"><span data-stu-id="f165f-115">Disabling a shared data source disconnects the report from its external source.</span></span> <span data-ttu-id="f165f-116">共有データ ソースが無効な間は、すべてのレポートと共有データ ソースを使用するサブスクリプションで共有データ ソースを使用できません。</span><span class="sxs-lookup"><span data-stu-id="f165f-116">While it is disabled, the data source is unavailable to all reports and subscriptions that use it.</span></span> <span data-ttu-id="f165f-117">共有データソースを無効にするには、レポートマネージャーでデータソースを開き、[**このデータソースを有効に**する] チェックボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="f165f-117">To disable a shared data source, open the data source in Report Manager and clear the **Enable this data source** check box.</span></span>  
  
 <span data-ttu-id="f165f-118">データ ソースが使用できない場合でも、レポートは読み込まれることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="f165f-118">Note that the report still loads even if the data source is unavailable.</span></span> <span data-ttu-id="f165f-119">レポートにはデータは含まれていませんが、適切な権限を持ったユーザーは、レポートに関連付けられたプロパティ ページ、セキュリティ設定、レポート履歴、およびサブスクリプション情報にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f165f-119">The report does not contain data, but users with appropriate permissions can access the property pages, security settings, report history, and subscription information associated with the report.</span></span>  
  
## <a name="pause-a-shared-schedule"></a><span data-ttu-id="f165f-120">共有スケジュールの一時停止</span><span class="sxs-lookup"><span data-stu-id="f165f-120">Pause a Shared Schedule</span></span>  
 <span data-ttu-id="f165f-121">レポートまたはサブスクリプションが共有スケジュールから実行される場合、スケジュールを一時停止して処理を中止できます。</span><span class="sxs-lookup"><span data-stu-id="f165f-121">If a report or subscription runs from a shared schedule, you can pause the schedule to prevent processing.</span></span> <span data-ttu-id="f165f-122">スケジュールによって駆動されるすべてのレポートおよびサブスクリプションの処理は、スケジュールが再開されるまで延期されます。</span><span class="sxs-lookup"><span data-stu-id="f165f-122">All report and subscription processing that is driven by the schedule is deferred until the schedule is resumed.</span></span> <span data-ttu-id="f165f-123">詳細については、「[共有スケジュールの一時停止と再開](schedules.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f165f-123">For more information, see [Pause and Resume Shared Schedules](schedules.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f165f-124">参照</span><span class="sxs-lookup"><span data-stu-id="f165f-124">See Also</span></span>  
 <span data-ttu-id="f165f-125">[Reporting Services レポート サーバー (ネイティブ モード)](../report-server/reporting-services-report-server-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f165f-125">[Reporting Services Report Server &#40;Native Mode&#41;](../report-server/reporting-services-report-server-native-mode.md) </span></span>  
 <span data-ttu-id="f165f-126">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="f165f-126">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="f165f-127">[[セキュリティのプロパティ] ページ、アイテム (レポート マネージャー)](../security-properties-page-items-report-manager.md)</span><span class="sxs-lookup"><span data-stu-id="f165f-127">[Security Properties Page, Items &#40;Report Manager&#41;](../security-properties-page-items-report-manager.md)</span></span>  
  
  
