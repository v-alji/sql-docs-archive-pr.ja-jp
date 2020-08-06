---
title: シノニム (データベース エンジン) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- synonyms [SQL Server], about synonyms
ms.assetid: 6210e1d5-075f-47e4-ac8d-f84bcf26fbc0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3494f4f5b13c422efb8e2a39597e131c10d81ed1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640840"
---
# <a name="synonyms-database-engine"></a><span data-ttu-id="57111-102">シノニム (データベース エンジン)</span><span class="sxs-lookup"><span data-stu-id="57111-102">Synonyms (Database Engine)</span></span>
  <span data-ttu-id="57111-103">シノニムは、次の目的で機能するデータベース オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="57111-103">A synonym is a database object that serves the following purposes:</span></span>  
  
-   <span data-ttu-id="57111-104">ベース オブジェクトと呼ばれる別のデータベース オブジェクトの代替名を提供します。ベース オブジェクトは、ローカル サーバーまたはリモート サーバーに配置できます。</span><span class="sxs-lookup"><span data-stu-id="57111-104">Provides an alternative name for another database object, referred to as the base object, that can exist on a local or remote server.</span></span>  
  
-   <span data-ttu-id="57111-105">ベース オブジェクトの名前や場所に加えられた変更からクライアント アプリケーションを保護する抽象層を提供します。</span><span class="sxs-lookup"><span data-stu-id="57111-105">Provides a layer of abstraction that protects a client application from changes made to the name or location of the base object.</span></span>  
  
 <span data-ttu-id="57111-106">たとえば、 **Server1** という名前のサーバーに [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]の **Employee**テーブルがあるとします。</span><span class="sxs-lookup"><span data-stu-id="57111-106">For example, consider the **Employee** table of [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], located on a server named **Server1**.</span></span> <span data-ttu-id="57111-107">クライアント アプリケーションで、このテーブルを別のサーバー ( **Server2**) から参照するには、 **Server1.AdventureWorks.Person.Employee**という 4 部構成の名前を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57111-107">To reference this table from another server, **Server2**, a client application would have to use the four-part name **Server1.AdventureWorks.Person.Employee**.</span></span> <span data-ttu-id="57111-108">また、テーブルの場所を別のサーバーなどに変更する場合は、その変更内容を反映してクライアント アプリケーションを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57111-108">Also, if the location of the table were to change, for example, to another server, the client application would have to be modified to reflect that change.</span></span>  
  
 <span data-ttu-id="57111-109">このような問題の両方に対処するには、 **Server1**の **Employee** テーブルに対して、 **Server2** に **EmpTable**というシノニムを作成できます。</span><span class="sxs-lookup"><span data-stu-id="57111-109">To address both these issues, you can create a synonym, **EmpTable**, on **Server2** for the **Employee** table on **Server1**.</span></span> <span data-ttu-id="57111-110">これで、クライアント アプリケーションから **Employee**テーブルを参照するときに、 **EmpTable** という 1 部構成の名前を使用するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="57111-110">Now, the client application only has to use the single-part name, **EmpTable**, to reference the **Employee** table.</span></span> <span data-ttu-id="57111-111">また、 **Employee** テーブルの場所が変更された場合は、 **Employee**テーブルの新しい場所を指すように、シノニムである **EmpTable** を変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57111-111">Also, if the location of the **Employee** table changes, you will have to modify the synonym, **EmpTable**, to point to the new location of the **Employee** table.</span></span> <span data-ttu-id="57111-112">ALTER SYNONYM というステートメントは存在しないので、 **EmpTable**というシノニムをいったん削除してから、 **Employee**の新しい場所を指す同じ名前のシノニムを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57111-112">Because there is no ALTER SYNONYM statement, you first have to drop the synonym, **EmpTable**, and then re-create the synonym with the same name, but point the synonym to the new location of **Employee**.</span></span>  
  
 <span data-ttu-id="57111-113">シノニムはスキーマに属しています。したがって、スキーマ内の他のオブジェクトと同様に、シノニムの名前は一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="57111-113">A synonym belongs to a schema, and like other objects in a schema, the name of a synonym must be unique.</span></span> <span data-ttu-id="57111-114">シノニムは、次のデータベース オブジェクトに対して作成できます。</span><span class="sxs-lookup"><span data-stu-id="57111-114">You can create synonyms for the following database objects:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57111-115">アセンブリ (CLR) ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="57111-115">Assembly (CLR) stored procedure</span></span>|<span data-ttu-id="57111-116">アセンブリ (CLR) テーブル値関数</span><span class="sxs-lookup"><span data-stu-id="57111-116">Assembly (CLR) table-valued function</span></span>|  
