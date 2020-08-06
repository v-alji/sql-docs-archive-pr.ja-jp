---
title: MSSQLSERVER_511 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2016
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 511 (Database Engine error)
ms.assetid: 0c85686a-53c1-4180-ba8c-2000e68a0d63
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5b69d2c043997e2947563de119bc4ee89fdf4e32
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714381"
---
# <a name="mssqlserver_511"></a><span data-ttu-id="c9041-102">MSSQLSERVER_511</span><span class="sxs-lookup"><span data-stu-id="c9041-102">MSSQLSERVER_511</span></span>
    
## <a name="details"></a><span data-ttu-id="c9041-103">詳細</span><span class="sxs-lookup"><span data-stu-id="c9041-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9041-104">製品名</span><span class="sxs-lookup"><span data-stu-id="c9041-104">Product Name</span></span>|<span data-ttu-id="c9041-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c9041-105">SQL Server</span></span>|  
|<span data-ttu-id="c9041-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="c9041-106">Event ID</span></span>|<span data-ttu-id="c9041-107">511</span><span class="sxs-lookup"><span data-stu-id="c9041-107">511</span></span>|  
|<span data-ttu-id="c9041-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="c9041-108">Event Source</span></span>|<span data-ttu-id="c9041-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c9041-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c9041-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c9041-110">Component</span></span>|<span data-ttu-id="c9041-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c9041-111">SQLEngine</span></span>|  
|<span data-ttu-id="c9041-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="c9041-112">Symbolic Name</span></span>|<span data-ttu-id="c9041-113">ROW_TOOBIG</span><span class="sxs-lookup"><span data-stu-id="c9041-113">ROW_TOOBIG</span></span>|  
|<span data-ttu-id="c9041-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="c9041-114">Message Text</span></span>|<span data-ttu-id="c9041-115">1 行のサイズ %d が許容最大値 %d を超えているので行を作成できません。</span><span class="sxs-lookup"><span data-stu-id="c9041-115">Cannot create a row of size %d which is greater than the allowable maximum of %d.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c9041-116">説明</span><span class="sxs-lookup"><span data-stu-id="c9041-116">Explanation</span></span>  
 <span data-ttu-id="c9041-117">実行しようとした操作が最大行サイズを超えました。</span><span class="sxs-lookup"><span data-stu-id="c9041-117">The operation you have tried has exceeded the maximum size of a row.</span></span> <span data-ttu-id="c9041-118">通常、最大行サイズは 8,060 バイトです。</span><span class="sxs-lookup"><span data-stu-id="c9041-118">Usually, the maximum size of a row is 8,060 bytes.</span></span> <span data-ttu-id="c9041-119">ストレージ形式によっては、データに使用できる行サイズを縮小するオーバーヘッドが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="c9041-119">Some storage formats contain overhead that can reduce the row size that is available for data.</span></span> <span data-ttu-id="c9041-120">たとえば、スパース列を使用する場合、最大行サイズは 8,018 バイトです。</span><span class="sxs-lookup"><span data-stu-id="c9041-120">For example, when you use sparse columns, the maximum size of a row is 8,018 bytes.</span></span> <span data-ttu-id="c9041-121">行を追加または削除する操作や列のデータ型を変更する操作では、データ ページ上の行を書き直すことが必要になる場合があります。その後、元の行は削除されます。</span><span class="sxs-lookup"><span data-stu-id="c9041-121">Some operations that add or remove rows and some operations that change the data type of a column require the row to be rewritten on the data page, and then the original row is removed.</span></span> <span data-ttu-id="c9041-122">これらの操作では、行サイズの制限を最大値の半分にすると効果的です。</span><span class="sxs-lookup"><span data-stu-id="c9041-122">In these operations, the effective limit to the size of the row is half the maximum limit.</span></span> <span data-ttu-id="c9041-123">これは、短時間ですが、元の行と変更された行の両方をデータ ページ上に含める必要があるためです。</span><span class="sxs-lookup"><span data-stu-id="c9041-123">This is because the original row and the modified row must both be contained on the data page for a short period.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="c9041-124">Null 以外の**varchar (max)** または**nvarchar (max)** の各列には、24バイトの追加の固定割り当てが必要です。これは、並べ替え操作中に8060バイトの行制限に対してカウントされます。</span><span class="sxs-lookup"><span data-stu-id="c9041-124">Each non-null  **varchar(max)** or **nvarchar(max)** column requires 24 bytes of additional fixed allocation which counts against the 8,060 byte row limit during a sort operation.</span></span> <span data-ttu-id="c9041-125">これにより、テーブル内に作成できる null 以外の**varchar (max)** または**nvarchar (max)** 列の数に対する暗黙の制限が作成されます。</span><span class="sxs-lookup"><span data-stu-id="c9041-125">This can create an implicit limit to the number of non-null **varchar(max)** or **nvarchar(max)** columns that can be created in a table.</span></span> <span data-ttu-id="c9041-126">テーブルの作成時やデータ挿入時に、最大行サイズが許容最大値の 8060 バイトを超えるという通常の警告以外の、特別なエラーは提供されません。</span><span class="sxs-lookup"><span data-stu-id="c9041-126">No special error is provided when the table is created (beyond the usual warning that the maximum row size exceeds the allowed maximum of 8060 bytes) or at the time of data insertion.</span></span> <span data-ttu-id="c9041-127">この大きな行サイズが原因で、クラスター化インデックス キーの更新や列セット全体の並べ替えなどの通常操作の一部でエラー (エラー 512 など) が発生する可能性があります。これは操作を実行するまでユーザーは予測することができません。</span><span class="sxs-lookup"><span data-stu-id="c9041-127">This large row size can cause errors (such as error 512) during some normal operations, such as a clustered index key update, or sorts of the full column set, which users cannot anticipate until performing an operation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c9041-128">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="c9041-128">User Action</span></span>  
 <span data-ttu-id="c9041-129">できる限り、行のサイズを縮小します。</span><span class="sxs-lookup"><span data-stu-id="c9041-129">If it is possible, reduce the size of the row.</span></span>  
  
 <span data-ttu-id="c9041-130">問題の原因が行の直接の更新であると考えられる場合は、複数の手順でテーブルを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c9041-130">If you think the problem is caused by an in-place update of the row, you must change the table in multiple steps.</span></span> <span data-ttu-id="c9041-131">新しいテーブルを作成し、新しいテーブルにデータを転送します。</span><span class="sxs-lookup"><span data-stu-id="c9041-131">Create a new table, and transfer the data into the new table.</span></span> <span data-ttu-id="c9041-132">その後、元のテーブルを削除して新しいテーブルの名前を変更するか、元のテーブルを切り捨て、元のテーブル内の行を変更し、そのテーブルにデータを戻します。</span><span class="sxs-lookup"><span data-stu-id="c9041-132">Then, either delete the original table and rename the new table, or truncate the original table, modify the rows in the original table, and then move the data back into it.</span></span>  
  
  
