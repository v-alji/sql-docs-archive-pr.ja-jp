---
title: キャッシュ更新オプション (レポートマネージャー) |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 227da40c-6bd2-48ec-aa9c-50ce6c1ca3a6
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 83b2ef4396c774f3ac344704756cd1c7e90d4e04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640775"
---
# <a name="cache-refresh-options-report-manager"></a><span data-ttu-id="52393-102">キャッシュ更新オプション (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="52393-102">Cache Refresh Options (Report Manager)</span></span>
  <span data-ttu-id="52393-103">[キャッシュ更新オプション] ページでは、レポートまたは共有データセットのデータの一時コピーを事前にキャッシュに読み込むスケジュールを作成できます。</span><span class="sxs-lookup"><span data-stu-id="52393-103">Use the Cache Refresh options page to create schedules for preloading the cache with temporary copies of data for a report or for a shared dataset.</span></span> <span data-ttu-id="52393-104">更新計画には、スケジュールと、パラメーターの値を指定またはオーバーライドするためのオプションが含まれます。</span><span class="sxs-lookup"><span data-stu-id="52393-104">A refresh plan includes a schedule and the option to specify or override values for parameters.</span></span> <span data-ttu-id="52393-105">共有データセットの場合、読み取り専用にマークされているパラメーターの値をオーバーライドすることはできません。</span><span class="sxs-lookup"><span data-stu-id="52393-105">For a shared dataset, you cannot override values for parameters that are marked read-only.</span></span> <span data-ttu-id="52393-106">更新オプション ページの一部として複数の更新計画を作成して使用できます。</span><span class="sxs-lookup"><span data-stu-id="52393-106">You can create and use more than one refresh plan as part of the refresh options page.</span></span>  
  
 <span data-ttu-id="52393-107">キャッシュ更新計画の関連レポートや共有データセットの追加、削除、変更、および表示が可能な既定のロールの割り当ては、コンテンツ マネージャー、個人用レポート、およびパブリッシャーです。</span><span class="sxs-lookup"><span data-stu-id="52393-107">Default role assignments that enable you to add, delete, change, and view related reports and shared datasets for cache refresh plans are Content Manager, My Reports, and Publisher.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="52393-108">この機能は、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]のすべてのエディションで使用できるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="52393-108">This feature is not available in every edition of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="52393-109">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52393-109">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="to-open-the-cache-refresh-plan-properties-page-for-a-report-or-shared-dataset"></a><span data-ttu-id="52393-110">レポートまたは共有データセットの [キャッシュ更新計画] プロパティ ページを開くには</span><span class="sxs-lookup"><span data-stu-id="52393-110">To open the Cache Refresh Plan properties page for a report or shared dataset</span></span>  
  
1.  <span data-ttu-id="52393-111">レポート マネージャーを開き、キャッシュ更新計画のプロパティを構成するレポートまたは共有データセットを探します。</span><span class="sxs-lookup"><span data-stu-id="52393-111">Open Report Manager, and locate the report or shared dataset for which you want to configure cache refresh plan properties.</span></span>  
  
2.  <span data-ttu-id="52393-112">レポートまたは共有データセットの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52393-112">Hover over the report or shared dataset, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="52393-113">ドロップダウン リストの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52393-113">In the drop-down list, click **Manage**.</span></span> <span data-ttu-id="52393-114">**[全般プロパティ**] ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="52393-114">The **General properties** page opens.</span></span>  
  
4.  <span data-ttu-id="52393-115">**[キャッシュ更新計画]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="52393-115">Click the **Cache Refresh Plan** tab.</span></span>  
  
5.  <span data-ttu-id="52393-116">新しいキャッシュ計画を作成するには、 **[新しいキャッシュ更新計画]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52393-116">To create a new cache plan, click **New Cache Refresh Plan**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="52393-117">キャッシュ更新計画を作成するには、SQL Server エージェント サービスを有効化し、開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52393-117">You must enable and start the SQL Server Agent service to create a cache refresh plan.</span></span>  
  
6.  <span data-ttu-id="52393-118">キャッシュ計画のコピーを作成してカスタマイズするには、 **[既存のものから新規作成]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52393-118">To create a copy of a cache plan and then customize it, click **New from Existing**.</span></span>  
  
