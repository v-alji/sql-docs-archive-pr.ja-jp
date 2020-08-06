---
title: 派生階層を削除する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting derived hierarchies [Master Data Services]
- derived hierarchies, deleting
ms.assetid: f46d660e-47f2-47ca-9372-1b5931540beb
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a49922c0d719415436d28eb48657a7fc93c547fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641718"
---
# <a name="delete-a-derived-hierarchy-master-data-services"></a><span data-ttu-id="c0ed5-102">派生階層を削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c0ed5-102">Delete a Derived Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="c0ed5-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]で、不要になった派生階層を削除します。</span><span class="sxs-lookup"><span data-stu-id="c0ed5-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete a derived hierarchy when you are sure you no longer need it.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c0ed5-104">派生階層を削除しても、その階層が基づいている属性リレーションシップには影響しません。</span><span class="sxs-lookup"><span data-stu-id="c0ed5-104">Deleting a derived hierarchy has no effect on the attribute relationships that the hierarchy is based on.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c0ed5-105">前提条件</span><span class="sxs-lookup"><span data-stu-id="c0ed5-105">Prerequisites</span></span>  
 <span data-ttu-id="c0ed5-106">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="c0ed5-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="c0ed5-107">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="c0ed5-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="c0ed5-108">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0ed5-108">You must be a model administrator.</span></span> <span data-ttu-id="c0ed5-109">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0ed5-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-a-derived-hierarchy"></a><span data-ttu-id="c0ed5-110">派生階層を削除するには</span><span class="sxs-lookup"><span data-stu-id="c0ed5-110">To delete a derived hierarchy</span></span>  
  
1.  <span data-ttu-id="c0ed5-111">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0ed5-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="c0ed5-112">[**モデルビュー** ] ページのメニューバーから [**管理**] をポイントし、[**派生階層**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0ed5-112">On the **Model View** page, from the menu bar, point to **Manage** and click **Derived Hierarchies**.</span></span>  
  
3.  <span data-ttu-id="c0ed5-113">**[派生階層のメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="c0ed5-113">On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="c0ed5-114">削除する派生階層の行を選択します。</span><span class="sxs-lookup"><span data-stu-id="c0ed5-114">Select the row for the derived hierarchy that you want to delete.</span></span>  
  
5.  <span data-ttu-id="c0ed5-115">[**選択した階層の削除**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0ed5-115">Click **Delete selected hierarchy**.</span></span>  
  
6.  <span data-ttu-id="c0ed5-116">確認のダイアログ ボックスで **[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c0ed5-116">In the confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ed5-117">参照</span><span class="sxs-lookup"><span data-stu-id="c0ed5-117">See Also</span></span>  
 <span data-ttu-id="c0ed5-118">[派生階層 &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="c0ed5-118">[Create a Derived Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="c0ed5-119">派生階層 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="c0ed5-119">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
