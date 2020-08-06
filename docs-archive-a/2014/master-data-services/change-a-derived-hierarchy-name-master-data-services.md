---
title: 派生階層名を変更する (マスター データ サービス) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, changing name
ms.assetid: 5765e710-d273-4675-aee2-5718273bfdc4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 230c4f9ebafd9519085ed40ae5115f2649df9bd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645727"
---
# <a name="change-a-derived-hierarchy-name-master-data-services"></a><span data-ttu-id="2227e-102">派生階層名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="2227e-102">Change a Derived Hierarchy Name (Master Data Services)</span></span>
  <span data-ttu-id="2227e-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、派生階層の名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="2227e-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of a derived hierarchy.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2227e-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="2227e-104">Prerequisites</span></span>  
 <span data-ttu-id="2227e-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="2227e-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="2227e-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="2227e-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="2227e-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2227e-107">You must be a model administrator.</span></span> <span data-ttu-id="2227e-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2227e-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-a-derived-hierarchy-name"></a><span data-ttu-id="2227e-109">派生階層名を変更するには</span><span class="sxs-lookup"><span data-stu-id="2227e-109">To change a derived hierarchy name</span></span>  
  
1.  <span data-ttu-id="2227e-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2227e-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="2227e-111">[**モデルビュー** ] ページのメニューバーから [**管理**] をポイントし、[**派生階層**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2227e-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Derived Hierarchies**.</span></span>  
  
3.  <span data-ttu-id="2227e-112">**[派生階層のメンテナンス]** ページの **[モデル]** の一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="2227e-112">On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="2227e-113">名前を変更する派生階層の行を選択します。</span><span class="sxs-lookup"><span data-stu-id="2227e-113">Select the row for the derived hierarchy that you want to rename.</span></span>  
  
5.  <span data-ttu-id="2227e-114">[**選択した派生階層の編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2227e-114">Click **Edit selected derived hierarchy**.</span></span>  
  
6.  <span data-ttu-id="2227e-115">[**派生階層の編集**] ページで、[**派生階層名の編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2227e-115">On the **Edit Derived Hierarchy** page, click **Edit derived hierarchy name**.</span></span>  
  
7.  <span data-ttu-id="2227e-116">**[派生階層名]** ボックスに、階層の更新後の名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="2227e-116">In the **Derived hierarchy name** box, type the updated name of the hierarchy.</span></span>  
  
8.  <span data-ttu-id="2227e-117">**[派生階層の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2227e-117">Click **Save derived hierarchy**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2227e-118">参照</span><span class="sxs-lookup"><span data-stu-id="2227e-118">See Also</span></span>  
 <span data-ttu-id="2227e-119">[派生階層 &#40;マスターデータサービス&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2227e-119">[Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="2227e-120">[派生階層 &#40;マスターデータサービスを作成し&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2227e-120">[Create a Derived Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="2227e-121">派生階層を削除する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="2227e-121">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)  
  
  
