---
title: コードの自動作成 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9adbd5e1-f28c-4fb5-afa7-082de2831f3e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 9c12e000b2f6ff2ecad07bd62f8c6c05afa36f82
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631137"
---
# <a name="automatic-code-creation-master-data-services"></a><span data-ttu-id="3d375-102">コードの自動作成 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3d375-102">Automatic Code Creation (Master Data Services)</span></span>
  <span data-ttu-id="3d375-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、Code 属性の数値または他の数値属性の数値を自動的に生成できます。</span><span class="sxs-lookup"><span data-stu-id="3d375-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], numeric values can be automatically generated for the Code attribute, or for any other numeric attribute.</span></span> <span data-ttu-id="3d375-104">コードを自動生成するときは、コードに他の値を入力してもかまいません。正確には、初期値が自動的に設定されます。</span><span class="sxs-lookup"><span data-stu-id="3d375-104">When codes are generated automatically, you are not prevented from entering other values for codes; rather an initial value is automatically set.</span></span>  
  
## <a name="generating-code-values"></a><span data-ttu-id="3d375-105">コード値の生成</span><span class="sxs-lookup"><span data-stu-id="3d375-105">Generating Code Values</span></span>  
 <span data-ttu-id="3d375-106">管理者は、関連付けられているエンティティのプロパティを編集することによって、Code 属性の値の自動生成を構成できます。</span><span class="sxs-lookup"><span data-stu-id="3d375-106">Administrators can configure automatically-generated values for the Code attribute by editing the associated entity's properties.</span></span> <span data-ttu-id="3d375-107">初期値を指定でき、後続の各値は 1 ずつ増分されます。</span><span class="sxs-lookup"><span data-stu-id="3d375-107">They can specify an initial value, and each subsequent value is increased by one.</span></span>  
  
 <span data-ttu-id="3d375-108">いずれかのツールで、またはステージング処理を使用してコード値を MDS に入力するとき、コード値をブランクのままにすると、コード値が自動的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="3d375-108">When you enter Code values into MDS, either in one of the tools or by using the staging process, you can leave the Code value blank and a Code value will be automatically generated.</span></span> <span data-ttu-id="3d375-109">または、自分で選択したコード値を指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="3d375-109">Or you can specify a Code value of your choice.</span></span>  
  
## <a name="generating-other-attribute-values"></a><span data-ttu-id="3d375-110">他の属性値の生成</span><span class="sxs-lookup"><span data-stu-id="3d375-110">Generating Other Attribute Values</span></span>  
 <span data-ttu-id="3d375-111">管理者は、ビジネス ルールを作成することによって、Code 以外の属性値を自動的に生成できます。</span><span class="sxs-lookup"><span data-stu-id="3d375-111">Administrators can automatically generate values for attributes other than Code by creating business rules.</span></span> <span data-ttu-id="3d375-112">初期値を指定できるだけでなく、後続の各値での増分値も指定できます。</span><span class="sxs-lookup"><span data-stu-id="3d375-112">They can specify an initial value, and specify the number each subsequent value is incremented by.</span></span>  
  
 <span data-ttu-id="3d375-113">いずれかのツールで、またはステージング処理を使用して属性値を MDS に入力するとき、属性値をブランクのままにできます。</span><span class="sxs-lookup"><span data-stu-id="3d375-113">When you enter attribute values into MDS, either in one of the tools or by using the staging process, you can leave the attribute value blank.</span></span> <span data-ttu-id="3d375-114">ビジネス ルールが適用されると、既存の最高の値に基づいて値が増分されます。</span><span class="sxs-lookup"><span data-stu-id="3d375-114">When business rules are applied, the values will be incremented based on the highest existing value.</span></span> <span data-ttu-id="3d375-115">たとえば、ルールが "1 から開始して 4 ずつ増加する生成値に対する既定の属性" であり、属性の現在最も高い値が 700 である場合、追加される次のメンバーの値は 704 になります。</span><span class="sxs-lookup"><span data-stu-id="3d375-115">For example, if your rule is "Default attribute to a generated value that starts at 1 and increments by 4" and the highest current value for the attribute is 700, the value for the next member that's added will be 704.</span></span>  
  
## <a name="deleting-automatically-generated-values"></a><span data-ttu-id="3d375-116">自動的に生成される値の削除</span><span class="sxs-lookup"><span data-stu-id="3d375-116">Deleting Automatically Generated Values</span></span>  
 <span data-ttu-id="3d375-117">管理者が Code 属性の値の自動生成を有効にした後、ユーザーが再利用するコード値を持っていたメンバーを誤って削除する場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d375-117">After an administrator enables automatically generated values for the Code attribute, users may accidentally delete a member that had a Code value they want to reuse.</span></span> <span data-ttu-id="3d375-118">"メンバーコードは既に削除されたメンバーによって使用されています" というエラーメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="3d375-118">The error message "The member code is already used by a member that was deleted" will be displayed.</span></span> <span data-ttu-id="3d375-119">この解決方法には、次の 2 つが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="3d375-119">There are two possible solutions:</span></span>  
  
-   <span data-ttu-id="3d375-120">管理者は、[**バージョン管理**] 機能領域で、メンバーが削除されたときに発生したトランザクションを元に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="3d375-120">In the **Version Management** functional area, an administrator can reverse the transaction that occurred when the member was deleted.</span></span> <span data-ttu-id="3d375-121">ただし、これは、以前のメンバーの属性と階層とコレクションのメンバーシップがすべて復元されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="3d375-121">However, this means that all of the former member's attributes and membership in hierarchies and collections is restored.</span></span> <span data-ttu-id="3d375-122">詳細については、「[トランザクションの反転 &#40;マスターデータサービス&#41;](reverse-a-transaction-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d375-122">For more information, see [Reverse a Transaction &#40;Master Data Services&#41;](reverse-a-transaction-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="3d375-123">管理者は、ステージング処理を使用して、メンバーを完全に削除できます。</span><span class="sxs-lookup"><span data-stu-id="3d375-123">An administrator can use the staging process to permanently delete the member.</span></span> <span data-ttu-id="3d375-124">詳細については、「 [&#40;マスターデータサービス&#41;のステージング処理を使用したメンバーの非アクティブ化または削除](add-update-and-delete-data-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d375-124">For more information, see [Deactivate or Delete Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="3d375-125">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="3d375-125">Related Tasks</span></span>  
  
|<span data-ttu-id="3d375-126">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="3d375-126">Task Description</span></span>|<span data-ttu-id="3d375-127">トピック</span><span class="sxs-lookup"><span data-stu-id="3d375-127">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="3d375-128">Code 属性の値を自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="3d375-128">Automatically generate values for the Code attribute.</span></span>|[<span data-ttu-id="3d375-129">Code 属性の値の自動生成 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3d375-129">Automatically Generate Code Attribute Values &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-code-attribute-values-master-data-services.md)|  
|<span data-ttu-id="3d375-130">他の属性の値を自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="3d375-130">Automatically generate values for other attributes.</span></span>|[<span data-ttu-id="3d375-131">Code 以外の属性の値の自動生成 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3d375-131">Automatically Generate Attribute Values Other Than Code &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="3d375-132">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="3d375-132">Related Content</span></span>  
  
-   [<span data-ttu-id="3d375-133">マスター データ サービス概要</span><span class="sxs-lookup"><span data-stu-id="3d375-133">Master Data Services Overview</span></span>](master-data-services-overview-mds.md)  
  
-   [<span data-ttu-id="3d375-134">ビジネス ルール (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3d375-134">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="3d375-135">エンティティ (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="3d375-135">Entities &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/entities-master-data-services.md)  
  
  
