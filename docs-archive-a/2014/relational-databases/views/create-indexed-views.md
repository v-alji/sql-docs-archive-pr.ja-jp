---
title: インデックス付きビューの作成 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexed views [SQL Server], creating
- clustered indexes, views
- CREATE INDEX statement
- large_value_types_out_of_row option
- indexed views [SQL Server]
- views [SQL Server], indexed views
ms.assetid: f86dd29f-52dd-44a9-91ac-1eb305c1ca8d
author: stevestein
ms.author: sstein
ms.openlocfilehash: d33ff37caca04f46edd6ad92d0686713829bb270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631726"
---
# <a name="create-indexed-views"></a><span data-ttu-id="cef9b-102">インデックス付きビューの作成</span><span class="sxs-lookup"><span data-stu-id="cef9b-102">Create Indexed Views</span></span>
  <span data-ttu-id="cef9b-103">このトピックでは、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で、 [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用し、インデックス付きビューを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-103">This topic describes how to create an indexed view in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="cef9b-104">ビューに作成する最初のインデックスは、一意なクラスター化インデックスにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-104">The first index created on a view must be a unique clustered index.</span></span> <span data-ttu-id="cef9b-105">一意のクラスター化インデックスを作成した後は、非クラスター化インデックスを追加で作成できます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-105">After the unique clustered index has been created, you can create more nonclustered indexes.</span></span> <span data-ttu-id="cef9b-106">ビューに一意のクラスター化インデックスを作成すると、そのビューは、クラスター化インデックスが定義されているテーブルと同じ方法でデータベースに格納されるので、クエリのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-106">Creating a unique clustered index on a view improves query performance because the view is stored in the database in the same way a table with a clustered index is stored.</span></span> <span data-ttu-id="cef9b-107">クエリ オプティマイザーではインデックス付きビューを使って、クエリの実行速度を高めることができます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-107">The query optimizer may use indexed views to speed up the query execution.</span></span> <span data-ttu-id="cef9b-108">オプティマイザーでビューを代用するかどうかを判別するために、ビューがクエリで参照されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="cef9b-108">The view does not have to be referenced in the query for the optimizer to consider that view for a substitution.</span></span>  
  
  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="cef9b-109">はじめに</span><span class="sxs-lookup"><span data-stu-id="cef9b-109">Before You Begin</span></span>  
 <span data-ttu-id="cef9b-110">次の手順は、インデックス付きビューの作成に必要な手順であり、インデックス付きビューの正常な実装に不可欠です。</span><span class="sxs-lookup"><span data-stu-id="cef9b-110">The following steps are required to create an indexed view and are critical to the successful implementation of the indexed view:</span></span>  
  
1.  <span data-ttu-id="cef9b-111">SET オプションが、ビューで参照されるすべての既存のテーブルに対して正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-111">Verify the SET options are correct for all existing tables that will be referenced in the view.</span></span>  
  
2.  <span data-ttu-id="cef9b-112">テーブルやビューを作成する前に、そのセッション用の SET オプションが正しく設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-112">Verify that the SET options for the session are set correctly before you create any tables and the view.</span></span>  
  
3.  <span data-ttu-id="cef9b-113">ビュー定義が決定的であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-113">Verify that the view definition is deterministic.</span></span>  
  
4.  <span data-ttu-id="cef9b-114">WITH SCHEMABINDING オプションを使ってビューを作成します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-114">Create the view by using the WITH SCHEMABINDING option.</span></span>  
  
5.  <span data-ttu-id="cef9b-115">ビューに一意のクラスター化インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-115">Create the unique clustered index on the view.</span></span>  
  
###  <a name="required-set-options-for-indexed-views"></a><a name="Restrictions"></a> <span data-ttu-id="cef9b-116">インデックス付きビューに必要な SET オプション</span><span class="sxs-lookup"><span data-stu-id="cef9b-116">Required SET Options for Indexed Views</span></span>  
 <span data-ttu-id="cef9b-117">クエリの実行時、異なる SET オプションがアクティブになっている場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] は同じ式を評価しても異なる結果を生成することがあります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-117">Evaluating the same expression can produce different results in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] when different SET options are active when the query is executed.</span></span> <span data-ttu-id="cef9b-118">たとえば、SET オプションの CONCAT_NULL_YIELDS_NULL を ON に設定した後、式 **'** abc **'** + NULL を実行すると NULL 値が返されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-118">For example, after the SET option CONCAT_NULL_YIELDS_NULL is set to ON, the expression **'** abc **'** + NULL returns the value NULL.</span></span> <span data-ttu-id="cef9b-119">CONCAT_NULL_YIELDS_NULL を OFF に設定した後、同じ式を実行すると値 **'** abc **'** が返されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-119">However, after CONCAT_NULL_YIEDS_NULL is set to OFF, the same expression produces **'** abc **'**.</span></span>  
  
 <span data-ttu-id="cef9b-120">ビューが正しく維持され、一貫性のある結果が返されるようにするには、インデックス付きビューで、いくつかの SET オプションに固定値が必要となります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-120">To make sure that the views can be maintained correctly and return consistent results, indexed views require fixed values for several SET options.</span></span> <span data-ttu-id="cef9b-121">次の条件が発生するたびに、次の表の SET オプションを**Requiredvalue**列に表示される値に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-121">The SET options in the following table must be set to the values shown in the **RequiredValue** column whenever the following conditions occur:</span></span>  
  
