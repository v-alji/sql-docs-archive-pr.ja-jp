---
title: 属性の型の変更 (Excel 用 MDS アドイン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 9d3001d9-8d0f-4e4a-8e04-4f666bf0df69
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a55ca53fcf6923957e2196840aea2fb5914e1746
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714481"
---
# <a name="change-the-attribute-type-mds-add-in-for-excel"></a><span data-ttu-id="2d395-102">属性の型の変更 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="2d395-102">Change the Attribute Type (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="2d395-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]では、許可される文字のデータ型または文字数が間違っている場合に、管理者が属性の型を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="2d395-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], administrators can change the attribute type when the data type or number of allowed characters is incorrect.</span></span>  
  
 <span data-ttu-id="2d395-104">属性の型を変更して制約リスト (ドメイン ベースの属性) を作成する場合は、「[ドメイン ベースの属性を作成する (Excel 用 MDS アドイン)](create-a-domain-based-attribute-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d395-104">If you want to change the attribute type to create a constrained list (domain-based attribute), see [Create a Domain-based Attribute &#40;MDS Add-in for Excel&#41;](create-a-domain-based-attribute-mds-add-in-for-excel.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d395-105">**[名前]** 列または **[コード]** 列の型または長さを更新することはできません。</span><span class="sxs-lookup"><span data-stu-id="2d395-105">You cannot update the type or length of the **Name** or **Code** columns.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2d395-106">前提条件</span><span class="sxs-lookup"><span data-stu-id="2d395-106">Prerequisites</span></span>  
 <span data-ttu-id="2d395-107">この手順を実行するには</span><span class="sxs-lookup"><span data-stu-id="2d395-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="2d395-108">**[システム管理]** および **[エクスプローラー]** 機能領域に対する権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="2d395-108">You must have permission to access the **System Administration** and **Explorer** functional areas.</span></span>  
  
-   <span data-ttu-id="2d395-109">モデル管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d395-109">You must be a model administrator.</span></span> <span data-ttu-id="2d395-110">詳細については、「[管理者 &#40;マスターデータサービス&#41;](../administrators-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d395-110">For more information, see [Administrators &#40;Master Data Services&#41;](../administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="2d395-111">既存のモデル、エンティティ、および属性が存在している必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d395-111">There must be an existing model, entity, and attribute.</span></span>  
  
### <a name="to-change-the-attribute-type"></a><span data-ttu-id="2d395-112">属性の型を変更するには</span><span class="sxs-lookup"><span data-stu-id="2d395-112">To change the attribute type</span></span>  
  
1.  <span data-ttu-id="2d395-113">Excel で、変更する列 (属性) を含むエンティティを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2d395-113">In Excel, load the entity that contains the column (attribute) you want to change.</span></span> <span data-ttu-id="2d395-114">詳細については、「 [MDS から Excel へのデータの読み込み](export-data-to-excel-from-master-data-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2d395-114">For more information, see [Load Data from MDS into Excel](export-data-to-excel-from-master-data-services.md).</span></span>  
  
2.  <span data-ttu-id="2d395-115">変更する列の任意のセルをクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d395-115">Click any cell in the column you want to change.</span></span>  
  
3.  <span data-ttu-id="2d395-116">**[モデルの構築]** グループの **[属性プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d395-116">In the **Build Model** group, click **Attribute Properties**.</span></span>  
  
4.  <span data-ttu-id="2d395-117">**[属性プロパティ]** ダイアログ ボックスで、必要に応じて設定を更新します。</span><span class="sxs-lookup"><span data-stu-id="2d395-117">In the **Attribute Properties** dialog box, update settings as needed.</span></span>  
  
5.  <span data-ttu-id="2d395-118">**[OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="2d395-118">Click **OK**.</span></span>  
  
## <a name="what-happens-when-you-change-the-attribute-type"></a><span data-ttu-id="2d395-119">属性の型を変更したときに実行される動作</span><span class="sxs-lookup"><span data-stu-id="2d395-119">What happens when you change the attribute type?</span></span>  
 <span data-ttu-id="2d395-120">属性が任意の MDS ビジネス ルールによって参照されるか、属性がサブスクリプション ビューに含まれるなど、属性に関する依存関係が存在する場合に、属性のデータ型を変更すると、MDS によって次の動作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="2d395-120">If there is any dependency on the attribute, such as the attribute is referenced by any MDS business rule or the attribute is included in a subscription view, and you change the data type of an attribute, MDS will:</span></span>  
  
-   <span data-ttu-id="2d395-121">属性のデータ型を変更します。</span><span class="sxs-lookup"><span data-stu-id="2d395-121">Change the data type of the attribute.</span></span>  
  
-   <span data-ttu-id="2d395-122">値を含まないサフィックス "_old" を持つ属性のコピーを生成します。</span><span class="sxs-lookup"><span data-stu-id="2d395-122">Generate a copy of the attribute with the suffix "_old" that does not contain any value.</span></span> <span data-ttu-id="2d395-123">これは**非推奨**の属性と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="2d395-123">This is called a **deprecated** attribute.</span></span>  
  
 <span data-ttu-id="2d395-124">ただし、元の属性に対する既存の依存関係すべては、変更後の属性ではなく非推奨の属性を指します。</span><span class="sxs-lookup"><span data-stu-id="2d395-124">However, all the existing dependencies on the original attribute will point to the deprecated attribute, and not to the changed one.</span></span>  
  
 <span data-ttu-id="2d395-125">この事実は、次のことを暗黙的に意味します。</span><span class="sxs-lookup"><span data-stu-id="2d395-125">This implies that:</span></span>  
  
-   <span data-ttu-id="2d395-126">変更後の属性を指すようにビジネス ルールを更新する必要があります。属性の新しいデータ型を使用する場合は、ロジックが同じにならない可能性があるからです。</span><span class="sxs-lookup"><span data-stu-id="2d395-126">You must refresh the business rules to point to the changed attribute because the logic may not be the same given the new data type of the attribute.</span></span> <span data-ttu-id="2d395-127">影響を受ける各ルールを編集し、その後、非推奨の属性 (_old) への参照を削除し、更新後の属性を指すように式を書き直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d395-127">You will have to edit each affected rule, and then rework the expressions to point to remove references from the deprecated attribute (_old) to point to the updated attribute.</span></span>  
  
-   <span data-ttu-id="2d395-128">[統合管理] の選択項目の下にある任意のサブスクリプションビューを開き、[表示] 行を選択します。次に、鉛筆アイコンをクリックして編集用に開き、[**ディスクの保存**] アイコンをクリックしてビュー定義を更新します。</span><span class="sxs-lookup"><span data-stu-id="2d395-128">You must open any subscription views under the Integration Management selection, select the view row, open it for editing by clicking the pencil icon, and then click the **Save disk** icon to refresh the view definition.</span></span> <span data-ttu-id="2d395-129">ビューの構文を再生成するために、他の変更を加える必要はありません。</span><span class="sxs-lookup"><span data-stu-id="2d395-129">No other change is needed to regenerate the view syntax.</span></span>  
  
-   <span data-ttu-id="2d395-130">この属性を含むステージング テーブルに対して、非推奨属性の列が追加されます。これは、ステージング コードが影響を受けることを意味します。</span><span class="sxs-lookup"><span data-stu-id="2d395-130">Staging tables that include the attribute will have a deprecated attribute column added to them, which means that your staging code will be affected.</span></span> <span data-ttu-id="2d395-131">非推奨の属性を除去するために、ビジネス ルールとサブスクリプション ビューを更新した後にその属性を削除することができます。</span><span class="sxs-lookup"><span data-stu-id="2d395-131">To get rid of the deprecated attribute, you can delete it after you have updated the business rules and subscription views.</span></span>  
  
 <span data-ttu-id="2d395-132">**非推奨の属性の削除**</span><span class="sxs-lookup"><span data-stu-id="2d395-132">**Deleting the deprecated attribute**</span></span>  
  
 <span data-ttu-id="2d395-133">任意の非推奨属性を削除する前に、既に説明したようにビジネス ルールを修正してサブスクリプション ビューを再生成するなど、その属性に対するすべての参照を削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2d395-133">Before you delete any deprecated attribute, you must remove any references to the attribute such as fixing the business rules and regenerating subscription views as described earlier.</span></span> <span data-ttu-id="2d395-134">そうしない場合は、非推奨の属性を削除しようとしたときに、オブジェクトによって参照されているために属性が削除できないことを示すエラーが [システム管理] Web ページで表示されます。</span><span class="sxs-lookup"><span data-stu-id="2d395-134">Otherwise, you will get an error in the System Administration web page when you attempt to delete the deprecated attribute stating that the attribute cannot be deleted because it is referenced by an object.</span></span>  
  
 <span data-ttu-id="2d395-135">属性を削除するには、「[属性 &#40;マスターデータサービスを削除](../delete-an-attribute-master-data-services.md)する」を参照してください&#41;</span><span class="sxs-lookup"><span data-stu-id="2d395-135">To delete an attribute, see [Delete an Attribute &#40;Master Data Services&#41;](../delete-an-attribute-master-data-services.md)</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="2d395-136">既存のデータと関連エンティティが存在する MDS 属性のデータ型を変更するのは面倒であり、エンティティに依存するビジネス ルールまたはサブスクリプション ビューが宣言されている場合は特にこのことが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="2d395-136">It is cumbersome to change data types for MDS attributes that have existing data and related entities, especially if there is a business rule or subscription view declared which depends on the entity.</span></span> <span data-ttu-id="2d395-137">ベスト プラクティスは、必要な値を保持できる十分な柔軟性を持つデータ型を使用して作業を開始することです。</span><span class="sxs-lookup"><span data-stu-id="2d395-137">The best practice is to start with a data type that is flexible enough to hold the necessary values.</span></span> <span data-ttu-id="2d395-138">たとえば、最初は文字列を小規模で開始できるとしても、時間の経過に伴って長くなる可能性があります。そのため、最悪のシナリオを考慮に入れてください。</span><span class="sxs-lookup"><span data-stu-id="2d395-138">For example, strings may start small, but may need to be lengthened over time, so consider the worst case scenarios.</span></span> <span data-ttu-id="2d395-139">一方、過度に長いテキスト文字列も負担になる可能性がある (たとえば、長い GUI テキスト ボックスは画面に収めるのが困難) ので、過度に長い文字列を避けてください。</span><span class="sxs-lookup"><span data-stu-id="2d395-139">Extra text string length can be burdensome (for example, wide GUI text boxes are hard to fit on the screen), so avoid too long string length.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d395-140">参照</span><span class="sxs-lookup"><span data-stu-id="2d395-140">See Also</span></span>  
 <span data-ttu-id="2d395-141">[属性 &#40;マスターデータサービス&#41;](../attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2d395-141">[Attributes &#40;Master Data Services&#41;](../attributes-master-data-services.md) </span></span>  
 [<span data-ttu-id="2d395-142">モデルの構築 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="2d395-142">Building a Model &#40;MDS Add-in for Excel&#41;</span></span>](building-a-model-mds-add-in-for-excel.md)  
  
  
