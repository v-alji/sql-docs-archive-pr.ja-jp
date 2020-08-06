---
title: データフローパフォーマンスカウンターのログの追加 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- performance counters [Integration Services]
- counters [Integration Services]
- logs [Integration Services], data flow counters
ms.assetid: b500d166-33ba-4b82-a92d-b0a333924e8d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 489bde1b0e5769f05d1063eb0af2376b659574de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87736678"
---
# <a name="add-a-log-for-data-flow-performance-counters"></a><span data-ttu-id="a4364-102">データ フロー パフォーマンス カウンターのログを追加する</span><span class="sxs-lookup"><span data-stu-id="a4364-102">Add a Log for Data Flow Performance Counters</span></span>
  <span data-ttu-id="a4364-103">この手順では、データ フロー エンジンによって提供されるパフォーマンス カウンターのログを追加する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a4364-103">This procedure describes how to add a log for the performance counters that the data flow engine provides.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4364-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] を実行するコンピューターに [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)]をインストールした後、コンピューターを [!INCLUDE[firstref_longhorn](../includes/firstref-longhorn-md.md)]にアップグレードすると、アップグレード プロセスにより [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のパフォーマンス カウンターがコンピューターから削除されます。</span><span class="sxs-lookup"><span data-stu-id="a4364-104">If you install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] on a computer that is running [!INCLUDE[winxpsvr](../includes/winxpsvr-md.md)], and then upgrade that computer to [!INCLUDE[firstref_longhorn](../includes/firstref-longhorn-md.md)], the upgrade process removes the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] performance counters from the computer.</span></span> <span data-ttu-id="a4364-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のパフォーマンス カウンターをコンピューターに復元するには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のセットアップを修復モードで実行してください。</span><span class="sxs-lookup"><span data-stu-id="a4364-105">To restore the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] performance counters on the computer, run [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Setup in repair mode.</span></span>  
  
### <a name="to-add-logging-of-performance-counters"></a><span data-ttu-id="a4364-106">パフォーマンス カウンターのログを追加するには</span><span class="sxs-lookup"><span data-stu-id="a4364-106">To add logging of performance counters</span></span>  
  
1.  <span data-ttu-id="a4364-107">**[コントロール パネル]** で、クラシック表示を使用している場合は **[管理ツール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4364-107">In **Control Panel**, if you are using Classic view, click **Administrative Tools**.</span></span> <span data-ttu-id="a4364-108">カテゴリ表示を使用している場合は、 **[パフォーマンスとメンテナンス]** をクリックしてから **[管理ツール]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4364-108">If you are using Category view, click **Performance and Maintenance** and then click **Administrative Tools**.</span></span>  
  
2.  <span data-ttu-id="a4364-109">**[パフォーマンス]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4364-109">Click **Performance**.</span></span>  
  
3.  <span data-ttu-id="a4364-110">**[パフォーマンス]** ダイアログ ボックスで、 **[パフォーマンス ログと警告]** を展開して、 **[カウンター ログ]** を右クリックし、 **[新しいログの設定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4364-110">In the **Performance** dialog box, expand **Performance Logs and Alerts**, right-click **Counter Logs**, and then click **New Log Settings**.</span></span> <span data-ttu-id="a4364-111">ログの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="a4364-111">Type the name of the log.</span></span> <span data-ttu-id="a4364-112">たとえば、「 **MyLog**」のように入力します。</span><span class="sxs-lookup"><span data-stu-id="a4364-112">For example, type **MyLog**.</span></span>  
  
4.  <span data-ttu-id="a4364-113">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4364-113">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="a4364-114">**[MyLog]** ダイアログ ボックスで、 **[カウンターの追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4364-114">In the **MyLog** dialog box, click **Add Counters**.</span></span>  
  
6.  <span data-ttu-id="a4364-115">ローカル コンピューターのパフォーマンス カウンターを記録するには、 **[ローカル コンピューターのカウンターを使う]** をオンにします。指定したコンピューターのパフォーマンス カウンターを記録するには、 **[次のコンピューターからカウンターを選ぶ]** をオンにし、一覧からコンピューターを選択します。</span><span class="sxs-lookup"><span data-stu-id="a4364-115">Click **Use local computer counters** to log performance counters on the local computer, or click **Select counters from computer** and then select a computer from the list to log performance counters on the specified computer.</span></span>  
  
7.  <span data-ttu-id="a4364-116">**[カウンターの追加]** ダイアログ ボックスで、 **[パフォーマンス オブジェクト]** 一覧の **[SQL Server:SSIS Pipeline]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4364-116">In the **Add Counters** dialog box, select **SQL Server:SSIS Pipeline** in the **Performance object** list.</span></span>  
  
8.  <span data-ttu-id="a4364-117">パフォーマンス カウンターを選択するには、次のいずれかの操作を行います。</span><span class="sxs-lookup"><span data-stu-id="a4364-117">To select performance counters, do one of the following:</span></span>  
  
    -   <span data-ttu-id="a4364-118">すべてのパフォーマンス カウンターを記録する場合は、 **[すべてのカウンター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4364-118">Select **All Counters** to log all performance counters.</span></span>  
  
    -   <span data-ttu-id="a4364-119">**[一覧からカウンターを選ぶ]** をオンにし、使用するパフォーマンス カウンターを選択します。</span><span class="sxs-lookup"><span data-stu-id="a4364-119">Select **Select counters in list** and select the performance counters to use.</span></span>  
  
9. <span data-ttu-id="a4364-120">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4364-120">Click **Add**.</span></span>  
  
10. <span data-ttu-id="a4364-121">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4364-121">Click **Close**.</span></span>  
  
11. <span data-ttu-id="a4364-122">**[MyLog]** ダイアログ ボックスの **[カウンター]** 一覧で、ログ パフォーマンス カウンターの一覧を確認します。</span><span class="sxs-lookup"><span data-stu-id="a4364-122">In the **MyLog** dialog box, review the list of logging performance counters in the **Counters** list.</span></span>  
  
12. <span data-ttu-id="a4364-123">カウンターを追加するには、手順 5. ～ 10. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="a4364-123">To add additional counters, repeat steps 5 through 10.</span></span>  
  
13. <span data-ttu-id="a4364-124">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a4364-124">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a4364-125">[パフォーマンス ログと警告] サービスは、Administrators グループのメンバーであるローカル アカウントまたはドメイン アカウントを使用して起動する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4364-125">You must start the Performance Logs and Alerts service using a local account or a domain account that is a member of the Administrators group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4364-126">参照</span><span class="sxs-lookup"><span data-stu-id="a4364-126">See Also</span></span>  
 <span data-ttu-id="a4364-127">[パフォーマンスカウンター](performance/performance-counters.md) </span><span class="sxs-lookup"><span data-stu-id="a4364-127">[Performance Counters](performance/performance-counters.md) </span></span>  
 <span data-ttu-id="a4364-128">[[ログ イベント] ウィンドウでログ エントリを表示する](../../2014/integration-services/view-log-entries-in-the-log-events-window.md)</span><span class="sxs-lookup"><span data-stu-id="a4364-128">[View Log Entries in the Log Events Window](../../2014/integration-services/view-log-entries-in-the-log-events-window.md)</span></span>  
  
  