|<span data-ttu-id="57111-117">アセンブリ (CLR) スカラー関数</span><span class="sxs-lookup"><span data-stu-id="57111-117">Assembly (CLR) scalar function</span></span>|<span data-ttu-id="57111-118">アセンブリ (CLR) 集計関数</span><span class="sxs-lookup"><span data-stu-id="57111-118">Assembly (CLR) aggregate functions</span></span>|  
|<span data-ttu-id="57111-119">レプリケーション フィルター プロシージャ</span><span class="sxs-lookup"><span data-stu-id="57111-119">Replication-filter-procedure</span></span>|<span data-ttu-id="57111-120">拡張ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="57111-120">Extended stored procedure</span></span>|  
|<span data-ttu-id="57111-121">SQL スカラー関数</span><span class="sxs-lookup"><span data-stu-id="57111-121">SQL scalar function</span></span>|<span data-ttu-id="57111-122">SQL テーブル値関数</span><span class="sxs-lookup"><span data-stu-id="57111-122">SQL table-valued function</span></span>|  
|<span data-ttu-id="57111-123">SQL インライン テーブル値関数</span><span class="sxs-lookup"><span data-stu-id="57111-123">SQL inline-tabled-valued function</span></span>|<span data-ttu-id="57111-124">SQL ストアド プロシージャ</span><span class="sxs-lookup"><span data-stu-id="57111-124">SQL stored procedure</span></span>|  
|<span data-ttu-id="57111-125">表示</span><span class="sxs-lookup"><span data-stu-id="57111-125">View</span></span>|<span data-ttu-id="57111-126">テーブル<sup>1</sup> (ユーザー定義)</span><span class="sxs-lookup"><span data-stu-id="57111-126">Table<sup>1</sup> (User-defined)</span></span>|  
  
 <span data-ttu-id="57111-127"><sup>1</sup>ローカル一時テーブルとグローバル一時テーブルが含まれます。</span><span class="sxs-lookup"><span data-stu-id="57111-127"><sup>1</sup> Includes local and global temporary tables</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57111-128">4 部構成の関数ベース オブジェクト名はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="57111-128">Four-part names for function base objects are not supported.</span></span>  
  
 <span data-ttu-id="57111-129">あるシノニムを別のシノニムのベース オブジェクトにすることはできません。また、シノニムからユーザー定義集計関数を参照することもできません。</span><span class="sxs-lookup"><span data-stu-id="57111-129">A synonym cannot be the base object for another synonym, and a synonym cannot reference a user-defined aggregate function.</span></span>  
  
 <span data-ttu-id="57111-130">シノニムとベース オブジェクトとのバインドは、名前だけで行われます。</span><span class="sxs-lookup"><span data-stu-id="57111-130">The binding between a synonym and its base object is by name only.</span></span> <span data-ttu-id="57111-131">ベース オブジェクトの存在、種類、および権限のチェックは、すべて実行時まで行われません。</span><span class="sxs-lookup"><span data-stu-id="57111-131">All existence, type, and permissions checking on the base object is deferred until run time.</span></span> <span data-ttu-id="57111-132">このため、ベース オブジェクトの変更や削除を行うことも、または削除してから元のベース オブジェクトと同じ名前の別のオブジェクトに置換することもできます。</span><span class="sxs-lookup"><span data-stu-id="57111-132">Therefore, the base object can be modified, dropped, or dropped and replaced by another object that has the same name as the original base object.</span></span> <span data-ttu-id="57111-133">たとえば、 **の**Person.Contact **テーブルを参照する** MyContacts [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)]というシノニムがあるとします。</span><span class="sxs-lookup"><span data-stu-id="57111-133">For example, consider a synonym, **MyContacts**, that references the **Person.Contact** table in [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)].</span></span> <span data-ttu-id="57111-134">**Contact** テーブルを削除し、 **Person.Contact**というビューに置き換えると、 **MyContacts** は **Person.Contact** ビューを参照するようになります。</span><span class="sxs-lookup"><span data-stu-id="57111-134">If the **Contact** table is dropped and replaced by a view named **Person.Contact**, **MyContacts** now references the **Person.Contact** view.</span></span>  
  
 <span data-ttu-id="57111-135">シノニムへの参照は、スキーマにはバインドされていません。</span><span class="sxs-lookup"><span data-stu-id="57111-135">References to synonyms are not schema-bound.</span></span> <span data-ttu-id="57111-136">したがって、シノニムはいつでも削除できます。</span><span class="sxs-lookup"><span data-stu-id="57111-136">Therefore, a synonym can be dropped at any time.</span></span> <span data-ttu-id="57111-137">ただし、シノニムを削除することにより、削除されたシノニムへの参照が未解決の状態になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="57111-137">However, by dropping a synonym, you run the risk of leaving dangling references to the synonym that was dropped.</span></span> <span data-ttu-id="57111-138">このような参照は、実行時まで見つかりません。</span><span class="sxs-lookup"><span data-stu-id="57111-138">These references will only be found at run time.</span></span>  
  
