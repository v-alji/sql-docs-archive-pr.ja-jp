---
title: 標準リレーションシップおよび標準リレーションシッププロパティの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- granularity attribute
- relationships [Analysis Services], regular relationships
ms.assetid: 840280d8-20c3-46c0-99ea-62479469c36b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 9b4f49e219a85d5577fb1acddfe14e7afd3b105d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644661"
---
# <a name="define-a-regular-relationship-and-regular-relationship-properties"></a><span data-ttu-id="343a8-102">ファクト リレーションシップとファクト リレーションシップのプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="343a8-102">Define a Regular Relationship and Regular Relationship Properties</span></span>
  <span data-ttu-id="343a8-103">新しいキューブ ディメンションまたは新しいメジャー グループが定義されると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、標準リレーションシップが存在するかどうかを検出し、ディメンションの使用法を `Regular` に設定しようと試みます。</span><span class="sxs-lookup"><span data-stu-id="343a8-103">When you define a new cube dimension or a new measure group, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will try to detect if a regular relationship exists and then set the dimension usage setting to `Regular`.</span></span> <span data-ttu-id="343a8-104">標準ディメンションのリレーションシップはキューブ デザイナーの **[ディメンションの使用法]** タブで表示または編集できます。</span><span class="sxs-lookup"><span data-stu-id="343a8-104">You can view or edit a regular dimension relationship on the **Dimension Usage** tab of Cube Designer.</span></span>  
  
 <span data-ttu-id="343a8-105">キューブ ディメンションとメジャー グループ間のリレーションシップを定義する場合は、粒度属性もそのリレーションシップに指定します。</span><span class="sxs-lookup"><span data-stu-id="343a8-105">When you define the relationship of a cube dimension to a measure group, you also specify the granularity attribute for that relationship.</span></span> <span data-ttu-id="343a8-106">粒度属性では、そのディメンションのキューブで使用できる最も低い詳細レベルを定義します (通常はディメンションのキー属性)。</span><span class="sxs-lookup"><span data-stu-id="343a8-106">The granularity attribute defines the lowest level of detail available in the cube for that dimension, which is generally the key attribute for the dimension.</span></span> <span data-ttu-id="343a8-107">ただし、特定のメジャー グループ内の特定のキューブ ディメンションの粒度を別のレベルに設定することが必要な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="343a8-107">However, sometimes you may want to set the granularity of a particular cube dimension in a particular measure group to a different grain.</span></span> <span data-ttu-id="343a8-108">たとえば、Sales Quotas メジャー グループまたは Budget メジャー グループを使用する場合、Time ディメンションの粒度属性を Day 属性ではなく Month 属性に設定できます。</span><span class="sxs-lookup"><span data-stu-id="343a8-108">For example, you may want to set the granularity attribute for the Time dimension to the Month attribute instead of to the Day attribute, if you are using a Sales Quotas or a Budget measure group.</span></span> <span data-ttu-id="343a8-109">粒度属性をキー属性以外の属性に指定する場合は、ディメンション内の他のすべての属性が、属性リレーションシップを介してこの属性に直接または間接的にリンクされるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="343a8-109">When you specify the granularity attribute to be an attribute other than the key attribute, you must guarantee that all other attributes in the dimension are directly or indirectly linked to this other attribute through attribute relationships.</span></span> <span data-ttu-id="343a8-110">リンクされていない属性があると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] でデータを適切に集計できなくなります。</span><span class="sxs-lookup"><span data-stu-id="343a8-110">If not, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will be unable to aggregate data correctly.</span></span>  
  
  
