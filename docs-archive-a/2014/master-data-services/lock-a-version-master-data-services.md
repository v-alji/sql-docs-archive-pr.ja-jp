---
title: バージョンをロックする (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], locking
- locking versions [Master Data Services]
ms.assetid: 7bb62a84-12d8-4b29-9b6e-6aa25410618e
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 68ef979b14d9bd228c7ca89a260b31b2fc6efccd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87738460"
---
# <a name="lock-a-version-master-data-services"></a><span data-ttu-id="287e1-102">バージョンをロックする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="287e1-102">Lock a Version (Master Data Services)</span></span>
  <span data-ttu-id="287e1-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデルのバージョンをロックして、モデルのメンバーおよびメンバーの属性に対する変更を防止します。</span><span class="sxs-lookup"><span data-stu-id="287e1-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], lock a version of a model to prevent changes to the model's members and their attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="287e1-104">バージョンをロックしても、モデル管理者は、引き続きメンバーの追加、編集、および削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="287e1-104">When a version is locked, model administrators can continue to add, edit, and remove members.</span></span> <span data-ttu-id="287e1-105">モデルに対する権限を持つその他のユーザーは、メンバーの表示のみを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="287e1-105">Other users with permission to the model can view members only.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="287e1-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="287e1-106">Prerequisites</span></span>  
 <span data-ttu-id="287e1-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="287e1-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="287e1-108">**[バージョン管理]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="287e1-108">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="287e1-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="287e1-109">You must be a model administrator.</span></span> <span data-ttu-id="287e1-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="287e1-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="287e1-111">バージョンのステータスは、 **[未処理]** である必要があります。</span><span class="sxs-lookup"><span data-stu-id="287e1-111">The version's status must be **Open**.</span></span>  
  
### <a name="to-lock-a-version"></a><span data-ttu-id="287e1-112">バージョンをロックするには</span><span class="sxs-lookup"><span data-stu-id="287e1-112">To lock a version</span></span>  
  
1.  <span data-ttu-id="287e1-113">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="287e1-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="287e1-114">**[バージョンの管理]** ページで、ロックするバージョンの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="287e1-114">On the **Manage Versions** page, select the row for the version that you want to lock.</span></span>  
  
3.  <span data-ttu-id="287e1-115">**[ロック]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="287e1-115">Click **Lock**.</span></span>  
  
4.  <span data-ttu-id="287e1-116">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="287e1-116">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="287e1-117">次の手順</span><span class="sxs-lookup"><span data-stu-id="287e1-117">Next Steps</span></span>  
  
-   [<span data-ttu-id="287e1-118">ビジネス ルールに対してバージョンを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="287e1-118">Validate a Version against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-a-version-against-business-rules-master-data-services.md)  
  
-   [<span data-ttu-id="287e1-119">バージョンをコミットする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="287e1-119">Commit a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/commit-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="287e1-120">参照</span><span class="sxs-lookup"><span data-stu-id="287e1-120">See Also</span></span>  
 <span data-ttu-id="287e1-121">[バージョン &#40;マスターデータサービス&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="287e1-121">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 [<span data-ttu-id="287e1-122">バージョンをロック解除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="287e1-122">Unlock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/unlock-a-version-master-data-services.md)  
  
  