## <a name="synonyms-and-schemas"></a><span data-ttu-id="57111-139">シノニムとスキーマ</span><span class="sxs-lookup"><span data-stu-id="57111-139">Synonyms and Schemas</span></span>  
 <span data-ttu-id="57111-140">所有者が自分ではない既定のスキーマのシノニムを作成する場合は、自分が所有しているスキーマ名でシノニム名を修飾する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57111-140">If you have a default schema that you do not own and want to create a synonym, you must qualify the synonym name with the name of a schema that you do own.</span></span> <span data-ttu-id="57111-141">たとえば、 **x**というスキーマを所有していて、既定のスキーマが **y** だとします。この状況で CREATE SYNONYM ステートメントを使用する場合は、1 部構成の名前を使用してシノニムに名前を付けるのではなく、スキーマ **x**をシノニム名のプレフィックスにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="57111-141">For example, if you own a schema **x**, but **y** is your default schema and you use the CREATE SYNONYM statement, you must prefix the name of the synonym with the schema **x**, instead of naming the synonym by using a single-part name.</span></span> <span data-ttu-id="57111-142">シノニムの作成方法の詳細については、「 [CREATE SYNONYM &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-synonym-transact-sql)テーブルがあるとします。</span><span class="sxs-lookup"><span data-stu-id="57111-142">For more information about how to create synonyms, see [CREATE SYNONYM &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-synonym-transact-sql).</span></span>  
  
## <a name="granting-permissions-on-a-synonym"></a><span data-ttu-id="57111-143">シノニムに対する権限の許可</span><span class="sxs-lookup"><span data-stu-id="57111-143">Granting Permissions on a Synonym</span></span>  
 <span data-ttu-id="57111-144">シノニムに対する権限を許可できるのは、シノニムの所有者、 **db_owner**、または **db_ddladmin** のみです。</span><span class="sxs-lookup"><span data-stu-id="57111-144">Only synonym owners, members of **db_owner**, or members of **db_ddladmin** can grant permission on a synonym.</span></span>  
  
 <span data-ttu-id="57111-145">次に示すシノニムに対する権限は、すべてまたはいくつかを許可 (GRANT)、拒否 (DENY)、または取り消す (REVOKE) ことができます。</span><span class="sxs-lookup"><span data-stu-id="57111-145">You can GRANT, DENY, REVOKE all or any of the following permissions on a synonym:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57111-146">CONTROL</span><span class="sxs-lookup"><span data-stu-id="57111-146">CONTROL</span></span>|<span data-ttu-id="57111-147">DELETE</span><span class="sxs-lookup"><span data-stu-id="57111-147">DELETE</span></span>|  
