---
title: サブレポートおよびパラメーターの追加 (レポート ビルダーおよび SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10093"
- sql12.rtp.rptdesigner.subreportproperties.general.f1
ms.assetid: 94f960f8-a629-4f1e-8277-c3b8f0680d98
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3aeede343763ea5fc8fbdfde179208f98fa1a2ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631548"
---
# <a name="add-a-subreport-and-parameters-report-builder-and-ssrs"></a><span data-ttu-id="b5810-102">サブレポートおよびパラメーターの追加 (レポート ビルダーおよび SSRS)</span><span class="sxs-lookup"><span data-stu-id="b5810-102">Add a Subreport and Parameters (Report Builder and SSRS)</span></span>
  <span data-ttu-id="b5810-103">複数の関連レポートのコンテナーであるメイン レポートを作成する場合は、レポートにサブレポートを追加します。</span><span class="sxs-lookup"><span data-stu-id="b5810-103">Add subreports to a report when you want to create a main report that is a container for multiple related reports.</span></span> <span data-ttu-id="b5810-104">サブレポートは別のレポートへの参照です。</span><span class="sxs-lookup"><span data-stu-id="b5810-104">A subreport is a reference to another report.</span></span> <span data-ttu-id="b5810-105">これらのレポートをデータ値で関係付けるには (たとえば、複数のレポートに同じ顧客のデータを表示する場合)、サブレポートとしてパラメーター化されたレポート (特定の顧客の詳細を示すレポートなど) をデザインする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5810-105">To relate the reports through data values (for example, to have multiple reports show data for the same customer), you must design a parameterized report (for example, a report that shows the details for a specific customer) as the subreport.</span></span> <span data-ttu-id="b5810-106">サブレポートをメイン レポートに追加するときは、サブレポートに渡すパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="b5810-106">When you add a subreport to the main report, you can specify parameters to pass to the subreport.</span></span>  
  
 <span data-ttu-id="b5810-107">また、サブレポートをテーブルまたはマトリックスの動的列または動的行に追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="b5810-107">You can also add subreports to dynamic rows or columns in a table or matrix.</span></span> <span data-ttu-id="b5810-108">メイン レポートを処理するとき、各行のサブレポートが処理されます。</span><span class="sxs-lookup"><span data-stu-id="b5810-108">When the main report is processed, the subreport is processed for each row.</span></span> <span data-ttu-id="b5810-109">この場合、データ領域または入れ子になったデータ領域を使用して、意図した結果が得られたか確認してください。</span><span class="sxs-lookup"><span data-stu-id="b5810-109">In this case, consider whether you can achieve the desired effect by using data regions or nested data regions.</span></span>  
  
 <span data-ttu-id="b5810-110">レポートにサブレポートを追加するには、サブレポートとして機能するレポートを最初に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5810-110">To add a subreport to a report, you must first create the report that will act as the subreport.</span></span> <span data-ttu-id="b5810-111">サブレポートの作成の詳細については、「 [サブレポート &#40;レポート ビルダーおよび SSRS&#41;](subreports-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5810-111">For more information on creating the subreport, see [Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-subreport"></a><span data-ttu-id="b5810-112">サブレポートを追加するには</span><span class="sxs-lookup"><span data-stu-id="b5810-112">To add a subreport</span></span>  
  
1.  <span data-ttu-id="b5810-113">**[挿入]** タブの **[サブレポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5810-113">On the **Insert** tab, click **Subreport**.</span></span>  
  
2.  <span data-ttu-id="b5810-114">デザイン画面でレポート上の場所をクリックし、ボックスをサブレポートの目的のサイズにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="b5810-114">On the design surface, click a location on the report and then drag a box to the desired size of the subreport.</span></span> <span data-ttu-id="b5810-115">または、デザイン画面をクリックして、既定のサイズのサブレポートを作成します。</span><span class="sxs-lookup"><span data-stu-id="b5810-115">Alternatively, click the design surface to create a subreport of default size.</span></span>  
  
3.  <span data-ttu-id="b5810-116">サブレポートを右クリックして **[サブレポートのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5810-116">Right-click the subreport, and then click **Subreport Properties**.</span></span>  
  
4.  <span data-ttu-id="b5810-117">**[サブレポートのプロパティ]** ダイアログ ボックスの **[名前]** ボックスに名前を入力するか、既定の名前をそのまま使用します。</span><span class="sxs-lookup"><span data-stu-id="b5810-117">In the **Subreport Properties** dialog box, type a name in the **Name** text box or accept the default.</span></span> <span data-ttu-id="b5810-118">名前はレポート内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5810-118">The name must be unique within the report.</span></span> <span data-ttu-id="b5810-119">既定では、Subreport1、Subreport2 など、一般的な名前が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b5810-119">By default, a general name such as Subreport1 or Subreport2 is assigned.</span></span>  
  
5.  <span data-ttu-id="b5810-120">**[次のレポートをサブレポートとして使用]** ボックスで、 **[参照]** をクリックするか、レポートの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="b5810-120">In the **Use this report as a subreport** box, click **Browse**, or type the name of the report.</span></span> <span data-ttu-id="b5810-121">**[参照]** をクリックする方法ではサブレポートへのパスが自動的に指定されるため、こちらの方法をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="b5810-121">Clicking **Browse** is preferred because the path to the subreport will be specified automatically.</span></span> <span data-ttu-id="b5810-122">レポートは、複数の方法で指定できます。</span><span class="sxs-lookup"><span data-stu-id="b5810-122">You can specify the report in the several ways.</span></span> <span data-ttu-id="b5810-123">詳細については、「[外部アイテムへのパスの指定 &#40;レポート ビルダーおよび SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5810-123">For more information, see [Specifying Paths to External Items &#40;Report Builder and SSRS&#41;](specifying-paths-to-external-items-report-builder-and-ssrs.md).</span></span>  
  
6.  <span data-ttu-id="b5810-124">(省略可) サブレポートが複数ページにまたがる場合にサブレポートの途中で罫線が表示されないようにするには、 **[改ページの罫線を省略する]** で **[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5810-124">(Optional) Click **Yes** for **Omit border on page break** to prevent a border from being rendered in the middle of the subreport if the subreport spans more than one page.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-specify-parameters-to-pass-to-a-subreport"></a><span data-ttu-id="b5810-125">サブレポートに渡すパラメーターを指定するには</span><span class="sxs-lookup"><span data-stu-id="b5810-125">To specify parameters to pass to a subreport</span></span>  
  
1.  <span data-ttu-id="b5810-126">デザイン ビューで、サブレポートを右クリックし、 **[サブレポートのプロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5810-126">In Design view, right-click the subreport and then click **Subreport Properties**.</span></span>  
  
2.  <span data-ttu-id="b5810-127">**[サブレポートのプロパティ]** ダイアログ ボックスで、 **[パラメーター]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5810-127">In the **Subreport Properties** dialog box, click **Parameters**.</span></span>  
  
3.  <span data-ttu-id="b5810-128">**[追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5810-128">Click **Add**.</span></span> <span data-ttu-id="b5810-129">パラメーター グリッドに、新しい行が追加されます。</span><span class="sxs-lookup"><span data-stu-id="b5810-129">A new row is added to the parameter grid.</span></span>  
  
4.  <span data-ttu-id="b5810-130">**[名前]** ボックスにサブレポートのパラメーターの名前を入力するか、ボックスの一覧からパラメーターを選択します。</span><span class="sxs-lookup"><span data-stu-id="b5810-130">In the **Name** text box, type the name of a parameter in the subreport or choose it from the list box.</span></span> <span data-ttu-id="b5810-131">この名前は、クエリ パラメーターではなく、サブレポートのレポート パラメーターの名前と一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5810-131">This name must match a report parameter, not a query parameter, in the subreport.</span></span>  
  
5.  <span data-ttu-id="b5810-132">**[値]** ボックスに、サブレポートに渡す値を入力するか、選択します。</span><span class="sxs-lookup"><span data-stu-id="b5810-132">In the **Value** list box, type or select a value to pass to the subreport.</span></span> <span data-ttu-id="b5810-133">この値には、静的テキストか、メイン レポートのフィールドまたは他のオブジェクトを参照する式を使用できます。</span><span class="sxs-lookup"><span data-stu-id="b5810-133">This value can be static text or an expression that references a field or other object in the main report.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b5810-134">レポート ビルダーでは、 **[パラメーター]** ボックスの一覧にパラメーターが存在せず、サブレポートに既定値が定義されている場合、サブレポートは正しく処理されます。</span><span class="sxs-lookup"><span data-stu-id="b5810-134">In Report Builder, if a parameter is missing from the **Parameters** list and the subreport has a default value defined, the subreport will be processed correctly.</span></span>  
    >   
    >  <span data-ttu-id="b5810-135">レポート デザイナーでは、サブレポートに必要なパラメーターが、 **[パラメーター]** の一覧に含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5810-135">In Report Designer, all parameters that are required by the subreport must be included in the **Parameters** list.</span></span> <span data-ttu-id="b5810-136">必要なパラメーターがない場合、サブレポートはメイン レポート内に正しく表示されません。</span><span class="sxs-lookup"><span data-stu-id="b5810-136">If a required parameter is missing, the subreport is not displayed correctly in the main report.</span></span>  
  
6.  <span data-ttu-id="b5810-137">各サブレポートのパラメーターの名前と値を指定するには、手順 3. ～ 5. を繰り返します。</span><span class="sxs-lookup"><span data-stu-id="b5810-137">Repeat steps 3-5 to specify a name and value for each subreport parameter.</span></span>  
  
7.  <span data-ttu-id="b5810-138">サブレポート パラメーターを削除するには、パラメーター グリッド内のパラメーターをクリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5810-138">To delete a subreport parameter, click the parameter in the parameter grid, and then click **Delete**.</span></span>  
  
8.  <span data-ttu-id="b5810-139">サブレポート パラメーターの順序を変更するには、パラメーターをクリックし、[上へ] ボタンまたは [下へ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="b5810-139">To change the order of a subreport parameter, click the parameter, and then click the up button or the down button.</span></span>  
  
     <span data-ttu-id="b5810-140">サブレポート パラメーターの順序を変更しても、サブレポートの処理には影響しません。</span><span class="sxs-lookup"><span data-stu-id="b5810-140">Changing the order of a subreport parameter does not affect the processing of the subreport.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5810-141">参照</span><span class="sxs-lookup"><span data-stu-id="b5810-141">See Also</span></span>  
 <span data-ttu-id="b5810-142">[サブレポート &#40;レポート ビルダーおよび SSRS&#41;](subreports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="b5810-142">[Subreports &#40;Report Builder and SSRS&#41;](subreports-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="b5810-143">レンダリングの動作 &#40;レポート ビルダーおよび SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="b5810-143">Rendering Behaviors &#40;Report Builder  and SSRS&#41;</span></span>](rendering-behaviors-report-builder-and-ssrs.md)  
  
  
