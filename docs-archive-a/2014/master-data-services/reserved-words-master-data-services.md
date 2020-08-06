---
title: 予約語 (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c54bb371cd8f797cfb36f015387e0e21339c0426
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641715"
---
# <a name="reserved-words-master-data-services"></a><span data-ttu-id="d9ba0-102">予約語 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d9ba0-102">Reserved Words (Master Data Services)</span></span>
  <span data-ttu-id="d9ba0-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、モデル オブジェクトまたはメンバーを作成するときに使用できない単語がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="d9ba0-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], when you create model objects or members, some words cannot be used.</span></span> <span data-ttu-id="d9ba0-104">これらの単語を使用すると、エラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d9ba0-104">Using these words may cause errors.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9ba0-105">特殊文字 (記号、ハイフネーションなど) の使用も極力控えてください。</span><span class="sxs-lookup"><span data-stu-id="d9ba0-105">You should also limit your use of special characters (symbols, hyphenation, etc.).</span></span>  
  
-   [<span data-ttu-id="d9ba0-106">モデル</span><span class="sxs-lookup"><span data-stu-id="d9ba0-106">Models</span></span>](#models)  
  
-   [<span data-ttu-id="d9ba0-107">エンティティ</span><span class="sxs-lookup"><span data-stu-id="d9ba0-107">Entities</span></span>](#entities)  
  
-   [<span data-ttu-id="d9ba0-108">明示的階層</span><span class="sxs-lookup"><span data-stu-id="d9ba0-108">Explicit Hierarchies</span></span>](#exhierarchies)  
  
-   [<span data-ttu-id="d9ba0-109">属性</span><span class="sxs-lookup"><span data-stu-id="d9ba0-109">Attributes</span></span>](#attributes)  
  
-   [<span data-ttu-id="d9ba0-110">メンバー</span><span class="sxs-lookup"><span data-stu-id="d9ba0-110">Members</span></span>](#members)  
  
##  <a name="models"></a><a name="models"></a><span data-ttu-id="d9ba0-111">モジュール</span><span class="sxs-lookup"><span data-stu-id="d9ba0-111">Models</span></span>  
 <span data-ttu-id="d9ba0-112">名前を "**名前**" に設定したモデルを作成する場合は、[**モデルと同じ名前のエンティティを作成**する] を選択しないでください。エンティティの名前には**名前**を使用できません。</span><span class="sxs-lookup"><span data-stu-id="d9ba0-112">If you create a model with the name set to **Name**, do not select **Create entity with same name as model** because **Name** cannot be used for the name of an entity.</span></span>  
  
##  <a name="entities"></a><a name="entities"></a><span data-ttu-id="d9ba0-113">事業</span><span class="sxs-lookup"><span data-stu-id="d9ba0-113">Entities</span></span>  
 <span data-ttu-id="d9ba0-114">エンティティ名には **Name** または **Code**を使用できません。</span><span class="sxs-lookup"><span data-stu-id="d9ba0-114">For entity names, you cannot use **Name** or **Code**.</span></span>  
  
##  <a name="explicit-hierarchies"></a><a name="exhierarchies"></a><span data-ttu-id="d9ba0-115">明示的階層</span><span class="sxs-lookup"><span data-stu-id="d9ba0-115">Explicit Hierarchies</span></span>  
 <span data-ttu-id="d9ba0-116">明示的階層名には **Name** または **Code**を使用できません。</span><span class="sxs-lookup"><span data-stu-id="d9ba0-116">For explicit hierarchy names, you cannot use **Name** or **Code**.</span></span>  
  
##  <a name="attributes"></a><a name="attributes"></a><span data-ttu-id="d9ba0-117">アトリビュート</span><span class="sxs-lookup"><span data-stu-id="d9ba0-117">Attributes</span></span>  
  
-   <span data-ttu-id="d9ba0-118">**ID**</span><span class="sxs-lookup"><span data-stu-id="d9ba0-118">**ID**</span></span>  
  
-   <span data-ttu-id="d9ba0-119">**コード**</span><span class="sxs-lookup"><span data-stu-id="d9ba0-119">**Code**</span></span>  
  
-   <span data-ttu-id="d9ba0-120">**名前**</span><span class="sxs-lookup"><span data-stu-id="d9ba0-120">**Name**</span></span>  
  
-   <span data-ttu-id="d9ba0-121">**EnterDTM**</span><span class="sxs-lookup"><span data-stu-id="d9ba0-121">**EnterDTM**</span></span>  
  
-   <span data-ttu-id="d9ba0-122">**EnterUserID**</span><span class="sxs-lookup"><span data-stu-id="d9ba0-122">**EnterUserID**</span></span>  
  
-   <span data-ttu-id="d9ba0-123">**EnterUserName**</span><span class="sxs-lookup"><span data-stu-id="d9ba0-123">**EnterUserName**</span></span>  
  
-   <span data-ttu-id="d9ba0-124">**LastChgDTM**</span><span class="sxs-lookup"><span data-stu-id="d9ba0-124">**LastChgDTM**</span></span>  
  
-   <span data-ttu-id="d9ba0-125">**LastChgUserID**</span><span class="sxs-lookup"><span data-stu-id="d9ba0-125">**LastChgUserID**</span></span>  
  
-   <span data-ttu-id="d9ba0-126">**Status_ID**</span><span class="sxs-lookup"><span data-stu-id="d9ba0-126">**Status_ID**</span></span>  
  
-   <span data-ttu-id="d9ba0-127">**ValidationStatus_ID**</span><span class="sxs-lookup"><span data-stu-id="d9ba0-127">**ValidationStatus_ID**</span></span>  
  
-   <span data-ttu-id="d9ba0-128">**Version_ID**</span><span class="sxs-lookup"><span data-stu-id="d9ba0-128">**Version_ID**</span></span>  
  
##  <a name="members"></a><a name="members"></a><span data-ttu-id="d9ba0-129">属する</span><span class="sxs-lookup"><span data-stu-id="d9ba0-129">Members</span></span>  
 <span data-ttu-id="d9ba0-130">メンバーの場合、 **Code**属性値に**MDMMemberStatus**または**ROOT**を使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="d9ba0-130">For members, you cannot use **MDMMemberStatus** or **ROOT** for the **Code** attribute value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9ba0-131">参照</span><span class="sxs-lookup"><span data-stu-id="d9ba0-131">See Also</span></span>  
 [<span data-ttu-id="d9ba0-132">マスター データ サービス概要</span><span class="sxs-lookup"><span data-stu-id="d9ba0-132">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
  
