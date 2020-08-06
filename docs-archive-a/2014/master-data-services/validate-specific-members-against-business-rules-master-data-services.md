---
title: ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 18af83146679eb77638dfbc98b31f198dc8e07b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640120"
---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a><span data-ttu-id="19d1f-102">ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="19d1f-102">Validate Specific Members against Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="19d1f-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、ビジネス ルールに対してメンバーのサブセットを更新または検証する場合にビジネス ルールを選択的に適用します。</span><span class="sxs-lookup"><span data-stu-id="19d1f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], apply business rules selectively when you want to update or validate subsets of members against business rules.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19d1f-104">ビジネス ルールをモデルのバージョンのすべてのメンバーに適用する場合は、「 [ビジネス ルールに対してバージョンを検証する (マスター データ サービス)](validate-a-version-against-business-rules-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="19d1f-104">If you want to apply business rules to all members in a version of a model, see [Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="19d1f-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="19d1f-105">Prerequisites</span></span>  
 <span data-ttu-id="19d1f-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="19d1f-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="19d1f-107">**[エクスプローラー]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="19d1f-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="19d1f-108">ビジネス ルールを適用するモデル オブジェクトに対して、 **更新** 権限が最低限必要です。</span><span class="sxs-lookup"><span data-stu-id="19d1f-108">You must have a minimum of **Update** permission to the model object you are applying business rules to.</span></span>  
  
### <a name="to-apply-business-rules-selectively"></a><span data-ttu-id="19d1f-109">ビジネス ルールを選択的に適用するには</span><span class="sxs-lookup"><span data-stu-id="19d1f-109">To apply business rules selectively</span></span>  
  
1.  <span data-ttu-id="19d1f-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] のホーム ページで、 **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="19d1f-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="19d1f-111">**[バージョン]** ボックスの一覧からバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="19d1f-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="19d1f-112">**[エクスプローラー]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19d1f-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="19d1f-113">メニュー バーの **[エンティティ]** をポイントして、ルールを適用するメンバーを含むエンティティの名前をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19d1f-113">From the menu bar, point to **Entities** and click the name of the entity that contains members you want to apply rules to.</span></span>  
  
5.  <span data-ttu-id="19d1f-114">**[ビジネス ルールの適用]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="19d1f-114">Click **Apply business rules**.</span></span> <span data-ttu-id="19d1f-115">ビジネス ルールは、グリッドに表示されているメンバーにのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="19d1f-115">Business rules are applied only to the members displayed in the grid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d1f-116">参照</span><span class="sxs-lookup"><span data-stu-id="19d1f-116">See Also</span></span>  
 <span data-ttu-id="19d1f-117">[ビジネスルールに対してバージョンを検証する &#40;マスターデータサービス&#41;](validate-a-version-against-business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="19d1f-117">[Validate a Version against Business Rules &#40;Master Data Services&#41;](validate-a-version-against-business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="19d1f-118">ビジネス ルール (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="19d1f-118">Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/business-rules-master-data-services.md)  
  
  