-   <span data-ttu-id="cef9b-122">ビューが作成され、そのビューのインデックスも作成されている。</span><span class="sxs-lookup"><span data-stu-id="cef9b-122">The view and subsequent indexes on the view are created.</span></span>  
  
-   <span data-ttu-id="cef9b-123">テーブルの作成時にビューで参照されるベース テーブル。</span><span class="sxs-lookup"><span data-stu-id="cef9b-123">The base tables referenced in the view at the time the table is created.</span></span>  
  
-   <span data-ttu-id="cef9b-124">インデックス付きビューに関与するテーブルで実行される挿入、更新、または削除操作がある。</span><span class="sxs-lookup"><span data-stu-id="cef9b-124">There is any insert, update, or delete operation performed on any table that participates in the indexed view.</span></span> <span data-ttu-id="cef9b-125">この要件には一括コピー、レプリケーション、分散クエリなどの操作も含まれます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-125">This requirement includes operations such as bulk copy, replication, and distributed queries.</span></span>  
  
-   <span data-ttu-id="cef9b-126">クエリ オプティマイザーで、クエリ プランの生成にインデックス付きビューが使用される。</span><span class="sxs-lookup"><span data-stu-id="cef9b-126">The indexed view is used by the query optimizer to produce the query plan.</span></span>  
  
    |<span data-ttu-id="cef9b-127">SET オプション</span><span class="sxs-lookup"><span data-stu-id="cef9b-127">SET options</span></span>|<span data-ttu-id="cef9b-128">必須値</span><span class="sxs-lookup"><span data-stu-id="cef9b-128">Required value</span></span>|<span data-ttu-id="cef9b-129">既定のサーバー値</span><span class="sxs-lookup"><span data-stu-id="cef9b-129">Default server value</span></span>|<span data-ttu-id="cef9b-130">Default</span><span class="sxs-lookup"><span data-stu-id="cef9b-130">Default</span></span><br /><br /> <span data-ttu-id="cef9b-131">OLE DB および ODBC 値</span><span class="sxs-lookup"><span data-stu-id="cef9b-131">OLE DB and ODBC value</span></span>|<span data-ttu-id="cef9b-132">Default</span><span class="sxs-lookup"><span data-stu-id="cef9b-132">Default</span></span><br /><br /> <span data-ttu-id="cef9b-133">DB-Library 値</span><span class="sxs-lookup"><span data-stu-id="cef9b-133">DB-Library value</span></span>|  
    |-----------------|--------------------|--------------------------|---------------------------------------|-----------------------------------|  
    |<span data-ttu-id="cef9b-134">ANSI_NULLS</span><span class="sxs-lookup"><span data-stu-id="cef9b-134">ANSI_NULLS</span></span>|<span data-ttu-id="cef9b-135">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-135">ON</span></span>|<span data-ttu-id="cef9b-136">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-136">ON</span></span>|<span data-ttu-id="cef9b-137">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-137">ON</span></span>|<span data-ttu-id="cef9b-138">OFF</span><span class="sxs-lookup"><span data-stu-id="cef9b-138">OFF</span></span>|  
    |<span data-ttu-id="cef9b-139">ANSI_PADDING</span><span class="sxs-lookup"><span data-stu-id="cef9b-139">ANSI_PADDING</span></span>|<span data-ttu-id="cef9b-140">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-140">ON</span></span>|<span data-ttu-id="cef9b-141">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-141">ON</span></span>|<span data-ttu-id="cef9b-142">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-142">ON</span></span>|<span data-ttu-id="cef9b-143">OFF</span><span class="sxs-lookup"><span data-stu-id="cef9b-143">OFF</span></span>|  
    |<span data-ttu-id="cef9b-144">ANSI_WARNINGS\*</span><span class="sxs-lookup"><span data-stu-id="cef9b-144">ANSI_WARNINGS\*</span></span>|<span data-ttu-id="cef9b-145">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-145">ON</span></span>|<span data-ttu-id="cef9b-146">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-146">ON</span></span>|<span data-ttu-id="cef9b-147">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-147">ON</span></span>|<span data-ttu-id="cef9b-148">OFF</span><span class="sxs-lookup"><span data-stu-id="cef9b-148">OFF</span></span>|  
    |<span data-ttu-id="cef9b-149">ARITHABORT</span><span class="sxs-lookup"><span data-stu-id="cef9b-149">ARITHABORT</span></span>|<span data-ttu-id="cef9b-150">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-150">ON</span></span>|<span data-ttu-id="cef9b-151">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-151">ON</span></span>|<span data-ttu-id="cef9b-152">OFF</span><span class="sxs-lookup"><span data-stu-id="cef9b-152">OFF</span></span>|<span data-ttu-id="cef9b-153">OFF</span><span class="sxs-lookup"><span data-stu-id="cef9b-153">OFF</span></span>|  
    |<span data-ttu-id="cef9b-154">CONCAT_NULL_YIELDS_NULL</span><span class="sxs-lookup"><span data-stu-id="cef9b-154">CONCAT_NULL_YIELDS_NULL</span></span>|<span data-ttu-id="cef9b-155">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-155">ON</span></span>|<span data-ttu-id="cef9b-156">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-156">ON</span></span>|<span data-ttu-id="cef9b-157">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-157">ON</span></span>|<span data-ttu-id="cef9b-158">OFF</span><span class="sxs-lookup"><span data-stu-id="cef9b-158">OFF</span></span>|  
    |<span data-ttu-id="cef9b-159">NUMERIC_ROUNDABORT</span><span class="sxs-lookup"><span data-stu-id="cef9b-159">NUMERIC_ROUNDABORT</span></span>|<span data-ttu-id="cef9b-160">OFF</span><span class="sxs-lookup"><span data-stu-id="cef9b-160">OFF</span></span>|<span data-ttu-id="cef9b-161">OFF</span><span class="sxs-lookup"><span data-stu-id="cef9b-161">OFF</span></span>|<span data-ttu-id="cef9b-162">OFF</span><span class="sxs-lookup"><span data-stu-id="cef9b-162">OFF</span></span>|<span data-ttu-id="cef9b-163">OFF</span><span class="sxs-lookup"><span data-stu-id="cef9b-163">OFF</span></span>|  
    |<span data-ttu-id="cef9b-164">QUOTED_IDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="cef9b-164">QUOTED_IDENTIFIER</span></span>|<span data-ttu-id="cef9b-165">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-165">ON</span></span>|<span data-ttu-id="cef9b-166">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-166">ON</span></span>|<span data-ttu-id="cef9b-167">ON</span><span class="sxs-lookup"><span data-stu-id="cef9b-167">ON</span></span>|<span data-ttu-id="cef9b-168">OFF</span><span class="sxs-lookup"><span data-stu-id="cef9b-168">OFF</span></span>|  
  
     <span data-ttu-id="cef9b-169">\*ANSI_WARNINGS を ON に設定すると、ARITHABORT は暗黙的に ON に設定されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-169">\*Setting ANSI_WARNINGS to ON implicitly sets ARITHABORT to ON.</span></span>  
  
 <span data-ttu-id="cef9b-170">OLE DB または ODBC サーバー接続を使用している場合、変更する必要があるのは ARITHABORT 設定の値だけです。</span><span class="sxs-lookup"><span data-stu-id="cef9b-170">If you are using an OLE DB or ODBC server connection, the only value that must be modified is the ARITHABORT setting.</span></span> <span data-ttu-id="cef9b-171">すべての DB-Library 値は、サーバー レベルで **sp_configure** を使用するか、アプリケーションから SET コマンドを使用して、正しく設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-171">All DB-Library values must be set correctly either at the server level by using **sp_configure** or from the application by using the SET command.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="cef9b-172">ARITHABORT ユーザー オプションは、そのサーバーのデータベースで初めてインデックス付きビューまたは計算列のインデックスが作成されたときすぐに、サーバー全体で ON に設定することを強くお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cef9b-172">We strongly recommend that you set the ARITHABORT user option to ON server-wide as soon as the first indexed view or index on a computed column is created in any database on the server.</span></span>  
  
