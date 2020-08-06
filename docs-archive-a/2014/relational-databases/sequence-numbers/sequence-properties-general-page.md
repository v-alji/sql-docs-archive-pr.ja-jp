---
title: '[順序のプロパティ] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.sequence.general.f1
ms.assetid: 0187f413-cdf0-48a2-b2e6-9b3578cd5811
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6fc969dc09663da8150461529ad1e1f1fb094539
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741682"
---
# <a name="sequence-properties-general-page"></a><span data-ttu-id="067b6-102">[順序のプロパティ]\([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="067b6-102">Sequence Properties (General Page)</span></span>
  <span data-ttu-id="067b6-103">シーケンス オブジェクトを作成し、そのプロパティを指定します。</span><span class="sxs-lookup"><span data-stu-id="067b6-103">Creates a sequence object and specifies its properties.</span></span> <span data-ttu-id="067b6-104">シーケンスは、シーケンスが作成された仕様に従って数値のシーケンスを生成するユーザー定義のスキーマ バインド オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="067b6-104">A sequence is a user-defined schema bound object that generates a sequence of numeric values according to the specification with which the sequence was created.</span></span> <span data-ttu-id="067b6-105">数値のシーケンスは、定義された間隔で昇順または降順に生成され、要求に応じて再起動 (繰り返し) するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="067b6-105">The sequence of numeric values is generated in an ascending or descending order at a defined interval and can be configured to restart (cycle) when exhausted.</span></span> <span data-ttu-id="067b6-106">ID 列とは異なり、シーケンスは、特定のテーブルに関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="067b6-106">Sequences, unlike identity columns, are not associated with specific tables.</span></span> <span data-ttu-id="067b6-107">アプリケーションは、シーケンス オブジェクトを参照して、次の値を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="067b6-107">Applications refer to a sequence object to retrieve its next value.</span></span> <span data-ttu-id="067b6-108">シーケンスとテーブルの関係は、アプリケーションによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="067b6-108">The relationship between sequences and tables is controlled by the application.</span></span> <span data-ttu-id="067b6-109">ユーザー アプリケーションは、シーケンス オブジェクトを参照し、複数の行とテーブル間で値を調整できます。</span><span class="sxs-lookup"><span data-stu-id="067b6-109">User applications can reference a sequence object and coordinate the values across multiple rows and tables.</span></span>  
  
 <span data-ttu-id="067b6-110">挿入時に生成される ID 列値とは異なり、アプリケーションで [NEXT VALUE の関数](/sql/t-sql/functions/next-value-for-transact-sql)を呼び出すことで、行を挿入せずに次のシーケンス番号を取得できます。</span><span class="sxs-lookup"><span data-stu-id="067b6-110">Unlike identity columns values which are generated at the time of insert, an application can obtain the next sequence number without inserting the row by calling the [NEXT VALUE FOR function](/sql/t-sql/functions/next-value-for-transact-sql).</span></span> <span data-ttu-id="067b6-111">一度に複数のシーケンス番号を取得するには、 [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) を使用します。</span><span class="sxs-lookup"><span data-stu-id="067b6-111">Use [sp_sequence_get_range](/sql/relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql) to get multiple sequence numbers at once.</span></span>  
  
 <span data-ttu-id="067b6-112">**CREATE SEQUENCE** および **NEXT VALUE FOR** 関数を両方使用する場合の詳細およびシナリオについては、「 [シーケンス番号](sequence-numbers.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="067b6-112">For information and scenarios that use both **CREATE SEQUENCE** and the **NEXT VALUE FOR** function, see [Sequence Numbers](sequence-numbers.md).</span></span>  
  
 <span data-ttu-id="067b6-113">このページには 2 とおりの方法でアクセスできます。オブジェクト エクスプローラーで **[シーケンス]** を右クリックして **[新しいシーケンス]** をクリックするか、既存のシーケンスを右クリックして **[プロパティ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="067b6-113">This page is accessed in two ways: either by right-clicking **Sequences** in Object Explorer and clicking **New Sequence**, or by right-clicking an existing sequence and clicking **Properties**.</span></span> <span data-ttu-id="067b6-114">既存のシーケンスを右クリックして **[プロパティ]** をクリックした場合は、オプションは編集不可能です。</span><span class="sxs-lookup"><span data-stu-id="067b6-114">When you right-click an existing sequence and click **Properties**, the options are not editable.</span></span> <span data-ttu-id="067b6-115">シーケンス オプションを変更するには、[ALTER SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-sequence-transact-sql) ステートメントを使用するか、シーケンス オブジェクトを削除してから再作成してください。</span><span class="sxs-lookup"><span data-stu-id="067b6-115">To change the sequence options use the [ALTER SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-sequence-transact-sql) statement or drop and recreate the sequence object.</span></span>  
  
## <a name="options"></a><span data-ttu-id="067b6-116">オプション</span><span class="sxs-lookup"><span data-stu-id="067b6-116">Options</span></span>  
 <span data-ttu-id="067b6-117">**[シーケンス名]**</span><span class="sxs-lookup"><span data-stu-id="067b6-117">**Sequence name**</span></span>  
 <span data-ttu-id="067b6-118">ここにシーケンス名を入力します。</span><span class="sxs-lookup"><span data-stu-id="067b6-118">Enter the sequence name here.</span></span>  
  
 <span data-ttu-id="067b6-119">**[シーケンス スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="067b6-119">**Sequence schema**</span></span>  
 <span data-ttu-id="067b6-120">このシーケンスを所有するスキーマを指定します。</span><span class="sxs-lookup"><span data-stu-id="067b6-120">Specify the schema that will own this sequence.</span></span>  
  
 <span data-ttu-id="067b6-121">**データの種類**</span><span class="sxs-lookup"><span data-stu-id="067b6-121">**Data type**</span></span>  
 <span data-ttu-id="067b6-122">シーケンスを任意の整数型として定義できます。</span><span class="sxs-lookup"><span data-stu-id="067b6-122">A sequence can be defined as any integer type.</span></span> <span data-ttu-id="067b6-123">これには次のものが含まれます</span><span class="sxs-lookup"><span data-stu-id="067b6-123">This includes:</span></span>  
  
|<span data-ttu-id="067b6-124">データ型</span><span class="sxs-lookup"><span data-stu-id="067b6-124">Data type</span></span>|<span data-ttu-id="067b6-125">Range</span><span class="sxs-lookup"><span data-stu-id="067b6-125">Range</span></span>|  
|---------------|-----------|  
|`tinyint`|<span data-ttu-id="067b6-126">0 ～ 255</span><span class="sxs-lookup"><span data-stu-id="067b6-126">0 to 255</span></span>|  
|`smallint`|<span data-ttu-id="067b6-127">-32,768 ～ 32,767</span><span class="sxs-lookup"><span data-stu-id="067b6-127">-32,768 to 32,767</span></span>|  
|`int`|<span data-ttu-id="067b6-128">-2,147,483,648 ～ 2,147,483,647</span><span class="sxs-lookup"><span data-stu-id="067b6-128">-2,147,483,648 to 2,147,483,647</span></span>|  
|`bigint`|<span data-ttu-id="067b6-129">-9,223,372,036,854,775,808 から 9,223,372,036,854,775,807</span><span class="sxs-lookup"><span data-stu-id="067b6-129">-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807</span></span>|  
  
-   <span data-ttu-id="067b6-130">`decimal` または `numeric` の場合、小数点以下を含みません。</span><span class="sxs-lookup"><span data-stu-id="067b6-130">`decimal` or `numeric` with a scale of 0.</span></span>  
  
-   <span data-ttu-id="067b6-131">これらの種類のいずれかに基づいている、すべてのユーザー定義データ型 (別名型) です。</span><span class="sxs-lookup"><span data-stu-id="067b6-131">Any user-defined data type (alias type) that is based on one of these types.</span></span>  
  
 <span data-ttu-id="067b6-132">**[精度]**</span><span class="sxs-lookup"><span data-stu-id="067b6-132">**Precision**</span></span>  
 <span data-ttu-id="067b6-133">`decimal` データ型または `numeric` データ型については、有効桁数を指定します </span><span class="sxs-lookup"><span data-stu-id="067b6-133">For `decimal` or `numeric` data types, specify the precision.</span></span> <span data-ttu-id="067b6-134">(小数点以下桁数は常に 0 です)。</span><span class="sxs-lookup"><span data-stu-id="067b6-134">(The scale is always 0.)</span></span>  
  
 <span data-ttu-id="067b6-135">**[開始値]**</span><span class="sxs-lookup"><span data-stu-id="067b6-135">**Start with value**</span></span>  
 <span data-ttu-id="067b6-136">シーケンス オブジェクトによって返される最初の値です。</span><span class="sxs-lookup"><span data-stu-id="067b6-136">The first value that will be returned by the sequence object.</span></span> <span data-ttu-id="067b6-137">**START** 値は、シーケンス オブジェクトの最小値以上および最大値以下にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="067b6-137">The **START** value must be a value that is less than or equal to the maximum and greater than or equal to the minimum value of the sequence object.</span></span> <span data-ttu-id="067b6-138">新しいシーケンス オブジェクトの既定の開始値は、昇順のシーケンス オブジェクトの最小値および降順のシーケンス オブジェクトの最大値です。</span><span class="sxs-lookup"><span data-stu-id="067b6-138">The default start value for a new sequence object is the minimum value for an ascending sequence object and the maximum value for a descending sequence object.</span></span>  
  
 <span data-ttu-id="067b6-139">**増分**</span><span class="sxs-lookup"><span data-stu-id="067b6-139">**Increment by**</span></span>  
 <span data-ttu-id="067b6-140">**NEXT VALUE FOR** 関数を呼び出すたびに必要なシーケンス オブジェクトの値を増分 (負の場合は減少) させるのに使用される値です。</span><span class="sxs-lookup"><span data-stu-id="067b6-140">The value that is used to increment (or decrement if negative) the value of the sequence object for each call to the **NEXT VALUE FOR** function.</span></span> <span data-ttu-id="067b6-141">増分値が負の値の場合はシーケンス オブジェクトは降順で、それ以外の場合は昇順です。</span><span class="sxs-lookup"><span data-stu-id="067b6-141">If the increment is a negative value the sequence object is descending, otherwise, it is ascending.</span></span> <span data-ttu-id="067b6-142">0 は増分として使用できません。</span><span class="sxs-lookup"><span data-stu-id="067b6-142">The increment cannot be 0.</span></span>  
  
 <span data-ttu-id="067b6-143">**最小値**</span><span class="sxs-lookup"><span data-stu-id="067b6-143">**Minimum value**</span></span>  
 <span data-ttu-id="067b6-144">シーケンスのオブジェクトの境界を指定します。</span><span class="sxs-lookup"><span data-stu-id="067b6-144">Specifies the bounds for sequence object.</span></span> <span data-ttu-id="067b6-145">新しいシーケンス オブジェクトの既定の最小値は、シーケンス オブジェクトのデータ型の最小値です。</span><span class="sxs-lookup"><span data-stu-id="067b6-145">The default minimum value for a new sequence object is the minimum value of the data type of the sequence object.</span></span> <span data-ttu-id="067b6-146">データ型の場合は0、 `tinyint` 他のすべてのデータ型の場合は負の値です。</span><span class="sxs-lookup"><span data-stu-id="067b6-146">This is zero for the `tinyint` data type and a negative number for all other data types.</span></span>  
  
 <span data-ttu-id="067b6-147">**最大値**</span><span class="sxs-lookup"><span data-stu-id="067b6-147">**Maximum value**</span></span>  
 <span data-ttu-id="067b6-148">シーケンスのオブジェクトの境界を指定します。</span><span class="sxs-lookup"><span data-stu-id="067b6-148">Specifies the bounds for sequence object.</span></span> <span data-ttu-id="067b6-149">新しいシーケンス オブジェクトの既定の最大値は、シーケンス オブジェクトのデータ型の最大値です。</span><span class="sxs-lookup"><span data-stu-id="067b6-149">The default maximum value for a new sequence object is the maximum value of the data type of the sequence object.</span></span>  
  
 <span data-ttu-id="067b6-150">**制限に達するとサイクルのシーケンスが再起動します。**</span><span class="sxs-lookup"><span data-stu-id="067b6-150">**Cycle-sequence will restart on reaching limit**</span></span>  
 <span data-ttu-id="067b6-151">オンにすると、最小値または最大値を超過した場合、シーケンス オブジェクトを最小値 (または降順シーケンス オブジェクトの最大値) から再起動することができます。</span><span class="sxs-lookup"><span data-stu-id="067b6-151">Select to allow the sequence object to restart from the minimum value (or maximum for descending sequence objects) when its minimum or maximum value is exceeded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="067b6-152">サイクルは開始値からではなく最小値または最大値から再起動されます。</span><span class="sxs-lookup"><span data-stu-id="067b6-152">Cycling does not restart from the start value but rather from the minimum/maximum value.</span></span>  
  
 <span data-ttu-id="067b6-153">**[キャッシュ オプション]**</span><span class="sxs-lookup"><span data-stu-id="067b6-153">**Cache options**</span></span>  
 <span data-ttu-id="067b6-154">シーケンス値のキャッシュを作成し、シーケンス番号を作成するのに必要なディスク IO の数を最小限に抑えることで、シーケンス オブジェクトを使用するアプリケーションのパフォーマンスを向上できます。</span><span class="sxs-lookup"><span data-stu-id="067b6-154">Creating a cache of sequence values can increase performance for applications that use sequence objects by minimizing the number of disk IOs that are required to create sequence numbers.</span></span>  
  
-   <span data-ttu-id="067b6-155">既定のキャッシュ サイズ - [!INCLUDE[ssDE](../../includes/ssde-md.md)] によってサイズが選択されますが、選択が一貫していない場合があるため、注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="067b6-155">Default cache size - The [!INCLUDE[ssDE](../../includes/ssde-md.md)] will select a size, however users should not rely upon the selection being consistent.</span></span> [!INCLUDE[msCoName](../../includes/msconame-md.md)] <span data-ttu-id="067b6-156">では、予告なしにキャッシュ サイズの算出方法を変更する場合があります。</span><span class="sxs-lookup"><span data-stu-id="067b6-156">might change the method of calculating the cache size without notice.</span></span>  
  
-   <span data-ttu-id="067b6-157">キャッシュなし - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではシーケンス番号がキャッシュに格納されません。</span><span class="sxs-lookup"><span data-stu-id="067b6-157">No cache - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will not cache sequence numbers.</span></span>  
  
-   <span data-ttu-id="067b6-158">キャッシュ サイズ - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではシーケンス値をキャッシュに格納します。</span><span class="sxs-lookup"><span data-stu-id="067b6-158">Cache with size - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] will cache sequence values.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="067b6-159">では、現在の値とキャッシュに残された値の数を追跡します。</span><span class="sxs-lookup"><span data-stu-id="067b6-159">keeps track of the current value and the number of values left in the cache.</span></span> <span data-ttu-id="067b6-160">したがって、キャッシュを格納するために必要なメモリ量は、常にシーケンス オブジェクトのデータ型の 2 つのインスタンスと等しくなります。</span><span class="sxs-lookup"><span data-stu-id="067b6-160">Therefore, the amount of memory that is required to store the cache is always two instances of the data type of the sequence object</span></span>  
  
 <span data-ttu-id="067b6-161">CACHE オプションを使用してシーケンス番号を作成する際に予期しないシャットダウン (電源障害など) が発生すると、キャッシュ内のシーケンス番号が失われる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="067b6-161">When created with the CACHE option, an unexpected shutdown, such as a power failure, can lose the sequence numbers in the cache.</span></span>  
  
 <span data-ttu-id="067b6-162">CREATE SEQUENCE のオプションの詳細については、「[CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="067b6-162">For additional information about the create sequence options, see [CREATE SEQUENCE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-sequence-transact-sql).</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="067b6-163">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="067b6-163">Permissions</span></span>  
 <span data-ttu-id="067b6-164">SCHEMA に対する **CREATE SEQUENCE**権限、 **ALTER**権限、または **CONTROL** 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="067b6-164">Requires **CREATE SEQUENCE**, **ALTER**, or **CONTROL** permission on the SCHEMA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="067b6-165">参照</span><span class="sxs-lookup"><span data-stu-id="067b6-165">See Also</span></span>  
 [<span data-ttu-id="067b6-166">sys.sequences &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="067b6-166">sys.sequences &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sequences-transact-sql)  
  
  
