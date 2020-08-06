---
title: 属性名を変更する (マスターデータサービス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], changing name
ms.assetid: d348f238-f59d-41c7-ad20-3ccd55bfd9e5
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: abbe5f666daed42b25b46f02e954343b57446145
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718375"
---
# <a name="change-an-attribute-name-master-data-services"></a><span data-ttu-id="0e5e7-102">属性名を変更する (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0e5e7-102">Change an Attribute Name (Master Data Services)</span></span>
  <span data-ttu-id="0e5e7-103">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]では、属性の名前を変更できます。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you can change the name of an attribute.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0e5e7-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="0e5e7-104">Prerequisites</span></span>  
 <span data-ttu-id="0e5e7-105">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="0e5e7-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="0e5e7-106">[**システム管理**] 機能領域にアクセスするためのアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="0e5e7-107">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-107">You must be a model administrator.</span></span> <span data-ttu-id="0e5e7-108">詳細については、「[管理者 &#40;マスターデータサービス&#41;](administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-change-an-attribute-name"></a><span data-ttu-id="0e5e7-109">属性名を変更するには</span><span class="sxs-lookup"><span data-stu-id="0e5e7-109">To change an attribute name</span></span>  
  
1.  <span data-ttu-id="0e5e7-110">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]で **[システム管理]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-110">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="0e5e7-111">**[モデル ビュー]** ページのメニュー バーから **[管理]** をポイントして **[エンティティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-111">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="0e5e7-112">**[エンティティのメンテナンス]** ページの **[モデル]** ボックスの一覧からモデルを選択します。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-112">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="0e5e7-113">名前を変更する属性を含むエンティティの行をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-113">Click the row for the entity that contains the attribute with the name you want to change.</span></span>  
  
5.  <span data-ttu-id="0e5e7-114">**[選択したエンティティの編集]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-114">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="0e5e7-115">[**エンティティの編集**] ページで、名前を変更する属性をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-115">On the **Edit Entity** page, click the attribute with the name you want to change.</span></span>  
  
7.  <span data-ttu-id="0e5e7-116">[**選択した属性の編集**] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-116">Click **Edit selected attribute**.</span></span>  
  
8.  <span data-ttu-id="0e5e7-117">**[名前]** ボックスに、属性の新しい名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-117">In the **Name** box, type the updated name of the attribute.</span></span> <span data-ttu-id="0e5e7-118">属性名として使用しない単語の一覧については、「[予約語 &#40;マスターデータサービス&#41;](reserved-words-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-118">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="0e5e7-119">**[属性の保存]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="0e5e7-119">Click **Save attribute**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e5e7-120">参照</span><span class="sxs-lookup"><span data-stu-id="0e5e7-120">See Also</span></span>  
 <span data-ttu-id="0e5e7-121">[テキスト属性 &#40;マスターデータサービスを作成し&#41;](create-a-text-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0e5e7-121">[Create a Text Attribute &#40;Master Data Services&#41;](create-a-text-attribute-master-data-services.md) </span></span>  
 <span data-ttu-id="0e5e7-122">[属性 &#40;マスターデータサービスの削除&#41;](delete-an-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="0e5e7-122">[Delete an Attribute &#40;Master Data Services&#41;](delete-an-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="0e5e7-123">属性 (マスター データ サービス)</span><span class="sxs-lookup"><span data-stu-id="0e5e7-123">Attributes &#40;Master Data Services&#41;</span></span>](attributes-master-data-services.md)  
  
  
