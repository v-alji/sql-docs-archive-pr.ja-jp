---
title: Code 属性の値の自動生成 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 19b354ee-2906-4cc7-ba2f-32b4543bddcf
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6c442f37ffe322985ba55b29b2c4cd539b8a3e05
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644010"
---
# <a name="automatically-generate-code-attribute-values-master-data-services"></a><span data-ttu-id="1e114-102">Code 属性の値の自動生成 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1e114-102">Automatically Generate Code Attribute Values (Master Data Services)</span></span>
  <span data-ttu-id="1e114-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、新しいメンバーが作成されるたびに、エンティティの Code 属性の値に整数を自動的に割り当てる場合は、Code 属性の値を自動的に生成します。</span><span class="sxs-lookup"><span data-stu-id="1e114-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], automatically generate values for an entity's Code attribute when you want an integer to be automatically assigned to the Code value each time a new member is created.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="1e114-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="1e114-104">Prerequisites</span></span>  
 <span data-ttu-id="1e114-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="1e114-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="1e114-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="1e114-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="1e114-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e114-107">You must be a model administrator.</span></span> <span data-ttu-id="1e114-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e114-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="1e114-109">エンティティが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1e114-109">The entity must exist.</span></span> <span data-ttu-id="1e114-110">詳細については、「[エンティティを作成する (マスター データ サービス)](../../2014/master-data-services/create-an-entity-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1e114-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-automatically-generate-code-values"></a><span data-ttu-id="1e114-111">コード値を自動的に生成するには</span><span class="sxs-lookup"><span data-stu-id="1e114-111">To automatically generate Code values</span></span>  
  
1.  <span data-ttu-id="1e114-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e114-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="1e114-113">[**モデルエクスプローラー** ] ページのメニューバーから [**管理**] をポイントし、[**エンティティ**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e114-113">On the **Model Explorer** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="1e114-114">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="1e114-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="1e114-115">コードを生成するエンティティの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="1e114-115">Select the row for the entity that you want to generate codes for.</span></span>  
  
5.  <span data-ttu-id="1e114-116">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e114-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="1e114-117">**[コード値を自動的に作成する]** チェック ボックスをオンにします。</span><span class="sxs-lookup"><span data-stu-id="1e114-117">Select the **Create Code values automatically** check box.</span></span>  
  
7.  <span data-ttu-id="1e114-118">**[開始]** ボックスに、増分を開始する値を入力します。</span><span class="sxs-lookup"><span data-stu-id="1e114-118">In the **Start with** box, type a number to begin incrementing.</span></span> <span data-ttu-id="1e114-119">メンバーが既に存在する場合は、コードは既存の最も大きい値に基づいて設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e114-119">If members already exist, the Code will be set based on the highest existing value.</span></span> <span data-ttu-id="1e114-120">たとえば、最も大きい既存のコード値が 299 の場合、次のメンバーのコード値は 300 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="1e114-120">For example, if the highest existing Code value is 299, the next member's Code value will be set to 300.</span></span>  
  
8.  <span data-ttu-id="1e114-121">[**エンティティの保存**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="1e114-121">Click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e114-122">参照</span><span class="sxs-lookup"><span data-stu-id="1e114-122">See Also</span></span>  
 <span data-ttu-id="1e114-123">[自動コード作成 &#40;マスターデータサービス&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="1e114-123">[Automatic Code Creation &#40;Master Data Services&#41;](../../2014/master-data-services/automatic-code-creation-master-data-services.md) </span></span>  
 [<span data-ttu-id="1e114-124">Code 以外の属性の値の自動生成 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="1e114-124">Automatically Generate Attribute Values Other Than Code &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/automatically-generate-attribute-values-other-than-code-master-data-services.md)  
  
  
