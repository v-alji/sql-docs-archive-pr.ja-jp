---
title: 多次元モデルでのアクション |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- actions [Analysis Services], creating
- report actions [Analysis Services]
- drillthrough actions [Analysis Services]
- cubes [Analysis Services], actions
ms.assetid: b9fee2b9-05a5-4077-848d-d8457326dc27
author: minewiskan
ms.author: owend
ms.openlocfilehash: ce42907190363be085e8f4d8e9adfbab52a70590
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639722"
---
# <a name="actions-in-multidimensional-models"></a><span data-ttu-id="81efe-102">多次元モデルのアクション</span><span class="sxs-lookup"><span data-stu-id="81efe-102">Actions in Multidimensional Models</span></span>
  <span data-ttu-id="81efe-103">アクションは、選択したキューブまたはキューブの一部でエンド ユーザーが行う操作です。</span><span class="sxs-lookup"><span data-stu-id="81efe-103">An action is an end user-initiated operation upon a selected cube or portion of a cube.</span></span> <span data-ttu-id="81efe-104">この操作では、選択されているアイテムをパラメーターとして設定してアプリケーションを起動したり、選択されているアイテムに関する情報を取得したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="81efe-104">The operation can start an application with the selected item as a parameter, or it can retrieve information about the selected item.</span></span> <span data-ttu-id="81efe-105">アクションの詳細については、「[アクション &#40;Analysis Services - 多次元データ&#41;](actions-analysis-services-multidimensional-data.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81efe-105">For more information about actions, see [Actions &#40;Analysis Services - Multidimensional Data&#41;](actions-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="81efe-106">キューブのアクションを作成するには、キューブ デザイナーの **[アクション]** タブを使用します。</span><span class="sxs-lookup"><span data-stu-id="81efe-106">Use the **Actions** tab of Cube Designer to build actions for a cube.</span></span> <span data-ttu-id="81efe-107">次の指定を行います。</span><span class="sxs-lookup"><span data-stu-id="81efe-107">Specify the following:</span></span>  
  
 <span data-ttu-id="81efe-108">**名前**</span><span class="sxs-lookup"><span data-stu-id="81efe-108">**Name**</span></span>  
 <span data-ttu-id="81efe-109">アクションを識別する名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="81efe-109">Select a name that identifies the action.</span></span>  
  
 <span data-ttu-id="81efe-110">**[アクションの対象]**</span><span class="sxs-lookup"><span data-stu-id="81efe-110">**Action Target**</span></span>  
 <span data-ttu-id="81efe-111">アクションをアタッチするオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="81efe-111">Select the object to which the action is attached.</span></span> <span data-ttu-id="81efe-112">一般に、クライアント アプリケーションでは、エンド ユーザーが対象オブジェクトを選択するとアクションが表示されます。ただし、クライアント アプリケーションは、どのエンド ユーザーの操作でアクションを表示するかを決定します。</span><span class="sxs-lookup"><span data-stu-id="81efe-112">Generally, in client applications, the action is displayed when end users select the target object; however, the client application determines which end-user operation displays actions.</span></span> <span data-ttu-id="81efe-113">**[対象になる種類]** には、次のいずれかのオブジェクトを選択します。</span><span class="sxs-lookup"><span data-stu-id="81efe-113">For **Target type**, select from the following objects:</span></span>  
  
-   <span data-ttu-id="81efe-114">[属性メンバー]</span><span class="sxs-lookup"><span data-stu-id="81efe-114">Attribute members</span></span>  
  
-   <span data-ttu-id="81efe-115">セル</span><span class="sxs-lookup"><span data-stu-id="81efe-115">Cells</span></span>  
  
-   <span data-ttu-id="81efe-116">キューブ</span><span class="sxs-lookup"><span data-stu-id="81efe-116">Cube</span></span>  
  
-   <span data-ttu-id="81efe-117">[ディメンションのメンバー]</span><span class="sxs-lookup"><span data-stu-id="81efe-117">Dimension members</span></span>  
  
-   <span data-ttu-id="81efe-118">Hierarchy</span><span class="sxs-lookup"><span data-stu-id="81efe-118">Hierarchy</span></span>  
  
-   <span data-ttu-id="81efe-119">[階層メンバー]</span><span class="sxs-lookup"><span data-stu-id="81efe-119">Hierarchy members</span></span>  
  
-   <span data-ttu-id="81efe-120">Level</span><span class="sxs-lookup"><span data-stu-id="81efe-120">Level</span></span>  
  
-   <span data-ttu-id="81efe-121">[レベル メンバー]</span><span class="sxs-lookup"><span data-stu-id="81efe-121">Level members</span></span>  
  
 <span data-ttu-id="81efe-122">対象になるオブジェクトの種類を選択したら、指定した種類のキューブ オブジェクトを **[対象になるオブジェクト]** から選択します。</span><span class="sxs-lookup"><span data-stu-id="81efe-122">After you select the target object type, under **Target object**, select the cube object of the designated type.</span></span>  
  
 <span data-ttu-id="81efe-123">**[条件 (省略可能)]**</span><span class="sxs-lookup"><span data-stu-id="81efe-123">**Condition (Optional)**</span></span>  
 <span data-ttu-id="81efe-124">ブール値に解決される多次元式 (MDX) を指定します。省略可能です。</span><span class="sxs-lookup"><span data-stu-id="81efe-124">Specify an optional Multidimensional Expressions (MDX) expression that resolves to a Boolean value.</span></span> <span data-ttu-id="81efe-125">値が `True` の場合、アクションは指定された対象オブジェクトに対して実行されます。</span><span class="sxs-lookup"><span data-stu-id="81efe-125">If the value is `True`, the action is performed on the specified target.</span></span> <span data-ttu-id="81efe-126">値が `False` の場合、アクションは実行されません。</span><span class="sxs-lookup"><span data-stu-id="81efe-126">If the value is `False`, the action is not performed.</span></span>  
  
 <span data-ttu-id="81efe-127">**[アクションの内容]**</span><span class="sxs-lookup"><span data-stu-id="81efe-127">**Action Content**</span></span>  
 <span data-ttu-id="81efe-128">アクションの種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="81efe-128">Select the type of action.</span></span> <span data-ttu-id="81efe-129">次の表は、使用できる種類をまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="81efe-129">The following table summarizes the available types.</span></span>  
  
|<span data-ttu-id="81efe-130">Type</span><span class="sxs-lookup"><span data-stu-id="81efe-130">Type</span></span>|<span data-ttu-id="81efe-131">説明</span><span class="sxs-lookup"><span data-stu-id="81efe-131">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="81efe-132">[データ セット]</span><span class="sxs-lookup"><span data-stu-id="81efe-132">Data Set</span></span>|<span data-ttu-id="81efe-133">データセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="81efe-133">Retrieves a dataset.</span></span>|  
|<span data-ttu-id="81efe-134">[専用]</span><span class="sxs-lookup"><span data-stu-id="81efe-134">Proprietary</span></span>|<span data-ttu-id="81efe-135">この一覧に表示されていないインターフェイスを使用して操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="81efe-135">Performs an operation by using an interface other than those listed in this table.</span></span>|  
|<span data-ttu-id="81efe-136">[行セット]</span><span class="sxs-lookup"><span data-stu-id="81efe-136">Row Set</span></span>|<span data-ttu-id="81efe-137">行セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="81efe-137">Retrieves a rowset.</span></span>|  
|<span data-ttu-id="81efe-138">ステートメント</span><span class="sxs-lookup"><span data-stu-id="81efe-138">Statement</span></span>|<span data-ttu-id="81efe-139">OLE DB コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="81efe-139">Runs an OLE DB command.</span></span>|  
|<span data-ttu-id="81efe-140">URL</span><span class="sxs-lookup"><span data-stu-id="81efe-140">URL</span></span>|<span data-ttu-id="81efe-141">インターネット ブラウザーで変数ページを表示します。</span><span class="sxs-lookup"><span data-stu-id="81efe-141">Displays a variable page in an Internet browser.</span></span>|  
  
 <span data-ttu-id="81efe-142">**[アクションの式]** に、アクションが実行されたときに渡されるパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="81efe-142">For **Action Expression**, specify the parameters that are passed when the action is run.</span></span> <span data-ttu-id="81efe-143">構文の評価結果は文字列型になる必要があり、MDX で記述した式を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="81efe-143">The syntax must evaluate to a string, and you must include an expression written in MDX.</span></span> <span data-ttu-id="81efe-144">たとえば、MDX 式では、構文に含まれるキューブの一部を指定できます。</span><span class="sxs-lookup"><span data-stu-id="81efe-144">For example, your MDX expression can indicate a part of the cube that is included in the syntax.</span></span> <span data-ttu-id="81efe-145">MDX 式が評価されてから、パラメーターが渡されます。</span><span class="sxs-lookup"><span data-stu-id="81efe-145">MDX expressions are evaluated before the parameters are passed.</span></span> <span data-ttu-id="81efe-146">また、MDX ビルダーを使用すると、MDX 式を作成できます。</span><span class="sxs-lookup"><span data-stu-id="81efe-146">Also, MDX Builder is available to help you build MDX expressions.</span></span>  
  
 <span data-ttu-id="81efe-147">**追加のプロパティ**</span><span class="sxs-lookup"><span data-stu-id="81efe-147">**Additional Properties**</span></span>  
 <span data-ttu-id="81efe-148">プロパティを選択します。</span><span class="sxs-lookup"><span data-stu-id="81efe-148">Select the property.</span></span> <span data-ttu-id="81efe-149">次の表は、使用できるプロパティをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="81efe-149">The following table summarizes the available properties.</span></span>  
  
|<span data-ttu-id="81efe-150">プロパティ</span><span class="sxs-lookup"><span data-stu-id="81efe-150">Property</span></span>|<span data-ttu-id="81efe-151">説明</span><span class="sxs-lookup"><span data-stu-id="81efe-151">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="81efe-152">**[呼び出し]**</span><span class="sxs-lookup"><span data-stu-id="81efe-152">**Invocation**</span></span>|<span data-ttu-id="81efe-153">アクションを実行する方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="81efe-153">Specifies how the action is run.</span></span> <span data-ttu-id="81efe-154">既定の [インタラクティブ] を指定すると、アクションはユーザーがオブジェクトにアクセスしたときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="81efe-154">Interactive, the default, specifies that the action is run when a user accesses an object.</span></span> <span data-ttu-id="81efe-155">次の設定が可能です。</span><span class="sxs-lookup"><span data-stu-id="81efe-155">The possible settings are:</span></span><br /><br /> <span data-ttu-id="81efe-156">Batch</span><span class="sxs-lookup"><span data-stu-id="81efe-156">Batch</span></span><br /><br /> <span data-ttu-id="81efe-157">Interactive</span><span class="sxs-lookup"><span data-stu-id="81efe-157">Interactive</span></span><br /><br /> <span data-ttu-id="81efe-158">[オープン時]</span><span class="sxs-lookup"><span data-stu-id="81efe-158">On Open</span></span>|  
|<span data-ttu-id="81efe-159">**Application**</span><span class="sxs-lookup"><span data-stu-id="81efe-159">**Application**</span></span>|<span data-ttu-id="81efe-160">アクションのアプリケーションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="81efe-160">Describes the application of the action.</span></span>|  
|<span data-ttu-id="81efe-161">**説明**</span><span class="sxs-lookup"><span data-stu-id="81efe-161">**Description**</span></span>|<span data-ttu-id="81efe-162">アクションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="81efe-162">Describes the action.</span></span>|  
|<span data-ttu-id="81efe-163">**Caption**</span><span class="sxs-lookup"><span data-stu-id="81efe-163">**Caption**</span></span>|<span data-ttu-id="81efe-164">アクションに関して表示されるキャプションを指定します。</span><span class="sxs-lookup"><span data-stu-id="81efe-164">Provides a caption that is displayed for the action.</span></span> <span data-ttu-id="81efe-165">キャプションが MDX の場合は、 `True` [**キャプションに mdx**を使用する] を指定します。</span><span class="sxs-lookup"><span data-stu-id="81efe-165">If the caption is MDX, specify `True` for **Caption is MDX**.</span></span>|  
|<span data-ttu-id="81efe-166">**True**</span><span class="sxs-lookup"><span data-stu-id="81efe-166">**Caption is MDX**</span></span>|<span data-ttu-id="81efe-167">キャプションが MDX の場合は `True`、MDX でない場合は `False` を指定します。</span><span class="sxs-lookup"><span data-stu-id="81efe-167">Specify `True` if the caption is MDX or `False` if it is not.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="81efe-168">HTML およびコマンド ラインのアクションの種類を定義するには、Analysis Services スクリプト言語 (ASSL) または分析管理オブジェクト (AMO) を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81efe-168">You must use Analysis Services Scripting Language (ASSL) or Analysis Management Objects (AMO) to define HTML and Command Line action types.</span></span> <span data-ttu-id="81efe-169">詳細については、「[アクション要素 &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/action-element-assl)」「[Type 要素 &#40;アクション&#41; &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/type-element-action-assl)」、および「[高度な AMO OLAP オブジェクトのプログラミング](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-advanced-objects)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81efe-169">For more information, see [Action Element &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/objects/action-element-assl), [Type Element &#40;Action&#41; &#40;ASSL&#41;](https://docs.microsoft.com/bi-reference/assl/properties/type-element-action-assl), and [Programming AMO OLAP Advanced Objects](https://docs.microsoft.com/bi-reference/amo/programming-amo-olap-advanced-objects).</span></span>  
  
## <a name="creating-a-reporting-action"></a><span data-ttu-id="81efe-170">レポート アクションの作成</span><span class="sxs-lookup"><span data-stu-id="81efe-170">Creating a Reporting Action</span></span>  
 <span data-ttu-id="81efe-171">レポート サーバーは、レポートに関する URL ベースの要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="81efe-171">The report server responds to URL-based requests for reports.</span></span> <span data-ttu-id="81efe-172">レポート アクションを作成するには、 **[キューブ]** メニューの **[新しいレポート アクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81efe-172">To create a reporting action, on the **Cube** menu, click **New Reporting Action**.</span></span> <span data-ttu-id="81efe-173">次のオプションは、レポート アクションに固有です。</span><span class="sxs-lookup"><span data-stu-id="81efe-173">The following options are specific to a reporting action.</span></span>  
  
 <span data-ttu-id="81efe-174">**レポートサーバー**</span><span class="sxs-lookup"><span data-stu-id="81efe-174">**Report Server**</span></span>  
 <span data-ttu-id="81efe-175">次の表で説明するプロパティは、レポート サーバーに対して指定されます。</span><span class="sxs-lookup"><span data-stu-id="81efe-175">The properties described in the following table are specified for the report server.</span></span>  
  
|<span data-ttu-id="81efe-176">プロパティ</span><span class="sxs-lookup"><span data-stu-id="81efe-176">Property</span></span>|<span data-ttu-id="81efe-177">説明</span><span class="sxs-lookup"><span data-stu-id="81efe-177">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="81efe-178">**サーバー名**</span><span class="sxs-lookup"><span data-stu-id="81efe-178">**Server name**</span></span>|<span data-ttu-id="81efe-179">サポート サーバーを稼働しているコンピューターの名前です。</span><span class="sxs-lookup"><span data-stu-id="81efe-179">The name of the computer running report server.</span></span>|  
|<span data-ttu-id="81efe-180">**[サーバー パス]**</span><span class="sxs-lookup"><span data-stu-id="81efe-180">**Server path**</span></span>|<span data-ttu-id="81efe-181">レポート サーバーによって公開されたパスです。</span><span class="sxs-lookup"><span data-stu-id="81efe-181">The path exposed by report server.</span></span>|  
|<span data-ttu-id="81efe-182">**[レポート形式]**</span><span class="sxs-lookup"><span data-stu-id="81efe-182">**Report format**</span></span>|<span data-ttu-id="81efe-183">HTML5、HTML3、Excel、または PDF です。</span><span class="sxs-lookup"><span data-stu-id="81efe-183">HTML5, HTML3, Excel, or PDF.</span></span>|  
  
 <span data-ttu-id="81efe-184">**[パラメーター (省略可能)]**</span><span class="sxs-lookup"><span data-stu-id="81efe-184">**Parameters (Optional)**</span></span>  
 <span data-ttu-id="81efe-185">パラメーターは、アクションが作成されると、URL 文字列の一部としてサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="81efe-185">The parameters are sent to the server as part of the URL string when the action is created.</span></span> <span data-ttu-id="81efe-186">パラメーターには、 **[パラメーター名]** と、MDX 式である **[パラメーター値]** が含まれます。</span><span class="sxs-lookup"><span data-stu-id="81efe-186">They include **Parameter Name** and **Parameter Value**, which is an MDX expression.</span></span>  
  
 <span data-ttu-id="81efe-187">レポート サーバーの URL は、次のように構成されます。</span><span class="sxs-lookup"><span data-stu-id="81efe-187">The report server URL is constructed as follows:</span></span>  
  
```  
  
http://  
host  
/  
virtualdirectory  
/Path&  
parametername1  
=  
parametervalue1  
& ...  
```  
  
 <span data-ttu-id="81efe-188">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="81efe-188">For example:</span></span>  
  
```  
http://localhost/ReportServer/Sales/YearlySalesByCategory?rs:Command=Render&Region=West  
```  
  
## <a name="creating-a-drillthrough-action"></a><span data-ttu-id="81efe-189">ドリルスルー アクションの作成</span><span class="sxs-lookup"><span data-stu-id="81efe-189">Creating a Drillthrough Action</span></span>  
 <span data-ttu-id="81efe-190">ドリルスルー アクションは、クライアント アプリケーションにドリルスルー ステートメントとして返される行セット アクションによって定義されます。</span><span class="sxs-lookup"><span data-stu-id="81efe-190">A drillthrough action is defined by a rowset action, which is returned to the client application as a drillthrough statement.</span></span> <span data-ttu-id="81efe-191">アクションの対象は、メジャー グループのメンバーです。</span><span class="sxs-lookup"><span data-stu-id="81efe-191">The action target is a member of a measure group.</span></span> <span data-ttu-id="81efe-192">新しいドリルスルー アクションを作成するには、 **[キューブ]** メニューの **[新しいドリルスルー アクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="81efe-192">To create a new drillthrough action, on the **Cube** menu, click **New Drillthrough Action**.</span></span> <span data-ttu-id="81efe-193">次のオプションは、ドリルスルー アクションに固有です。</span><span class="sxs-lookup"><span data-stu-id="81efe-193">The following options are specific to a drillthrough action:</span></span>  
  
 <span data-ttu-id="81efe-194">**[ドリルスルー列]**</span><span class="sxs-lookup"><span data-stu-id="81efe-194">**Drillthrough Columns**</span></span>  
 <span data-ttu-id="81efe-195">1 つまたは複数のディメンションと、アクションによってクライアント アプリケーションに返されるドリルスルー列をディメンションごとに選択します。</span><span class="sxs-lookup"><span data-stu-id="81efe-195">Select one or more dimensions and, for each dimension, the drillthrough columns returned to the client application by the action.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81efe-196">参照</span><span class="sxs-lookup"><span data-stu-id="81efe-196">See Also</span></span>  
 [<span data-ttu-id="81efe-197">多次元モデルのキューブ</span><span class="sxs-lookup"><span data-stu-id="81efe-197">Cubes in Multidimensional Models</span></span>](cubes-in-multidimensional-models.md)  
  
  
