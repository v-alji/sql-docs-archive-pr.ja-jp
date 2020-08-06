---
title: 属性 | の KeyColumn プロパティを変更します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- binding attributes [Analysis Services]
- attributes [Analysis Services], binding
- key columns [Analysis Services]
ms.assetid: a2643be4-8123-4cc3-baf9-e5ec54a1669d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3367a7aec84ba59efd118a56745bb76fc5266061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741433"
---
# <a name="modify-the-keycolumn-property-of-an-attribute"></a><span data-ttu-id="fa1ea-102">属性の KeyColumns プロパティの変更</span><span class="sxs-lookup"><span data-stu-id="fa1ea-102">Modify the KeyColumn Property of an Attribute</span></span>
  <span data-ttu-id="fa1ea-103">属性の **KeyColumns** プロパティは変更できます。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-103">You can modify the **KeyColumns** property of an attribute.</span></span> <span data-ttu-id="fa1ea-104">たとえば、単一キーではなく複合キーをその属性のキーとして指定する場合があります。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-104">For example, you might want to specify a composite key instead of a single key as the key for the attribute.</span></span>  
  
### <a name="to-modify-the-keycolumns-property-of-an-attribute"></a><span data-ttu-id="fa1ea-105">属性の KeyColumns プロパティを変更するには</span><span class="sxs-lookup"><span data-stu-id="fa1ea-105">To modify the KeyColumns property of an attribute</span></span>  
  
1.  <span data-ttu-id="fa1ea-106">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]で、 **KeyColumns** プロパティを変更するプロジェクトを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-106">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project in which you want to modify the **KeyColumns** property.</span></span>  
  
2.  <span data-ttu-id="fa1ea-107">次のいずれかの手順を実行して、ディメンション デザイナーを開きます。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-107">Open Dimension Designer by doing one of the following procedures:</span></span>  
  
    -   <span data-ttu-id="fa1ea-108">**ソリューション エクスプローラー**では、 **[ディメンション]** フォルダー内のディメンションを右クリックし、 **[開く]** または **[デザイナーの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-108">In **Solution Explorer**, right-click the dimension in the **Dimensions** folder, and then either click **Open** or **View Designer**.</span></span>  
  
         <span data-ttu-id="fa1ea-109">または</span><span class="sxs-lookup"><span data-stu-id="fa1ea-109">-or-</span></span>  
  
    -   <span data-ttu-id="fa1ea-110">キューブデザイナーの [**キューブ構造**] タブで、[**ディメンション**] ペインのキューブディメンションを展開し、[\*\*編集 \<dimension> \*\*] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-110">In Cube Designer, on the **Cube Structure** tab, expand the cube dimension in the **Dimensions** pane and click **Edit \<dimension>**.</span></span>  
  
3.  <span data-ttu-id="fa1ea-111">**[ディメンション構造]** タブの **[属性]** ペインで、変更する **KeyColumns** プロパティを含む属性をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-111">On the **Dimension Structure** tab, in the **Attributes** pane, click the attribute whose **KeyColumns** property you want to modify.</span></span>  
  
4.  <span data-ttu-id="fa1ea-112">**[プロパティ]** ウィンドウで、 **KeyColumns** プロパティの値をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-112">In the **Properties** window, click the value for the **KeyColumns** property.</span></span>  
  
5.  <span data-ttu-id="fa1ea-113">プロパティ ボックスの値のセルに表示される参照ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-113">Click the browse **(...)** button that appears in the value cell of the property box.</span></span>  
  
     <span data-ttu-id="fa1ea-114">**[キー列]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-114">The **Key Columns** dialog box opens.</span></span>  
  
6.  <span data-ttu-id="fa1ea-115">既存のキー列を削除するには、**[キー列]** の一覧で列を選択し、**[\<]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-115">To remove an existing key column, in the **Key Columns** list, select the column, and then click the **\<** button.</span></span>  
  
7.  <span data-ttu-id="fa1ea-116">キー列を追加するには、**[使用できる列]** の一覧で列を選択し、**[>]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-116">To add a key column, in the **Available Columns** list, select the column, and then click the **>** button.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="fa1ea-117">複数のキー列を定義する場合、 **[キー列]** の一覧での列の順序が表示順序に影響します。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-117">If you define multiple key columns, the order in which those columns appear in the **Key Columns** list affects the display order.</span></span> <span data-ttu-id="fa1ea-118">たとえば、Month 属性には、月および年という 2 つのキー列があります。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-118">For example, a month attribute has two key columns: month and year.</span></span> <span data-ttu-id="fa1ea-119">一覧で年の列が月の列よりも前に表示される場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] により、まず年順に並べ替えられ、続いて月順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-119">If the year column appears in the list before the month column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will sort by year and then by month.</span></span> <span data-ttu-id="fa1ea-120">月の列が年の列よりも前に表示される場合は、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] により、まず月順に並べ替えられ、続いて年順に並べ替えられます。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-120">If the month column appears before the year column, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will sort by month and then by year.</span></span>  
  
8.  <span data-ttu-id="fa1ea-121">キー列の順序を変更するには、列を選択し、 **[上へ]** または **[下へ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fa1ea-121">To change the order of key columns, select a column, and then click the **Up** or **Down** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa1ea-122">参照</span><span class="sxs-lookup"><span data-stu-id="fa1ea-122">See Also</span></span>  
 [<span data-ttu-id="fa1ea-123">ディメンションの属性のプロパティの参照</span><span class="sxs-lookup"><span data-stu-id="fa1ea-123">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
  
  
