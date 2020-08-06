---
title: ディメンションへのディメンションインテリジェンスの追加 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], dimension intelligence
- dimensions [Analysis Services], Business Intelligence enhancements
- dimension intelligence [Analysis Services]
- Type property
ms.assetid: b64fa386-eac2-4286-a320-0631a1887aac
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5cad591d3e89dc306571efa9aeef9d81a235c9fa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634120"
---
# <a name="add-dimension-intelligence-to-a-dimension"></a><span data-ttu-id="f0d97-102">ディメンションへのディメンション インテリジェンスの追加</span><span class="sxs-lookup"><span data-stu-id="f0d97-102">Add Dimension Intelligence to a Dimension</span></span>
  <span data-ttu-id="f0d97-103">ディメンションに標準のビジネスの種類を指定するには、ディメンション インテリジェンス拡張機能をキューブまたはディメンションに追加します。</span><span class="sxs-lookup"><span data-stu-id="f0d97-103">Add the dimension intelligence enhancement to a cube or a dimension to specify a standard business type for a dimension.</span></span> <span data-ttu-id="f0d97-104">この拡張機能により、ディメンション属性に対応する型も指定されます。</span><span class="sxs-lookup"><span data-stu-id="f0d97-104">This enhancement also specifies the corresponding types for dimension attributes.</span></span> <span data-ttu-id="f0d97-105">クライアント アプリケーションでは、指定された種類をデータの分析時に使用できます。</span><span class="sxs-lookup"><span data-stu-id="f0d97-105">Client applications can use these type specifications when analyzing data.</span></span>  
  
 <span data-ttu-id="f0d97-106">ディメンション インテリジェンスを追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページの **[ディメンション インテリジェンスの定義]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="f0d97-106">To add dimension intelligence, you use the Business Intelligence Wizard, and select the **Define dimension intelligence** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="f0d97-107">次に、ウィザードに従って、ディメンション インテリジェンスの適用先となるディメンションを選択し、選択したディメンションの属性を識別します。</span><span class="sxs-lookup"><span data-stu-id="f0d97-107">This wizard then guides you through the steps of selecting a dimension to which you want to apply dimension intelligence and identifying the attributes for the selected dimension.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="f0d97-108">ディメンションの選択</span><span class="sxs-lookup"><span data-stu-id="f0d97-108">Selecting a Dimension</span></span>  
 <span data-ttu-id="f0d97-109">ウィザードの最初の **[ディメンション インテリジェンス オプションの設定]** ページで、ディメンション インテリジェンスの適用先になるディメンションを指定します。</span><span class="sxs-lookup"><span data-stu-id="f0d97-109">On the first **Set Dimension Intelligence Options** page of the wizard, you specify the dimension to which you want to apply dimension intelligence.</span></span> <span data-ttu-id="f0d97-110">選択したディメンションに追加されたディメンション インテリジェンス拡張機能により、ディメンションが変更されます。</span><span class="sxs-lookup"><span data-stu-id="f0d97-110">The dimension intelligence enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="f0d97-111">これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="f0d97-111">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f0d97-112">ディメンションに **[勘定科目]** を選択した場合は、ディメンションに勘定科目インテリジェンスを指定します。</span><span class="sxs-lookup"><span data-stu-id="f0d97-112">If you select **Account** as the dimension, you will be specifying account intelligence for the dimension.</span></span> <span data-ttu-id="f0d97-113">詳細については、「 [ディメンションへの勘定科目インテリジェンスの追加](bi-wizard-add-account-intelligence-to-a-dimension.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f0d97-113">For more information, see [Add Account Intelligence to a Dimension](bi-wizard-add-account-intelligence-to-a-dimension.md).</span></span>  
  
