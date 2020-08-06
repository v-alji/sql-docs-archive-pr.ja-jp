---
title: バージョンをロック解除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- unlocking versions [Master Data Services]
- versions [Master Data Services], unlocking
ms.assetid: b4cf4404-40f3-46fb-801d-cbf80a95448c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 6c522f8141c799ce4c1680a1aaf4ea8d6c2250ec
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740117"
---
# <a name="unlock-a-version-master-data-services"></a><span data-ttu-id="39e97-102">バージョンをロック解除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="39e97-102">Unlock a Version (Master Data Services)</span></span>
  <span data-ttu-id="39e97-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデルのバージョンをロック解除して、モデルのメンバーおよびメンバーの属性に対する変更を有効にします。</span><span class="sxs-lookup"><span data-stu-id="39e97-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], unlock a version of a model to enable changes to the model's members and their attributes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="39e97-104">[前提条件]</span><span class="sxs-lookup"><span data-stu-id="39e97-104">Prerequisites</span></span>  
 <span data-ttu-id="39e97-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="39e97-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="39e97-106">**[バージョン管理]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="39e97-106">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="39e97-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e97-107">You must be a model administrator.</span></span> <span data-ttu-id="39e97-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39e97-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="39e97-109">バージョンのステータスは、 **[ロック済み]** である必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e97-109">The version's status must be **Locked**.</span></span> <span data-ttu-id="39e97-110">詳細については、「 [バージョンをロックする (マスター データ サービス)](../../2014/master-data-services/lock-a-version-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39e97-110">For more information, see [Lock a Version &#40;Master Data Services&#41;](../../2014/master-data-services/lock-a-version-master-data-services.md).</span></span>  
  
### <a name="to-unlock-a-version"></a><span data-ttu-id="39e97-111">バージョンをロック解除するには</span><span class="sxs-lookup"><span data-stu-id="39e97-111">To unlock a version</span></span>  
  
1.  <span data-ttu-id="39e97-112">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e97-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="39e97-113">**[バージョンの管理]** ページで、ロック解除するバージョンの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="39e97-113">On the **Manage Versions** page, select the row for the version you want to unlock.</span></span>  
  
3.  <span data-ttu-id="39e97-114">**[ロックを解除]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e97-114">Click **Unlock**.</span></span>  
  
4.  <span data-ttu-id="39e97-115">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="39e97-115">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="39e97-116">次の手順</span><span class="sxs-lookup"><span data-stu-id="39e97-116">Next Steps</span></span>  
  
-   [<span data-ttu-id="39e97-117">バージョンをロックする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="39e97-117">Lock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="39e97-118">参照</span><span class="sxs-lookup"><span data-stu-id="39e97-118">See Also</span></span>  
 [<span data-ttu-id="39e97-119">バージョン (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="39e97-119">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
  
