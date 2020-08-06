---
title: 論理レコードの競合の検出および解決 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- logical records [SQL Server replication]
- conflict resolution [SQL Server replication], merge replication
ms.assetid: f2e55040-ca69-4ccf-97d1-c362e1633f26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f9822cd153af67538a36a894de0ec1b4716e54cf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87630972"
---
# <a name="detecting-and-resolving-conflicts-in-logical-records"></a><span data-ttu-id="86b74-102">論理レコードの競合の検出および解決</span><span class="sxs-lookup"><span data-stu-id="86b74-102">Detecting and Resolving Conflicts in Logical Records</span></span>
  <span data-ttu-id="86b74-103">ここでは、論理レコードの使用時に利用できる、競合検出および競合解決方法のさまざまな組み合わせを紹介します。</span><span class="sxs-lookup"><span data-stu-id="86b74-103">This topic covers the various combinations of conflict detection and conflict resolution approaches possible when using logical records.</span></span> <span data-ttu-id="86b74-104">マージ レプリケーションでの競合は、複数のノードが同じデータを変更したとき、またはマージ レプリケーションが変更をレプリケートするときに制約違反などの特定の種類のエラーに遭遇したときに発生します。</span><span class="sxs-lookup"><span data-stu-id="86b74-104">A conflict in merge replication occurs when more than one node changes the same data, or merge replication encounters certain types of errors, such as a constraint violation, when replicating changes.</span></span> <span data-ttu-id="86b74-105">競合の検出および解決の詳細については、「 [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86b74-105">For more information about conflict detection and resolution, see [Advanced Merge Replication Conflict Detection and Resolution](advanced-merge-replication-conflict-detection-and-resolution.md).</span></span>

 <span data-ttu-id="86b74-106">アーティクルに対して競合の追跡と競合解決のレベルを指定するには、「 [マージ アーティクルの競合追跡と解決のレベルを指定](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86b74-106">To specify the conflict tracking and resolution level for an article, see [Specify the Conflict Tracking and Resolution Level for Merge Articles](../publish/specify-merge-replication-properties.md#interactive-conflict-resolution).</span></span>

## <a name="conflict-detection"></a><span data-ttu-id="86b74-107">競合検出</span><span class="sxs-lookup"><span data-stu-id="86b74-107">Conflict Detection</span></span>
 <span data-ttu-id="86b74-108">論理レコードの競合検出方法は、 **column_tracking** と **logical_record_level_conflict_detection**の 2 つのアーティクル プロパティによって決定されます。</span><span class="sxs-lookup"><span data-stu-id="86b74-108">The way in which conflicts are detected for logical records is determined by two article properties: **column_tracking** and **logical_record_level_conflict_detection**.</span></span> [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] <span data-ttu-id="86b74-109">以降のバージョンでは、論理レコード レベルの検出もサポートしています。</span><span class="sxs-lookup"><span data-stu-id="86b74-109">and later versions also support logical record-level detection.</span></span>

 <span data-ttu-id="86b74-110">**logical_record_level_conflict_detection** アーティクル プロパティは TRUE または FALSE のいずれかに設定できます。</span><span class="sxs-lookup"><span data-stu-id="86b74-110">The **logical_record_level_conflict_detection** article property can be set to TRUE or FALSE.</span></span> <span data-ttu-id="86b74-111">この値はトップ レベルの親アーティクルに対してのみ設定してください。子アーティクルでは無視されます。</span><span class="sxs-lookup"><span data-stu-id="86b74-111">The value should only be set for the top-level parent article and will be ignored by child articles.</span></span> <span data-ttu-id="86b74-112">この値が FALSE の場合、マージ レプリケーションは以前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のように、アーティクルの **column_tracking** プロパティの値のみに基づいて、競合を検出します。</span><span class="sxs-lookup"><span data-stu-id="86b74-112">If this value is FALSE, merge replication detects conflicts as in previous versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], based solely on the value of the **column_tracking** property for the article.</span></span> <span data-ttu-id="86b74-113">この値が TRUE の場合、マージ レプリケーションはアーティクルの **column_tracking** プロパティを無視し、論理レコードのどこかで変更が行われた場合に競合を検出します。</span><span class="sxs-lookup"><span data-stu-id="86b74-113">If this value is TRUE, merge replication will ignore the **column_tracking** property of the article, and detect a conflict if changes are made anywhere in the logical record.</span></span> <span data-ttu-id="86b74-114">たとえば、次のシナリオについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="86b74-114">For example, consider this scenario:</span></span>

 <span data-ttu-id="86b74-115">![値を持つ 3 つのテーブルの論理レコード](../media/logical-records-05.gif "値を持つ 3 つのテーブルの論理レコード")</span><span class="sxs-lookup"><span data-stu-id="86b74-115">![Three table logical record with values](../media/logical-records-05.gif "Three table logical record with values")</span></span>

 <span data-ttu-id="86b74-116">**Customers**、 **Orders**、または **OrderItems** テーブルの Customer2 論理レコードに対して 2 人のユーザーが値を変更した場合に競合が検出されます。</span><span class="sxs-lookup"><span data-stu-id="86b74-116">A conflict is detected if two users change any values for the Customer2 logical record in the **Customers**, **Orders**, or **OrderItems** tables.</span></span> <span data-ttu-id="86b74-117">この例では、UPDATE ステートメントにより変更が行われていますが、INSERT または DELETE ステートメントによる変更でも競合が検出されることがあります。</span><span class="sxs-lookup"><span data-stu-id="86b74-117">This example involves changes made via an UPDATE statement, but the conflict can also be detected by changes made with INSERT or DELETE statements.</span></span>

## <a name="conflict-resolution"></a><span data-ttu-id="86b74-118">競合解決</span><span class="sxs-lookup"><span data-stu-id="86b74-118">Conflict Resolution</span></span>
 <span data-ttu-id="86b74-119">既定では、マージ レプリケーションは優先度に基づくロジックを使用して競合を解決します。</span><span class="sxs-lookup"><span data-stu-id="86b74-119">By default, merge replication uses priority-based logic to resolve conflicts.</span></span> <span data-ttu-id="86b74-120">2 つのサブスクライバー データベースで競合する変更が行われた場合、サブスクリプションの優先度が高いサブスクライバー側の変更が優先されます。優先度が同じである場合は、パブリッシャーに先に到達した変更が優先されます。</span><span class="sxs-lookup"><span data-stu-id="86b74-120">If a conflicting change is made in two Subscriber databases, the change for the Subscriber with the higher subscription priority wins, or if the priority is the same, the first change to reach the Publisher wins.</span></span> <span data-ttu-id="86b74-121">行レベルおよび列レベルの検出では、優先度の低い行は常に優先される行全体で上書きされます。</span><span class="sxs-lookup"><span data-stu-id="86b74-121">With row-level and column-level detection, the entire winning row always overwrites the losing row.</span></span>

 <span data-ttu-id="86b74-122">**logical_record_level_conflict_resolution** アーティクル プロパティは TRUE または FALSE のどちらかに設定できます。</span><span class="sxs-lookup"><span data-stu-id="86b74-122">The **logical_record_level_conflict_resolution** article property can be set to TRUE or FALSE.</span></span> <span data-ttu-id="86b74-123">この値はトップ レベルの親アーティクルに対してのみ設定してください。子アーティクルでは無視されます。</span><span class="sxs-lookup"><span data-stu-id="86b74-123">The value should only be set for the top-level parent article and will be ignored by child articles.</span></span> <span data-ttu-id="86b74-124">この値が TRUE の場合、優先される論理レコード全体が優先度の低い論理レコードを上書きします。</span><span class="sxs-lookup"><span data-stu-id="86b74-124">If the value is TRUE, the entire winning logical record overwrites the losing logical record.</span></span> <span data-ttu-id="86b74-125">FALSE の場合、優先される個々の行は、別のサブスクライバーまたはパブリッシャーからのものである可能性があります。</span><span class="sxs-lookup"><span data-stu-id="86b74-125">If it is FALSE, individual winning rows can come from different Subscribers or Publishers.</span></span> <span data-ttu-id="86b74-126">たとえば、 **Orders** テーブルの行についてはサブスクライバー A が優先され、 **OrderItems** テーブルの関連する行についてはサブスクライバー B が優先される、という場合があります。</span><span class="sxs-lookup"><span data-stu-id="86b74-126">For example, Subscriber A could win a conflict on a row from the **Orders** table, and Subscriber B could win on a related row from the **OrderItems** table.</span></span> <span data-ttu-id="86b74-127">この結果、論理レコードの **Orders** 行はサブスクライバー A のものになり、 **OrderItems** 行はサブスクライバー B のものとなります。</span><span class="sxs-lookup"><span data-stu-id="86b74-127">The result is a logical record with the **Orders** row from Subscriber A and the **OrderItems** row from Subscriber B.</span></span>

## <a name="interaction-of-conflict-resolution-and-detection-settings"></a><span data-ttu-id="86b74-128">競合解決と検出の設定の相関関係</span><span class="sxs-lookup"><span data-stu-id="86b74-128">Interaction of Conflict Resolution and Detection Settings</span></span>
 <span data-ttu-id="86b74-129">競合の結果は、競合の検出および解決の設定の相関関係によって異なります。</span><span class="sxs-lookup"><span data-stu-id="86b74-129">The outcome of conflicts depends on the interaction of conflict detection and resolution settings.</span></span> <span data-ttu-id="86b74-130">次の例では、優先度に基づく競合解決法が使用されているものとします。</span><span class="sxs-lookup"><span data-stu-id="86b74-130">For the examples below, it is assumed that the priority-based conflict resolution is being used.</span></span> <span data-ttu-id="86b74-131">論理レコードを使用する場合、以下のケースが考えられます。</span><span class="sxs-lookup"><span data-stu-id="86b74-131">When using logical records, the possibilities are:</span></span>

-   <span data-ttu-id="86b74-132">行レベルまたは列レベルの検出、行レベルの解決</span><span class="sxs-lookup"><span data-stu-id="86b74-132">Row or column level detection, row level resolution</span></span>

-   <span data-ttu-id="86b74-133">列レベルの検出、論理レコード レベルの解決</span><span class="sxs-lookup"><span data-stu-id="86b74-133">Column level detection, logical record resolution</span></span>

-   <span data-ttu-id="86b74-134">行レベルの検出、論理レコード レベルの解決</span><span class="sxs-lookup"><span data-stu-id="86b74-134">Row level detection, logical record resolution</span></span>

-   <span data-ttu-id="86b74-135">論理レコード レベルの検出、論理レコード レベルの解決</span><span class="sxs-lookup"><span data-stu-id="86b74-135">Logical record detection, logical record resolution</span></span>

### <a name="row-or-column-level-detection-row-level-resolution"></a><span data-ttu-id="86b74-136">行レベルまたは列レベルの検出、行レベルの解決</span><span class="sxs-lookup"><span data-stu-id="86b74-136">Row or Column Level Detection, Row Level Resolution</span></span>
 <span data-ttu-id="86b74-137">この例では、パブリケーションは次のように構成されています。</span><span class="sxs-lookup"><span data-stu-id="86b74-137">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="86b74-138">**column_tracking** は TRUE または FALSE</span><span class="sxs-lookup"><span data-stu-id="86b74-138">**column_tracking** is TRUE or FALSE</span></span>

-   <span data-ttu-id="86b74-139">**logical_record_level_conflict_detection** は FALSE</span><span class="sxs-lookup"><span data-stu-id="86b74-139">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="86b74-140">**logical_record_level_conflict_resolution** は FALSE</span><span class="sxs-lookup"><span data-stu-id="86b74-140">**logical_record_level_conflict_resolution** is FALSE</span></span>

 <span data-ttu-id="86b74-141">この場合、検出は行レベルまたは列レベルであり、解決は行レベルです。</span><span class="sxs-lookup"><span data-stu-id="86b74-141">In this case, detection is at the row or column level and resolution is at the row level.</span></span> <span data-ttu-id="86b74-142">これらは、論理レコードに対するすべての変更を 1 つの単位としてレプリケートさせる利点を活かしながら、論理レコード レベルでの競合の検出または解決を行わないように設定されています。</span><span class="sxs-lookup"><span data-stu-id="86b74-142">These settings are used to take advantage of having all changes to a logical record replicate as a unit, but without conflict detection or resolution at the logical record level.</span></span>

### <a name="column-level-detection-logical-record-resolution"></a><span data-ttu-id="86b74-143">列レベルの検出、論理レコード レベルの解決</span><span class="sxs-lookup"><span data-stu-id="86b74-143">Column Level Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="86b74-144">この例では、パブリケーションは次のように構成されています。</span><span class="sxs-lookup"><span data-stu-id="86b74-144">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="86b74-145">**column_tracking** は TRUE</span><span class="sxs-lookup"><span data-stu-id="86b74-145">**column_tracking** is TRUE</span></span>

-   <span data-ttu-id="86b74-146">**logical_record_level_conflict_detection** は FALSE</span><span class="sxs-lookup"><span data-stu-id="86b74-146">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="86b74-147">**logical_record_level_conflict_resolution** は TRUE</span><span class="sxs-lookup"><span data-stu-id="86b74-147">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="86b74-148">パブリッシャーとサブスクライバーは同じデータセットから開始され、論理レコードは **orders** テーブルと **customers** テーブル間で定義されています。</span><span class="sxs-lookup"><span data-stu-id="86b74-148">A Publisher and Subscriber start with the same data set, and a logical record is defined between the **orders** and **customers** tables.</span></span> <span data-ttu-id="86b74-149">パブリッシャーは **customers** テーブルの **custcol1** 列および **orders** テーブルの **ordercol1** 列を変更します。</span><span class="sxs-lookup"><span data-stu-id="86b74-149">The Publisher changes the **custcol1** column in the **customers** table and the **ordercol1** in the **orders** table.</span></span> <span data-ttu-id="86b74-150">サブスクライバーは **customers** テーブルの同じ行の **custcol1** および **orders** テーブルの同じ行の **ordercol2** 列を変更します。</span><span class="sxs-lookup"><span data-stu-id="86b74-150">The Subscriber changes **custcol1** in the same row of the **customers** table and the **ordercol2** column in the same row of the **orders** table.</span></span> <span data-ttu-id="86b74-151">**customers** テーブルの同じ列に対する変更で競合が発生しますが、 **orders** テーブルへの変更では競合は発生しません。</span><span class="sxs-lookup"><span data-stu-id="86b74-151">The changes to the same column in the **customer** table result in a conflict, but the changes to the **orders** table are not in conflict.</span></span>

 <span data-ttu-id="86b74-152">競合は論理レコード レベルで解決されるため、レプリケーション処理中にパブリッシャー側で行われた変更が優先され、サブスクライバー テーブルの変更を置換します。</span><span class="sxs-lookup"><span data-stu-id="86b74-152">Because the conflicts are resolved at the logical record level, the winning changes made at the Publisher replace the changes made in the Subscriber tables during replication processing.</span></span>

 <span data-ttu-id="86b74-153">![関連する行に対する変更を示す一連のテーブル](../media/logical-records-06.gif "関連する行に対する変更を示す一連のテーブル")</span><span class="sxs-lookup"><span data-stu-id="86b74-153">![Series of tables showing changes to related rows](../media/logical-records-06.gif "Series of tables showing changes to related rows")</span></span>

### <a name="row-level-detection-logical-record-resolution"></a><span data-ttu-id="86b74-154">行レベルの検出、論理レコード レベルの解決</span><span class="sxs-lookup"><span data-stu-id="86b74-154">Row Level Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="86b74-155">この例では、パブリケーションは次のように構成されています。</span><span class="sxs-lookup"><span data-stu-id="86b74-155">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="86b74-156">**column_tracking** は FALSE</span><span class="sxs-lookup"><span data-stu-id="86b74-156">**column_tracking** is FALSE</span></span>

-   <span data-ttu-id="86b74-157">**logical_record_level_conflict_detection** は FALSE</span><span class="sxs-lookup"><span data-stu-id="86b74-157">**logical_record_level_conflict_detection** is FALSE</span></span>

-   <span data-ttu-id="86b74-158">**logical_record_level_conflict_resolution** は TRUE</span><span class="sxs-lookup"><span data-stu-id="86b74-158">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="86b74-159">パブリッシャーとサブスクライバーは同じデータセットから開始します。</span><span class="sxs-lookup"><span data-stu-id="86b74-159">A Publisher and Subscriber start with the same data set.</span></span> <span data-ttu-id="86b74-160">パブリッシャーは **customers** テーブルの **custcol1** 列を変更します。</span><span class="sxs-lookup"><span data-stu-id="86b74-160">The Publisher changes the **custcol1** column in the **customers** table.</span></span> <span data-ttu-id="86b74-161">サブスクライバーは **customers** テーブルの **custcol2** 列および **orders** テーブルの **ordercol2** 列を変更します。</span><span class="sxs-lookup"><span data-stu-id="86b74-161">The Subscriber changes **custcol2** in the **customers** table and the **ordercol2** column in the **orders** table.</span></span> <span data-ttu-id="86b74-162">**customers** テーブルの同じ行に対する変更で競合が発生しますが、サブスクライバーの **orders** テーブルへの変更では競合は発生しません。</span><span class="sxs-lookup"><span data-stu-id="86b74-162">The changes to the same row in the **customers** table result in a conflict, but the Subscriber changes to the **orders** table are not in conflict.</span></span>

 <span data-ttu-id="86b74-163">競合は論理レコード レベルで解決されるため、同期中にパブリッシャー側で行われた変更が優先され、サブスクライバー テーブルの変更を置換します。</span><span class="sxs-lookup"><span data-stu-id="86b74-163">Because the conflicts are resolved at the logical record level, during synchronization the winning changes made at the Publisher replace the changes made in the Subscriber tables.</span></span>

 <span data-ttu-id="86b74-164">![関連する行に対する変更を示す一連のテーブル](../media/logical-records-07.gif "関連する行に対する変更を示す一連のテーブル")</span><span class="sxs-lookup"><span data-stu-id="86b74-164">![Series of tables showing changes to related rows](../media/logical-records-07.gif "Series of tables showing changes to related rows")</span></span>

### <a name="logical-record-detection-logical-record-resolution"></a><span data-ttu-id="86b74-165">論理レコード レベルの検出、論理レコード レベルの解決</span><span class="sxs-lookup"><span data-stu-id="86b74-165">Logical Record Detection, Logical Record Resolution</span></span>
 <span data-ttu-id="86b74-166">この例では、パブリケーションは次のように構成されています。</span><span class="sxs-lookup"><span data-stu-id="86b74-166">In this example, the publication is configured with:</span></span>

-   <span data-ttu-id="86b74-167">**logical_record_level_conflict_detection** は TRUE</span><span class="sxs-lookup"><span data-stu-id="86b74-167">**logical_record_level_conflict_detection** is TRUE</span></span>

-   <span data-ttu-id="86b74-168">**logical_record_level_conflict_resolution** は TRUE</span><span class="sxs-lookup"><span data-stu-id="86b74-168">**logical_record_level_conflict_resolution** is TRUE</span></span>

 <span data-ttu-id="86b74-169">パブリッシャーとサブスクライバーは同じデータセットから開始します。</span><span class="sxs-lookup"><span data-stu-id="86b74-169">A Publisher and Subscriber start with the same data set.</span></span> <span data-ttu-id="86b74-170">パブリッシャーは **customers** テーブルの **custcol1** 列を変更します。</span><span class="sxs-lookup"><span data-stu-id="86b74-170">The Publisher changes the **custcol1** column in the **customers** table.</span></span> <span data-ttu-id="86b74-171">サブスクライバーは **orders** テーブルの **ordercol1** 列を変更します。</span><span class="sxs-lookup"><span data-stu-id="86b74-171">The Subscriber changes the **ordercol1** column in the **orders** table.</span></span> <span data-ttu-id="86b74-172">同じ行または列に対する変更はありませんが、 **custid**=1 の同じ論理レコードが変更されているため、この変更は論理レコード レベルでは競合として検出されます。</span><span class="sxs-lookup"><span data-stu-id="86b74-172">There are no changes to the same row or columns, but because the changes are made in the same logical record for **custid**=1, the changes are detected as a conflict at the logical record level.</span></span>

 <span data-ttu-id="86b74-173">競合は論理レコード レベルでも解決されるため、同期中にパブリッシャー側で行われた変更が優先され、サブスクライバー テーブルの変更を置換します。</span><span class="sxs-lookup"><span data-stu-id="86b74-173">Because the conflicts are also resolved at the logical record level, during synchronization the winning change made at the Publisher replaces the change made in the Subscriber tables.</span></span>

 <span data-ttu-id="86b74-174">![関連する行に対する変更を示す一連のテーブル](../media/logical-records-08.gif "関連する行に対する変更を示す一連のテーブル")</span><span class="sxs-lookup"><span data-stu-id="86b74-174">![Series of tables showing changes to related rows](../media/logical-records-08.gif "Series of tables showing changes to related rows")</span></span>

## <a name="see-also"></a><span data-ttu-id="86b74-175">参照</span><span class="sxs-lookup"><span data-stu-id="86b74-175">See Also</span></span>
 [<span data-ttu-id="86b74-176">論理レコードによる関連行への変更のグループ化</span><span class="sxs-lookup"><span data-stu-id="86b74-176">Group Changes to Related Rows with Logical Records</span></span>](group-changes-to-related-rows-with-logical-records.md)


