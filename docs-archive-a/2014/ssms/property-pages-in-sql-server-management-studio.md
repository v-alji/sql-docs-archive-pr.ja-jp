---
title: SQL Server Management Studio のプロパティ ページ | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- property pages [SQL Server Management Studio]
ms.assetid: 719282c3-e9cc-4e0e-9a83-7fb8b8b17f67
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3fae6a07fbaa2a259fcca5c3807094b31e0d52d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87737411"
---
# <a name="property-pages-in-sql-server-management-studio"></a><span data-ttu-id="8920e-102">SQL Server Management Studio のプロパティ ページ</span><span class="sxs-lookup"><span data-stu-id="8920e-102">Property Pages in SQL Server Management Studio</span></span>
  <span data-ttu-id="8920e-103">[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] のプロパティ ページのダイアログ ボックスでは、カテゴリの展開や折りたたみができる共通の形式で情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8920e-103">Property page dialog boxes in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] all use a common format displaying information with expanding and collapsing categories.</span></span> <span data-ttu-id="8920e-104">表示されるフィールドは、プロパティごとに異なります。</span><span class="sxs-lookup"><span data-stu-id="8920e-104">The fields shown depend on the particular property.</span></span> <span data-ttu-id="8920e-105">淡色で表示されているプロパティは変更できません。</span><span class="sxs-lookup"><span data-stu-id="8920e-105">Properties shown in gray are read-only.</span></span> <span data-ttu-id="8920e-106">[項目別] および [アルファベット順] ボタンはプロパティ ページの上部にあります。</span><span class="sxs-lookup"><span data-stu-id="8920e-106">Categorized and Alphabetic buttons are near the top of each property page.</span></span>  
  
 <span data-ttu-id="8920e-107">以下の表に、 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] のプロパティ ページのダイアログ ボックスで使用される共通の要素について示します。</span><span class="sxs-lookup"><span data-stu-id="8920e-107">The following table describes the common elements of [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] property page dialog boxes.</span></span>  
  
|<span data-ttu-id="8920e-108">要素</span><span class="sxs-lookup"><span data-stu-id="8920e-108">Element</span></span>|<span data-ttu-id="8920e-109">説明</span><span class="sxs-lookup"><span data-stu-id="8920e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8920e-110">**項目別**</span><span class="sxs-lookup"><span data-stu-id="8920e-110">**Categorized**</span></span>|<span data-ttu-id="8920e-111">選択したオブジェクトのすべてのプロパティおよびプロパティ値を項目順に表示します。</span><span class="sxs-lookup"><span data-stu-id="8920e-111">Lists all properties and property values for the selected object, sorted by category.</span></span> <span data-ttu-id="8920e-112">項目別表示では、項目を折りたたんで、表示するプロパティの数を少なくすることができます。</span><span class="sxs-lookup"><span data-stu-id="8920e-112">In category view, you can collapse a category to reduce the number of visible properties.</span></span> <span data-ttu-id="8920e-113">項目の展開または折りたたみを行うと、項目名の左側に正符号 (+) または負符号 (-) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8920e-113">When you expand or collapse a category, you see a plus sign (+) or minus sign (-) to the left of the category name.</span></span> <span data-ttu-id="8920e-114">項目はアルファベット順に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8920e-114">Categories are listed alphabetically.</span></span>|  
|<span data-ttu-id="8920e-115">**アルファベット順**</span><span class="sxs-lookup"><span data-stu-id="8920e-115">**Alphabetic**</span></span>|<span data-ttu-id="8920e-116">選択したオブジェクトのすべてのプロパティおよびプロパティ値をアルファベット順に表示します。</span><span class="sxs-lookup"><span data-stu-id="8920e-116">Lists all properties and property values for the selected object, sorted alphabetically.</span></span>|  
|<span data-ttu-id="8920e-117">プロパティ名</span><span class="sxs-lookup"><span data-stu-id="8920e-117">Property name</span></span>|<span data-ttu-id="8920e-118">表の 1 列目にプロパティ名が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8920e-118">The first column in the grid lists the property names.</span></span>|  
|<span data-ttu-id="8920e-119">Properties</span><span class="sxs-lookup"><span data-stu-id="8920e-119">Properties</span></span>|<span data-ttu-id="8920e-120">表の 2 列目にはプロパティ値が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8920e-120">The second column in the grid lists the property values.</span></span>|  
|<span data-ttu-id="8920e-121">説明ペイン</span><span class="sxs-lookup"><span data-stu-id="8920e-121">Description pane</span></span>|<span data-ttu-id="8920e-122">説明ペインはページの最下部にあり、プロパティの種類と、プロパティの短い説明が表示されます。</span><span class="sxs-lookup"><span data-stu-id="8920e-122">The description pane appears at the bottom of the page and shows the property type and a short description of the property.</span></span> <span data-ttu-id="8920e-123">ショートカット メニューの **[説明]** を使用して、プロパティの説明の表示と非表示を切り替えることができます。</span><span class="sxs-lookup"><span data-stu-id="8920e-123">You can turn the description of the property off and on using the **Description** command on the shortcut menu.</span></span>|  
  
  