### <a name="deterministic-views"></a><span data-ttu-id="cef9b-173">決定的なビュー</span><span class="sxs-lookup"><span data-stu-id="cef9b-173">Deterministic Views</span></span>  
 <span data-ttu-id="cef9b-174">インデックス付きビューの定義は決定的である必要があります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-174">The definition of an indexed view must be deterministic.</span></span> <span data-ttu-id="cef9b-175">選択リストのすべての式と、WHERE 句および GROUP BY 句が決定的である場合、ビューは決定的であるといえます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-175">A view is deterministic if all expressions in the select list, as well as the WHERE and GROUP BY clauses, are deterministic.</span></span> <span data-ttu-id="cef9b-176">決定的な式では、特定の入力値セットで評価するとき常に同じ結果が返されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-176">Deterministic expressions always return the same result any time they are evaluated with a specific set of input values.</span></span> <span data-ttu-id="cef9b-177">決定的な式には、決定的な関数のみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-177">Only deterministic functions can participate in deterministic expressions.</span></span> <span data-ttu-id="cef9b-178">たとえば、DATEADD 関数は、3 つのパラメーターの任意の引数値セットに対して常に同じ結果を返すため、決定的であるといえます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-178">For example, the DATEADD function is deterministic because it always returns the same result for any given set of argument values for its three parameters.</span></span> <span data-ttu-id="cef9b-179">GETDATE は、常に同じ引数で起動されるにもかかわらず、返す値は実行のたびに変化するため、非決定的であるといえます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-179">GETDATE is not deterministic because it is always invoked with the same argument, but the value it returns changes each time it is executed.</span></span>  
  
 <span data-ttu-id="cef9b-180">ビュー列が決定的かどうかを判断するには、 **COLUMNPROPERTY** 関数の [IsDeterministic](/sql/t-sql/functions/columnproperty-transact-sql) プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-180">To determine whether a view column is deterministic, use the **IsDeterministic** property of the [COLUMNPROPERTY](/sql/t-sql/functions/columnproperty-transact-sql) function.</span></span> <span data-ttu-id="cef9b-181">スキーマ バインドを含むビューの決定的な列が正確であるかどうかを判断するには、COLUMNPROPERTY 関数の **IsPrecise** プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-181">To determine if a deterministic column in a view with schema binding is precise, use the **IsPrecise** property of the COLUMNPROPERTY function.</span></span> <span data-ttu-id="cef9b-182">COLUMNPROPERTY では、TRUE の場合は 1、FALSE の場合は 0、有効でない入力に対しては NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-182">COLUMNPROPERTY returns 1 if TRUE, 0 if FALSE, and NULL for input that is not valid.</span></span> <span data-ttu-id="cef9b-183">これは、列が決定的でないか、正確でないことを表します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-183">This means the column is not deterministic or not precise.</span></span>  
  
 <span data-ttu-id="cef9b-184">式が決定的でも、浮動小数点式が含まれる場合は、正確な結果はプロセッサのアーキテクチャまたはマイクロコードのバージョンによって異なる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-184">Even if an expression is deterministic, if it contains float expressions, the exact result may depend on the processor architecture or version of microcode.</span></span> <span data-ttu-id="cef9b-185">データの整合性を確保するため、このような式は、インデックス付きビューの非キー列としてのみ含めることができます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-185">To ensure data integrity, such expressions can participate only as non-key columns of indexed views.</span></span> <span data-ttu-id="cef9b-186">浮動小数点式を含まない決定的な式は、正確な式です。</span><span class="sxs-lookup"><span data-stu-id="cef9b-186">Deterministic expressions that do not contain float expressions are called precise.</span></span> <span data-ttu-id="cef9b-187">インデックス ビューのキー列と WHERE または GROUP BY 句には、正確で決定的な式だけを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-187">Only precise deterministic expressions can participate in key columns and in WHERE or GROUP BY clauses of indexed views.</span></span>  
  
