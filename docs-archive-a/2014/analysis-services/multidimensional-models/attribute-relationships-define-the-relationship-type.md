---
title: 属性リレーションシップのリレーションシップの種類を定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- removing member properties
- deleting member properties
- member properties [Analysis Services], adding
- adding member properties
- member properties [Analysis Services], removing
ms.assetid: 893a9084-d0fe-425c-b251-7518d3b3b65b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 605ba513b7cd47d9e719a619de4ebfb745360ba6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87632165"
---
# <a name="define-the-relationship-type-of-an-attribute-relationship"></a><span data-ttu-id="a56f6-102">属性リレーションシップの種類の定義</span><span class="sxs-lookup"><span data-stu-id="a56f6-102">Define the Relationship Type of an Attribute Relationship</span></span>
  <span data-ttu-id="a56f6-103">属性リレーションシップのリレーションシップの種類を定義するには、ディメンション デザイナーの **[属性リレーションシップ]** タブを使用します。ディメンション デザイナーには、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]からアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="a56f6-103">You define the relationship type of an attribute relationship by using the **Attribute Relationships** tab in Dimension Designer, which can be accessed from [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
### <a name="to-set-the-relationship-type-of-an-attribute-relationship"></a><span data-ttu-id="a56f6-104">属性リレーションシップのリレーションシップの種類を設定するには</span><span class="sxs-lookup"><span data-stu-id="a56f6-104">To set the relationship type of an attribute relationship</span></span>  
  
1.  <span data-ttu-id="a56f6-105">ディメンション デザイナーで、作業するディメンションを開き、 **[属性リレーションシップ]** タブをクリックします。</span><span class="sxs-lookup"><span data-stu-id="a56f6-105">In Dimension Designer, open the dimension with which you want to work, and then click on the **Attribute Relationships** tab.</span></span>  
  
2.  <span data-ttu-id="a56f6-106">ダイアグラムまたは **[属性リレーションシップ]** ペインで、属性リレーションシップを右クリックし、 **[リレーションシップの種類]** をクリックして、 **[可変]** または **[固定]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a56f6-106">In the diagram or in the **Attribute Relationships** pane, right-click the attribute relationship, click **Relationship Type**, and then click either **Flexible** or **Rigid**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="a56f6-107">**[属性リレーションシップ]** ペインを表示するには、ツール バーの **[リスト ビューの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a56f6-107">To display the **Attribute Relationships** pane, click **Show List Views** on the toolbar.</span></span>  
  
     <span data-ttu-id="a56f6-108">可変のリレーションシップでは、メンバー間のリレーションシップが時間の経過と共に変化します。</span><span class="sxs-lookup"><span data-stu-id="a56f6-108">In a flexible relationship, relationships between members change over time.</span></span> <span data-ttu-id="a56f6-109">固定のリレーションシップでは、メンバー間のリレーションシップが時間の経過と共に変化しません。</span><span class="sxs-lookup"><span data-stu-id="a56f6-109">In a rigid relationship, relationships between members do not change over time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a56f6-110">参照</span><span class="sxs-lookup"><span data-stu-id="a56f6-110">See Also</span></span>  
 [<span data-ttu-id="a56f6-111">属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="a56f6-111">Define Attribute Relationships</span></span>](attribute-relationships-define.md)  
  
  
