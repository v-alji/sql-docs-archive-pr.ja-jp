---
title: '[パラメーター] プロパティページ (レポートマネージャー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: ebb53598-2378-46ae-8935-d5192f8ea49a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ddaf6598225c36bd6490797e52aeb1a5fed1b60a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634311"
---
# <a name="parameters-properties-page-report-manager"></a><span data-ttu-id="733d4-102">[パラメーター] プロパティ ページ (レポート マネージャー)</span><span class="sxs-lookup"><span data-stu-id="733d4-102">Parameters Properties Page (Report Manager)</span></span>
  <span data-ttu-id="733d4-103">パラメーター化されたレポートのパラメーター設定を表示または変更するには、[パラメーター] プロパティ ページを使用します。</span><span class="sxs-lookup"><span data-stu-id="733d4-103">Use the Parameters properties page to view or modify parameter settings for a parameterized report.</span></span>  
  
 <span data-ttu-id="733d4-104">パラメーターは、レポートをパブリッシュする前にレポート定義で指定します。</span><span class="sxs-lookup"><span data-stu-id="733d4-104">Parameters are specified in the report definition before the report is published.</span></span> <span data-ttu-id="733d4-105">レポートがパブリッシュされた後、パラメーターのプロパティ値の一部は変更することができます。</span><span class="sxs-lookup"><span data-stu-id="733d4-105">After the report is published, you can modify some parameter property values.</span></span> <span data-ttu-id="733d4-106">変更可能な値は、レポート内でパラメーターがどのように定義されているかによって異なります。</span><span class="sxs-lookup"><span data-stu-id="733d4-106">The values that you can modify will vary based on how the parameters are defined in the report.</span></span> <span data-ttu-id="733d4-107">たとえば、パラメーターに静的な値の一覧が定義されている場合、別の静的な値を既定値として選択できますが、一覧から値を追加または削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="733d4-107">For example, if a list of static values is defined for a parameter, you can choose a different static value to use as a default, but you cannot add or remove values from the list.</span></span> <span data-ttu-id="733d4-108">同様に、パラメーターがクエリに基づいている場合、そのクエリのすべての側面 (使用されるデータセット、NULL または空白の値が許可されるかどうか、既定値が指定されているかどうかなど) は、パブリケーションの前にレポートの中で定義されます。</span><span class="sxs-lookup"><span data-stu-id="733d4-108">Similarly, if the parameter is based on a query, all aspects of that query (including the dataset that is used, whether null or blank values are allowed, and whether a default value is provided) are defined in the report before publication.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="733d4-109">ナビゲーション</span><span class="sxs-lookup"><span data-stu-id="733d4-109">Navigation</span></span>  
 <span data-ttu-id="733d4-110">ユーザー インターフェイス (UI) のこの場所に移動するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="733d4-110">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-parameters-properties-page"></a><span data-ttu-id="733d4-111">[パラメーター] プロパティ ページを開くには</span><span class="sxs-lookup"><span data-stu-id="733d4-111">To open the Parameters properties page</span></span>  
  
1.  <span data-ttu-id="733d4-112">レポート マネージャーを開き、パラメーターの設定を変更するレポートを探します。</span><span class="sxs-lookup"><span data-stu-id="733d4-112">Open Report Manager, and locate the report for which you want to modify parameter settings.</span></span>  
  
