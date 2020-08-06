---
title: '[XML インデックス] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.xmlindexes
ms.assetid: eef38310-4498-4ccc-bb77-5bbd1c7cc477
author: stevestein
ms.author: sstein
ms.openlocfilehash: f1fb23a801a9129611c032fa1d659caf624088aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642450"
---
# <a name="xml-indexes-dialog-box-visual-database-tools"></a><span data-ttu-id="c4487-102">[XML インデックス] ダイアログ ボックス (Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="c4487-102">XML Indexes Dialog Box (Visual Database Tools)</span></span>
  <span data-ttu-id="c4487-103">**[XML インデックス]** ダイアログ ボックスを使用すると、 **[インデックス/キー]** ダイアログ ボックスではできない、データ型が XML の列に対するインデックスの作成を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="c4487-103">Use the **XML Indexes** dialog box to create indexes for columns of the data type XML, which cannot be indexed using the **Index/Keys** dialog box.</span></span> <span data-ttu-id="c4487-104">各 XML 列に複数の XML インデックスを作成できますが、最初に作成したインデックス (プライマリ インデックス) が他のインデックス (セカンダリ インデックス) の基になります。</span><span class="sxs-lookup"><span data-stu-id="c4487-104">Each XML column can have more than one XML Index, but the first one created (primary) will be the basis of the others (secondary).</span></span> <span data-ttu-id="c4487-105">プライマリ XML インデックスを削除すると、セカンダリ インデックスも削除されます。</span><span class="sxs-lookup"><span data-stu-id="c4487-105">If you delete the primary XML index, the secondary indexes will also be deleted.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c4487-106">オプション</span><span class="sxs-lookup"><span data-stu-id="c4487-106">Options</span></span>  
 <span data-ttu-id="c4487-107">**[選択された XML インデックス]**</span><span class="sxs-lookup"><span data-stu-id="c4487-107">**Selected XML Index**</span></span>  
 <span data-ttu-id="c4487-108">既存の XML インデックスを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="c4487-108">Lists existing XML indexes.</span></span> <span data-ttu-id="c4487-109">特定のインデックスを選択すると、右側のグリッドにそのプロパティが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c4487-109">Select to show its properties in the grid to the right.</span></span> <span data-ttu-id="c4487-110">一覧が空の場合、テーブルには何も定義されていません。</span><span class="sxs-lookup"><span data-stu-id="c4487-110">If the list is empty, none have been defined for the table.</span></span>  
  
 <span data-ttu-id="c4487-111">**追加**</span><span class="sxs-lookup"><span data-stu-id="c4487-111">**Add**</span></span>  
 <span data-ttu-id="c4487-112">XML インデックスを新規作成します。</span><span class="sxs-lookup"><span data-stu-id="c4487-112">Create a new XML index.</span></span>  
  
 <span data-ttu-id="c4487-113">**削除**</span><span class="sxs-lookup"><span data-stu-id="c4487-113">**Delete**</span></span>  
 <span data-ttu-id="c4487-114">**[選択された XML インデックス]** ボックスで選択されている XML インデックスを削除します。</span><span class="sxs-lookup"><span data-stu-id="c4487-114">Delete XML index selected in the **Selected XML Index** list.</span></span> <span data-ttu-id="c4487-115">プライマリ XML インデックスを削除すると、セカンダリ インデックスもすべて削除されることを示すメッセージが表示されます。このとき、削除を続行するか取り消すかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="c4487-115">If you delete the primary XML index, you will be notified that this will delete all secondary ones as well, and you can either continue or cancel the action.</span></span>  
  
 <span data-ttu-id="c4487-116">**[全般] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c4487-116">**General Category**</span></span>  
 <span data-ttu-id="c4487-117">展開して **[列]** 、 **[Is Primary]** 、および **[型]** のプロパティ フィールドを表示します。</span><span class="sxs-lookup"><span data-stu-id="c4487-117">When expanded, shows the property fields for **Columns**, **Is Primary**, and **Type**.</span></span>  
  
 <span data-ttu-id="c4487-118">**[列]**</span><span class="sxs-lookup"><span data-stu-id="c4487-118">**Columns**</span></span>  
 <span data-ttu-id="c4487-119">このインデックスの並べ替えが昇順で行われることを示します。</span><span class="sxs-lookup"><span data-stu-id="c4487-119">Shows that this index is sorted in ascending order.</span></span>  
  
 <span data-ttu-id="c4487-120">**[Is Primary]**</span><span class="sxs-lookup"><span data-stu-id="c4487-120">**Is Primary**</span></span>  
 <span data-ttu-id="c4487-121">このインデックスがプライマリ インデックスかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="c4487-121">Indicates whether this is the primary index.</span></span> <span data-ttu-id="c4487-122">列に対して最初に作成された XML インデックスが、他のインデックスの基準になります。</span><span class="sxs-lookup"><span data-stu-id="c4487-122">The first XML index created on the column will be the basis of the others.</span></span>  
  
 <span data-ttu-id="c4487-123">**[主な参照名]**</span><span class="sxs-lookup"><span data-stu-id="c4487-123">**Primary reference name**</span></span>  
 <span data-ttu-id="c4487-124">セカンダリ インデックスが選択されている場合に、プライマリ インデックスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="c4487-124">Shows the name of the primary index if this is a secondary index.</span></span> <span data-ttu-id="c4487-125">セカンダリ インデックスが選択されている場合のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="c4487-125">Only available if this is a secondary index.</span></span>  
  
 <span data-ttu-id="c4487-126">**[2 番目の型]**</span><span class="sxs-lookup"><span data-stu-id="c4487-126">**Secondary type**</span></span>  
 <span data-ttu-id="c4487-127">セカンダリ インデックスの種類を表示します。</span><span class="sxs-lookup"><span data-stu-id="c4487-127">Shows the type of secondary index.</span></span> <span data-ttu-id="c4487-128">セカンダリ インデックスが選択されている場合のみ有効です。</span><span class="sxs-lookup"><span data-stu-id="c4487-128">Only available if this is a secondary index.</span></span>  
  
 <span data-ttu-id="c4487-129">**Type**</span><span class="sxs-lookup"><span data-stu-id="c4487-129">**Type**</span></span>  
 <span data-ttu-id="c4487-130">このインデックスが XML インデックスであることを示します。</span><span class="sxs-lookup"><span data-stu-id="c4487-130">Shows that this is an XML index.</span></span>  
  
 <span data-ttu-id="c4487-131">**[IDENTITY] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c4487-131">**Identity Category**</span></span>  
 <span data-ttu-id="c4487-132">展開して、 **[オブジェクト名]** プロパティ フィールドと **[説明]** プロパティ フィールドを表示します。</span><span class="sxs-lookup"><span data-stu-id="c4487-132">When expanded, shows the **Name** and **Description** property fields.</span></span>  
  
 <span data-ttu-id="c4487-133">**Name**</span><span class="sxs-lookup"><span data-stu-id="c4487-133">**Name**</span></span>  
 <span data-ttu-id="c4487-134">XML インデックスの名前を表示します。</span><span class="sxs-lookup"><span data-stu-id="c4487-134">Shows the name of the XML index.</span></span> <span data-ttu-id="c4487-135">新しいキーまたはインデックスを作成した場合、このプロパティには、テーブル デザイナーのアクティブ ウィンドウのテーブルに基づいて、既定の名前が設定されます。</span><span class="sxs-lookup"><span data-stu-id="c4487-135">When a new one is created, it is given a default name based on the table in the active window in Table Designer.</span></span> <span data-ttu-id="c4487-136">名前はいつでも変更できます。</span><span class="sxs-lookup"><span data-stu-id="c4487-136">You can change the name at any time.</span></span>  
  
 <span data-ttu-id="c4487-137">**説明**</span><span class="sxs-lookup"><span data-stu-id="c4487-137">**Description**</span></span>  
 <span data-ttu-id="c4487-138">インデックスの説明を記述します。</span><span class="sxs-lookup"><span data-stu-id="c4487-138">Describe the index.</span></span> <span data-ttu-id="c4487-139">より詳細な説明を記述する場合は、 **[説明]** をクリックしてから、プロパティ フィールドの右に表示される省略記号ボタン ( **[...]** ) をクリックします。</span><span class="sxs-lookup"><span data-stu-id="c4487-139">To write a more detailed description, click **Description** and then click the ellipsis button (**...**) that appears to the right of the property field.</span></span> <span data-ttu-id="c4487-140">これにより、テキストを書くことができる領域が大きくなります。</span><span class="sxs-lookup"><span data-stu-id="c4487-140">This provides a larger area in which to write text.</span></span>  
  
 <span data-ttu-id="c4487-141">**[テーブル デザイナー] カテゴリ**</span><span class="sxs-lookup"><span data-stu-id="c4487-141">**Table Designer Category**</span></span>  
 <span data-ttu-id="c4487-142">展開してこの XML インデックスのプロパティに関する情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c4487-142">When expanded, shows information about the properties of this XML index.</span></span>  
  
 <span data-ttu-id="c4487-143">**[FILL の指定]**</span><span class="sxs-lookup"><span data-stu-id="c4487-143">**Fill Specification**</span></span>  
 <span data-ttu-id="c4487-144">展開して **[FILL FACTOR]** および **[インデックスの埋め込み]** の情報を表示します。</span><span class="sxs-lookup"><span data-stu-id="c4487-144">When expanded, shows information for **Fill Factor** and **Pad Index**.</span></span>  
  
 <span data-ttu-id="c4487-145">**[FILL FACTOR]**</span><span class="sxs-lookup"><span data-stu-id="c4487-145">**Fill Factor**</span></span>  
 <span data-ttu-id="c4487-146">システムが使用できるインデックス ページの割合を指定します。</span><span class="sxs-lookup"><span data-stu-id="c4487-146">Specify what percentage of the index page the system can fill.</span></span> <span data-ttu-id="c4487-147">ページがいっぱいになった場合、新しいデータが追加されると、システムはそのページを分割する必要があります。これによりパフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="c4487-147">Once a page is full, the system must split the page if new data is added, which impairs performance.</span></span>  
  
