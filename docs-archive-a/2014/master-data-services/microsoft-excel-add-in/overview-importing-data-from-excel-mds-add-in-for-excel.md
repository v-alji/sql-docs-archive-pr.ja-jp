---
title: データのパブリッシュ (Excel 用 MDS アドイン) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ea84a9aa-aeec-411b-ab8d-bc1b14f864a3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ab37a353469d1902394a3e2cd8060d9be82abb40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720216"
---
# <a name="publishing-data-mds-add-in-for-excel"></a><span data-ttu-id="472b7-102">データのパブリッシュ (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="472b7-102">Publishing Data (MDS Add-in for Excel)</span></span>
  <span data-ttu-id="472b7-103">[!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]で、他のユーザーとデータを共有するには、データを MDS リポジトリにパブリッシュします。</span><span class="sxs-lookup"><span data-stu-id="472b7-103">In the [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], publish data to the MDS repository when you want to share it with other users.</span></span> <span data-ttu-id="472b7-104">パブリッシュされたデータはすぐに、他のアドイン ユーザーがダウンロードできるようになります。</span><span class="sxs-lookup"><span data-stu-id="472b7-104">As soon as data is published, it is available for other users of the Add-in to download.</span></span>  
  
 <span data-ttu-id="472b7-105">データを発行すると、追加または更新したすべてのデータが MDS リポジトリに発行されます。</span><span class="sxs-lookup"><span data-stu-id="472b7-105">When you publish data, any data you've added or updated is published to the MDS repository.</span></span> <span data-ttu-id="472b7-106">削除したデータは発行されません。データの削除は個別に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="472b7-106">Data you've deleted is not published-you must delete data separately.</span></span> <span data-ttu-id="472b7-107">詳細については、「 [行の削除 (Excel 用 MDS アドイン)](delete-a-row-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="472b7-107">For more information, see [Delete a Row &#40;MDS Add-in for Excel&#41;](delete-a-row-mds-add-in-for-excel.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="472b7-108">パブリッシュは、新しいエンティティの作成には使用できません。</span><span class="sxs-lookup"><span data-stu-id="472b7-108">Publishing cannot be used to create a new entity.</span></span> <span data-ttu-id="472b7-109">エンティティの作成の詳細については、「[エンティティを作成する (Excel 用 MDS アドイン)](create-an-entity-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="472b7-109">For more information about creating entities, see [Create an Entity &#40;MDS Add-in for Excel&#41;](create-an-entity-mds-add-in-for-excel.md).</span></span>  
  
## <a name="when-multiple-users-publish-at-the-same-time"></a><span data-ttu-id="472b7-110">複数のユーザーが同時にパブリッシュした場合</span><span class="sxs-lookup"><span data-stu-id="472b7-110">When Multiple Users Publish at the Same Time</span></span>  
 <span data-ttu-id="472b7-111">複数のユーザーが同じデータの更新をパブリッシュする場合があります。</span><span class="sxs-lookup"><span data-stu-id="472b7-111">Multiple users can publish updates to the same data.</span></span> <span data-ttu-id="472b7-112">各ユーザーがパブリッシュすると、更新がデータベースに保存されます。</span><span class="sxs-lookup"><span data-stu-id="472b7-112">As each user publishes, the update is saved to the database.</span></span> <span data-ttu-id="472b7-113">つまり、最後に更新されたデータを操作していなかったユーザーが、パブリッシュ時に値を変更する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="472b7-113">This means that a user who was not working with the most recently-updated data can still change the value when he or she publishes.</span></span>  
  
 <span data-ttu-id="472b7-114">実行した更新だけがデータベースにパブリッシュされます。</span><span class="sxs-lookup"><span data-stu-id="472b7-114">Only the updates you make are published to the database.</span></span> <span data-ttu-id="472b7-115">ワークシート内の古いデータはパブリッシュされません。</span><span class="sxs-lookup"><span data-stu-id="472b7-115">Any out-of-date data in the worksheet is not published.</span></span>  
  
## <a name="transactions-and-annotations"></a><span data-ttu-id="472b7-116">トランザクションと注釈</span><span class="sxs-lookup"><span data-stu-id="472b7-116">Transactions and Annotations</span></span>  
 <span data-ttu-id="472b7-117">パブリッシュされた各変更は、トランザクションとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="472b7-117">Each published change is saved as a transaction.</span></span> <span data-ttu-id="472b7-118">必要に応じて、変更を行った理由を説明する注釈 (コメント) をトランザクションに追加できます。</span><span class="sxs-lookup"><span data-stu-id="472b7-118">If you choose, you can add annotations (comments) to a transaction, to explain why you made the change.</span></span>  
  
-   <span data-ttu-id="472b7-119">削除に注釈を付けることはできませんが、削除は管理者が取り消すことができるトランザクションとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="472b7-119">You cannot annotate deletions, although deletions are saved as transactions that can be reversed by an administrator.</span></span>  
  
-   <span data-ttu-id="472b7-120">メンバーの**コード**値を変更した場合、そのメンバーはトランザクションとして記録されず、そのメンバーの以前のトランザクションはすべて使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="472b7-120">If you change the **Code** value for a member, it is not recorded as a transaction, and all previous transactions for the member are unavailable.</span></span>  
  
-   <span data-ttu-id="472b7-121">他のユーザーがメンバーに対して行ったトランザクションを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="472b7-121">You can view transactions made to a member by other users.</span></span> <span data-ttu-id="472b7-122">また、特定の属性に対する権限を失った場合でも、メンバーに対して行ったすべてのトランザクションを表示できます。</span><span class="sxs-lookup"><span data-stu-id="472b7-122">You can also view all transactions you've made to a member, even if you no longer have permission to specific attributes.</span></span>  
  
 <span data-ttu-id="472b7-123">メンバーに対して行われたすべてのトランザクションを表示することができます。</span><span class="sxs-lookup"><span data-stu-id="472b7-123">You can view all transactions made to a member.</span></span> <span data-ttu-id="472b7-124">詳細については、「 [メンバーのすべての注釈またはトランザクションの表示 (Excel 用 MDS アドイン)](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="472b7-124">For more information, see [View All Annotations or Transactions for a Member &#40;MDS Add-in for Excel&#41;](view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="472b7-125">500 文字を超える注釈を入力すると、その注釈は自動的に切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="472b7-125">If you enter an annotation of more than 500 characters, the annotation is automatically truncated.</span></span>  
  
## <a name="business-rule-and-other-validation"></a><span data-ttu-id="472b7-126">ビジネス ルールとその他の検証</span><span class="sxs-lookup"><span data-stu-id="472b7-126">Business Rule and Other Validation</span></span>  
 <span data-ttu-id="472b7-127">データを発行すると、MDS リポジトリへの追加前に、データが正確であることを確保する検証が実行されます。</span><span class="sxs-lookup"><span data-stu-id="472b7-127">When you publish data, validation is performed to ensure data is accurate before it's added to the MDS repository.</span></span> <span data-ttu-id="472b7-128">データが指定した条件を満たしていない場合は、リポジトリにパブリッシュされません。</span><span class="sxs-lookup"><span data-stu-id="472b7-128">If the data does not meet specified criteria, it will not be published to the repository.</span></span> <span data-ttu-id="472b7-129">詳細については、「[データの検証 (Excel 用 MDS アドイン)](validating-data-mds-add-in-for-excel.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="472b7-129">For more information, see [Validating Data &#40;MDS Add-in for Excel&#41;](validating-data-mds-add-in-for-excel.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="472b7-130">Related Tasks</span><span class="sxs-lookup"><span data-stu-id="472b7-130">Related Tasks</span></span>  
  
|<span data-ttu-id="472b7-131">タスクの説明</span><span class="sxs-lookup"><span data-stu-id="472b7-131">Task Description</span></span>|<span data-ttu-id="472b7-132">トピック</span><span class="sxs-lookup"><span data-stu-id="472b7-132">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="472b7-133">アクティブなワークシートのデータをパブリッシュして MDS リポジトリに戻します。</span><span class="sxs-lookup"><span data-stu-id="472b7-133">Publish data from the active worksheet back to the MDS repository.</span></span>|[<span data-ttu-id="472b7-134">Excel から MDS へのデータのパブリッシュ &#40;Excel 用 MDS アドイン&#41;</span><span class="sxs-lookup"><span data-stu-id="472b7-134">Publish Data from Excel to MDS &#40;MDS Add-in for Excel&#41;</span></span>](import-data-from-excel-to-master-data-services-mds-add-in-for-excel.md)|  
|<span data-ttu-id="472b7-135">MDS リポジトリとワークシートから行を同時に削除します。</span><span class="sxs-lookup"><span data-stu-id="472b7-135">Delete a row from the MDS repository and from the worksheet at the same time.</span></span>|[<span data-ttu-id="472b7-136">行の削除 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="472b7-136">Delete a Row &#40;MDS Add-in for Excel&#41;</span></span>](delete-a-row-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a><span data-ttu-id="472b7-137">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="472b7-137">Related Content</span></span>  
  
-   [<span data-ttu-id="472b7-138">データの更新 (Excel 用 MDS アドイン)</span><span class="sxs-lookup"><span data-stu-id="472b7-138">Refreshing Data &#40;MDS Add-in for Excel&#41;</span></span>](refreshing-data-mds-add-in-for-excel.md)  
  
-   [<span data-ttu-id="472b7-139">Microsoft Excel 用マスター データ サービス アドイン</span><span class="sxs-lookup"><span data-stu-id="472b7-139">Master Data Services Add-in for Microsoft Excel</span></span>](master-data-services-add-in-for-microsoft-excel.md)  
  
  