## <a name="cache-refresh-options"></a><span data-ttu-id="52393-119">キャッシュ更新オプション</span><span class="sxs-lookup"><span data-stu-id="52393-119">Cache Refresh Options</span></span>  
 <span data-ttu-id="52393-120">**削除**</span><span class="sxs-lookup"><span data-stu-id="52393-120">**Delete**</span></span>  
 <span data-ttu-id="52393-121">現在選択しているすべての更新計画を削除します。</span><span class="sxs-lookup"><span data-stu-id="52393-121">Deletes all of the currently selected refresh plans.</span></span>  
  
 <span data-ttu-id="52393-122">**[既存のものから新規作成]**</span><span class="sxs-lookup"><span data-stu-id="52393-122">**New from existing**</span></span>  
 <span data-ttu-id="52393-123">このオプションは、キャッシュ更新計画が 1 つだけ選択されている場合に有効になります。</span><span class="sxs-lookup"><span data-stu-id="52393-123">This option is enabled when one and only one cache refresh plan is selected.</span></span> <span data-ttu-id="52393-124">このオプションでは、新しい更新計画が元の計画からコピーされて作成されます。</span><span class="sxs-lookup"><span data-stu-id="52393-124">This option will create a new refresh plan which is copied from the original plan.</span></span> <span data-ttu-id="52393-125">キャッシュ更新計画ページは、選択された計画の詳細があらかじめ設定された状態で開きます。</span><span class="sxs-lookup"><span data-stu-id="52393-125">The cache refresh plan page opens pre-populated with details from the plan that was selected.</span></span> <span data-ttu-id="52393-126">その後、更新計画オプションを変更して、新しい説明で計画を保存できます。</span><span class="sxs-lookup"><span data-stu-id="52393-126">You can then modify the refresh plan options and save the plan with a new description.</span></span>  
  
 <span data-ttu-id="52393-127">**[新しいキャッシュ更新計画]**</span><span class="sxs-lookup"><span data-stu-id="52393-127">**New cache refresh plan**</span></span>  
 <span data-ttu-id="52393-128">現在のキャッシュ更新オプションで使用する、新しい更新計画を作成する場合にクリックします。</span><span class="sxs-lookup"><span data-stu-id="52393-128">Click to create a new refresh plan to be used in the current cache refresh options.</span></span>  
  
 <span data-ttu-id="52393-129">**[編集]**</span><span class="sxs-lookup"><span data-stu-id="52393-129">**Edit**</span></span>  
 <span data-ttu-id="52393-130">現在の更新計画を編集するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="52393-130">Select this option to edit the current refresh plan.</span></span>  
  
