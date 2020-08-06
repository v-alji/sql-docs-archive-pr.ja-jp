---
title: バージョンをコピーする (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- versions [Master Data Services], copying
- copying versions [Master Data Services]
ms.assetid: f4678a02-bbe9-4f21-9e32-627eae053fe7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ca5c0bd92a54963257b461fac1425ef6b0385369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87716397"
---
# <a name="copy-a-version-master-data-services"></a><span data-ttu-id="b94db-102">バージョンをコピーする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b94db-102">Copy a Version (Master Data Services)</span></span>
  <span data-ttu-id="b94db-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]でモデルのバージョンをコピーして、新しいバージョンを作成します。</span><span class="sxs-lookup"><span data-stu-id="b94db-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], copy a version of the model to create a new version of it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b94db-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="b94db-104">Prerequisites</span></span>  
 <span data-ttu-id="b94db-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="b94db-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="b94db-106">**[バージョン管理]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b94db-106">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="b94db-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="b94db-107">You must be a model administrator.</span></span> <span data-ttu-id="b94db-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b94db-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-copy-a-version"></a><span data-ttu-id="b94db-109">バージョンをコピーするには</span><span class="sxs-lookup"><span data-stu-id="b94db-109">To copy a version</span></span>  
  
1.  <span data-ttu-id="b94db-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b94db-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="b94db-111">**[バージョンの管理]** ページで、コピーするバージョンの行を選択します。</span><span class="sxs-lookup"><span data-stu-id="b94db-111">On the **Manage Versions** page, select the row for the version that you want to copy.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b94db-112">[!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)]の設定によっては、コピーできるのは **[コミット]** (committed) 状態のバージョンだけである場合があります。</span><span class="sxs-lookup"><span data-stu-id="b94db-112">Depending on a setting in [!INCLUDE[ssMDScfgmgr](../includes/ssmdscfgmgr-md.md)], you might be able to copy versions with the **Committed** status only.</span></span> <span data-ttu-id="b94db-113">詳細については、「[システム設定 &#40;マスター データ サービス&#41;](../../2014/master-data-services/system-settings-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b94db-113">For more information, see [System Settings &#40;Master Data Services&#41;](../../2014/master-data-services/system-settings-master-data-services.md).</span></span>  
  
3.  <span data-ttu-id="b94db-114">[**コピー**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b94db-114">Click **Copy**.</span></span>  
  
4.  <span data-ttu-id="b94db-115">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="b94db-115">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b94db-116">次の手順</span><span class="sxs-lookup"><span data-stu-id="b94db-116">Next Steps</span></span>  
  
-   [<span data-ttu-id="b94db-117">バージョン名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b94db-117">Change a Version Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-version-name-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="b94db-118">参照</span><span class="sxs-lookup"><span data-stu-id="b94db-118">See Also</span></span>  
 [<span data-ttu-id="b94db-119">バージョン (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="b94db-119">Versions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/versions-master-data-services.md)  
  
  
