---
title: DQS ログ ファイルの重大度レベルの構成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
f1_keywords:
- sql12.dqs.admin.config.log.f1
helpviewer_keywords:
- severity levels
- log files,severity levels
- dqs log files,severity levels
- logging,severity levels
- configure severity levels
ms.assetid: 66ffcdec-4bf7-4dd5-a221-fd9baefeeef4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 46fb9de1fbe1e3e59b20bb2ac7afeebe19ba2da5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712410"
---
# <a name="configure-severity-levels-for-dqs-log-files"></a><span data-ttu-id="3022a-102">DQS ログ ファイルの重大度レベルの構成</span><span class="sxs-lookup"><span data-stu-id="3022a-102">Configure Severity Levels for DQS Log Files</span></span>
  <span data-ttu-id="3022a-103">このトピックでは、 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] を使用して [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)](DQS) の各種のアクティビティやモジュールの重大度レベルを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3022a-103">This topic describes how to configure severity levels for various activities and modules in [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) by using [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)].</span></span> <span data-ttu-id="3022a-104">重大度レベルとは、DQS で発生するイベントの重大度を定義したものです。</span><span class="sxs-lookup"><span data-stu-id="3022a-104">Severity levels define the intensity of events that occur in DQS.</span></span> <span data-ttu-id="3022a-105">DQS のイベントの重大度レベルは次のとおりです。ここでは、重大度が高いものから順に示しています。</span><span class="sxs-lookup"><span data-stu-id="3022a-105">DQS events have the following severity levels, in the decreasing order of severity:</span></span>  
  
-   <span data-ttu-id="3022a-106">**Fatal**: 予期しない深刻な結果を引き起こす可能性がある重大な実行時エラー。</span><span class="sxs-lookup"><span data-stu-id="3022a-106">**Fatal**: Critical runtime errors that might cause severe/unexpected results.</span></span>  
  
-   <span data-ttu-id="3022a-107">**Error**: その他の実行時エラー。</span><span class="sxs-lookup"><span data-stu-id="3022a-107">**Error**: Other runtime errors.</span></span>  
  
-   <span data-ttu-id="3022a-108">**Warn**: エラーの原因になる可能性があるイベントに関する警告。</span><span class="sxs-lookup"><span data-stu-id="3022a-108">**Warn**: Warning about events that might result in an error.</span></span>  
  
-   <span data-ttu-id="3022a-109">**Info**: エラーまたは警告以外の一般的なイベントに関する情報</span><span class="sxs-lookup"><span data-stu-id="3022a-109">**Info**: Information about general events that is not an error or a warning.</span></span> <span data-ttu-id="3022a-110">(DQS のプロセスが開始されたなど)。</span><span class="sxs-lookup"><span data-stu-id="3022a-110">For example, a DQS process has started.</span></span>  
  
-   <span data-ttu-id="3022a-111">**Debug**: イベントに関する詳細な情報。</span><span class="sxs-lookup"><span data-stu-id="3022a-111">**Debug**: Detailed (verbose) information about the event.</span></span>  
  
 <span data-ttu-id="3022a-112">DQS の各種のアクティビティやモジュールの重大度レベルを構成することで、DQS の対応するアクティビティやモジュールについて、DQS ログ ファイルに書き込む情報をフィルター処理できます。</span><span class="sxs-lookup"><span data-stu-id="3022a-112">By configuring severity levels for various DQS activities and modules, you are filtering the information that you want to be logged, and written to the DQS log file for the respective DQS activity or module.</span></span> <span data-ttu-id="3022a-113">たとえば、DQS のアクティビティの重大度レベルを **Warn**に設定すると、DQS のアクティビティに関連するメッセージのうち、警告メッセージとそれよりも重大度が高いメッセージ (Error と Fatal) だけがログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="3022a-113">For example, if you set the severity level of a DQS activity to **Warn**, only warning and higher severity messages (Error and Fatal) associated with the DQS activity will be logged.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="3022a-114">はじめに</span><span class="sxs-lookup"><span data-stu-id="3022a-114">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="3022a-115">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="3022a-115">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="3022a-116">Permissions</span><span class="sxs-lookup"><span data-stu-id="3022a-116">Permissions</span></span>  
 <span data-ttu-id="3022a-117">ログの重大度設定を構成するには、DQS_MAIN データベースの dqs_administrator ロールが必要です。</span><span class="sxs-lookup"><span data-stu-id="3022a-117">You must have the dqs_administrator role on the DQS_MAIN database to configure log severity settings.</span></span>  
  
