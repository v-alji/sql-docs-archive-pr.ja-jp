---
title: 属性リレーションシップの作成、変更、または削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Analysis Services], member properties
- member properties [Analysis Services], creating
ms.assetid: 137b2f40-5dfb-4141-9110-70f961f259cb
author: minewiskan
ms.author: owend
ms.openlocfilehash: b0e25140a75feda708850a2328498fb13df28a0c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632168"
---
# <a name="create-modify-or-delete-an-attribute-relationship"></a><span data-ttu-id="444bb-102">属性リレーションシップの作成、変更、または削除</span><span class="sxs-lookup"><span data-stu-id="444bb-102">Create, Modify, or Delete an Attribute Relationship</span></span>
  <span data-ttu-id="444bb-103">**のディメンション デザイナーの** [属性リレーションシップ] [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]タブを使用すると、ディメンションの属性間の属性リレーションシップを作成、変更、または削除することができます。</span><span class="sxs-lookup"><span data-stu-id="444bb-103">You can create, modify, or delete an attribute relationship between attributes in a dimension by using the **Attribute Relationships** tab of Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-create-an-attribute-relationship"></a><span data-ttu-id="444bb-104">属性リレーションシップを作成するには</span><span class="sxs-lookup"><span data-stu-id="444bb-104">To create an Attribute Relationship</span></span>  
  
1.  <span data-ttu-id="444bb-105">ディメンション デザイナーで、属性リレーションシップの作成対象となる属性が含まれているディメンションを開きます。</span><span class="sxs-lookup"><span data-stu-id="444bb-105">In Dimension Designer, open the dimension that contains the attributes that you want to create an attribute relationship between.</span></span>  
  
2.  <span data-ttu-id="444bb-106">**[属性リレーションシップ]** タブのダイアグラムまたは **[属性]** ペインで、属性を右クリックし、 **[新しい属性リレーションシップ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="444bb-106">On the **Attribute Relationships** tab, right-click an attribute in the diagram or in the **Attributes** pane, and then select **New Attribute Relationship**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="444bb-107">**[属性]** ペインを表示するには、ツール バーの **[リスト ビューの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="444bb-107">To display the **Attributes** pane, click **Show List Views** on the toolbar.</span></span>  
  
3.  <span data-ttu-id="444bb-108">**[属性リレーションシップの作成]** ダイアログ ボックスで、基になる属性と関連属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="444bb-108">In the **Create Attribute Relationship** dialog box, select a source attribute and a related attribute.</span></span>  
  
4.  <span data-ttu-id="444bb-109">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="444bb-109">In the **Relationship type** list, select a relationship type, and then click **OK**.</span></span>  
  
### <a name="to-modify-an-attribute-relationship"></a><span data-ttu-id="444bb-110">属性リレーションシップを変更するには</span><span class="sxs-lookup"><span data-stu-id="444bb-110">To modify an Attribute Relationship</span></span>  
  
1.  <span data-ttu-id="444bb-111">ディメンション デザイナーで、変更する属性リレーションシップが含まれているディメンションを開きます。</span><span class="sxs-lookup"><span data-stu-id="444bb-111">In Dimension Designer, open the dimension that contains the attribute relationship that you want to modify.</span></span>  
  
2.  <span data-ttu-id="444bb-112">**[属性リレーションシップ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="444bb-112">Click the **Attribute Relationships** tab.</span></span>  
  
3.  <span data-ttu-id="444bb-113">ダイアグラムまたは **[属性リレーションシップ]** ペインで、属性リレーションシップを右クリックし、 **[属性リレーションシップの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="444bb-113">Right-click the attribute relationship in the diagram or in the **Attribute Relationships** pane, and select **Edit Attribute Relationship**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="444bb-114">**[属性リレーションシップ]** ペインを表示するには、ツール バーの **[リスト ビューの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="444bb-114">To display the **Attribute Relationships** pane, click **Show List Views** on the toolbar.</span></span>  
  
4.  <span data-ttu-id="444bb-115">**[属性リレーションシップの編集]** ダイアログ ボックスで、基になる属性と関連属性を選択します。</span><span class="sxs-lookup"><span data-stu-id="444bb-115">In the **Edit Attribute Relationship** dialog box, select a source attribute and a related attribute.</span></span>  
  
5.  <span data-ttu-id="444bb-116">**[リレーションシップの種類]** ボックスの一覧で、リレーションシップの種類を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="444bb-116">In the **Relationship type** list, select a relationship type, and then click **OK**.</span></span>  
  
### <a name="to-delete-an-attribute-relationship"></a><span data-ttu-id="444bb-117">属性リレーションシップを削除するには</span><span class="sxs-lookup"><span data-stu-id="444bb-117">To delete an Attribute Relationship</span></span>  
  
1.  <span data-ttu-id="444bb-118">ディメンション デザイナーで、削除する属性リレーションシップが含まれているディメンションを開きます。</span><span class="sxs-lookup"><span data-stu-id="444bb-118">In Dimension Designer, open the dimension that contains the attribute relationship that you want to delete.</span></span>  
  
2.  <span data-ttu-id="444bb-119">**[属性リレーションシップ]** タブのダイアグラムまたは **[属性リレーションシップ]** ペインで、属性リレーションシップを右クリックし、 **[削除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="444bb-119">On the **Attribute Relationships** tab, right-click the attribute relationship in the diagram or in the **Attribute Relationships** pane, and then select **Delete**.</span></span>  
  
3.  <span data-ttu-id="444bb-120">**[オブジェクトの削除]** ダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="444bb-120">In the **Delete Objects** dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="444bb-121">参照</span><span class="sxs-lookup"><span data-stu-id="444bb-121">See Also</span></span>  
 <span data-ttu-id="444bb-122">[のディメンション デザイナーでは、[ディメンション構造] ビューの](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)</span><span class="sxs-lookup"><span data-stu-id="444bb-122">[Attribute Relationships](../multidimensional-models-olap-logical-dimension-objects/attribute-relationships.md)</span></span>  
  
  