## <a name="specifying-dimension-attributes"></a><span data-ttu-id="f0d97-114">ディメンション属性の指定</span><span class="sxs-lookup"><span data-stu-id="f0d97-114">Specifying Dimension Attributes</span></span>  
 <span data-ttu-id="f0d97-115">[**ディメンションインテリジェンスの定義**] ページの [**ディメンションの種類**] ボックスの一覧で、選択したディメンションのプロパティが設定され `Type` ます。</span><span class="sxs-lookup"><span data-stu-id="f0d97-115">On the **Define Dimension Intelligence** page, in **Dimension Type** list, the selection that you make sets the dimension's `Type` property.</span></span> <span data-ttu-id="f0d97-116">`Type` プロパティの設定により、サーバーとクライアント アプリケーションにディメンションのコンテンツに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="f0d97-116">The `Type` property setting provides information to servers and client applications about the contents of a dimension.</span></span> <span data-ttu-id="f0d97-117">一部の設定はクライアント アプリケーションにガイダンス情報のみを提供するもので、これらの設定は省略できます。</span><span class="sxs-lookup"><span data-stu-id="f0d97-117">Some settings only provide guidance for client applications; these settings are optional.</span></span> <span data-ttu-id="f0d97-118">[勘定科目] や [時間] などのその他の設定は特定の動作を決定するので、特定のビジネス インテリジェンス拡張機能を実装するために必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="f0d97-118">Other settings, such as Accounts or Time, determine specific behaviors and may be required to implement particular business intelligence enhancements.</span></span> <span data-ttu-id="f0d97-119">たとえば、SQL Server Management Studio では、通貨ディメンションを識別し、適切な通貨換算規則を設定するためにディメンションの種類が使用されます。</span><span class="sxs-lookup"><span data-stu-id="f0d97-119">For example, the SQL Server Management Studio uses the dimension type to identify a Currency dimension and set the appropriate currency conversion rules.</span></span> <span data-ttu-id="f0d97-120">**[ディメンションの種類]** の既定値は **[標準]** で、ディメンションのコンテンツに関する仮定は行われません。</span><span class="sxs-lookup"><span data-stu-id="f0d97-120">The default setting for the **Dimension Type** is **Regular**, which makes no assumptions about the contents of the dimension.</span></span>  
  
 <span data-ttu-id="f0d97-121">ディメンションの種類を選択したら、 **[ディメンションの属性]** の **[追加]** 列で、ディメンションに対応する属性がある標準の属性型の隣のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f0d97-121">After selecting the dimension type, in **Dimension attributes**, in the **Include** column, select the check box next to each standard attribute type for which there is a corresponding attribute in the dimension.</span></span> <span data-ttu-id="f0d97-122">最後に、 **[ディメンションの属性]** 列で、ドロップダウン リストを展開し、選択した属性の型に対応するディメンション内の属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0d97-122">Finally, in the **Dimension Attribute** column, expand the drop-down list, and select the attribute in the dimension that corresponds to the selected attribute type.</span></span> <span data-ttu-id="f0d97-123">一覧から属性を選択すると、その属性の `Type` プロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="f0d97-123">Selecting the attribute from the list sets the attribute `Type` property for the attributes.</span></span>  
  
 <span data-ttu-id="f0d97-124">たとえば、勘定科目ディメンションにディメンション インテリジェンスを追加するには、</span><span class="sxs-lookup"><span data-stu-id="f0d97-124">For example, you want to add dimension intelligence to an Accounts dimension.</span></span> <span data-ttu-id="f0d97-125">**[ディメンションの種類]** で **[勘定科目]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="f0d97-125">In **Dimension Type**, you select **Accounts**.</span></span> <span data-ttu-id="f0d97-126">次に、このディメンションに **[勘定科目の種類]** 属性と **[勘定科目の説明]** 属性がある場合は、 **[追加]** 列で、 **[勘定科目名]** と **[勘定科目の種類]** の、各勘定科目の種類に対応するチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="f0d97-126">Then, if the dimension has **Account Type** and **Account Description** attributes, in the **Include** column, you select the check boxes for the **Account Name** and **Account Type** account types.</span></span> <span data-ttu-id="f0d97-127">さらに **[ディメンションの属性]** 列で、これらの勘定科目の種類をディメンションの **[勘定科目の説明]** 属性と **[勘定科目の種類]** 属性にそれぞれ関連付けます。</span><span class="sxs-lookup"><span data-stu-id="f0d97-127">In the **Dimension Attribute** column, you then associate these account types with the **Account Description** and **Account Type** attributes, respectively, in the dimension.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d97-128">参照</span><span class="sxs-lookup"><span data-stu-id="f0d97-128">See Also</span></span>  
 [<span data-ttu-id="f0d97-129">ビジネス インテリジェンス ウィザードを使用したタイム インテリジェンス計算の定義</span><span class="sxs-lookup"><span data-stu-id="f0d97-129">Define Time Intelligence Calculations using the Business Intelligence Wizard</span></span>](define-time-intelligence-calculations-using-the-business-intelligence-wizard.md)  
  
  