### <a name="additional-requirements"></a><span data-ttu-id="cef9b-188">その他の要件</span><span class="sxs-lookup"><span data-stu-id="cef9b-188">Additional Requirements</span></span>  
 <span data-ttu-id="cef9b-189">SET オプションと決定的な関数の要件に加えて、次の要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-189">In addition to the SET options and deterministic function requirements, the following requirements must be met:</span></span>  
  
-   <span data-ttu-id="cef9b-190">CREATE INDEX を実行するユーザーが、ビューの所有者であること。</span><span class="sxs-lookup"><span data-stu-id="cef9b-190">The user that executes CREATE INDEX must be the owner of the view.</span></span>  
  
-   <span data-ttu-id="cef9b-191">インデックスを作成する場合は、IGNORE_DUP_KEY オプションを OFF に設定する必要があります (既定の設定)。</span><span class="sxs-lookup"><span data-stu-id="cef9b-191">When you create the index, the IGNORE_DUP_KEY option must be set to OFF (the default setting).</span></span>  
  
-   <span data-ttu-id="cef9b-192">ビュー定義では、 _schema_ **.** _tablename_ という 2 つの部分から構成される名前でテーブルが参照されていること。</span><span class="sxs-lookup"><span data-stu-id="cef9b-192">Tables must be referenced by two-part names, _schema_**.**_tablename_ in the view definition.</span></span>  
  
-   <span data-ttu-id="cef9b-193">ビューで参照されているユーザー定義関数が、WITH SCHEMABINDING オプションを使用して作成されていること。</span><span class="sxs-lookup"><span data-stu-id="cef9b-193">User-defined functions referenced in the view must be created by using the WITH SCHEMABINDING option.</span></span>  
  
-   <span data-ttu-id="cef9b-194">ビューで参照されるすべてのユーザー定義関数は、_スキーマ_という2つの部分で構成される名前で参照されている必要があり**ます。**_関数_。</span><span class="sxs-lookup"><span data-stu-id="cef9b-194">Any user-defined functions referenced in the view must be referenced by two-part names, _schema_**.**_function_.</span></span>  
  
-   <span data-ttu-id="cef9b-195">ユーザー定義関数のデータ アクセス プロパティが NO SQL に、外部アクセス プロパティが NO に設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-195">The data access property of a user-defined function must be NO SQL, and external access property must be NO.</span></span>  
  
-   <span data-ttu-id="cef9b-196">共通言語ランタイム (CLR) 関数をビューの選択リストに使用することはできますが、クラスター化インデックス キーの定義に含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="cef9b-196">Common language runtime (CLR) functions can appear in the select list of the view, but cannot be part of the definition of the clustered index key.</span></span> <span data-ttu-id="cef9b-197">CLR 関数は、ビューの WHERE 句や、ビューの JOIN 操作の ON 句では使用できません。</span><span class="sxs-lookup"><span data-stu-id="cef9b-197">CLR functions cannot appear in the WHERE clause of the view or the ON clause of a JOIN operation in the view.</span></span>  
  