2.  <span data-ttu-id="733d4-113">レポートの上にマウス ポインターを移動し、下矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="733d4-113">Hover over the report, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="733d4-114">ドロップダウン メニューの **[管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="733d4-114">In the drop-down menu, click **Manage**.</span></span> <span data-ttu-id="733d4-115">この操作により、レポートの [全般] プロパティ ページが開きます。</span><span class="sxs-lookup"><span data-stu-id="733d4-115">This opens the General properties page for the report.</span></span>  
  
4.  <span data-ttu-id="733d4-116">[**パラメーター** ] タブを選択します。[**パラメーター** ] タブが表示されていない場合、レポートにはパラメーターが含まれません。</span><span class="sxs-lookup"><span data-stu-id="733d4-116">Select the **Parameters** tab. If the **Parameters** tab is not visible, the report does not contain parameters.</span></span>  
  
## <a name="options"></a><span data-ttu-id="733d4-117">Options</span><span class="sxs-lookup"><span data-stu-id="733d4-117">Options</span></span>  
 <span data-ttu-id="733d4-118">**パラメーター名**</span><span class="sxs-lookup"><span data-stu-id="733d4-118">**Parameter Name**</span></span>  
 <span data-ttu-id="733d4-119">パラメーターの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="733d4-119">Specifies the name of the parameter.</span></span>  
  
 <span data-ttu-id="733d4-120">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="733d4-120">**Data Type**</span></span>  
 <span data-ttu-id="733d4-121">パラメーターのデータ型を指定します。</span><span class="sxs-lookup"><span data-stu-id="733d4-121">Specifies the data type of the parameter.</span></span>  
  
 <span data-ttu-id="733d4-122">**[既定値あり]**</span><span class="sxs-lookup"><span data-stu-id="733d4-122">**Has Default**</span></span>  
 <span data-ttu-id="733d4-123">パラメーターが既定値を持っていることを指定する場合は、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="733d4-123">Select this check box to specify whether the parameter has a default value.</span></span> <span data-ttu-id="733d4-124">このチェック ボックスをオンにすると、 **[既定値]** が使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="733d4-124">Selecting this check box enables **Default Value**.</span></span> <span data-ttu-id="733d4-125">レポート パラメーターで null 値が許容される場合は、 **[Null]** も使用可能になります。</span><span class="sxs-lookup"><span data-stu-id="733d4-125">It also enables **Null** if the report parameter accepts null values.</span></span> <span data-ttu-id="733d4-126">**[既定値あり]** チェック ボックスをオフにする場合、値を非表示にするか、レポートの実行時にユーザーに値の指定を求めるメッセージが表示されるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="733d4-126">If **Has Default** is not selected, you must either hide the value or prompt the user to provide a value when the report runs.</span></span>  
  
 <span data-ttu-id="733d4-127">**既定値**</span><span class="sxs-lookup"><span data-stu-id="733d4-127">**Default Value**</span></span>  
 <span data-ttu-id="733d4-128">パラメーターの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="733d4-128">Specify a value for the parameter.</span></span> <span data-ttu-id="733d4-129">既定値を指定するには、 **[既定値あり]** チェック ボックスをオンにして、 **[NULL]** チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="733d4-129">To specify a default value, **Has Default** must be selected, and **Null** must not be selected.</span></span> <span data-ttu-id="733d4-130">既定値は、レポート定義で指定される場合があります。</span><span class="sxs-lookup"><span data-stu-id="733d4-130">A default value may be provided through the report definition.</span></span> <span data-ttu-id="733d4-131">**[既定値]** が 1 つ以上の静的な値で作成されている場合、それらの値はレポートから発生します。</span><span class="sxs-lookup"><span data-stu-id="733d4-131">If **Default Value** is populated with one or more static values, those values originate with the report.</span></span> <span data-ttu-id="733d4-132">**[既定値]** が **[クエリ ベース]** の場合、パラメーター値はレポートで定義されたクエリによって決まります。</span><span class="sxs-lookup"><span data-stu-id="733d4-132">If **Default value** is **Query Based**, the parameter value is determined by a query that is defined in the report.</span></span>  
  
 <span data-ttu-id="733d4-133">**[既定値]** で値が受け入れられる場合は、レポートで使用されるデータ処理拡張機能に有効な定数または構文を入力することができます。</span><span class="sxs-lookup"><span data-stu-id="733d4-133">If **Default Value** accepts a value, you can type a constant or syntax that is valid for the data processing extension used with the report.</span></span> <span data-ttu-id="733d4-134">たとえば、データ処理拡張機能のクエリ言語がワイルドカードをサポートする場合、既定値としてワイルドカード文字を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="733d4-134">For example, if the query language of the data processing extension supports wildcards, you can specify a wildcard character as a default value.</span></span>  
  
 <span data-ttu-id="733d4-135">続けてユーザーにプロンプトが表示されるように指定すると、既定値は、ユーザーが使用または変更できる初期値になります。</span><span class="sxs-lookup"><span data-stu-id="733d4-135">If you subsequently specify that a prompt be displayed to the user, the default value becomes an initial value that users can either use or modify.</span></span> <span data-ttu-id="733d4-136">パラメーター値にプロンプトを表示しない場合は、この値がレポートを実行するすべてのユーザーに使用されます。</span><span class="sxs-lookup"><span data-stu-id="733d4-136">If you do not prompt for a parameter value, this value is used for all users who run the report.</span></span>  
  
 <span data-ttu-id="733d4-137">**Null**</span><span class="sxs-lookup"><span data-stu-id="733d4-137">**Null**</span></span>  
 <span data-ttu-id="733d4-138">NULL を既定値として使用する場合に、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="733d4-138">Select this check box to specify null as the default value.</span></span> <span data-ttu-id="733d4-139">NULL 値とは、ユーザーがパラメーター値を指定しなくてもレポートを実行できるという意味です。</span><span class="sxs-lookup"><span data-stu-id="733d4-139">A null value means that the report runs even if the user does not provide a parameter value.</span></span> <span data-ttu-id="733d4-140">この列にチェック ボックスがない場合は、パラメーターに NULL 値を使用できません。</span><span class="sxs-lookup"><span data-stu-id="733d4-140">If there is no check box in this column, the parameter does not accept null values.</span></span>  
  
 <span data-ttu-id="733d4-141">**Hide**</span><span class="sxs-lookup"><span data-stu-id="733d4-141">**Hide**</span></span>  
 <span data-ttu-id="733d4-142">このチェック ボックスをオンにすると、レポートの上部に表示されるパラメーター領域のパラメーターが非表示になります。</span><span class="sxs-lookup"><span data-stu-id="733d4-142">Select this check box to hide the parameter in the parameter area that appears at the top of the report.</span></span> <span data-ttu-id="733d4-143">チェック ボックスをオンにしても、このパラメーターはサブスクリプション定義ページには表示され、レポート URL で指定できます。</span><span class="sxs-lookup"><span data-stu-id="733d4-143">The parameter will still appear in subscription definition pages and it can still be specified on a report URL.</span></span> <span data-ttu-id="733d4-144">常に指定した既定値を使用してレポートを実行する場合にはパラメーターを隠しておくと便利です。</span><span class="sxs-lookup"><span data-stu-id="733d4-144">Hiding the parameter is useful when you want to always run the report with a default value that you specify.</span></span>  
  
 <span data-ttu-id="733d4-145">レポートにパラメーターを表示する場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="733d4-145">Clear this check box if you want the parameter to be visible in the report.</span></span>  
  
 <span data-ttu-id="733d4-146">**ユーザーにメッセージを表示**</span><span class="sxs-lookup"><span data-stu-id="733d4-146">**Prompt User**</span></span>  
 <span data-ttu-id="733d4-147">テキスト ボックスを表示して、ユーザーにパラメーター値の入力を要求する場合に、このチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="733d4-147">Select this check box to display a text box that prompts users for a parameter value.</span></span>  
  
 <span data-ttu-id="733d4-148">自動実行モードでレポートを実行する場合 (たとえば、レポート ヒストリまたはレポート実行スナップショットを生成する場合)、すべてのユーザーに同じパラメーター値を使用する場合、またはユーザーによる値の入力を要求しない場合は、このチェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="733d4-148">Clear this check box if you want to run the report in unattended mode (for example, to generate report history or report execution snapshots), if you want to use the same parameter value for all users, or if you do not require user input for the value.</span></span>  
  
 <span data-ttu-id="733d4-149">**テキストの表示**</span><span class="sxs-lookup"><span data-stu-id="733d4-149">**Display Text**</span></span>  
 <span data-ttu-id="733d4-150">パラメーター テキスト ボックスの隣に表示するテキスト文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="733d4-150">Provide a text string that appears next to the parameter text box.</span></span> <span data-ttu-id="733d4-151">この文字列により、ラベルまたは説明のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="733d4-151">This string provides a label or descriptive text.</span></span> <span data-ttu-id="733d4-152">文字列の長さに制限はありません。</span><span class="sxs-lookup"><span data-stu-id="733d4-152">There is no limit on string length.</span></span> <span data-ttu-id="733d4-153">長いテキスト文字列は、表示領域内で折り返されます。</span><span class="sxs-lookup"><span data-stu-id="733d4-153">Longer text strings wrap within the space provided.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733d4-154">参照</span><span class="sxs-lookup"><span data-stu-id="733d4-154">See Also</span></span>  
 <span data-ttu-id="733d4-155">[[全般] プロパティページ、レポート &#40;レポートマネージャー&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="733d4-155">[General Properties Page, Reports &#40;Report Manager&#41;](../../2014/reporting-services/general-properties-page-reports-report-manager.md) </span></span>  
 [<span data-ttu-id="733d4-156">レポート マネージャー F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="733d4-156">Report Manager F1 Help</span></span>](../../2014/reporting-services/report-manager-f1-help.md)  
  
  
