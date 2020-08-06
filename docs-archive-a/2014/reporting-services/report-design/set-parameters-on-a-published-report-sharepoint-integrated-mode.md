---
title: パブリッシュされたレポートのパラメーターの設定 (SharePoint 統合モードでの Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- SharePoint integration [Reporting Services], content management
- report parameters [Reporting Services]
ms.assetid: dec5d985-a6c1-4dd8-8a66-a848e89a2e18
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4d0a2b1a23f382adb9e0cdddbebcded0050d34bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631541"
---
# <a name="set-parameters-on-a-published-report-reporting-services-in-sharepoint-integrated-mode"></a><span data-ttu-id="52716-102">パブリッシュ済みレポートのパラメーターの設定 (Reporting Services の SharePoint 統合モード)</span><span class="sxs-lookup"><span data-stu-id="52716-102">Set Parameters on a Published Report (Reporting Services in SharePoint Integrated Mode)</span></span>
  <span data-ttu-id="52716-103">パラメーター化されたレポートとは、レポートの実行時にデータのフィルター処理に使用する入力値を受け取るレポートです。</span><span class="sxs-lookup"><span data-stu-id="52716-103">A parameterized report is a report that accepts input values that are used to filter data when you run the report.</span></span> <span data-ttu-id="52716-104">パラメーターは、レポートの作成時に定義します。</span><span class="sxs-lookup"><span data-stu-id="52716-104">Parameters are defined when the report is created.</span></span> <span data-ttu-id="52716-105">レポート定義でレポート パラメーターがどのように定義されているかによって、単一の値、複数の値、または動的な値を受け入れることができます。動的な値は、直前の選択に応じて変化します (たとえば、製品カテゴリを選択したとき、次の選択ではそのカテゴリの特定の製品を選択するなど)。</span><span class="sxs-lookup"><span data-stu-id="52716-105">Depending on how a report parameter is defined in the report definition, it can accept a single value, multiple values, or dynamic values, which change in response to a previous selection (for example, when you select product category, your next selection might be a specific product from that category).</span></span> <span data-ttu-id="52716-106">パラメーターには既定値を指定することもできます。フィルター選択したレポートを自動的に実行する場合に既定値を使用することも、既定値を別の値に置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="52716-106">A parameter can have a default value, which can be used to run a filtered version of the report automatically or possibly be replaced with a different value.</span></span>  
  
 <span data-ttu-id="52716-107">このようなプロパティはレポート定義で設定することも、レポートがパブリッシュされた後で設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="52716-107">These properties can be set in the report definition, or after the report is published.</span></span> <span data-ttu-id="52716-108">パブリッシュされたレポートの一部のパラメーター プロパティを変更して、値や表示プロパティを変更することはできますが、パラメーターの名前やデータ型を変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="52716-108">Although you can modify some parameter properties in a published to change the value and display properties, you cannot change a parameter name or the data type.</span></span> <span data-ttu-id="52716-109">パラメーター名とデータ型は、レポート作成者のみがレポート定義内で変更できます。</span><span class="sxs-lookup"><span data-stu-id="52716-109">The parameter name and data type can only be changed by the report author in the report definition.</span></span>  
  
 <span data-ttu-id="52716-110">パラメーター化されたレポートを実行する際、有効な値を示すドロップダウン リストがレポートに含まれており、そこから選択できることもありますが、一般的には入力する値の種類を知っておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="52716-110">To run a parameterized report, you typically must know which values to type, although a report might include drop-down lists of valid values from which to choose.</span></span>  
  
 <span data-ttu-id="52716-111">パブリッシュ済みレポートのパラメーター プロパティを設定するには、レポートに対する "アイテムの編集" 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="52716-111">To set parameter properties on a published report, you must have Edit Items permission for the report.</span></span> <span data-ttu-id="52716-112">SharePoint サイトから実行するレポートの、一部またはすべてのパラメーター プロパティを変更できます。</span><span class="sxs-lookup"><span data-stu-id="52716-112">You can modify some or all of the parameter properties on a report that you run from a SharePoint site.</span></span> <span data-ttu-id="52716-113">繰り返し使用するパラメーター値の組み合わせを保存することで、レポートを個人用にカスタマイズすることはできません。</span><span class="sxs-lookup"><span data-stu-id="52716-113">You cannot personalize a report by saving a combination of parameter values that you want to use repeatedly.</span></span> <span data-ttu-id="52716-114">指定した既定値は、レポートを開いたすべてのユーザーによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="52716-114">Any default values that you specify are used by all users who open the report.</span></span>  
  
 <span data-ttu-id="52716-115">レポートを常に表示するように構成されたレポート ビューアー Web パーツにレポートを埋め込む場合には、レポート ビューアー Web パーツのプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="52716-115">If the report is embedded in a Report Viewer Web part that is configured to always show that report, set the properties on the Report Viewer Web Part.</span></span> <span data-ttu-id="52716-116">詳細については、「[レポート ビューアー Web パーツを Web ページに追加する &#40;Reporting Services の SharePoint 統合モード&#41;](../report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52716-116">For more information, see [Add the Report Viewer Web Part to a Web Page &#40;Reporting Services in SharePoint Integrated Mode&#41;](../report-server-sharepoint/add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
### <a name="to-run-a-parameterized-report"></a><span data-ttu-id="52716-117">パラメーター化されたレポートを実行するには</span><span class="sxs-lookup"><span data-stu-id="52716-117">To run a parameterized report</span></span>  
  
1.  <span data-ttu-id="52716-118">レポートが格納されているライブラリを開きます。</span><span class="sxs-lookup"><span data-stu-id="52716-118">Open the library that contains the report.</span></span>  
  
2.  <span data-ttu-id="52716-119">レポート名をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52716-119">Click the report name.</span></span> <span data-ttu-id="52716-120">パラメーターのあるレポートをあらかじめ調べておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="52716-120">You must know in advance which reports have parameters.</span></span> <span data-ttu-id="52716-121">レポートの外観からは、パラメーター化されているかどうか判別できません。</span><span class="sxs-lookup"><span data-stu-id="52716-121">There is no visual identifier on the report to indicate that it is parameterized.</span></span>  
  
3.  <span data-ttu-id="52716-122">レポートを開き、使用するパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="52716-122">When the report opens, specify the parameters you want to use.</span></span> <span data-ttu-id="52716-123">パラメーター領域は、レポート ビューアー Web パーツのプロパティ設定に応じて、表示、折りたたみ、または非表示になっています。</span><span class="sxs-lookup"><span data-stu-id="52716-123">The Parameters area might be visible, collapsed, or hidden depending on how properties are set on the Report Viewer Web Part.</span></span>  
  
    1.  <span data-ttu-id="52716-124">パラメーター領域が表示されている場合は、各パラメーターの値を選択します。</span><span class="sxs-lookup"><span data-stu-id="52716-124">If the Parameters area is visible, choose a value for each parameter.</span></span>  
  
    2.  <span data-ttu-id="52716-125">レポートの縦方向に色付きの細い枠が表示され、その中央部に矢印がある場合、パラメーター領域が折りたたまれています。</span><span class="sxs-lookup"><span data-stu-id="52716-125">If there is a thin strip of color that runs down the length of the report that has an arrow in the middle of it, the Parameters area is collapsed.</span></span> <span data-ttu-id="52716-126">矢印をクリックすると、展開できます。</span><span class="sxs-lookup"><span data-stu-id="52716-126">You can click the arrow to expand it.</span></span>  
  
    3.  <span data-ttu-id="52716-127">パラメーター領域が非表示になっている場合、値を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="52716-127">If the Parameters area is hidden, you cannot specify a value.</span></span>  
  
4.  <span data-ttu-id="52716-128">パラメーター領域の下部にある **[適用]** をクリックすると、レポートが実行されます。</span><span class="sxs-lookup"><span data-stu-id="52716-128">Click **Apply** at the bottom of the Parameters area to run the report.</span></span>  
  
     <span data-ttu-id="52716-129">期待する結果を得られない値の組み合わせを指定してしまう可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="52716-129">It is possible to specify a combination of values that do not give you the results you expect.</span></span> <span data-ttu-id="52716-130">必要な情報が得られない場合は、作成者によるレポートの変更が必要である可能性があります。</span><span class="sxs-lookup"><span data-stu-id="52716-130">The report might need to be modified by the report author if you are not getting the information you require.</span></span>  
  
5.  <span data-ttu-id="52716-131">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52716-131">Click **OK**.</span></span>  
  
### <a name="to-set-parameter-properties"></a><span data-ttu-id="52716-132">パラメーター プロパティを設定するには</span><span class="sxs-lookup"><span data-stu-id="52716-132">To set parameter properties</span></span>  
  
1.  <span data-ttu-id="52716-133">レポートが格納されているライブラリまたはフォルダーを開きます。</span><span class="sxs-lookup"><span data-stu-id="52716-133">Open the library or folder that contains the report.</span></span>  
  
2.  <span data-ttu-id="52716-134">レポートをポイントして、下向きの矢印をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52716-134">Point to the report and click the down arrow.</span></span>  
  
3.  <span data-ttu-id="52716-135">**[パラメーターの管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52716-135">Click **Manage Parameters**.</span></span> <span data-ttu-id="52716-136">レポートにパラメーターが含まれている場合、ページに各パラメーターが一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="52716-136">If the report contains parameters, each parameter will be listed on the page.</span></span> <span data-ttu-id="52716-137">一覧には、パラメーターの名前、データ型、既定で使用されるデータ値、およびレポートを開いたときにパラメーター領域を表示するかどうかが示されます。</span><span class="sxs-lookup"><span data-stu-id="52716-137">The list shows the parameter name, data type, data value that is used by default, and whether it is visible in the parameter area when you open the report.</span></span>  
  
4.  <span data-ttu-id="52716-138">一覧で、設定を変更するパラメーターをクリックします。</span><span class="sxs-lookup"><span data-stu-id="52716-138">Click a parameter in the list to modify its settings.</span></span>  
  
5.  <span data-ttu-id="52716-139">[既定値] に、パラメーターの値を入力します。</span><span class="sxs-lookup"><span data-stu-id="52716-139">In Default Value, enter a value for the parameter.</span></span> <span data-ttu-id="52716-140">この値は検証されないため、レポートに対して有効な値を入力するように注意してください。</span><span class="sxs-lookup"><span data-stu-id="52716-140">The value will not be validated, so be sure that you are providing a value that works for the report.</span></span>  
  
    1.  <span data-ttu-id="52716-141">レポートの作成時に定義された既定値を使用するには、 **[レポート定義で指定されている値式を使用]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="52716-141">Choose **Use value expression specified in report definition** if you want to use the default value that was defined when the report was created.</span></span> <span data-ttu-id="52716-142">レポート定義で既定値が指定されていない場合、このオプションは使用できません。</span><span class="sxs-lookup"><span data-stu-id="52716-142">If the report definition does not provide a default value, this option will be unavailable.</span></span>  
  
    2.  <span data-ttu-id="52716-143">レポート定義の既定値を置き換える値を指定するには、 **[レポートの既定値をオーバーライド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="52716-143">Choose **Override the report default value** if you want to specify a replacement for the report definition default value.</span></span> <span data-ttu-id="52716-144">NULL 値が許可されるレポート パラメーターについては、 **[Null]** チェック ボックスをオンにすることで、そのパラメーターに基づくフィルター処理を無効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="52716-144">Optionally, for report parameters that accept null values, you can select the **Null** check box to prevent filtering based on that parameter.</span></span>  
  
    3.  <span data-ttu-id="52716-145">レポートが処理される前に各ユーザーが値を指定できるようにするには、 **[パラメーターは既定値を持たない]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="52716-145">Choose **Parameter does not have a default value** if you want each user to specify a value before the report is processed.</span></span> <span data-ttu-id="52716-146">このオプションを選択した場合、ユーザーに値の指定を求めるための表示設定を行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="52716-146">If you select this option, you should set display settings that prompt the user to specify a value.</span></span>  
  
     <span data-ttu-id="52716-147">すべてのパラメーターに既定値があれば、ユーザーがレポートを開くと自動的にその既定値を使用してレポートが実行されます。</span><span class="sxs-lookup"><span data-stu-id="52716-147">Note that if all parameter values have a default value, the report will automatically run with those values when the user opens the report.</span></span> <span data-ttu-id="52716-148">ただし、レポート領域が表示される場合には、ユーザーは既定値をオーバーライドしてレポートを再実行することができます。</span><span class="sxs-lookup"><span data-stu-id="52716-148">However, if the parameter area is displayed, users can override the default value and re-run the report.</span></span>  
  
6.  <span data-ttu-id="52716-149">パラメーターを表示するかどうかを決定する表示オプションを設定します。</span><span class="sxs-lookup"><span data-stu-id="52716-149">Set display options to determine whether the parameter is visible.</span></span>  
  
    1.  <span data-ttu-id="52716-150">ページにパラメーターを表示するには、 **[ユーザーにメッセージを表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="52716-150">Choose **Prompt User** to show the parameter on the page.</span></span> <span data-ttu-id="52716-151">フィールド内に表示される入力要求テキストで、ユーザーが入力する必要のあるデータの形式や型に関する簡単な説明を示すことができます。</span><span class="sxs-lookup"><span data-stu-id="52716-151">You can specify prompt text that appears within a field to provide a brief statement about the format or type of data that the user must provide.</span></span>  
  
    2.  <span data-ttu-id="52716-152">既定値を使用し、パラメーター領域にパラメーターを表示しない場合には、 **[非表示]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="52716-152">Choose **Hidden** if you are using a default value and you do not want the parameter to be visible in the Parameters area.</span></span>  
  
    3.  <span data-ttu-id="52716-153">既定値を使用し、パラメーター領域にもサブスクリプション ページにもパラメーターを表示しない場合には、 **[内部]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="52716-153">Choose **Internal** if you are using a default value and you do not want the parameter to be visible in the Parameters area or on subscription pages.</span></span>  
  
7.  <span data-ttu-id="52716-154">**[Apply]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="52716-154">Click **Apply**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52716-155">参照</span><span class="sxs-lookup"><span data-stu-id="52716-155">See Also</span></span>  
 [<span data-ttu-id="52716-156">レポート サーバー アイテムの SharePoint サイトおよびリスト権限のリファレンス</span><span class="sxs-lookup"><span data-stu-id="52716-156">SharePoint Site and List Permission Reference for Report Server Items</span></span>](../security/sharepoint-site-and-list-permission-reference-for-report-server-items.md)  
  
  