|<span data-ttu-id="57111-148">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="57111-148">EXECUTE</span></span>|<span data-ttu-id="57111-149">INSERT</span><span class="sxs-lookup"><span data-stu-id="57111-149">INSERT</span></span>|  
|<span data-ttu-id="57111-150">SELECT</span><span class="sxs-lookup"><span data-stu-id="57111-150">SELECT</span></span>|<span data-ttu-id="57111-151">TAKE OWNERSHIP</span><span class="sxs-lookup"><span data-stu-id="57111-151">TAKE OWNERSHIP</span></span>|  
|<span data-ttu-id="57111-152">UPDATE</span><span class="sxs-lookup"><span data-stu-id="57111-152">UPDATE</span></span>|<span data-ttu-id="57111-153">VIEW DEFINITION</span><span class="sxs-lookup"><span data-stu-id="57111-153">VIEW DEFINITION</span></span>|  
  
## <a name="using-synonyms"></a><span data-ttu-id="57111-154">シノニムの使用</span><span class="sxs-lookup"><span data-stu-id="57111-154">Using Synonyms</span></span>  
 <span data-ttu-id="57111-155">いくつかの SQL ステートメントや式のコンテキストでは、参照先のベース オブジェクトの代わりにシノニムを使用できます。</span><span class="sxs-lookup"><span data-stu-id="57111-155">You can use synonyms in place of their referenced base object in several SQL statements and expression contexts.</span></span> <span data-ttu-id="57111-156">次の表に、これに該当するステートメントや式のコンテキストを示します。</span><span class="sxs-lookup"><span data-stu-id="57111-156">The following table contains a list of these statements and expression contexts:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57111-157">SELECT</span><span class="sxs-lookup"><span data-stu-id="57111-157">SELECT</span></span>|<span data-ttu-id="57111-158">INSERT</span><span class="sxs-lookup"><span data-stu-id="57111-158">INSERT</span></span>|  
|<span data-ttu-id="57111-159">UPDATE</span><span class="sxs-lookup"><span data-stu-id="57111-159">UPDATE</span></span>|<span data-ttu-id="57111-160">DELETE</span><span class="sxs-lookup"><span data-stu-id="57111-160">DELETE</span></span>|  
|<span data-ttu-id="57111-161">EXECUTE</span><span class="sxs-lookup"><span data-stu-id="57111-161">EXECUTE</span></span>|<span data-ttu-id="57111-162">副選択式</span><span class="sxs-lookup"><span data-stu-id="57111-162">Sub-selects</span></span>|  
  
 <span data-ttu-id="57111-163">前に示したコンテキストでシノニムを扱っているときは、ベース オブジェクトが影響を受けます。</span><span class="sxs-lookup"><span data-stu-id="57111-163">When you are working with synonyms in the contexts previously stated, the base object is affected.</span></span> <span data-ttu-id="57111-164">たとえば、シノニムが参照するベース オブジェクトがテーブルの場合に、シノニムに行を挿入すると、実際に参照先のテーブルに行が挿入されます。</span><span class="sxs-lookup"><span data-stu-id="57111-164">For example, if a synonym references a base object that is a table and you insert a row into the synonym, you are actually inserting a row into the referenced table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="57111-165">リンク サーバー上のシノニムを参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="57111-165">You cannot reference a synonym that is located on a linked server.</span></span>  
  
 <span data-ttu-id="57111-166">OBJECT_ID 関数のパラメーターとしてシノニムを使用できます。ただし、この関数はベース オブジェクトではなく、シノニムのオブジェクト ID を返します。</span><span class="sxs-lookup"><span data-stu-id="57111-166">You can use a synonym as the parameter for the OBJECT_ID function; however, the function returns the object ID of the synonym, not the base object.</span></span>  
  
 <span data-ttu-id="57111-167">DDL ステートメントでシノニムを参照することはできません。</span><span class="sxs-lookup"><span data-stu-id="57111-167">You cannot reference a synonym in a DDL statement.</span></span> <span data-ttu-id="57111-168">たとえば、 `dbo.MyProduct`という名前のシノニムを参照する次のステートメントでは、エラーが生成されます。</span><span class="sxs-lookup"><span data-stu-id="57111-168">For example, the following statements, which reference a synonym named `dbo.MyProduct`, generate errors:</span></span>  
  