-   <span data-ttu-id="cef9b-198">ビュー定義で使用する CLR ユーザー定義型の CLR 関数やメソッドは、次の表のようにプロパティが設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-198">CLR functions and methods of CLR user-defined types used in the view definition must have the properties set as shown in the following table.</span></span>  
  
    |<span data-ttu-id="cef9b-199">プロパティ</span><span class="sxs-lookup"><span data-stu-id="cef9b-199">Property</span></span>|<span data-ttu-id="cef9b-200">Note</span><span class="sxs-lookup"><span data-stu-id="cef9b-200">Note</span></span>|  
    |--------------|----------|  
    |<span data-ttu-id="cef9b-201">DETERMINISTIC = TRUE</span><span class="sxs-lookup"><span data-stu-id="cef9b-201">DETERMINISTIC = TRUE</span></span>|<span data-ttu-id="cef9b-202">Microsoft .NET Framework メソッドの属性として、明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-202">Must be declared explicitly as an attribute of the Microsoft .NET Framework method.</span></span>|  
    |<span data-ttu-id="cef9b-203">PRECISE = TRUE</span><span class="sxs-lookup"><span data-stu-id="cef9b-203">PRECISE = TRUE</span></span>|<span data-ttu-id="cef9b-204">.NET Framework メソッドの属性として、明示的に宣言する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-204">Must be declared explicitly as an attribute of the .NET Framework method.</span></span>|  
    |<span data-ttu-id="cef9b-205">DATA ACCESS = NO SQL</span><span class="sxs-lookup"><span data-stu-id="cef9b-205">DATA ACCESS = NO SQL</span></span>|<span data-ttu-id="cef9b-206">DataAccess 属性を DataAccessKind.None に、SystemDataAccess 属性を SystemDataAccessKind.None に設定することで決定されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-206">Determined by setting DataAccess attribute to DataAccessKind.None and SystemDataAccess attribute to SystemDataAccessKind.None.</span></span>|  
    |<span data-ttu-id="cef9b-207">EXTERNAL ACCESS = NO</span><span class="sxs-lookup"><span data-stu-id="cef9b-207">EXTERNAL ACCESS = NO</span></span>|<span data-ttu-id="cef9b-208">CLR ルーチンの場合は、このプロパティの既定値は NO です。</span><span class="sxs-lookup"><span data-stu-id="cef9b-208">This property defaults to NO for CLR routines.</span></span>|  
  
-   <span data-ttu-id="cef9b-209">ビューが、WITH SCHEMABINDING オプションを使って作成されていること。</span><span class="sxs-lookup"><span data-stu-id="cef9b-209">The view must be created by using the WITH SCHEMABINDING option.</span></span>  
  
-   <span data-ttu-id="cef9b-210">ビューが、ビューと同じデータベース内のベース テーブルのみを参照していること。</span><span class="sxs-lookup"><span data-stu-id="cef9b-210">The view must reference only base tables that are in the same database as the view.</span></span> <span data-ttu-id="cef9b-211">ビューでは、他のビューを参照できません。</span><span class="sxs-lookup"><span data-stu-id="cef9b-211">The view cannot reference other views.</span></span>  
  
-   <span data-ttu-id="cef9b-212">ビュー定義の SELECT ステートメントには、次の Transact-SQL 要素を使用できません。</span><span class="sxs-lookup"><span data-stu-id="cef9b-212">The SELECT statement in the view definition must not contain the following Transact-SQL elements:</span></span>  
  
    ||||  
    |-|-|-|  
    |<span data-ttu-id="cef9b-213">COUNT</span><span class="sxs-lookup"><span data-stu-id="cef9b-213">COUNT</span></span>|<span data-ttu-id="cef9b-214">行セット関数 (OPENDATASOURCE、OPENQUERY、OPENROWSET、および OPENXML)</span><span class="sxs-lookup"><span data-stu-id="cef9b-214">ROWSET functions (OPENDATASOURCE, OPENQUERY, OPENROWSET, AND OPENXML)</span></span>|<span data-ttu-id="cef9b-215">外部結合 (LEFT、RIGHT、または FULL)</span><span class="sxs-lookup"><span data-stu-id="cef9b-215">OUTER joins (LEFT, RIGHT, or FULL)</span></span>|  
    |<span data-ttu-id="cef9b-216">派生テーブル (FROM 句で SELECT ステートメントを指定することで定義される)</span><span class="sxs-lookup"><span data-stu-id="cef9b-216">Derived table (defined by specifying a SELECT statement in the FROM clause)</span></span>|<span data-ttu-id="cef9b-217">自己結合</span><span class="sxs-lookup"><span data-stu-id="cef9b-217">Self-joins</span></span>|<span data-ttu-id="cef9b-218">SELECT \* または SELECT *table_name*を使用して、列を指定します。\*</span><span class="sxs-lookup"><span data-stu-id="cef9b-218">Specifying columns by using SELECT \* or SELECT *table_name*.\*</span></span>|  
    |<span data-ttu-id="cef9b-219">DISTINCT</span><span class="sxs-lookup"><span data-stu-id="cef9b-219">DISTINCT</span></span>|<span data-ttu-id="cef9b-220">STDEV、STDEVP、VAR、VARP、または AVG</span><span class="sxs-lookup"><span data-stu-id="cef9b-220">STDEV, STDEVP, VAR, VARP, or AVG</span></span>|<span data-ttu-id="cef9b-221">共通テーブル式 (CTE)</span><span class="sxs-lookup"><span data-stu-id="cef9b-221">Common table expression (CTE)</span></span>|  
    |<span data-ttu-id="cef9b-222">`float`\*、 `text` 、 `ntext` 、 `image` 、 `XML` 、または `filestream` 列</span><span class="sxs-lookup"><span data-stu-id="cef9b-222">`float`\*, `text`, `ntext`, `image`, `XML`, or `filestream` columns</span></span>|<span data-ttu-id="cef9b-223">サブクエリ</span><span class="sxs-lookup"><span data-stu-id="cef9b-223">Subquery</span></span>|<span data-ttu-id="cef9b-224">順位付け関数または集計関数が含まれている OVER 句</span><span class="sxs-lookup"><span data-stu-id="cef9b-224">OVER clause, which includes ranking or aggregate window functions</span></span>|  
    |<span data-ttu-id="cef9b-225">フルテキスト述語 (CONTAIN、FREETEXT)</span><span class="sxs-lookup"><span data-stu-id="cef9b-225">Full-text predicates (CONTAIN, FREETEXT)</span></span>|<span data-ttu-id="cef9b-226">NULL 値を許容する式を参照する SUM 関数</span><span class="sxs-lookup"><span data-stu-id="cef9b-226">SUM function that references a nullable expression</span></span>|<span data-ttu-id="cef9b-227">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="cef9b-227">ORDER BY</span></span>|  
    |<span data-ttu-id="cef9b-228">CLR ユーザー定義集計関数</span><span class="sxs-lookup"><span data-stu-id="cef9b-228">CLR user-defined aggregate function</span></span>|<span data-ttu-id="cef9b-229">TOP</span><span class="sxs-lookup"><span data-stu-id="cef9b-229">TOP</span></span>|<span data-ttu-id="cef9b-230">CUBE、ROLLUP、または GROUPING SETS 演算子</span><span class="sxs-lookup"><span data-stu-id="cef9b-230">CUBE, ROLLUP, or GROUPING SETS operators</span></span>|  
    |<span data-ttu-id="cef9b-231">MIN、MAX</span><span class="sxs-lookup"><span data-stu-id="cef9b-231">MIN, MAX</span></span>|<span data-ttu-id="cef9b-232">UNION、EXCEPT、または INTERSECT 演算子。</span><span class="sxs-lookup"><span data-stu-id="cef9b-232">UNION, EXCEPT, or INTERSECT operators</span></span>|<span data-ttu-id="cef9b-233">TABLESAMPLE</span><span class="sxs-lookup"><span data-stu-id="cef9b-233">TABLESAMPLE</span></span>|  
    |<span data-ttu-id="cef9b-234">テーブル変数</span><span class="sxs-lookup"><span data-stu-id="cef9b-234">Table variables</span></span>|<span data-ttu-id="cef9b-235">OUTER APPLY または CROSS APPLY</span><span class="sxs-lookup"><span data-stu-id="cef9b-235">OUTER APPLY or CROSS APPLY</span></span>|<span data-ttu-id="cef9b-236">PIVOT、UNPIVOT</span><span class="sxs-lookup"><span data-stu-id="cef9b-236">PIVOT, UNPIVOT</span></span>|  
    |<span data-ttu-id="cef9b-237">スパース列セット</span><span class="sxs-lookup"><span data-stu-id="cef9b-237">Sparse column sets</span></span>|<span data-ttu-id="cef9b-238">インラインまたは複数ステートメントのテーブル値関数</span><span class="sxs-lookup"><span data-stu-id="cef9b-238">Inline or multi-statement table-valued functions</span></span>|<span data-ttu-id="cef9b-239">OFFSET</span><span class="sxs-lookup"><span data-stu-id="cef9b-239">OFFSET</span></span>|  
    |<span data-ttu-id="cef9b-240">CHECKSUM_AGG</span><span class="sxs-lookup"><span data-stu-id="cef9b-240">CHECKSUM_AGG</span></span>|||  
  
     <span data-ttu-id="cef9b-241">\*インデックス付きビューには列を含めることができますが `float` 、このような列をクラスター化インデックスキーに含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="cef9b-241">\*The indexed view can contain `float` columns; however, such columns cannot be included in the clustered index key.</span></span>  
  
