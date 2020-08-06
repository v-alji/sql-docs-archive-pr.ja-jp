---
title: ビジネス ルールに対してバージョンを検証する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- validating versions [Master Data Services]
- validating versions [Master Data Services], about validating versions
- versions [Master Data Services], validating
- business rules [Master Data Services], applying to all members
ms.assetid: 5aee7901-6d05-41d4-8bbb-c6f26791d1df
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 085fa071ca511c9d838c140547419bf87fb857bb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640121"
---
# <a name="validate-a-version-against-business-rules-master-data-services"></a><span data-ttu-id="d84e5-102">ビジネス ルールに対してバージョンを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d84e5-102">Validate a Version against Business Rules (Master Data Services)</span></span>
  <span data-ttu-id="d84e5-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、ビジネス ルールをモデル バージョンのすべてのメンバーに適用するためにバージョンが検証されます。</span><span class="sxs-lookup"><span data-stu-id="d84e5-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], validate a version to apply business rules to all members in the model version.</span></span>  
  
 <span data-ttu-id="d84e5-104">この手順では、 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web アプリケーションを使用してデータを検証する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d84e5-104">This procedure explains how to use the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application to validate data.</span></span> <span data-ttu-id="d84e5-105">MDS データベースの権限がある場合は、代わりにストアド プロシージャを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="d84e5-105">If you have permission in the MDS database, you can use a stored procedure instead.</span></span> <span data-ttu-id="d84e5-106">詳細については、「 [検証ストアド プロシージャ (マスター データ サービス)](validation-stored-procedure-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d84e5-106">For more information, see [Validation Stored Procedure &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d84e5-107">バージョンをコミットするには、すべてのメンバーが検証に合格する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d84e5-107">All members must pass validation before a version can be committed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d84e5-108">前提条件</span><span class="sxs-lookup"><span data-stu-id="d84e5-108">Prerequisites</span></span>  
 <span data-ttu-id="d84e5-109">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="d84e5-109">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d84e5-110">**[バージョン管理]** 機能領域にアクセスする権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="d84e5-110">You must have permission to access the **Version Management** functional area.</span></span>  
  
-   <span data-ttu-id="d84e5-111">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d84e5-111">You must be a model administrator.</span></span> <span data-ttu-id="d84e5-112">詳細については、「[管理者 &#40;マスターデータサービス&#41;](../../2014/master-data-services/administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d84e5-112">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="d84e5-113">バージョンの状態は、 **[未処理]** または **[ロック済み]** である必要があります。</span><span class="sxs-lookup"><span data-stu-id="d84e5-113">The version's status must be **Open** or **Locked**.</span></span>  
  
-   <span data-ttu-id="d84e5-114">**[バージョンの検証]** ページに **[検証成功]** 以外の状態のメンバーが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d84e5-114">On the **Validate Versions** page, members must exist with a status other than **Validation succeeded**.</span></span>  
  
### <a name="to-validate-a-version"></a><span data-ttu-id="d84e5-115">バージョンを検証するには</span><span class="sxs-lookup"><span data-stu-id="d84e5-115">To validate a version</span></span>  
  
1.  <span data-ttu-id="d84e5-116">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[バージョン管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d84e5-116">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **Version Management**.</span></span>  
  
2.  <span data-ttu-id="d84e5-117">**[バージョンの管理]** ページのメニュー バーから **[バージョンの検証]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d84e5-117">On the **Manage Versions** page, from the menu bar, click **Validate Version**.</span></span>  
  
3.  <span data-ttu-id="d84e5-118">**[バージョンの検証]** ページで、検証するモデルおよびバージョンを選択します。</span><span class="sxs-lookup"><span data-stu-id="d84e5-118">On the **Validate Versions** page, select the model and version you want to validate.</span></span>  
  
4.  <span data-ttu-id="d84e5-119">**[検証]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d84e5-119">Click **Validate**.</span></span>  
  
5.  <span data-ttu-id="d84e5-120">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="d84e5-120">In the confirmation dialog box, click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="d84e5-121">バージョンの検証が完了すると、進行状況インジケーターが表示されなくなります。</span><span class="sxs-lookup"><span data-stu-id="d84e5-121">When the progress indicator is no longer displayed, the version has finished validation.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d84e5-122">次の手順</span><span class="sxs-lookup"><span data-stu-id="d84e5-122">Next Steps</span></span>  
  
-   [<span data-ttu-id="d84e5-123">バージョンをロックする (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d84e5-123">Lock a Version &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/lock-a-version-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="d84e5-124">参照</span><span class="sxs-lookup"><span data-stu-id="d84e5-124">See Also</span></span>  
 <span data-ttu-id="d84e5-125">[検証の状態 &#40;マスターデータサービス&#41;](../../2014/master-data-services/validation-statuses-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d84e5-125">[Validation Statuses &#40;Master Data Services&#41;](../../2014/master-data-services/validation-statuses-master-data-services.md) </span></span>  
 <span data-ttu-id="d84e5-126">[検証ストアドプロシージャ &#40;マスターデータサービス&#41;](validation-stored-procedure-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d84e5-126">[Validation Stored Procedure &#40;Master Data Services&#41;](validation-stored-procedure-master-data-services.md) </span></span>  
 <span data-ttu-id="d84e5-127">[バージョン &#40;マスターデータサービス&#41;](../../2014/master-data-services/versions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d84e5-127">[Versions &#40;Master Data Services&#41;](../../2014/master-data-services/versions-master-data-services.md) </span></span>  
 <span data-ttu-id="d84e5-128">[ビジネスルール &#40;マスターデータサービス&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d84e5-128">[Business Rules &#40;Master Data Services&#41;](../../2014/master-data-services/business-rules-master-data-services.md) </span></span>  
 [<span data-ttu-id="d84e5-129">ビジネス ルールに対して特定のメンバーを検証する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="d84e5-129">Validate Specific Members against Business Rules &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/validate-specific-members-against-business-rules-master-data-services.md)  
  
  
