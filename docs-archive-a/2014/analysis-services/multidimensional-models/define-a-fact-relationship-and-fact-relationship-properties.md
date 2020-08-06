---
title: ファクトリレーションシップとファクトリレーションシップのプロパティを定義する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- fact dimensions [Analysis Services]
ms.assetid: d8e41724-da77-4ac1-bc42-956b5d91ea5d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 15f67a4bdf699bbc6443fc76ce54bcfb35831827
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714650"
---
# <a name="define-a-fact-relationship-and-fact-relationship-properties"></a><span data-ttu-id="3599b-102">ファクト リレーションシップとファクト リレーションシップのプロパティの定義</span><span class="sxs-lookup"><span data-stu-id="3599b-102">Define a Fact Relationship and Fact Relationship Properties</span></span>
  <span data-ttu-id="3599b-103">新しいキューブ ディメンションまたは新しいメジャー グループが定義されると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、ファクト ディメンションのリレーションシップが存在するかどうかを検出し、ディメンションの使用法を `Fact` に設定しようと試みます。</span><span class="sxs-lookup"><span data-stu-id="3599b-103">When you define a new cube dimension or a new measure group, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] will try to detect if a fact dimension relationship exists and then set the dimension usage setting to `Fact`.</span></span> <span data-ttu-id="3599b-104">ファクト ディメンションのリレーションシップはキューブ デザイナーの **[ディメンションの使用法]** タブで表示または編集できます。</span><span class="sxs-lookup"><span data-stu-id="3599b-104">You can view or edit a fact dimension relationship on the **Dimension Usage** tab of Cube Designer.</span></span> <span data-ttu-id="3599b-105">ディメンションとメジャー グループ間のファクト リレーションシップには次の制約があります。</span><span class="sxs-lookup"><span data-stu-id="3599b-105">The fact relationship between a dimension and a measure group has the following constraints:</span></span>  
  
-   <span data-ttu-id="3599b-106">1 つのキューブ ディメンションには、特定のメジャー グループに対してファクト リレーションシップを 1 つだけ設定できます。</span><span class="sxs-lookup"><span data-stu-id="3599b-106">A cube dimension can have only one fact relationship to a particular measure group.</span></span>  
  
-   <span data-ttu-id="3599b-107">1 つのキューブ ディメンションには、複数のメジャー グループに対して個別のファクト リレーションシップを設定できます。</span><span class="sxs-lookup"><span data-stu-id="3599b-107">A cube dimension can have separate fact relationships to multiple measure groups.</span></span>  
  
-   <span data-ttu-id="3599b-108">リレーションシップの粒度属性は、ディメンションのキー属性 (取引番号など) である必要があります。</span><span class="sxs-lookup"><span data-stu-id="3599b-108">The granularity attribute for the relationship must be the key attribute (such as Transaction Number) for the dimension.</span></span> <span data-ttu-id="3599b-109">これにより、ディメンションとファクト テーブル内のファクトとの間に一対一リレーションシップが作成されます。</span><span class="sxs-lookup"><span data-stu-id="3599b-109">This creates a one-to-one relationship between the dimension and facts in the fact table.</span></span>  
  
  