## <a name="cache-refresh-plan-options"></a><span data-ttu-id="52393-131">キャッシュ更新計画オプション</span><span class="sxs-lookup"><span data-stu-id="52393-131">Cache Refresh Plan Options</span></span>  
 <span data-ttu-id="52393-132">**説明**</span><span class="sxs-lookup"><span data-stu-id="52393-132">**Description**</span></span>  
 <span data-ttu-id="52393-133">キャッシュ更新計画の説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="52393-133">Specify a description for the cache refresh plan.</span></span>  
  
 <span data-ttu-id="52393-134">**[アイテム固有のスケジュール]**</span><span class="sxs-lookup"><span data-stu-id="52393-134">**Item-specific schedule**</span></span>  
 <span data-ttu-id="52393-135">このアイテムでのみ使用されるスケジュールを作成する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="52393-135">Select this option to create a schedule that is used only by this item.</span></span>  
  
 <span data-ttu-id="52393-136">**構成**</span><span class="sxs-lookup"><span data-stu-id="52393-136">**Configure**</span></span>  
 <span data-ttu-id="52393-137">クリックすると、[スケジュール] ページが開きます。このページは、頻度に関する情報の指定に使用します。</span><span class="sxs-lookup"><span data-stu-id="52393-137">Click to open the Schedule page, which is used to specify frequency information.</span></span>  
  
 <span data-ttu-id="52393-138">詳細については、「[新しいスケジュール: スケジュールの編集ページ &#40;レポートマネージャー&#41;](../../2014/reporting-services/new-schedule-edit-schedule-page-report-manager.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52393-138">For more information, see [New Schedule: Edit Schedule Page &#40;Report Manager&#41;](../../2014/reporting-services/new-schedule-edit-schedule-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="52393-139">**共有スケジュール**</span><span class="sxs-lookup"><span data-stu-id="52393-139">**Shared schedule**</span></span>  
 <span data-ttu-id="52393-140">既存のスケジュールを選択するには、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="52393-140">Select this option to select an existing schedule.</span></span>  
  
 <span data-ttu-id="52393-141">詳細については、「 [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="52393-141">For more information, see [Create, Modify, and Delete Schedules](subscriptions/create-modify-and-delete-schedules.md).</span></span>  
  
 **@\<** *Parameter* **>**  
 <span data-ttu-id="52393-142">パラメーター値の 1 つの組み合わせを指定します。</span><span class="sxs-lookup"><span data-stu-id="52393-142">Specify one combination of parameter values.</span></span> <span data-ttu-id="52393-143">このセクションは、現在のデータセットまたはレポートでパラメーターが使用されている場合にのみ表示されます。</span><span class="sxs-lookup"><span data-stu-id="52393-143">This section appears only if the current dataset or report has parameters.</span></span>  
  
 <span data-ttu-id="52393-144">次のセクションの「 [パラメーターの指定](#Parameters) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52393-144">See [Specifying Parameters](#Parameters) in the next section.</span></span>  
  
 <span data-ttu-id="52393-145">**既定値を使用**</span><span class="sxs-lookup"><span data-stu-id="52393-145">**Use Default**</span></span>  
 <span data-ttu-id="52393-146">このパラメーターに事前定義済みの既定値を使用する場合は、このオプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="52393-146">Select this option to use the predefined default value for this parameter.</span></span>  
  
##  <a name="specifying-parameters"></a><a name="Parameters"></a><span data-ttu-id="52393-147">パラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="52393-147">Specifying Parameters</span></span>  
 <span data-ttu-id="52393-148">キャッシュ更新計画を作成するには、各レポートまたは共有データセットのパラメーターに値が指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="52393-148">To create a cache refresh plan, each report or shared dataset parameter must have a value.</span></span> <span data-ttu-id="52393-149">レポートまたは共有データセット アイテムの定義に既定値が指定されていない場合は、ユーザーが値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52393-149">If the report or shared dataset item does not have a default value specified in the definition, you must specify a value.</span></span> <span data-ttu-id="52393-150">既定値が指定されている場合は、この手順で値を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="52393-150">If a default value exists, you do not need to provide one here.</span></span> <span data-ttu-id="52393-151">値を指定すると、既定値はオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="52393-151">If you do provide a value, the value overrides the default value.</span></span>  
  
 <span data-ttu-id="52393-152">パラメーター値の複数の組み合わせを指定する場合は、各組み合わせに対して個別のキャッシュ更新計画を作成します。</span><span class="sxs-lookup"><span data-stu-id="52393-152">To specify multiple combinations of parameter values, create a separate cache refresh plan for each combination.</span></span>  
  
 <span data-ttu-id="52393-153">レポートまたは共有データセットのパラメーターで行われる追加、変更、および削除は、キャッシュ更新計画に影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="52393-153">Additions, changes, and deletions made to parameters on a report or shared dataset can affect the cache refresh plan.</span></span> <span data-ttu-id="52393-154">レポートで既定値のパラメーターを追加したり、パラメーターを削除したり、共有データセット パラメーターのデータ型や読み取り専用オプションを変更したりすると、変更はキャッシュ更新計画が次回処理されるときに有効になります。</span><span class="sxs-lookup"><span data-stu-id="52393-154">If you add a parameter with a default value for a report, remove a parameter, or change the data type or the read-only option for a shared dataset parameter, the changes take affect the next time the cache refresh plan is processed.</span></span>  
  
### <a name="shared-dataset-parameters"></a><span data-ttu-id="52393-155">共有データセット パラメーター</span><span class="sxs-lookup"><span data-stu-id="52393-155">Shared Dataset Parameters</span></span>  
 <span data-ttu-id="52393-156">共有データセットの場合、次の情報が共有データセット定義から取得されます。</span><span class="sxs-lookup"><span data-stu-id="52393-156">For a shared dataset, the following information is derived from the shared dataset definition:</span></span>  
  
-   <span data-ttu-id="52393-157">**[Name]** クエリ パラメーターの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="52393-157">**Name** Specifies the name of the query parameter.</span></span>  
  
-   <span data-ttu-id="52393-158">**[Type]** クエリ パラメーターのデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="52393-158">**Type** Specifies the data type of the query parameter.</span></span> <span data-ttu-id="52393-159">このデータ型は、データ プロバイダーがデータセット クエリを処理するまで不明なため、データ型の検証は共有データセットが処理されるまで実行されません。</span><span class="sxs-lookup"><span data-stu-id="52393-159">Because this data type is unknown until the data provider processes the dataset query, data type validation cannot occur until the shared dataset is processed.</span></span>  
  
-   <span data-ttu-id="52393-160">**[Nullable]** NULL が有効な値かどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="52393-160">**Nullable** Specifies whether NULL is a valid value.</span></span>  
  
-   <span data-ttu-id="52393-161">**[ReadOnly]** このパラメーターが、共有データセット定義で読み取り専用としてマークされているかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="52393-161">**ReadOnly** Specifies whether this parameter is marked read-only in the shared dataset definition.</span></span> <span data-ttu-id="52393-162">読み取り専用パラメーターは、キャッシュ更新オプションのパラメーターの一覧に表示されません。したがって、読み取り専用パラメーターには、共有データセット定義で既定値が指定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="52393-162">Read only parameters do not appear in the parameter list for cache refresh options and must have a default specified as part of the shared dataset definition.</span></span>  
  
-   <span data-ttu-id="52393-163">**[DefaultValues]** 共有データセット定義で指定されている既定値です。</span><span class="sxs-lookup"><span data-stu-id="52393-163">**DefaultValues** Default values that have been specified in the shared dataset definition.</span></span> <span data-ttu-id="52393-164">クエリ パラメーターには、複数値を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="52393-164">Query parameters can be multivalued.</span></span> <span data-ttu-id="52393-165">既定値をオーバーライドするには、テキスト ボックスのプロンプト領域に新しい値を入力します。</span><span class="sxs-lookup"><span data-stu-id="52393-165">To override the default values, type new values in the text box prompt areas.</span></span>  
  
 <span data-ttu-id="52393-166">共有データセット定義で、パラメーターに **[クエリから省略]** オプションが指定されている場合、既定値を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="52393-166">If the shared dataset definition specifies the option **Omit from query** for a parameter, you do not need to provide a default value.</span></span> <span data-ttu-id="52393-167">このフラグは、データセット パラメーターがクエリで使用されないことを示します。</span><span class="sxs-lookup"><span data-stu-id="52393-167">This flag indicates that the dataset parameter is not used in the query.</span></span> <span data-ttu-id="52393-168">たとえば、このパラメーターが共有データセット定義に表示されるのは、それがデータセット フィルターでのみ使用されるレポート パラメーターである場合です。</span><span class="sxs-lookup"><span data-stu-id="52393-168">For example, the parameter appears in the shared dataset definition because it is a report parameter that is used in the dataset filter only.</span></span>  
  
 <span data-ttu-id="52393-169">データセット パラメーター オプションを表示または変更するには、共有データセット定義を編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52393-169">To view or change dataset parameter options, you must edit the shared dataset definition.</span></span> <span data-ttu-id="52393-170">詳細については、「 [共有データセットの管理](report-data/manage-shared-datasets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52393-170">For more information, see [Manage Shared Datasets](report-data/manage-shared-datasets.md).</span></span>  
  
### <a name="report-parameters"></a><span data-ttu-id="52393-171">レポート パラメーター</span><span class="sxs-lookup"><span data-stu-id="52393-171">Report Parameters</span></span>  
 <span data-ttu-id="52393-172">レポートの場合、キャッシュ更新計画を正常に作成するには、各パラメーター値が有効でなければなりません。</span><span class="sxs-lookup"><span data-stu-id="52393-172">For a report, each parameter value must be valid before you can successfully create a cache refresh plan.</span></span> <span data-ttu-id="52393-173">各レポート パラメーターに、既定値を入力または選択する必要があります。</span><span class="sxs-lookup"><span data-stu-id="52393-173">You must type or select a default value for each report parameter.</span></span> <span data-ttu-id="52393-174">ユーザーが値を設定すると、レポート サーバー上のレポート パラメーターに定義されている既定値がオーバーライドされます。</span><span class="sxs-lookup"><span data-stu-id="52393-174">The value that you set overrides the default value that is defined for the report parameter on the report server.</span></span>  
  
 <span data-ttu-id="52393-175">パラメーターは、レポート サーバー上のパラメーター プロパティで指定されている要件を満たしている必要があります。</span><span class="sxs-lookup"><span data-stu-id="52393-175">Parameters must conform to the requirements specified in the parameter properties on the report server.</span></span> <span data-ttu-id="52393-176">たとえば、レポートパラメーターの AllowBlank プロパティが false の場合、空の文字列は有効な値ではありません。</span><span class="sxs-lookup"><span data-stu-id="52393-176">For example, if the property AllowBlank is false for a report parameter, an empty string is not a valid value.</span></span>  
  
 <span data-ttu-id="52393-177">レポート パラメーター オプションを表示または変更するには、レポート パラメーターをレポート内で編集するか、レポート サーバー上で個別に編集します。</span><span class="sxs-lookup"><span data-stu-id="52393-177">To view or change report parameter options, you must edit the report parameters in the report, or independently, on the report server.</span></span> <span data-ttu-id="52393-178">詳細については、「[レポートパラメーターの概念 &#40;レポートビルダーと SSRS&#41;](report-design/report-parameters-concepts-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52393-178">For more information, see [Report Parameters Concept &#40;Report Builder and SSRS&#41;](report-design/report-parameters-concepts-report-builder-and-ssrs.md).</span></span>  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-inactive"></a><span data-ttu-id="52393-179">キャッシュ更新計画が非アクティブになる条件</span><span class="sxs-lookup"><span data-stu-id="52393-179">Conditions that Cause a Cache Refresh Plan to be Inactive</span></span>  
 <span data-ttu-id="52393-180">次の状況においては、共有データセットまたはレポートのキャッシュ更新計画が非アクティブになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="52393-180">The following conditions can cause a shared dataset or report cache refresh plan to become inactive.</span></span>  
  
-   <span data-ttu-id="52393-181">共有データセット キャッシュまたはレポート キャッシュ オプションが無効化されている。</span><span class="sxs-lookup"><span data-stu-id="52393-181">The shared dataset cache or report cache option is disabled.</span></span>  
  
-   <span data-ttu-id="52393-182">必要なパラメーター値が定義されていないか、無効であるか、または存在しない。</span><span class="sxs-lookup"><span data-stu-id="52393-182">The required parameter values are not defined, not valid, or missing.</span></span> <span data-ttu-id="52393-183">レポートが正常に処理されるには、レポートのクエリすべてが有効である必要があります。</span><span class="sxs-lookup"><span data-stu-id="52393-183">All queries for a report must be valid before the report will be processed.</span></span> <span data-ttu-id="52393-184">サブレポートを持つレポートの場合、サブレポートのデータセットを含むすべてのデータセット クエリが最初に処理されます。</span><span class="sxs-lookup"><span data-stu-id="52393-184">For a report that has subreports, all dataset queries, including datasets for the subreport, are processed first.</span></span> <span data-ttu-id="52393-185">いずれかのデータセットを正常に処理できない場合、レポートは実行されません。</span><span class="sxs-lookup"><span data-stu-id="52393-185">If any dataset cannot be successfully processed, the report cannot run.</span></span>  
  
## <a name="conditions-that-cause-a-cache-refresh-plan-to-be-reactivated"></a><span data-ttu-id="52393-186">キャッシュ更新計画が再アクティブ化される条件</span><span class="sxs-lookup"><span data-stu-id="52393-186">Conditions that Cause a Cache Refresh Plan to be Reactivated</span></span>  
 <span data-ttu-id="52393-187">計画が非アクティブになった後、以下の手順のいずれかを実行することで、キャッシュ更新計画の評価を開始することができます。</span><span class="sxs-lookup"><span data-stu-id="52393-187">After a plan is inactive, do one of the following to trigger evaluation of a cache refresh plan:</span></span>  
  
-   <span data-ttu-id="52393-188">計画のオプションを変更する。</span><span class="sxs-lookup"><span data-stu-id="52393-188">Change an option for the plan.</span></span>  
  
-   <span data-ttu-id="52393-189">更新計画に関連付けられている共有データセットまたはレポートのキャッシュを有効化する。</span><span class="sxs-lookup"><span data-stu-id="52393-189">Enable caching for a shared dataset or report that is associated with the refresh plan.</span></span>  
  
-   <span data-ttu-id="52393-190">更新計画に関連付けられているデータセット クエリ パラメーターの読み取り専用オプションをオフまたはオンにし、その後レポート サーバーに新しい定義を保存する。</span><span class="sxs-lookup"><span data-stu-id="52393-190">Clear or select the read-only option for a dataset query parameter associated with the refresh plan, and then save the new definition to the report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52393-191">参照</span><span class="sxs-lookup"><span data-stu-id="52393-191">See Also</span></span>  
 <span data-ttu-id="52393-192">[アイテムレベルのタスク](security/tasks-and-permissions-item-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="52393-192">[Item-Level Tasks](security/tasks-and-permissions-item-level-tasks.md) </span></span>  
 <span data-ttu-id="52393-193">[レポート マネージャー &#40;SSRS ネイティブ モード&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="52393-193">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="52393-194">[レポートマネージャーの F1 ヘルプ](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="52393-194">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="52393-195">[レポートのキャッシュ &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="52393-195">[Caching Reports &#40;SSRS&#41;](report-server/caching-reports-ssrs.md) </span></span>  
 [<span data-ttu-id="52393-196">共有データセットを管理する</span><span class="sxs-lookup"><span data-stu-id="52393-196">Manage Shared Datasets</span></span>](report-data/manage-shared-datasets.md)  
  
  
