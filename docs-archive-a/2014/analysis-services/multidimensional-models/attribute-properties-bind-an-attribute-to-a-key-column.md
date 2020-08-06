---
title: キー列に属性をバインドする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- names [Analysis Services], attributes
- renaming attributes
- attributes [Analysis Services], renaming
ms.assetid: c0b0abaa-5c9b-4182-9d5f-fc16cd941d54
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f909dae8db02007ee69a240d0b29c6c5cc566d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645877"
---
# <a name="bind-an-attribute-to-a-key-column"></a><span data-ttu-id="875bb-102">キー列への属性のバインド</span><span class="sxs-lookup"><span data-stu-id="875bb-102">Bind an attribute to a Key column</span></span>
  <span data-ttu-id="875bb-103">この手順では、ディメンション内にある属性の `Name` プロパティの設定を変更する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="875bb-103">This procedure describes how to change the setting for the `Name` property of an attribute in a dimension.</span></span>  
  
### <a name="to-bind-an-attribute-to-a-key-column"></a><span data-ttu-id="875bb-104">キー列に属性をバインドするには</span><span class="sxs-lookup"><span data-stu-id="875bb-104">To bind an attribute to a key column</span></span>  
  
1.  <span data-ttu-id="875bb-105">ディメンション デザイナーで、名前を変更する属性が含まれているディメンションを開きます。</span><span class="sxs-lookup"><span data-stu-id="875bb-105">In Dimension Designer, open the dimension that contains the attribute you want to rename.</span></span>  
  
2.  <span data-ttu-id="875bb-106">[ディメンション ビルダー] ビューの **[属性]** ペインで、表示形式を **[ツリー]** または **[一覧]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="875bb-106">In the **Attributes** pane of the Dimension Builder view, change the display format to either **Tree** or **List**.</span></span> <span data-ttu-id="875bb-107">[属性] ペインの形式を変更する方法の詳細については、「 [ディメンション デザイナーのツリー、一覧、グリッドでの属性の表示](view-attributes-in-dimension-designer.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="875bb-107">For more information about how to change the format of the Attributes pane, see [View Attributes in a Tree, List or Grid in Dimension Designer](view-attributes-in-dimension-designer.md).</span></span>  
  
3.  <span data-ttu-id="875bb-108">構成する属性を右クリックして、 **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="875bb-108">Right-click the attribute you want to configure, and then click **Rename**.</span></span>  
  
4.  <span data-ttu-id="875bb-109">新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="875bb-109">Type the new name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="875bb-110">また、 `Name` の [**プロパティ**] ウィンドウで、選択した属性のプロパティを設定することもでき [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="875bb-110">You can also set the `Name` property of a selected attribute in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
  
