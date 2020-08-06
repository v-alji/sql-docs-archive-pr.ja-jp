---
title: ディメンションの属性にカスタムメンバー式を設定する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Business Intelligence enhancements [Analysis Services], custom member formulas
- member formulas [Analysis Services]
- dimensions [Analysis Services], Business Intelligence enhancements
- custom member formulas [Analysis Services]
- CustomRollupColumn property
ms.assetid: c4467b08-ce59-4de7-a2d9-c22e246bdd52
author: minewiskan
ms.author: owend
ms.openlocfilehash: 112f8944bd20b2b6a464b0d84fb8ac1a0e89d976
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634119"
---
# <a name="set-custom-member-formulas-for-attributes-in-a-dimension"></a><span data-ttu-id="3ee6b-102">ディメンションの属性に対するカスタム メンバー式の設定</span><span class="sxs-lookup"><span data-stu-id="3ee6b-102">Set Custom Member Formulas for Attributes in a Dimension</span></span>
  <span data-ttu-id="3ee6b-103">キューブまたはディメンションにカスタム メンバー式の拡張機能を追加して、多次元式 (MDX) の式の結果を持つディメンション メンバーに関連付けられている既定の集計を置換します</span><span class="sxs-lookup"><span data-stu-id="3ee6b-103">Add a custom member formula enhancement to a cube or dimension to replace the default aggregation that is associated with a dimension member with the results of a Multidimensional Expressions (MDX) expression.</span></span> <span data-ttu-id="3ee6b-104">(この拡張機能により、ディメンションの指定した属性で `CustomRollupColumn` プロパティが設定されます)。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-104">(This enhancement sets the `CustomRollupColumn` property on a specified attribute in a dimension.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3ee6b-105">カスタム メンバー式は、既存のデータ ソースを基にしたディメンションのみに使用できます。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-105">A custom member formula is available only for dimensions that are based on existing data sources.</span></span> <span data-ttu-id="3ee6b-106">データ ソースを使用せずに作成されたディメンションに対しては、スキーマ生成ウィザードを実行し、データ ソース ビューを作成してからカスタム メンバー式を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-106">For dimensions that were created without using a data source, you must run the Schema Generation Wizard to create a data source view before adding a custom member formula.</span></span>  
  
 <span data-ttu-id="3ee6b-107">カスタム メンバー式を追加するには、ビジネス インテリジェンス ウィザードを使用して、 **[拡張機能の選択]** ページで **[カスタム メンバー式の作成]** オプションを選択します。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-107">To add a custom member formula, you use the Business Intelligence Wizard, and select the **Create a custom member formula** option on the **Choose Enhancement** page.</span></span> <span data-ttu-id="3ee6b-108">このウィザードでは、カスタム メンバー式の適用先となるディメンションを選択し、カスタム メンバー式を有効にする手順が示されます。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-108">This wizard then guides you through the steps of selecting a dimension to which you want to apply a custom member formula and enabling the custom member formula.</span></span>  
  
## <a name="selecting-a-dimension"></a><span data-ttu-id="3ee6b-109">ディメンションの選択</span><span class="sxs-lookup"><span data-stu-id="3ee6b-109">Selecting a Dimension</span></span>  
 <span data-ttu-id="3ee6b-110">ウィザードの最初の **[カスタム メンバー式の作成]** ページで、カスタム メンバー式の適用先となるディメンションを指定します。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-110">On the first **Create a Custom Member Formula** page of the wizard, you specify the dimension to which you want to apply a custom member formula.</span></span> <span data-ttu-id="3ee6b-111">この選択したディメンションに追加されるカスタム メンバー式の拡張機能が、ディメンションへの変更内容になります。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-111">The custom member formula enhancement added to this selected dimension will result in changes to the dimension.</span></span> <span data-ttu-id="3ee6b-112">これらの変更は、選択したディメンションを含むすべてのキューブによって継承されます。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-112">These changes will be inherited by all cubes that include the selected dimension.</span></span>  
  
## <a name="enabling-a-custom-member-formula"></a><span data-ttu-id="3ee6b-113">カスタム メンバー式の有効化</span><span class="sxs-lookup"><span data-stu-id="3ee6b-113">Enabling a Custom Member Formula</span></span>  
 <span data-ttu-id="3ee6b-114">**[カスタム メンバー式の作成]** の 2 ページ目で、カスタム メンバー式が含まれている基になる列を、ディメンションの 1 つまたは複数の属性に関連付けます。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-114">On the second **Create a Custom Member Formula** page, you associate the source column that contains the custom member formula with one or more attributes in the dimension.</span></span> <span data-ttu-id="3ee6b-115">**[属性]** 列で、カスタム メンバー式の列に関連付ける属性の横のチェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-115">In the **Attribute** column, select the check box next to the attribute that you want to associate with the custom member formula column.</span></span> <span data-ttu-id="3ee6b-116">各属性を選択すると、ウィザードに **[列の選択]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-116">After you select each attribute, the wizard displays the **Select a Column** dialog box.</span></span> <span data-ttu-id="3ee6b-117">このダイアログ ボックスで、式が含まれているディメンション テーブルの列をクリックします。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-117">In this dialog box, click the column in the dimension table that contains the formula.</span></span> <span data-ttu-id="3ee6b-118">**[列の選択]** ダイアログ ボックスを閉じた後で選択を変更する場合は、変更する **[基になる列]** セルをクリックし、省略記号 (**[...]**) をクリックして **[列の選択]** ダイアログ ボックスを再び開きます。</span><span class="sxs-lookup"><span data-stu-id="3ee6b-118">If you want to change a selection after you close the **Select a Column** dialog box, click the **Source Column** cell that you want to change, and then click the ellipsis (**...**) to open the **Select a Column** dialog box again.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee6b-119">参照</span><span class="sxs-lookup"><span data-stu-id="3ee6b-119">See Also</span></span>  
 [<span data-ttu-id="3ee6b-120">ビジネス インテリジェンス ウィザードを使用したディメンションの拡張</span><span class="sxs-lookup"><span data-stu-id="3ee6b-120">Use the Business Intelligence Wizard to Enhance Dimensions</span></span>](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
  
  
