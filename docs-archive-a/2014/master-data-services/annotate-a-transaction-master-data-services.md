---
title: トランザクションの注釈を設定する (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- annotations [Master Data Services], for transactions
ms.assetid: f5a6b2ca-56de-4e42-9da8-fba0ac3e8d92
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c384f4241d0ddcd78fd8942fe28da8c0b5b1e77c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718387"
---
# <a name="annotate-a-transaction-master-data-services"></a><span data-ttu-id="0202c-102">トランザクションの注釈を設定する (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="0202c-102">Annotate a Transaction (Master Data Services)</span></span>
  <span data-ttu-id="0202c-103">履歴を参照する目的でトランザクションの詳細をサポートする場合、 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でトランザクションの注釈を設定します。</span><span class="sxs-lookup"><span data-stu-id="0202c-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], annotate a transaction when you want to provide supporting details about the transaction for historical purposes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0202c-104">注釈は削除できません。</span><span class="sxs-lookup"><span data-stu-id="0202c-104">You cannot delete annotations.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0202c-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="0202c-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="0202c-106">作成したトランザクションの注釈を設定するためには、 **[エクスプローラー]** 機能領域へのアクセス権限と、注釈を設定するモデル オブジェクトに対する **更新** 権限が最低限必要です。</span><span class="sxs-lookup"><span data-stu-id="0202c-106">To annotate transactions that you created, you must have permission to access the **Explorer** functional area, and have a minimum of **Update** permission to the model object you want to annotate.</span></span>  
  
-   <span data-ttu-id="0202c-107">すべてのユーザーのトランザクションの注釈を設定するためには、 **[バージョン管理]** 機能領域へのアクセス権限を持っているモデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0202c-107">To annotate transactions for all users, you must have permission to access the **Version Management** functional area and be a model administrator.</span></span> <span data-ttu-id="0202c-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0202c-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-annotate-a-transaction-in-explorer"></a><span data-ttu-id="0202c-109">[エクスプローラー] でトランザクションの注釈を設定するには</span><span class="sxs-lookup"><span data-stu-id="0202c-109">To annotate a transaction in Explorer</span></span>  
  
1.  <span data-ttu-id="0202c-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="0202c-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="0202c-111">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="0202c-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="0202c-112">**[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0202c-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="0202c-113">メニュー バーの **[エンティティ]** をポイントして、注釈を設定するトランザクションを持つメンバーを含むエンティティの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0202c-113">From the menu bar, point to **Entities** and click the entity that contains the member with a transaction you want to annotate.</span></span>  
  
5.  <span data-ttu-id="0202c-114">グリッドで、メンバーの行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0202c-114">In the grid, click the row of the member.</span></span>  
  
6.  <span data-ttu-id="0202c-115">**[トランザクションの表示]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0202c-115">Click **View Transactions**.</span></span>  
  
7.  <span data-ttu-id="0202c-116">**[トランザクションの表示]** ダイアログ ボックスで、注釈を設定するトランザクションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="0202c-116">In the **View Transactions** dialog box, click the transaction you want to annotate.</span></span>  
  
8.  <span data-ttu-id="0202c-117">ダイアログ ボックスの下部にあるボックスに、注釈を入力します。</span><span class="sxs-lookup"><span data-stu-id="0202c-117">In the box at the bottom of the dialog box, type your annotation.</span></span>  
  
9. <span data-ttu-id="0202c-118">**[注釈の追加]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0202c-118">Click **Add Annotation**.</span></span> <span data-ttu-id="0202c-119">**[注釈]** ペインに注釈が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0202c-119">The annotation is displayed in the **Annotations** pane.</span></span>  
  
### <a name="to-annotate-a-transaction-in-version-management-administrators-only"></a><span data-ttu-id="0202c-120">[バージョン管理] でトランザクションに注釈を設定する (管理者のみ)</span><span class="sxs-lookup"><span data-stu-id="0202c-120">To annotate a transaction in Version Management (administrators only)</span></span>  
  
1.  <span data-ttu-id="0202c-121">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] ホーム ページで、 **[バージョン管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0202c-121">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="0202c-122">メニュー バーの **[トランザクション]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0202c-122">On the menu bar, click **Transactions**.</span></span>  
  
3.  <span data-ttu-id="0202c-123">**[トランザクション]** ペインで、注釈を設定するトランザクションのグリッド内の行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0202c-123">In the **Transactions** pane, click the row in the grid for the transaction you want to annotate.</span></span>  
  
4.  <span data-ttu-id="0202c-124">**[トランザクションの注釈]** ペインの **[注釈]** ボックスに注釈を入力します。</span><span class="sxs-lookup"><span data-stu-id="0202c-124">In the **Transaction Annotations** pane, in the **Annotation** box, type your annotation.</span></span>  
  
5.  <span data-ttu-id="0202c-125">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0202c-125">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0202c-126">参照</span><span class="sxs-lookup"><span data-stu-id="0202c-126">See Also</span></span>  
 <span data-ttu-id="0202c-127">[注釈 &#40;マスターデータサービス&#41;](../../2014/master-data-services/annotations-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0202c-127">[Annotations &#40;Master Data Services&#41;](../../2014/master-data-services/annotations-master-data-services.md) </span></span>  
 [<span data-ttu-id="0202c-128">トランザクション (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0202c-128">Transactions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/transactions-master-data-services.md)  
  
  