```  
ALTER TABLE dbo.MyProduct  
   ADD NewFlag int null;  
EXEC ('ALTER TABLE dbo.MyProduct  
   ADD NewFlag int null');  
```  
  
 <span data-ttu-id="57111-169">次の権限ステートメントは、シノニムのみに関連付けられ、ベース オブジェクトには影響しません。</span><span class="sxs-lookup"><span data-stu-id="57111-169">The following permission statements are associated only with the synonym and not the base object:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57111-170">GRANT</span><span class="sxs-lookup"><span data-stu-id="57111-170">GRANT</span></span>|<span data-ttu-id="57111-171">DENY</span><span class="sxs-lookup"><span data-stu-id="57111-171">DENY</span></span>|  
|<span data-ttu-id="57111-172">REVOKE</span><span class="sxs-lookup"><span data-stu-id="57111-172">REVOKE</span></span>||  
  
 <span data-ttu-id="57111-173">シノニムはスキーマ バインド オブジェクトではないので、次のスキーマ バインド式コンテキストからは参照できません。</span><span class="sxs-lookup"><span data-stu-id="57111-173">Synonyms are not schema-bound and, therefore, cannot be referenced by the following schema-bound expression contexts:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="57111-174">CHECK 制約</span><span class="sxs-lookup"><span data-stu-id="57111-174">CHECK constraints</span></span>|<span data-ttu-id="57111-175">計算列</span><span class="sxs-lookup"><span data-stu-id="57111-175">Computed columns</span></span>|  
