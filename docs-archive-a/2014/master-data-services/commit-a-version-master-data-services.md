---
title: バージョンをコミットする (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: cec3244d4ddaa78d9168e3ede503fa16756633a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87715538"
---
# <a name="commit-a-version-master-data-services"></a><span data-ttu-id="c1963-102">バージョンをコミットする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1963-102">Commit a Version (Master Data Services)</span></span>
  <span data-ttu-id="c1963-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデルのバージョンをコミットして、モデルのメンバーおよびメンバーの属性に対する変更を防止します。</span><span class="sxs-lookup"><span data-stu-id="c1963-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], commit a version of a model to prevent changes to the model's members and their attributes.</span></span> <span data-ttu-id="c1963-104">コミットしたバージョンはロック解除できません。</span><span class="sxs-lookup"><span data-stu-id="c1963-104">Committed versions cannot be unlocked.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c1963-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="c1963-105">Prerequisites</span></span>  
 <span data-ttu-id="c1963-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="c1963-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="c1963-107">**[バージョン管理]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="c1963-107">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="c1963-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1963-108">You must be a model administrator.</span></span> <span data-ttu-id="c1963-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1963-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="c1963-110">バージョンのステータスは、 **[ロック済み]** である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1963-110">The version's status must be **Locked**.</span></span> <span data-ttu-id="c1963-111">詳細については、「 [バージョンをロックする (マスター データ サービス)](../../2014/master-data-services/lock-a-version-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c1963-111">For more information, see [Lock a Version &#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="c1963-112">すべてのメンバーが正常に検証されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1963-112">All members must have validated successfully.</span></span>  
  
### <a name="to-commit-a-version"></a><span data-ttu-id="c1963-113">バージョンをコミットするには</span><span class="sxs-lookup"><span data-stu-id="c1963-113">To commit a version</span></span>  
  
1.  <span data-ttu-id="c1963-114">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1963-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="c1963-115">**[バージョンの管理]** ページのメニュー バーの **[バージョンの検証]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1963-115">On the **Manage Versions** page, on the menu bar, click **Validate Version**.</span></span>  
  
3.  <span data-ttu-id="c1963-116">**[バージョンの検証]** ページで、コミットするモデルおよびバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="c1963-116">On the **Validate Version** page, select the model and version you want to commit.</span></span>  
  
4.  <span data-ttu-id="c1963-117">**[コミット]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1963-117">Click **Commit**.</span></span>  
  
5.  <span data-ttu-id="c1963-118">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c1963-118">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c1963-119">次の手順</span><span class="sxs-lookup"><span data-stu-id="c1963-119">Next Steps</span></span>  
  
-   [<span data-ttu-id="c1963-120">バージョン フラグを作成する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1963-120">Create a Version Flag &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [<span data-ttu-id="c1963-121">バージョンにフラグを割り当てる (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1963-121">Assign a Flag to a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [<span data-ttu-id="c1963-122">バージョンをコピーする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1963-122">Copy a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="c1963-123">参照</span><span class="sxs-lookup"><span data-stu-id="c1963-123">See Also</span></span>  
 [<span data-ttu-id="c1963-124">バージョン (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c1963-124">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
  
