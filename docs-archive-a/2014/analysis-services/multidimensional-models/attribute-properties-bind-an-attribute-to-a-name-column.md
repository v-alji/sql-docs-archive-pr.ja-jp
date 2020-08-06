---
title: 名前列に属性をバインドする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- binding attributes [Analysis Services]
- name columns [Analysis Services]
- attributes [Analysis Services], binding
ms.assetid: 467f0cf3-8691-476d-a7fb-a5df4e374eaf
author: minewiskan
ms.author: owend
ms.openlocfilehash: e25c59d34744e7a067c2b3e83d248c4674772737
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644677"
---
# <a name="bind-an-attribute-to-a-name-column"></a><span data-ttu-id="892a3-102">名前列への属性のバインド</span><span class="sxs-lookup"><span data-stu-id="892a3-102">Bind an Attribute to a Name Column</span></span>
  <span data-ttu-id="892a3-103">この手順では、ディメンション デザイナーの **[属性]** ペインと、 **[オブジェクトのバインド]** ダイアログ ボックスを使用して、手動で名前列に属性をバインドする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="892a3-103">This procedure describes how to bind an attribute to a name column manually by using the **Attributes** pane in the Dimension Designer and by using the **Object Binding** dialog box.</span></span>  
  
### <a name="to-bind-an-attribute-to-a-name-column"></a><span data-ttu-id="892a3-104">名前列に属性をバインドするには</span><span class="sxs-lookup"><span data-stu-id="892a3-104">To bind an attribute to a name column</span></span>  
  
1.  <span data-ttu-id="892a3-105">ディメンション デザイナーで、属性を作成するディメンションを開きます。</span><span class="sxs-lookup"><span data-stu-id="892a3-105">In Dimension Designer, open the dimension in which you want to create the attribute.</span></span>  
  
2.  <span data-ttu-id="892a3-106">**[ディメンション構造]** タブの **[属性]** ペインで、構成する属性を右クリックし、 **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="892a3-106">On the **Dimension Structure** tab, in the **Attributes** pane, right-click the attribute that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="892a3-107">**[プロパティ]** ウィンドウで、 **[NameColumn]** プロパティを探し、 **[(新規)]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="892a3-107">In the **Properties** window, locate the **NameColumn** property, and then select **(new)**.</span></span>  
  
4.  <span data-ttu-id="892a3-108">**[オブジェクトのバインド]** ダイアログ ボックスの **[バインドの種類]** ボックスの一覧で、 **[列のバインド]** を選択します。</span><span class="sxs-lookup"><span data-stu-id="892a3-108">In the **Object Binding** dialog box, for **Binding type**, select **Column binding**.</span></span>  
  
5.  <span data-ttu-id="892a3-109">**[基になる列]** ボックスの一覧で、属性をバインドする列を選択し、 **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="892a3-109">In the **Source column** list, select the column to which the attribute will be bound, and then click **OK**.</span></span>  
  
  
