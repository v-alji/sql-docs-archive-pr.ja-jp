---
title: データソースに時間テーブル以外のテーブルを生成してディメンションを作成する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data sources [Analysis Services], dimensions without data source
- dimensions [Analysis Services], standard
- dimensions [Analysis Services], creating without data source
- standard dimensions [Analysis Services]
ms.assetid: a37f7a46-7451-4582-ba19-2595196d97bc
author: minewiskan
ms.author: owend
ms.openlocfilehash: 49dbfb0c1fc15c1cbf703514e0fc693dfabf1e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737062"
---
# <a name="create-a-dimension-by-generating-a-non-time-table-in-the-data-source"></a><span data-ttu-id="739ba-102">データ ソースに時間テーブル以外のテーブルを生成することによるディメンションの作成</span><span class="sxs-lookup"><span data-stu-id="739ba-102">Create a Dimension by Generating a Non-Time Table in the Data Source</span></span>
  <span data-ttu-id="739ba-103">では [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 、のディメンションウィザードを使用し [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] て、既存のデータソースを使用せずにディメンションを作成できます。</span><span class="sxs-lookup"><span data-stu-id="739ba-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], you can use the Dimension Wizard in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to create a dimension without using an existing data source.</span></span> <span data-ttu-id="739ba-104">この操作を行うには、ウィザードの **[作成方法の選択]** ページで **[データ ソースに時間テーブル以外のテーブルを生成]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="739ba-104">You do this by selecting the **Generate a non-time table in the data source** option of the **Select Creation Method** page of the wizard.</span></span> <span data-ttu-id="739ba-105">基になるデータ ソースに新しいディメンション テーブルを作成するには、基になるデータ ソースにオブジェクトを作成する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="739ba-105">To create a new dimension table in the underlying data source, you must have permission to create objects in the underlying data source.</span></span> <span data-ttu-id="739ba-106">定義済みのデータ ソース ビューを使用せずにディメンションを定義する場合、ディメンションを最初から定義することも、ディメンション テンプレートを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="739ba-106">When defining a dimension without a predefined data source view, you can either define the dimension from scratch or use a dimension template.</span></span>  
  
 <span data-ttu-id="739ba-107">ディメンション ウィザードで提供されるサンプルのディメンション テンプレートから、一般的に使用される種類のディメンションを構築できます。</span><span class="sxs-lookup"><span data-stu-id="739ba-107">The Dimension Wizard provides sample dimension templates from which you can build a common dimension type.</span></span> <span data-ttu-id="739ba-108">次のディメンションの種類から選択できます。</span><span class="sxs-lookup"><span data-stu-id="739ba-108">You can select from the following types of dimensions:</span></span>  
  
-   <span data-ttu-id="739ba-109">Account</span><span class="sxs-lookup"><span data-stu-id="739ba-109">Account</span></span>  
  
-   <span data-ttu-id="739ba-110">Customer</span><span class="sxs-lookup"><span data-stu-id="739ba-110">Customer</span></span>  
  
-   <span data-ttu-id="739ba-111">Date</span><span class="sxs-lookup"><span data-stu-id="739ba-111">Date</span></span>  
  
-   <span data-ttu-id="739ba-112">部署</span><span class="sxs-lookup"><span data-stu-id="739ba-112">Department</span></span>  
  
-   <span data-ttu-id="739ba-113">Destination Currency</span><span class="sxs-lookup"><span data-stu-id="739ba-113">Destination Currency</span></span>  
  
-   <span data-ttu-id="739ba-114">Employee</span><span class="sxs-lookup"><span data-stu-id="739ba-114">Employee</span></span>  
  
-   <span data-ttu-id="739ba-115">[地理的な場所]</span><span class="sxs-lookup"><span data-stu-id="739ba-115">Geography</span></span>  
  
-   <span data-ttu-id="739ba-116">Internet Sales Order Details</span><span class="sxs-lookup"><span data-stu-id="739ba-116">Internet Sales Order Details</span></span>  
  
-   <span data-ttu-id="739ba-117">組織</span><span class="sxs-lookup"><span data-stu-id="739ba-117">Organization</span></span>  
  
-   <span data-ttu-id="739ba-118">Product</span><span class="sxs-lookup"><span data-stu-id="739ba-118">Product</span></span>  
  
-   <span data-ttu-id="739ba-119">Promotion</span><span class="sxs-lookup"><span data-stu-id="739ba-119">Promotion</span></span>  
  
-   <span data-ttu-id="739ba-120">Reseller Sales Order Details</span><span class="sxs-lookup"><span data-stu-id="739ba-120">Reseller Sales Order Details</span></span>  
  
-   <span data-ttu-id="739ba-121">Reseller</span><span class="sxs-lookup"><span data-stu-id="739ba-121">Reseller</span></span>  
  
-   <span data-ttu-id="739ba-122">Sales Channel</span><span class="sxs-lookup"><span data-stu-id="739ba-122">Sales Channel</span></span>  
  
-   <span data-ttu-id="739ba-123">Sales Reason</span><span class="sxs-lookup"><span data-stu-id="739ba-123">Sales Reason</span></span>  
  
-   <span data-ttu-id="739ba-124">Sales Summary Order Details</span><span class="sxs-lookup"><span data-stu-id="739ba-124">Sales Summary Order Details</span></span>  
  
-   <span data-ttu-id="739ba-125">Sales Territory</span><span class="sxs-lookup"><span data-stu-id="739ba-125">Sales Territory</span></span>  
  
-   <span data-ttu-id="739ba-126">シナリオ</span><span class="sxs-lookup"><span data-stu-id="739ba-126">Scenario</span></span>  
  
-   <span data-ttu-id="739ba-127">Source Currency</span><span class="sxs-lookup"><span data-stu-id="739ba-127">Source Currency</span></span>  
  
 <span data-ttu-id="739ba-128">それぞれの標準テンプレートでは、ディメンションに含めるように選択できる属性がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="739ba-128">Each of the standard templates supports attributes that you can choose to include in the dimension.</span></span> <span data-ttu-id="739ba-129">また、データでよく使用するディメンションの独自のテンプレート ファイルを追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="739ba-129">You can also add your own template files for dimensions that are commonly used with your data.</span></span> <span data-ttu-id="739ba-130">ディメンション テンプレートは次のフォルダーにあります。</span><span class="sxs-lookup"><span data-stu-id="739ba-130">The dimension templates are located in the following folder:</span></span>  
  
 `C:\Program Files\Microsoft SQL Server\100\Tools\Templates\olap\1033\Dimension Templates`  
  
 <span data-ttu-id="739ba-131">ディメンション ウィザードを完了した後、ディメンション デザイナーを使用して、ディメンションの属性と階層を追加、削除、および設定できます。</span><span class="sxs-lookup"><span data-stu-id="739ba-131">You can use Dimension Designer after you complete the Dimension Wizard to add, remove, and configure attributes and hierarchies in the dimension.</span></span>  
  
 <span data-ttu-id="739ba-132">データ ソースを使用せずに時間ディメンション以外のディメンションを作成している場合、ディメンション ウィザードでは、ディメンションの種類を指定し、キー属性と緩やかに変化するディメンションを識別する手順が示されます。</span><span class="sxs-lookup"><span data-stu-id="739ba-132">When you are creating a non-time dimension without using a data source, the Dimension Wizard guides you through the steps of specifying the dimension type, and identifying the key attribute and slowly changing dimensions.</span></span>  
  
## <a name="specify-dimension-type"></a><span data-ttu-id="739ba-133">ディメンションの種類の指定</span><span class="sxs-lookup"><span data-stu-id="739ba-133">Specify Dimension Type</span></span>  
 <span data-ttu-id="739ba-134">ディメンション ウィザードの **[ディメンションの種類を指定]** ページでは、ディメンションの種類を指定できます。</span><span class="sxs-lookup"><span data-stu-id="739ba-134">On the **Specify Dimension Type** page of the Dimension Wizard, you can specify the dimension type.</span></span> <span data-ttu-id="739ba-135">テンプレートを基にディメンションを構築している場合、ディメンションの種類は自動的に定義されます。</span><span class="sxs-lookup"><span data-stu-id="739ba-135">If you are building the dimension based on a template, the dimension type is defined for you.</span></span> <span data-ttu-id="739ba-136">このページでは、指定したディメンションの種類に標準的な属性があれば、選択することもできます。</span><span class="sxs-lookup"><span data-stu-id="739ba-136">On this page, you can also select standard attributes for the specified dimension type if any are available.</span></span>  
  
 <span data-ttu-id="739ba-137">ディメンションの種類に対応するテンプレートを選択した場合は、そのディメンションの種類のオプションでこのページが作成されます。</span><span class="sxs-lookup"><span data-stu-id="739ba-137">If you selected a template that corresponds to a dimension type, this page is populated with the options for that dimension type.</span></span> <span data-ttu-id="739ba-138">テンプレートを選択しなかった場合や、該当するディメンションの種類がない場合、既定のディメンションの種類は **[標準]** です。</span><span class="sxs-lookup"><span data-stu-id="739ba-138">If you did not select a template, or if there is no corresponding dimension type, the default dimension type is **Regular**.</span></span> <span data-ttu-id="739ba-139">ディメンションの種類がまだ選択されていない場合は、作成するディメンションに最適な種類を選択します。</span><span class="sxs-lookup"><span data-stu-id="739ba-139">If a dimension type is not already selected, select the most appropriate type for the dimension that you are creating.</span></span> <span data-ttu-id="739ba-140">適切な種類が **[ディメンションの種類]** の一覧に表示されていない場合は、 **[標準]** を使用します。</span><span class="sxs-lookup"><span data-stu-id="739ba-140">If no appropriate type is listed for **Dimension type**, use **Regular**.</span></span>  
  
 <span data-ttu-id="739ba-141">ディメンションの種類を選択すると、そのディメンションに適用する属性の型が **[ディメンションの属性]** ボックスの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="739ba-141">When you select a dimension type, the wizard lists the attribute types that apply to this dimension under **Dimension attributes**.</span></span> <span data-ttu-id="739ba-142">属性の型を選択するには、属性の型の横にある **[追加]** チェック ボックスをオンにし、 **[ディメンションの属性]** で属性名を入力します。</span><span class="sxs-lookup"><span data-stu-id="739ba-142">To select an attribute type, select the **Include** check box next to the attribute type, and type the name for the attribute under **Dimension Attribute**.</span></span> <span data-ttu-id="739ba-143">既定の名前は、 **[属性の型]** の値と同じです。</span><span class="sxs-lookup"><span data-stu-id="739ba-143">The default name is the same as **Attribute Type**.</span></span>  
  
## <a name="identify-key-attribute-and-changing-dimensions"></a><span data-ttu-id="739ba-144">キー属性と変化するディメンションの識別</span><span class="sxs-lookup"><span data-stu-id="739ba-144">Identify Key Attribute and Changing Dimensions</span></span>  
 <span data-ttu-id="739ba-145">**[ディメンションのキーおよび種類を指定]** ページで、ディメンションのキー属性とする属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="739ba-145">On the **Specify Dimension Key and Type** page, select the attribute that you want to be the key attribute for the dimension.</span></span> <span data-ttu-id="739ba-146">通常、キー属性はメイン ディメンション テーブルの主キー列に対応しており、ディメンションのリーフ メンバーのインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="739ba-146">The key attribute typically corresponds to the primary key column in the main dimension table, and it typically indexes the leaf members of the dimension.</span></span>  
  
 <span data-ttu-id="739ba-147">テンプレートを選択しており、そのテンプレートでキー属性が定義されている場合は、その属性が既定のキー属性となります。</span><span class="sxs-lookup"><span data-stu-id="739ba-147">If you selected a template, and a key attribute is defined in the template, that attribute is the default key attribute.</span></span> <span data-ttu-id="739ba-148">テンプレートを選択しても、そのテンプレートでキー属性が定義されていない場合は、一覧の先頭の属性が既定となります。</span><span class="sxs-lookup"><span data-stu-id="739ba-148">If you selected a template but no key attribute is defined in the template, the default is the first attribute in the list.</span></span> <span data-ttu-id="739ba-149">この一覧には、 **[ディメンションの種類を指定]** ページで選択したすべての属性が含まれます。</span><span class="sxs-lookup"><span data-stu-id="739ba-149">The list contains all the attributes that you selected on the **Specify Dimension Type** page.</span></span> <span data-ttu-id="739ba-150">**[ディメンションの種類を指定]** ページで選択したどの属性も、キー属性に選択できます。</span><span class="sxs-lookup"><span data-stu-id="739ba-150">You can select any one of the attributes that you selected on the **Specify Dimension Type** page to be the key attribute.</span></span> <span data-ttu-id="739ba-151">属性を選択しなかった場合は、ウィザードによってキー属性が自動的に作成され、ディメンション名と "ID" を連結した名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="739ba-151">If you did not select any attributes, the wizard automatically creates a key attribute and names it by concatenating the dimension name and "ID".</span></span>  
  
 <span data-ttu-id="739ba-152">最後に、このディメンションが変化するディメンションかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="739ba-152">Finally, specify whether this dimension is a changing dimension.</span></span> <span data-ttu-id="739ba-153">変化するディメンションのメンバーは、時間の経過と共に階層内の別の場所に移動します。</span><span class="sxs-lookup"><span data-stu-id="739ba-153">Members in a changing dimension move over time to different locations in the hierarchy.</span></span> <span data-ttu-id="739ba-154">ウィザードでは、追加の列が生成され、それらの列に対応する属性が作成されます。</span><span class="sxs-lookup"><span data-stu-id="739ba-154">The wizard generates additional columns and creates attributes that correspond to those columns.</span></span> <span data-ttu-id="739ba-155">こうした列を使用すると、ユーザーは、変更を考慮してディメンションに対するクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="739ba-155">These columns will let users query the dimension in such a way as to factor in the change.</span></span> <span data-ttu-id="739ba-156">スキーマ生成ウィザードを使用して後で作成するパッケージでは、緩やかに変化するディメンションの特性に基づき、代理キーが管理されます。</span><span class="sxs-lookup"><span data-stu-id="739ba-156">Any packages that you subsequently create with the Schema Generation Wizard manage surrogate keys based on slowly changing dimension characteristics of the dimension.</span></span>  
  
 <span data-ttu-id="739ba-157">**[変化するディメンション]** チェック ボックスをオンにすると、ディメンション ウィザードでは、次の表に示す属性が定義されます。</span><span class="sxs-lookup"><span data-stu-id="739ba-157">When you select the **This is a changing dimension** check box, the Dimension Wizard defines the attributes indicated in the following table:</span></span>  
  
|<span data-ttu-id="739ba-158">属性</span><span class="sxs-lookup"><span data-stu-id="739ba-158">Attribute</span></span>|<span data-ttu-id="739ba-159">Type</span><span class="sxs-lookup"><span data-stu-id="739ba-159">Type</span></span>|  
|---------------|----------|  
|<span data-ttu-id="739ba-160">SCD のオリジナル ID</span><span class="sxs-lookup"><span data-stu-id="739ba-160">SCD OriginalID</span></span>|<span data-ttu-id="739ba-161">SCDOriginalID</span><span class="sxs-lookup"><span data-stu-id="739ba-161">SCDOriginalID</span></span>|  
|<span data-ttu-id="739ba-162">SCD の終了日</span><span class="sxs-lookup"><span data-stu-id="739ba-162">SCD End Date</span></span>|<span data-ttu-id="739ba-163">SCDEndDate</span><span class="sxs-lookup"><span data-stu-id="739ba-163">SCDEndDate</span></span>|  
|<span data-ttu-id="739ba-164">SCD の開始日</span><span class="sxs-lookup"><span data-stu-id="739ba-164">SCD Start Date</span></span>|<span data-ttu-id="739ba-165">SCDStartDate</span><span class="sxs-lookup"><span data-stu-id="739ba-165">SCDStartDate</span></span>|  
|<span data-ttu-id="739ba-166">SCD ステータス</span><span class="sxs-lookup"><span data-stu-id="739ba-166">SCD Status</span></span>|<span data-ttu-id="739ba-167">SCDStatus</span><span class="sxs-lookup"><span data-stu-id="739ba-167">SCDStatus</span></span>|  
  
 <span data-ttu-id="739ba-168">既定では、緩やかに変化するディメンションのこれらの属性が定義されているテンプレートを使用する場合、 **[変化するディメンション]** チェック ボックスがオンになっています。</span><span class="sxs-lookup"><span data-stu-id="739ba-168">By default, the **This is a changing dimension** check box is selected if you use a template that has these slowly changing dimension attributes defined.</span></span> <span data-ttu-id="739ba-169">チェック ボックスをオフにすると、緩やかに変化するディメンション属性はディメンションから削除されます。</span><span class="sxs-lookup"><span data-stu-id="739ba-169">If you clear the check box, the slowly changing dimension attributes are removed from the dimension.</span></span>  
  
 <span data-ttu-id="739ba-170">ディメンション デザイナーを使用すると、緩やかに変化するディメンションのプロパティを構成できます。</span><span class="sxs-lookup"><span data-stu-id="739ba-170">You can use Dimension Designer to configure properties for a slowly changing dimension.</span></span>  
  
## <a name="completing-the-dimension-wizard"></a><span data-ttu-id="739ba-171">ディメンション ウィザードの完了</span><span class="sxs-lookup"><span data-stu-id="739ba-171">Completing the Dimension Wizard</span></span>  
 <span data-ttu-id="739ba-172">**[ウィザードの完了]** ページで、新しいディメンションの名前を入力し、ディメンション構造を表示します。</span><span class="sxs-lookup"><span data-stu-id="739ba-172">On the **Completing the Wizard** page, type a name for the new dimension and view the dimension structure.</span></span> <span data-ttu-id="739ba-173">**[完了]** をクリックした後にスキーマ生成ウィザードを開始するには、 **[今すぐスキーマを生成する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="739ba-173">Select the **Generate schema now** check box to start the Schema Generation Wizard after you click **Finish**.</span></span> <span data-ttu-id="739ba-174">追加オブジェクトを作成する計画がある場合は、このチェック ボックスはオンにしないでください。</span><span class="sxs-lookup"><span data-stu-id="739ba-174">In most cases, you should not select this check box if you plan to create additional objects.</span></span> <span data-ttu-id="739ba-175">このチェック ボックスを選択しない場合は、ディメンション デザイナーを使用して後でスキーマを作成できます。</span><span class="sxs-lookup"><span data-stu-id="739ba-175">If you do not select this check box, you can use Dimension Designer to generate the schema later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="739ba-176">参照</span><span class="sxs-lookup"><span data-stu-id="739ba-176">See Also</span></span>  
 <span data-ttu-id="739ba-177">[時間テーブルを生成して時間ディメンションを作成する](create-a-time-dimension-by-generating-a-time-table.md) </span><span class="sxs-lookup"><span data-stu-id="739ba-177">[Create a Time Dimension by Generating a Time Table](create-a-time-dimension-by-generating-a-time-table.md) </span></span>  
 [<span data-ttu-id="739ba-178">Create a Time Dimension by Generating a Time Table</span><span class="sxs-lookup"><span data-stu-id="739ba-178">Create a Time Dimension by Generating a Time Table</span></span>](create-a-time-dimension-by-generating-a-time-table.md)  
  
  