|<span data-ttu-id="57111-176">既定式</span><span class="sxs-lookup"><span data-stu-id="57111-176">Default expressions</span></span>|<span data-ttu-id="57111-177">ルール式</span><span class="sxs-lookup"><span data-stu-id="57111-177">Rule expressions</span></span>|  
|<span data-ttu-id="57111-178">スキーマ バインド ビュー</span><span class="sxs-lookup"><span data-stu-id="57111-178">Schema-bound views</span></span>|<span data-ttu-id="57111-179">スキーマ バインド関数</span><span class="sxs-lookup"><span data-stu-id="57111-179">Schema-bound functions</span></span>|  
  
 <span data-ttu-id="57111-180">スキーマ バインド関数の詳細については、「[ユーザー定義関数の作成 &#40;データベース エンジン&#41;](../user-defined-functions/create-user-defined-functions-database-engine.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57111-180">For more information about schema-bound functions, see [Create User-defined Functions &#40;Database Engine&#41;](../user-defined-functions/create-user-defined-functions-database-engine.md).</span></span>  
  
## <a name="getting-information-about-synonyms"></a><span data-ttu-id="57111-181">シノニムに関する情報の取得</span><span class="sxs-lookup"><span data-stu-id="57111-181">Getting Information About Synonyms</span></span>  
 <span data-ttu-id="57111-182">sys.synonyms カタログ ビューには、特定のデータベースの各シノニムを表すエントリが含まれています。</span><span class="sxs-lookup"><span data-stu-id="57111-182">The sys.synonyms catalog view contains an entry for each synonym in a given database.</span></span> <span data-ttu-id="57111-183">シノニム名やベース オブジェクト名など、シノニムのメタデータがこのカタログ ビューに表示されます。</span><span class="sxs-lookup"><span data-stu-id="57111-183">This catalog view exposes synonym metadata such as the name of the synonym and the name of the base object.</span></span> <span data-ttu-id="57111-184">カタログビューの詳細につい `sys.synonyms` ては、「 [Sys &#40;transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-synonyms-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57111-184">For more information about the `sys.synonyms` catalog view, see [sys.synonyms &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-synonyms-transact-sql).</span></span>  
  
 <span data-ttu-id="57111-185">拡張プロパティを使用すれば、説明用テキスト、指示テキスト、定型入力、および表記規則をシノニムのプロパティとして追加できます。</span><span class="sxs-lookup"><span data-stu-id="57111-185">By using extended properties, you can add descriptive or instructional text, input masks, and formatting rules as properties of a synonym.</span></span> <span data-ttu-id="57111-186">プロパティはデータベースに格納されるので、プロパティを読み取るアプリケーションはすべて、同じ方法でオブジェクトを評価できます。</span><span class="sxs-lookup"><span data-stu-id="57111-186">Because the property is stored in the database, all applications that read the property can evaluate the object in the same way.</span></span> <span data-ttu-id="57111-187">詳細については、「[sp_addextendedproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57111-187">For more information, see [sp_addextendedproperty &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql).</span></span>  
  
 <span data-ttu-id="57111-188">シノニムのベース オブジェクトの基本データ型を調べるには、OBJECTPROPERTYEX 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="57111-188">To find the base type of the base object of a synonym, use the OBJECTPROPERTYEX function.</span></span> <span data-ttu-id="57111-189">詳細については、「[OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="57111-189">For more information, see [OBJECTPROPERTYEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/objectproperty-transact-sql).</span></span>  
  
### <a name="examples"></a><span data-ttu-id="57111-190">例</span><span class="sxs-lookup"><span data-stu-id="57111-190">Examples</span></span>  
 <span data-ttu-id="57111-191">次の例は、ローカル オブジェクトであるシノニムのベース オブジェクトの基本データ型を返します。</span><span class="sxs-lookup"><span data-stu-id="57111-191">The following example returns the base type of a synonym's base object that is a local object.</span></span>  
  
```  
USE tempdb;  
GO  
CREATE SYNONYM MyEmployee   
FOR AdventureWorks2012.HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('MyEmployee'), 'BaseType') AS BaseType;  
```  
  
 <span data-ttu-id="57111-192">次の例は、 `Server1`というサーバー上のリモート オブジェクトであるシノニムのベース オブジェクトの基本データ型を返します。</span><span class="sxs-lookup"><span data-stu-id="57111-192">The following example returns the base type of a synonym's base object that is a remote object located on a server named `Server1`.</span></span>  
  
```  
EXECUTE sp_addlinkedserver Server1;  
GO  
CREATE SYNONYM MyRemoteEmployee  
FOR Server1.AdventureWorks2012.HumanResources.Employee;  
GO  
SELECT OBJECTPROPERTYEX(OBJECT_ID('MyRemoteEmployee'), 'BaseType') AS BaseType;  
GO  
```  
  
## <a name="related-content"></a><span data-ttu-id="57111-193">関連コンテンツ</span><span class="sxs-lookup"><span data-stu-id="57111-193">Related Content</span></span>  
 [<span data-ttu-id="57111-194">シノニムの作成</span><span class="sxs-lookup"><span data-stu-id="57111-194">Create Synonyms</span></span>](create-synonyms.md)  
  
 [<span data-ttu-id="57111-195">CREATE SYNONYM &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="57111-195">CREATE SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-synonym-transact-sql)  
  
 [<span data-ttu-id="57111-196">DROP SYNONYM &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="57111-196">DROP SYNONYM &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-synonym-transact-sql)  
  
  
