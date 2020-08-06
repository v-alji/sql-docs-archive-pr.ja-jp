---
title: データベースディメンションの定義 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- dimensions [Analysis Services], defining
ms.assetid: fe84588b-66a3-4100-a1cf-59b21b7adf01
author: minewiskan
ms.author: owend
ms.openlocfilehash: ad5334e71b0f133f80933a7d1702d8ada7565501
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712566"
---
# <a name="define-database-dimensions"></a><span data-ttu-id="1c4fa-102">データベース ディメンションの定義</span><span class="sxs-lookup"><span data-stu-id="1c4fa-102">Define Database Dimensions</span></span>
  <span data-ttu-id="1c4fa-103">のディメンションデザイナーを使用して [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトまたはデータベース内の既存のデータベースディメンションを構成します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-103">Use Dimension Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] to configure an existing database dimension in a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="1c4fa-104">ディメンション デザイナーを使用すると、次の操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-104">You can use Dimension Designer to do the following:</span></span>  
  
-   <span data-ttu-id="1c4fa-105">ディメンションレベルのプロパティを構成します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-105">Configure the dimension-level properties.</span></span>  
  
-   <span data-ttu-id="1c4fa-106">ディメンション属性を追加および構成します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-106">Add and configure dimension attributes.</span></span>  
  
-   <span data-ttu-id="1c4fa-107">ユーザー定義階層を定義および構成します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-107">Define and configure user-defined hierarchies.</span></span>  
  
-   <span data-ttu-id="1c4fa-108">属性間のリレーションシップを定義および構成します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-108">Define and configure relationships between attributes.</span></span>  
  
-   <span data-ttu-id="1c4fa-109">ディメンションの翻訳を定義します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-109">Define dimension translations.</span></span>  
  
-   <span data-ttu-id="1c4fa-110">処理済みのディメンションの場合、ディメンション構造を参照し、データを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-110">For processed dimensions, you can browse the dimension structure and view data.</span></span>  
  
 <span data-ttu-id="1c4fa-111">ディメンション、属性、または階層を変更した後は、変更を表示するために、そのディメンションを処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-111">After you modify a dimension, attribute, or hierarchy, you must process that dimension to view the changes.</span></span> <span data-ttu-id="1c4fa-112">プロジェクト モードで作業する場合は、処理する前に [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスへの変更を配置します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-112">When working in project mode, you deploy the changes to the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance before processing.</span></span>  
  
 <span data-ttu-id="1c4fa-113">ディメンション デザイナーでディメンションを開く方法の詳細については、「 [ソリューション エクスプローラーでのデータベース ディメンションの変更または削除](database-dimensions-modify-or-delete-a-database-dimension-in-solution-explorer.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-113">For more information about how to open a dimension in Dimension Designer, see [Modify or Delete a Database Dimension in Solution Explorer](database-dimensions-modify-or-delete-a-database-dimension-in-solution-explorer.md).</span></span>  
  
 <span data-ttu-id="1c4fa-114">ディメンション デザイナーには、次の表で説明しているように、3 つの異なるタブがあります。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-114">Dimension Designer has three different tabs, which are described in the following table.</span></span>  
  
|<span data-ttu-id="1c4fa-115">タブ</span><span class="sxs-lookup"><span data-stu-id="1c4fa-115">Tab</span></span>|<span data-ttu-id="1c4fa-116">説明</span><span class="sxs-lookup"><span data-stu-id="1c4fa-116">Description</span></span>|  
|---------|-----------------|  
|<span data-ttu-id="1c4fa-117">**[ディメンション構造]**</span><span class="sxs-lookup"><span data-stu-id="1c4fa-117">**Dimension Structure**</span></span>|<span data-ttu-id="1c4fa-118">このタブを使用すると、ディメンションの構造を操作したり、ディメンションのデータソースビュースキーマを確認または作成したり、属性を操作したり、ユーザー定義階層の属性を整理したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-118">Use this tab to work with the structure of a dimension-to examine or create the data source view schema for a dimension, to work with attributes, and to organize attributes in user-defined hierarchies.</span></span>|  
|<span data-ttu-id="1c4fa-119">**のディメンション デザイナーでは、[ディメンション構造] ビューの**</span><span class="sxs-lookup"><span data-stu-id="1c4fa-119">**Attribute Relationships**</span></span>|<span data-ttu-id="1c4fa-120">ディメンションの属性リレーションシップを作成、変更、または削除するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-120">Use this tab to create, modify, or delete the attribute relationships of a dimension.</span></span>|  
|<span data-ttu-id="1c4fa-121">**翻訳**</span><span class="sxs-lookup"><span data-stu-id="1c4fa-121">**Translations**</span></span>|<span data-ttu-id="1c4fa-122">ディメンションのメタデータの翻訳を異なる言語で追加および編集するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-122">Use this tab to add and edit translations of dimension metadata in different languages.</span></span>|  
|<span data-ttu-id="1c4fa-123">**ブラウザー**</span><span class="sxs-lookup"><span data-stu-id="1c4fa-123">**Browser**</span></span>|<span data-ttu-id="1c4fa-124">処理済みディメンションのメンバーを調べるときや、ディメンションのメタデータの翻訳を確認するときに使用します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-124">Use this tab to examine the members of a processed dimension and to review translations of dimension metadata.</span></span>|  
  
 <span data-ttu-id="1c4fa-125">次のトピックでは、ディメンション デザイナーで実行できるタスクについて説明します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-125">The following topics describe the tasks that you can perform in Dimension Designer.</span></span>  
  
 [<span data-ttu-id="1c4fa-126">ディメンションの属性のプロパティの参照</span><span class="sxs-lookup"><span data-stu-id="1c4fa-126">Dimension Attribute Properties Reference</span></span>](dimension-attribute-properties-reference.md)  
 <span data-ttu-id="1c4fa-127">ディメンションの属性を定義して構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-127">Describes how to define and configure a dimension attribute.</span></span>  
  
 [<span data-ttu-id="1c4fa-128">ユーザー定義階層の作成</span><span class="sxs-lookup"><span data-stu-id="1c4fa-128">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)  
 <span data-ttu-id="1c4fa-129">ユーザー定義階層を定義して構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-129">Describes how to define and configure a user-defined hierarchy.</span></span>  
  
 [<span data-ttu-id="1c4fa-130">属性リレーションシップの定義</span><span class="sxs-lookup"><span data-stu-id="1c4fa-130">Define Attribute Relationships</span></span>](attribute-relationships-define.md)  
 <span data-ttu-id="1c4fa-131">属性のリレーションシップを定義して構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-131">Describes how to define and configure an attribute relationship.</span></span>  
  
 [<span data-ttu-id="1c4fa-132">ビジネス インテリジェンス ウィザードを使用したディメンションの拡張</span><span class="sxs-lookup"><span data-stu-id="1c4fa-132">Use the Business Intelligence Wizard to Enhance Dimensions</span></span>](../use-the-business-intelligence-wizard-to-enhance-dimensions.md)  
 <span data-ttu-id="1c4fa-133">ビジネス インテリジェンス ウィザードを使用してディメンションを拡張する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="1c4fa-133">Describes how to use the Business Intelligence Wizard to enhance a dimension.</span></span>  
  
  