##  <a name="configure-severity-levels-at-activity-level"></a><a name="ConfigureActivity"></a><span data-ttu-id="3022a-118">アクティビティレベルでの重大度レベルの構成</span><span class="sxs-lookup"><span data-stu-id="3022a-118">Configure Severity Levels at Activity Level</span></span>  
 <span data-ttu-id="3022a-119">DQS のドメイン管理、ナレッジ検出、照合ポリシー、データ クレンジング、データ照合、および参照データ サービスの各アクティビティについて、ログの重大度設定を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="3022a-119">You can configure log severity settings for the following activities in DQS: domain management, knowledge discovery, matching policy, data cleansing, data matching, and reference data services.</span></span> <span data-ttu-id="3022a-120">そのためには、次の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="3022a-120">To do so:</span></span>  
  
1.  [!INCLUDE[ssDQSInitialStep](../includes/ssdqsinitialstep-md.md)]<span data-ttu-id="3022a-121">[Data Quality Client アプリケーションを実行](../../2014/data-quality-services/run-the-data-quality-client-application.md)します。</span><span class="sxs-lookup"><span data-stu-id="3022a-121">[Run the Data Quality Client Application](../../2014/data-quality-services/run-the-data-quality-client-application.md).</span></span>  
  
2.  <span data-ttu-id="3022a-122">[!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] のホーム画面で **[構成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3022a-122">In the [!INCLUDE[ssDQSClient](../includes/ssdqsclient-md.md)] home screen, click **Configuration**.</span></span>  
  
3.  <span data-ttu-id="3022a-123">次に、[**ログの設定**] タブをクリックします。重大度レベルを選択できる DQS アクティビティが一覧表示されます。**ドメイン管理**、**ナレッジ検出**、**クレンジングプロジェクト (RDS)**、**照合ポリシーと照合プロジェクト**、および**RDS**。</span><span class="sxs-lookup"><span data-stu-id="3022a-123">Next, click the **Log Settings** tab. The following DQS activities are listed for which you can select a severity level: **Domain Management**, **Knowledge Discovery**, **Cleansing Project (Ex. RDS)**, **Matching Policy and Matching Project**, and **RDS**.</span></span>  
  
4.  <span data-ttu-id="3022a-124">DQS のアクティビティについて、ログに記録する重大度レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3022a-124">For a DQS activity, select the severity level that you want to be logged.</span></span> <span data-ttu-id="3022a-125">**[Fatal]**、 **[Error]**、 **[Warn]**、 **[Info]**、および **[Debug]** のいずれかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="3022a-125">You can select one among the following: **Fatal**, **Error**, **Warn**, **Info**, and **Debug**.</span></span> <span data-ttu-id="3022a-126">たとえば、ナレッジ検出アクティビティに対する重大なメッセージだけを DQS ログ ファイルに書き込む場合は、 **[ナレッジ検出]** アクティビティのドロップダウン リストで **[Fatal]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="3022a-126">For example, if you want only fatal messages to be written to the DQS log files for the knowledge discovery activity, select **Fatal** in the drop-down list against the **Knowledge Discovery** activity.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3022a-127">既定では、各アクティビティについて **[Error]** が選択されています。</span><span class="sxs-lookup"><span data-stu-id="3022a-127">By default, **Error** is selected for each of the activities.</span></span> <span data-ttu-id="3022a-128">つまり、既定では、各アクティビティのエラー メッセージと重大なメッセージが DQS ログ ファイルに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="3022a-128">This implies that error and fatal messages will be written to the DQS log files for each activity, by default.</span></span>  
  
5.  <span data-ttu-id="3022a-129">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3022a-129">Click **Close**.</span></span>  
  
##  <a name="configure-severity-levels-at-module-level-advanced"></a><a name="ConfigureModule"></a><span data-ttu-id="3022a-130">モジュールレベルでの重大度レベルの構成 (詳細)</span><span class="sxs-lookup"><span data-stu-id="3022a-130">Configure Severity Levels at Module Level (Advanced)</span></span>  
 <span data-ttu-id="3022a-131">**[ログの設定]** タブの **[詳細設定]** セクションでは、モジュール レベルでログの重大度設定を構成することができます。</span><span class="sxs-lookup"><span data-stu-id="3022a-131">The **Advanced** section in the **Log Settings** tab enables you to configure log severity settings at a module level.</span></span> <span data-ttu-id="3022a-132">モジュールとは、DQS の機能に含まれる個々の機能を実装する DQS システムのアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="3022a-132">Modules are DQS system assemblies that implement various functionalities within a feature in DQS.</span></span> <span data-ttu-id="3022a-133">たとえば、ドメイン管理アクティビティには、ドメイン ルールの定義、ルールの条件の定義、複合ドメインのクロス ドメイン ルールの定義など、さまざまな機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="3022a-133">For example, the domain management activity contains various functionalities such as defining domain rules, defining rule conditions, defining cross-domain rules for composite domains, and so on.</span></span>  
  
 <span data-ttu-id="3022a-134">アクティビティ レベルよりも詳しい調査が必要なときは、</span><span class="sxs-lookup"><span data-stu-id="3022a-134">At times, the granularity level at the activity level is not sufficient.</span></span> <span data-ttu-id="3022a-135">アクティビティ内の特定のモジュールで発生している問題を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="3022a-135">You might want to investigate an issue that is occurring in a particular module within an activity.</span></span> <span data-ttu-id="3022a-136">モジュール レベルでログの重大度を構成することで、問題をより正確に切り分けて追跡することができます。</span><span class="sxs-lookup"><span data-stu-id="3022a-136">It helps to have an option to configure log severities at the module level to isolate and track the issue more precisely.</span></span>  
  
 <span data-ttu-id="3022a-137">アクティビティ レベルで指定したログの重大度設定によって、そのアクティビティを構成するすべてのモジュールのログの重大度設定が決まります。</span><span class="sxs-lookup"><span data-stu-id="3022a-137">The log severity setting specified at the activity level determines the log severity setting of all the modules that constitute the activity.</span></span> <span data-ttu-id="3022a-138">ただし、アクティビティ レベルとモジュール レベルでログの重大度設定が異なる場合は、モジュール レベルの重大度設定が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3022a-138">However, if there is any conflict between the log severity settings at the activity and module levels, the severity settings at the module level are considered.</span></span>  
  
> [!NOTE]
>  -   <span data-ttu-id="3022a-139">既定では、 **[詳細設定]** セクションで **Microsoft.Ssdqs.Core.Startup** モジュールが事前に構成されており、重大度レベルは **[Info]** に設定されています。</span><span class="sxs-lookup"><span data-stu-id="3022a-139">By default, the **Microsoft.Ssdqs.Core.Startup** module is preconfigured in the **Advanced** section with the severity level set as **Info**.</span></span> <span data-ttu-id="3022a-140">この設定により、DQS のサービスの開始と終了に関するイベントのうち、重大度が Info のイベントとそれよりも重大度が高いイベント (Warn、Error、および Fatal) がログに記録されます。</span><span class="sxs-lookup"><span data-stu-id="3022a-140">This is done to enable logging of events of severity Info and higher (Warn, Error, and Fatal) that are related to starting and stopping of DQS services.</span></span>  
> -   <span data-ttu-id="3022a-141">モジュール レベルでのログの重大度レベルの構成は、DQS システムのアセンブリについて理解している DQS の上級ユーザー以外にはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="3022a-141">You should configure log severity levels at the module level only if you are an advanced DQS user who is familiar with the DQS system assemblies.</span></span>  
  
 <span data-ttu-id="3022a-142">モジュール レベルでログの重大度レベルを構成するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="3022a-142">To configure log severity levels at the module level:</span></span>  
  
1.  <span data-ttu-id="3022a-143">**[ログの設定]** タブで、 **[詳細設定]** の下矢印をクリックして領域を表示します。</span><span class="sxs-lookup"><span data-stu-id="3022a-143">In the **Log Settings** tab, click the down arrow against **Advanced** to display the area.</span></span>  
  
2.  <span data-ttu-id="3022a-144">表示されたグリッドで、 **[モジュール]** 列のドロップダウン リストからモジュール名を選択します。</span><span class="sxs-lookup"><span data-stu-id="3022a-144">In the grid that appears, select a module name from the drop-down list in the **Module** column.</span></span>  
  
3.  <span data-ttu-id="3022a-145">次に、 **[重大度]** 列のドロップダウン リストからモジュールの重大度レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3022a-145">Next, select a severity level for the module from the drop-down list in the **Severity** column.</span></span> <span data-ttu-id="3022a-146">**[Fatal]**、 **[Error]**、 **[Warn]**、 **[Info]**、および **[Debug]** のいずれかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="3022a-146">You can select one among the following: **Fatal**, **Error**, **Warn**, **Info**, and **Debug**.</span></span>  
  
     <span data-ttu-id="3022a-147">たとえば、ドメイン管理アクティビティに含まれるドメイン ルールの定義機能に対してドメイン管理アクティビティとは異なる粒度を設定するには、 **[Microsoft.Ssdqs.DomainRules.Define]** モジュールを選択し、別の重大度レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3022a-147">For example, within the domain management activity, you can set a different granularity level for the domain rule definition functionality than the domain management activity by selecting the **Microsoft.Ssdqs.DomainRules.Define** module, and selecting a different log severity level.</span></span> <span data-ttu-id="3022a-148">同様に、クロス ドメイン ルール機能に対して異なる粒度を設定するには、 **[Microsoft.Ssdqs.DomainRules.Condition.CrossDomain]** モジュールを選択し、別の重大度レベルを選択します。</span><span class="sxs-lookup"><span data-stu-id="3022a-148">Similarly, you can set a different granularity level for the cross-domain rule functionality by selecting the **Microsoft.Ssdqs.DomainRules.Condition.CrossDomain** module, and selecting a different log severity level.</span></span>  
  
4.  <span data-ttu-id="3022a-149">必要に応じて、他のモジュールに対して手順 2. および 3. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="3022a-149">Repeat steps 2 and 3 for other modules, if required.</span></span> <span data-ttu-id="3022a-150">**[モジュールを追加します]** アイコンと **[モジュールを削除します]** アイコンをクリックして、グリッドの行を追加したり削除したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="3022a-150">You can also add or delete rows to the grid by clicking the **Add Module** and **Remove Module** icons.</span></span>  
  
5.  <span data-ttu-id="3022a-151">**[閉じる]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3022a-151">Click **Close**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3022a-152">参照</span><span class="sxs-lookup"><span data-stu-id="3022a-152">See Also</span></span>  
 [<span data-ttu-id="3022a-153">DQS ログ ファイルの詳細設定の構成</span><span class="sxs-lookup"><span data-stu-id="3022a-153">Configure Advanced Settings for DQS Log Files</span></span>](../../2014/data-quality-services/configure-advanced-settings-for-dqs-log-files.md)  
  
  