-   <span data-ttu-id="cef9b-242">GROUP BY が存在する場合、VIEW 定義には COUNT_BIG(\*) を含める必要があります。HAVING を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="cef9b-242">If GROUP BY is present, the VIEW definition must contain COUNT_BIG(\*) and must not contain HAVING.</span></span> <span data-ttu-id="cef9b-243">このような GROUP BY 制限は、インデックス付きビュー定義にのみ適用されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-243">These GROUP BY restrictions are applicable only to the indexed view definition.</span></span> <span data-ttu-id="cef9b-244">クエリがこの GROUP BY 制限を満たしていない場合でも、実行プランでインデックス付きビューを使用することはできます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-244">A query can use an indexed view in its execution plan even if it does not satisfy these GROUP BY restrictions.</span></span>  
  
-   <span data-ttu-id="cef9b-245">ビュー定義に GROUP BY 句を指定した場合、一意のクラスター化インデックスのキーでは、GROUP BY 句で指定した列のみを参照できること。</span><span class="sxs-lookup"><span data-stu-id="cef9b-245">If the view definition contains a GROUP BY clause, the key of the unique clustered index can reference only the columns specified in the GROUP BY clause.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="cef9b-246">推奨事項</span><span class="sxs-lookup"><span data-stu-id="cef9b-246">Recommendations</span></span>  
 <span data-ttu-id="cef9b-247">インデックス付きビューで `datetime` 文字リテラルと `smalldatetime` 文字列リテラルを参照するときは、決定的な日付形式スタイルを使用して、そのリテラルを目的の日付型に明示的に変換することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cef9b-247">When you refer to `datetime` and `smalldatetime` string literals in indexed views, we recommend that you explicitly convert the literal to the date type you want by using a deterministic date format style.</span></span> <span data-ttu-id="cef9b-248">決定的な日付形式の一覧については、「[CAST および CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cef9b-248">For a list of the date format styles that are deterministic, see [CAST and CONVERT &#40;Transact-SQL&#41;](/sql/t-sql/functions/cast-and-convert-transact-sql).</span></span> <span data-ttu-id="cef9b-249">`datetime` 型または `smalldatetime` 型への文字列の暗黙的な変換が必要な式は非決定的であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-249">Expressions that involve implicit conversion of character strings to `datetime` or `smalldatetime` are considered nondeterministic.</span></span> <span data-ttu-id="cef9b-250">これは、サーバー セッションの LANGUAGE および DATEFORMAT の設定によって結果が異なるためです。</span><span class="sxs-lookup"><span data-stu-id="cef9b-250">This is because the results depend on the LANGUAGE and DATEFORMAT settings of the server session.</span></span> <span data-ttu-id="cef9b-251">たとえば、式 `CONVERT (datetime, '30 listopad 1996', 113)` では、言語が異なると文字列 '`listopad`' が異なる月を意味するので、結果が LANGUAGE の設定によって異なります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-251">For example, the results of the expression `CONVERT (datetime, '30 listopad 1996', 113)` depend on the LANGUAGE setting because the string '`listopad`' means different months in different languages.</span></span> <span data-ttu-id="cef9b-252">同様に、式 `DATEADD(mm,3,'2000-12-01')`の場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では DATEFORMAT の設定に基づいて、文字列 `'2000-12-01'` が解釈されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-252">Similarly, in the expression `DATEADD(mm,3,'2000-12-01')`, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] interprets the string `'2000-12-01'` based on the DATEFORMAT setting.</span></span>  
  
 <span data-ttu-id="cef9b-253">照合順序間で行われる Unicode 以外の文字データの暗黙的な変換も非決定的であると見なされます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-253">Implicit conversion of non-Unicode character data between collations is also considered nondeterministic.</span></span>  
  
###  <a name="considerations"></a><a name="Considerations"></a> <span data-ttu-id="cef9b-254">考慮事項</span><span class="sxs-lookup"><span data-stu-id="cef9b-254">Considerations</span></span>  
 <span data-ttu-id="cef9b-255">インデックス付きビューの列の **large_value_types_out_of_row** オプションの設定は、ベース テーブルの対応する列の設定が継承されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-255">The setting of the **large_value_types_out_of_row** option of columns in an indexed view is inherited from the setting of the corresponding column in the base table.</span></span> <span data-ttu-id="cef9b-256">この値は、 [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql)を使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-256">This value is set by using [sp_tableoption](/sql/relational-databases/system-stored-procedures/sp-tableoption-transact-sql).</span></span> <span data-ttu-id="cef9b-257">式から形成される列に対する既定の設定は 0 です。</span><span class="sxs-lookup"><span data-stu-id="cef9b-257">The default setting for columns formed from expressions is 0.</span></span> <span data-ttu-id="cef9b-258">つまり、大きい値の型は行内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-258">This means that large value types are stored in-row.</span></span>  
  
 <span data-ttu-id="cef9b-259">インデックス付きビューはパーティション分割されたテーブルに作成でき、インデックス付きビュー自体をパーティション分割できます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-259">Indexed views can be created on a partitioned table, and can themselves be partitioned.</span></span>  
  
 <span data-ttu-id="cef9b-260">[!INCLUDE[ssDE](../../includes/ssde-md.md)] でインデックス付きビューが使用されないようにするには、クエリに OPTION (EXPAND VIEWS) ヒントを含めます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-260">To prevent the [!INCLUDE[ssDE](../../includes/ssde-md.md)] from using indexed views, include the OPTION (EXPAND VIEWS) hint on the query.</span></span> <span data-ttu-id="cef9b-261">これによって、オプションの 1 つが正しく設定されていない場合、オプティマイザーもビューのインデックスを使用できません。</span><span class="sxs-lookup"><span data-stu-id="cef9b-261">Also, if any of the listed options are incorrectly set, this will prevent the optimizer from using the indexes on the views.</span></span> <span data-ttu-id="cef9b-262">OPTION (EXPAND VIEWS) ヒントの詳細については、「[SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cef9b-262">For more information about the OPTION (EXPAND VIEWS) hint, see [SELECT &#40;Transact-SQL&#41;](/sql/t-sql/queries/select-transact-sql).</span></span>  
  
 <span data-ttu-id="cef9b-263">ビューが削除されると、ビューのすべてのインデックスも削除されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-263">All indexes on a view are dropped when the view is dropped.</span></span> <span data-ttu-id="cef9b-264">クラスター化インデックスが削除されると、ビューのすべての非クラスター化インデックスと自動的に作成された統計も削除されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-264">All nonclustered indexes and auto-created statistics on the view are dropped when the clustered index is dropped.</span></span> <span data-ttu-id="cef9b-265">ユーザーが作成したビューの統計は、保持されます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-265">User-created statistics on the view are maintained.</span></span> <span data-ttu-id="cef9b-266">非クラスター化インデックスは、個別に削除できます。</span><span class="sxs-lookup"><span data-stu-id="cef9b-266">Nonclustered indexes can be individually dropped.</span></span> <span data-ttu-id="cef9b-267">ビュー上のクラスター化インデックスを削除すると、格納された結果セットも削除され、オプティマイザーは、ビューの処理を標準的なビューと同様の処理に戻します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-267">Dropping the clustered index on the view removes the stored result set, and the optimizer returns to processing the view like a standard view.</span></span>  
  
 <span data-ttu-id="cef9b-268">テーブルとビューのインデックスは無効にされる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-268">Indexes on tables and views can be disabled.</span></span> <span data-ttu-id="cef9b-269">テーブルのクラスター化インデックスが無効になると、そのテーブルに関連するビューのインデックスも無効になります。</span><span class="sxs-lookup"><span data-stu-id="cef9b-269">When a clustered index on a table is disabled, indexes on views associated with the table are also disabled.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="cef9b-270">セキュリティ</span><span class="sxs-lookup"><span data-stu-id="cef9b-270">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="cef9b-271">Permissions</span><span class="sxs-lookup"><span data-stu-id="cef9b-271">Permissions</span></span>  
 <span data-ttu-id="cef9b-272">データベースの CREATE VIEW 権限と、ビューが作成されているスキーマの ALTER 権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="cef9b-272">Requires CREATE VIEW permission in the database and ALTER permission on the schema in which the view is being created.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="cef9b-273">Transact-SQL の使用</span><span class="sxs-lookup"><span data-stu-id="cef9b-273">Using Transact-SQL</span></span>  
  
#### <a name="to-create-an-indexed-view"></a><span data-ttu-id="cef9b-274">インデックス付きビューを作成するには</span><span class="sxs-lookup"><span data-stu-id="cef9b-274">To create an indexed view</span></span>  
  
1.  <span data-ttu-id="cef9b-275">**オブジェクト エクスプローラー**で、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-275">In **Object Explorer**, connect to an instance of [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="cef9b-276">[標準] ツール バーの **[新しいクエリ]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cef9b-276">On the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="cef9b-277">次の例をコピーしてクエリ ウィンドウに貼り付け、 **[実行]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="cef9b-277">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="cef9b-278">この例では、ビューとそのビューのインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-278">The example creates a view and an index on that view.</span></span> <span data-ttu-id="cef9b-279">ここでは、インデックス付きビューを使用する 2 つのクエリを実行します。</span><span class="sxs-lookup"><span data-stu-id="cef9b-279">Two queries are included that use the indexed view.</span></span>  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    --Set the options to support indexed views.  
    SET NUMERIC_ROUNDABORT OFF;  
    SET ANSI_PADDING, ANSI_WARNINGS, CONCAT_NULL_YIELDS_NULL, ARITHABORT,  
        QUOTED_IDENTIFIER, ANSI_NULLS ON;  
    GO  
    --Create view with schemabinding.  
    IF OBJECT_ID ('Sales.vOrders', 'view') IS NOT NULL  
    DROP VIEW Sales.vOrders ;  
    GO  
    CREATE VIEW Sales.vOrders  
    WITH SCHEMABINDING  
    AS  
        SELECT SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Revenue,  
            OrderDate, ProductID, COUNT_BIG(*) AS COUNT  
        FROM Sales.SalesOrderDetail AS od, Sales.SalesOrderHeader AS o  
        WHERE od.SalesOrderID = o.SalesOrderID  
        GROUP BY OrderDate, ProductID;  
    GO  
    --Create an index on the view.  
    CREATE UNIQUE CLUSTERED INDEX IDX_V1   
        ON Sales.vOrders (OrderDate, ProductID);  
    GO  
    --This query can use the indexed view even though the view is   
    --not specified in the FROM clause.  
    SELECT SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Rev,   
        OrderDate, ProductID  
    FROM Sales.SalesOrderDetail AS od  
        JOIN Sales.SalesOrderHeader AS o ON od.SalesOrderID=o.SalesOrderID  
            AND ProductID BETWEEN 700 and 800  
            AND OrderDate >= CONVERT(datetime,'05/01/2002',101)  
    GROUP BY OrderDate, ProductID  
    ORDER BY Rev DESC;  
    GO  
    --This query can use the above indexed view.  
    SELECT  OrderDate, SUM(UnitPrice*OrderQty*(1.00-UnitPriceDiscount)) AS Rev  
    FROM Sales.SalesOrderDetail AS od  
        JOIN Sales.SalesOrderHeader AS o ON od.SalesOrderID=o.SalesOrderID  
            AND DATEPART(mm,OrderDate)= 3  
            AND DATEPART(yy,OrderDate) = 2002  
    GROUP BY OrderDate  
    ORDER BY OrderDate ASC;  
    GO  
    ```  
  
 <span data-ttu-id="cef9b-280">詳細については、「[CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cef9b-280">For more information, see [CREATE VIEW &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-view-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cef9b-281">参照</span><span class="sxs-lookup"><span data-stu-id="cef9b-281">See Also</span></span>  
 <span data-ttu-id="cef9b-282">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cef9b-282">[CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql) </span></span>  
 <span data-ttu-id="cef9b-283">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cef9b-283">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="cef9b-284">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cef9b-284">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 <span data-ttu-id="cef9b-285">[SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cef9b-285">[SET ANSI_WARNINGS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-warnings-transact-sql) </span></span>  
 <span data-ttu-id="cef9b-286">[SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cef9b-286">[SET ARITHABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-arithabort-transact-sql) </span></span>  
 <span data-ttu-id="cef9b-287">[SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cef9b-287">[SET CONCAT_NULL_YIELDS_NULL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-concat-null-yields-null-transact-sql) </span></span>  
 <span data-ttu-id="cef9b-288">[SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="cef9b-288">[SET NUMERIC_ROUNDABORT &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-numeric-roundabort-transact-sql) </span></span>  
 [<span data-ttu-id="cef9b-289">SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cef9b-289">SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-quoted-identifier-transact-sql)  
  
  