-   <span data-ttu-id="c4487-148">値 100 は、ページがいっぱいになることを示しています。必要な記憶領域は最小限ですが、最も非効率的です。</span><span class="sxs-lookup"><span data-stu-id="c4487-148">A value of 100 means the pages will be full; this requires the least amount of storage space but is the least efficient.</span></span> <span data-ttu-id="c4487-149">この設定は、データに変更がない (たとえば読み取り専用テーブルのデータ) 場合にだけ使用します。</span><span class="sxs-lookup"><span data-stu-id="c4487-149">This setting should be used only when there will be no changes to the data, for example, on a read-only table.</span></span>  
  
-   <span data-ttu-id="c4487-150">値が小さいほどデータ ページ上の空き領域が大きくなり、インデックスが増大したときにデータ ページを分割する必要性が小さくなります。</span><span class="sxs-lookup"><span data-stu-id="c4487-150">A lower value leaves more empty space on the data pages, which reduces the need to split data pages as indexes grow.</span></span> <span data-ttu-id="c4487-151">ただし、より大きな記憶領域が必要になります。</span><span class="sxs-lookup"><span data-stu-id="c4487-151">However, it requires more storage space.</span></span> <span data-ttu-id="c4487-152">この設定は、テーブル内のデータに変更が生じることが予想される場合に適しています。</span><span class="sxs-lookup"><span data-stu-id="c4487-152">This setting is more appropriate when there will be changes to the data in the table.</span></span>  
  
 <span data-ttu-id="c4487-153">**[インデックスの埋め込み]**</span><span class="sxs-lookup"><span data-stu-id="c4487-153">**Pad Index**</span></span>  
 <span data-ttu-id="c4487-154">**[FILL FACTOR]** で指定されている空き領域 (埋め込み) の割合と同じ比率で、このインデックスにページを提供します。</span><span class="sxs-lookup"><span data-stu-id="c4487-154">Provide pages in this index the same percentage of empty space (padding) that is specified in **Fill Factor**.</span></span>  
  
 <span data-ttu-id="c4487-155">**[無効化]**</span><span class="sxs-lookup"><span data-stu-id="c4487-155">**Is Disabled**</span></span>  
 <span data-ttu-id="c4487-156">インデックスを無効にするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4487-156">Specify whether this index is disabled.</span></span> <span data-ttu-id="c4487-157">無効にされたインデックスは、検索をサポートせず、テーブルに新たなアイテムが追加されても更新されません。</span><span class="sxs-lookup"><span data-stu-id="c4487-157">Disabled indexes do not support searches, nor do they get updated when new items are added to the table.</span></span> <span data-ttu-id="c4487-158">インデックスを無効にすると、一括挿入や一括更新のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="c4487-158">You can improve performance for bulk inserts and updates by disabling an index.</span></span>  
  
 <span data-ttu-id="c4487-159">**[ページのロックを許可]**</span><span class="sxs-lookup"><span data-stu-id="c4487-159">**Page Locks Allowed**</span></span>  
 <span data-ttu-id="c4487-160">インデックスでページレベルのロックを許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4487-160">Specify whether page-level locking is allowed on this index.</span></span> <span data-ttu-id="c4487-161">ページレベル ロックの許可、非許可はデータベースのパフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="c4487-161">Allowing or disallowing page-level locking affects database performance.</span></span>  
  
 <span data-ttu-id="c4487-162">**[統計値を再計算する]**</span><span class="sxs-lookup"><span data-stu-id="c4487-162">**Re-compute Statistics**</span></span>  
 <span data-ttu-id="c4487-163">インデックスが作成されたときに新しい統計を計算します。</span><span class="sxs-lookup"><span data-stu-id="c4487-163">Compute new statistics when the index is created.</span></span> <span data-ttu-id="c4487-164">統計情報の再計算により、インデックスの構築には前よりも時間がかかりますが、通常はクエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="c4487-164">Re-computing statistics slows the building of indexes but usually improves query performance.</span></span>  
  
 <span data-ttu-id="c4487-165">**[行のロックを許可]**</span><span class="sxs-lookup"><span data-stu-id="c4487-165">**Row Locks Allowed**</span></span>  
 <span data-ttu-id="c4487-166">該当するインデックスで行レベルのロックを許可するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="c4487-166">Specify whether row-level locking is allowed on this index.</span></span> <span data-ttu-id="c4487-167">行レベル ロックの許可、非許可はデータベースのパフォーマンスに影響を与えます。</span><span class="sxs-lookup"><span data-stu-id="c4487-167">Allowing or disallowing row-level locking affects database performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4487-168">参照</span><span class="sxs-lookup"><span data-stu-id="c4487-168">See Also</span></span>  
 [<span data-ttu-id="c4487-169">XML インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="c4487-169">Create XML Indexes</span></span>](../../relational-databases/xml/create-xml-indexes.md)  
  
  
