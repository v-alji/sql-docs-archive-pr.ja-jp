---
title: データの検証 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f8e97ff6481996b2e16436e1f78478bd234fe6ce
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641042"
---
# <a name="validating-data-mds-add-in-for-excel"></a><span data-ttu-id="a47c0-102">データの検証 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="a47c0-102">Validating Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="a47c0-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]でデータをパブリッシュするときに、以下の 2 種類の検証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="a47c0-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], when you publish data, two types of validation take place:</span></span>  
  
-   <span data-ttu-id="a47c0-104">定義されているすべてのビジネス ルールがデータに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a47c0-104">Any defined business rules are applied to the data.</span></span>  
  
-   <span data-ttu-id="a47c0-105">許可されている属性値 (文字数やデータ型など) に対してデータがチェックされます。</span><span class="sxs-lookup"><span data-stu-id="a47c0-105">Data is checked against allowed attribute values (for example, number of characters or type of data).</span></span>  
  
 <span data-ttu-id="a47c0-106">どちらの場合も、有効なデータが MDS リポジトリにパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="a47c0-106">In each case, valid data is published to the MDS repository.</span></span> <span data-ttu-id="a47c0-107">無効なデータは強調表示され、エラーの詳細は状態列で確認できます。</span><span class="sxs-lookup"><span data-stu-id="a47c0-107">Data that is not valid is highlighted, and details of the error can be shown in status columns.</span></span>  
  
## <a name="when-validation-occurs"></a><span data-ttu-id="a47c0-108">検証が実行されるタイミング</span><span class="sxs-lookup"><span data-stu-id="a47c0-108">When Validation Occurs</span></span>  
 <span data-ttu-id="a47c0-109">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、新しいデータまたは変更されたデータをパブリッシュするとき、またはビジネス ルールを手動で適用するときに、検証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="a47c0-109">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], validation occurs when you publish new or changed data, or when you manually apply business rules.</span></span>  
  
 <span data-ttu-id="a47c0-110">ビジネス ルールの検証に失敗しても、データは MDS リポジトリにパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="a47c0-110">When business rules fail, the data is still published to the MDS repository.</span></span> <span data-ttu-id="a47c0-111">入力の検証が失敗した場合は、データはリポジトリにパブリッシュされません。</span><span class="sxs-lookup"><span data-stu-id="a47c0-111">When input validation fails, the data is not published to the repository.</span></span>  
  
## <a name="validation-statuses"></a><span data-ttu-id="a47c0-112">検証状態</span><span class="sxs-lookup"><span data-stu-id="a47c0-112">Validation Statuses</span></span>  
 <span data-ttu-id="a47c0-113">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で考えられる検証状態は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a47c0-113">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], the following validation statuses are possible.</span></span>  
  
|<span data-ttu-id="a47c0-114">Status</span><span class="sxs-lookup"><span data-stu-id="a47c0-114">Status</span></span>|<span data-ttu-id="a47c0-115">説明</span><span class="sxs-lookup"><span data-stu-id="a47c0-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a47c0-116">エラー</span><span class="sxs-lookup"><span data-stu-id="a47c0-116">Error</span></span>|<span data-ttu-id="a47c0-117">行内の 1 つ以上の値で、MDS 管理者によって定義されたビジネス ルールに対する検証が失敗しました。</span><span class="sxs-lookup"><span data-stu-id="a47c0-117">One or more values in the row failed validation against business rules defined by an MDS administrator.</span></span>|  
|<span data-ttu-id="a47c0-118">未検証</span><span class="sxs-lookup"><span data-stu-id="a47c0-118">Not Validated</span></span>|<span data-ttu-id="a47c0-119">行内の値は、ビジネス ルールに対してまだ検証されていません。</span><span class="sxs-lookup"><span data-stu-id="a47c0-119">Values in the row have not yet been validated against business rules.</span></span>|  
|<span data-ttu-id="a47c0-120">Success</span><span class="sxs-lookup"><span data-stu-id="a47c0-120">Success</span></span>|<span data-ttu-id="a47c0-121">行内のすべての値は、ビジネス ルールに対する検証にパスしました。</span><span class="sxs-lookup"><span data-stu-id="a47c0-121">All values in the row have passed validation against business rules.</span></span>|  
  
## <a name="input-statuses"></a><span data-ttu-id="a47c0-122">入力状態</span><span class="sxs-lookup"><span data-stu-id="a47c0-122">Input Statuses</span></span>  
 <span data-ttu-id="a47c0-123">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で考えられる入力状態は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a47c0-123">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], the following input statuses are possible</span></span>  
  
|<span data-ttu-id="a47c0-124">Status</span><span class="sxs-lookup"><span data-stu-id="a47c0-124">Status</span></span>|<span data-ttu-id="a47c0-125">説明</span><span class="sxs-lookup"><span data-stu-id="a47c0-125">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a47c0-126">エラー</span><span class="sxs-lookup"><span data-stu-id="a47c0-126">Error</span></span>|<span data-ttu-id="a47c0-127">行内の 1 つまたは複数の値が、長さやデータ型などのシステム要件を満たしていません。</span><span class="sxs-lookup"><span data-stu-id="a47c0-127">One or more values in the row don't meet system requirements like length or data type.</span></span> <span data-ttu-id="a47c0-128">MDS リポジトリ内の値は更新されません。</span><span class="sxs-lookup"><span data-stu-id="a47c0-128">The value is not updated in the MDS repository.</span></span>|  
|<span data-ttu-id="a47c0-129">新しい行</span><span class="sxs-lookup"><span data-stu-id="a47c0-129">New Row</span></span>|<span data-ttu-id="a47c0-130">行内の値は、まだ MDS リポジトリにパブリッシュされていません。</span><span class="sxs-lookup"><span data-stu-id="a47c0-130">The values in the row have not yet been published to the MDS repository.</span></span>|  
|<span data-ttu-id="a47c0-131">[読み取り専用]</span><span class="sxs-lookup"><span data-stu-id="a47c0-131">Read Only</span></span>|<span data-ttu-id="a47c0-132">ログインしているユーザーは、行内の 1 つ以上の値に対して読み取り専用の権限を持っていて、値は更新されません。</span><span class="sxs-lookup"><span data-stu-id="a47c0-132">The logged in user has Read-only permissions to one or more values in the row and the value(s) cannot be updated.</span></span>|  
|<span data-ttu-id="a47c0-133">変更なし</span><span class="sxs-lookup"><span data-stu-id="a47c0-133">Unchanged</span></span>|<span data-ttu-id="a47c0-134">行の値は、ワークシート内で変更されていません。</span><span class="sxs-lookup"><span data-stu-id="a47c0-134">No values in the row have been changed in the worksheet.</span></span> <span data-ttu-id="a47c0-135">これは、リポジトリ内の値が変更されていないという意味ではありません。シート内の最新のデータを取得するには、 **[接続と読み込み]** グループで、 **[読み込みまたは更新]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="a47c0-135">This does not mean the values in the repository have not changed; to get the latest data in the sheet, in the **Connect and Load** group, click **Load or Refresh**.</span></span><br /><br /> <span data-ttu-id="a47c0-136">これは、各行の既定の設定です。</span><span class="sxs-lookup"><span data-stu-id="a47c0-136">This is the default setting for each row.</span></span>|  
  
## <a name="related-tasks"></a><span data-ttu-id="a47c0-137">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="a47c0-137">Related Tasks</span></span>  
  
|<span data-ttu-id="a47c0-138">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="a47c0-138">Task Description</span></span>|<span data-ttu-id="a47c0-139">トピック</span><span class="sxs-lookup"><span data-stu-id="a47c0-139">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="a47c0-140">定義されているビジネス ルールで失敗する値を決定します。</span><span class="sxs-lookup"><span data-stu-id="a47c0-140">Determine which values do not pass the defined business rules.</span></span>|[<span data-ttu-id="a47c0-141">ビジネス ルールの適用 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="a47c0-141">Apply Business Rules &#40;MDS Add-in for Excel&#41;</span></span>](apply-business-rules-mds-add-in-for-excel.md)|  
|<span data-ttu-id="a47c0-142">検証エラーを修正するために、メンバーに対して実行されたすべてのトランザクションを確認します。</span><span class="sxs-lookup"><span data-stu-id="a47c0-142">To help correct validation errors, view all transactions that have taken place for a member.</span></span>|[<span data-ttu-id="a47c0-143">メンバーのすべての注釈またはトランザクションの表示 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="a47c0-143">View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;</span></span>](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="a47c0-144">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="a47c0-144">Related Content</span></span>  
  
-   [<span data-ttu-id="a47c0-145">データ &#40;Excel 用 MDS アドインの公開&#41;</span><span class="sxs-lookup"><span data-stu-id="a47c0-145">Publishing Data &#40;MDS Add-in for Excel&#41;</span></span>](overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
