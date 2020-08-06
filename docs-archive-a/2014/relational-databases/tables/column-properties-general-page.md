---
title: '[列のプロパティ] ([全般] ページ) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.columnproperties.general.f1
ms.assetid: a745890b-994e-4c23-8028-5c83751e60c4
author: stevestein
ms.author: sstein
ms.openlocfilehash: 29a82df217eef719b4f0efffb3fc0c24b36a27aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87646107"
---
# <a name="column-properties-general-page"></a><span data-ttu-id="28a63-102">[列のプロパティ] ([全般] ページ)</span><span class="sxs-lookup"><span data-stu-id="28a63-102">Column Properties (General Page)</span></span>
  <span data-ttu-id="28a63-103">このページを使用すると、選択されている列のプロパティを表示できます。</span><span class="sxs-lookup"><span data-stu-id="28a63-103">Use this page to view properties for the selected column.</span></span>  
  
 <span data-ttu-id="28a63-104">このページの情報は読み取り専用です。</span><span class="sxs-lookup"><span data-stu-id="28a63-104">Information on this page is read-only.</span></span> <span data-ttu-id="28a63-105">列を変更するには、 **[列のプロパティ]** ダイアログ ボックスを閉じて、オブジェクト エクスプローラーでそのテーブルを展開して [列] を展開します。次に、列を右クリックして、 **[デザイン]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="28a63-105">To modify the column, close the **Column Properties** dialog box, expand the table and columns in Object Explorer, right-click the column, and then click **Design**.</span></span>  
  
## <a name="options"></a><span data-ttu-id="28a63-106">オプション</span><span class="sxs-lookup"><span data-stu-id="28a63-106">Options</span></span>  
 <span data-ttu-id="28a63-107">**Name**</span><span class="sxs-lookup"><span data-stu-id="28a63-107">**Name**</span></span>  
 <span data-ttu-id="28a63-108">列の名前です。</span><span class="sxs-lookup"><span data-stu-id="28a63-108">The name of the column.</span></span>  
  
 <span data-ttu-id="28a63-109">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="28a63-109">**Data Type**</span></span>  
 <span data-ttu-id="28a63-110">列が保持できるデータ型です。</span><span class="sxs-lookup"><span data-stu-id="28a63-110">The type of data that the column can hold.</span></span> <span data-ttu-id="28a63-111">データ型がユーザー定義データ型である場合は、ユーザー定義データ型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="28a63-111">If the data type is a user-defined data type, the user-defined data type is displayed.</span></span> <span data-ttu-id="28a63-112">データ型がユーザー定義データ型でない場合は、システム データ型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="28a63-112">If the data type is not a user-defined data type, then the system data type is displayed.</span></span> <span data-ttu-id="28a63-113">詳細については、「[データ型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a63-113">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
 <span data-ttu-id="28a63-114">**[システム型]**</span><span class="sxs-lookup"><span data-stu-id="28a63-114">**System Type**</span></span>  
 <span data-ttu-id="28a63-115">列が保持できるデータ型です。</span><span class="sxs-lookup"><span data-stu-id="28a63-115">The type of data that the column can hold.</span></span> <span data-ttu-id="28a63-116">データ型がシステム データ型である場合は、システム データ型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="28a63-116">If the data type is a system data type, then the system data type is displayed.</span></span> <span data-ttu-id="28a63-117">データ型がユーザー定義型である場合は、ユーザー定義データ型を形成するシステム データ型が表示されます。</span><span class="sxs-lookup"><span data-stu-id="28a63-117">If the data type is a user-defined data type, the system data type that makes up the user-defined data type is displayed.</span></span>  
  
 <span data-ttu-id="28a63-118">**主キー**</span><span class="sxs-lookup"><span data-stu-id="28a63-118">**Primary Key**</span></span>  
 <span data-ttu-id="28a63-119">列が主キーであるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-119">Indicates whether the column is a primary key.</span></span> <span data-ttu-id="28a63-120">指定できる値は、 **[True]** および **[False]** です。</span><span class="sxs-lookup"><span data-stu-id="28a63-120">Possible values are **True**and **False**.</span></span>  
  
 <span data-ttu-id="28a63-121">**[NULL を許容]**</span><span class="sxs-lookup"><span data-stu-id="28a63-121">**Allow Nulls**</span></span>  
 <span data-ttu-id="28a63-122">列が NULL 値を許容するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-122">Indicates whether the column accepts null values.</span></span> <span data-ttu-id="28a63-123">指定できる値は、 **[True]** および **[False]** です。</span><span class="sxs-lookup"><span data-stu-id="28a63-123">Possible values are **True** and **False**.</span></span>  
  
 <span data-ttu-id="28a63-124">**[計算値]**</span><span class="sxs-lookup"><span data-stu-id="28a63-124">**Is Computed**</span></span>  
 <span data-ttu-id="28a63-125">列の値が、計算された式の結果であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-125">Indicates whether the column value is the result of a computed expression.</span></span>  
  
 <span data-ttu-id="28a63-126">**[計算されたテキスト]**</span><span class="sxs-lookup"><span data-stu-id="28a63-126">**Computed text**</span></span>  
 <span data-ttu-id="28a63-127">列テキストの計算に使用されたステートメントを示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-127">Indicates the statement used to compute the column text.</span></span> <span data-ttu-id="28a63-128">詳細については、「 [テーブルの計算列の指定](specify-computed-columns-in-a-table.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a63-128">For more information, [Specify Computed Columns in a Table](specify-computed-columns-in-a-table.md).</span></span>  
  
 <span data-ttu-id="28a63-129">**[ID]**</span><span class="sxs-lookup"><span data-stu-id="28a63-129">**Identity**</span></span>  
 <span data-ttu-id="28a63-130">列がテーブルの ID 列であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-130">Indicates whether the column is the identity column for the table.</span></span> <span data-ttu-id="28a63-131">指定できる値は、 **[True]** および **[False]** です。</span><span class="sxs-lookup"><span data-stu-id="28a63-131">Possible values are **True** and **False**.</span></span>  
  
 <span data-ttu-id="28a63-132">**[IDENTITY シード]**</span><span class="sxs-lookup"><span data-stu-id="28a63-132">**Identity Seed**</span></span>  
 <span data-ttu-id="28a63-133">ID 列の最初の行の値を示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-133">Indicates the initial row value for an identity column.</span></span>  
  
 <span data-ttu-id="28a63-134">**[IDENTITY インクリメント]**</span><span class="sxs-lookup"><span data-stu-id="28a63-134">**Identity Increment**</span></span>  
 <span data-ttu-id="28a63-135">**[ID の増分値]** プロパティは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で挿入される行の ID 値が生成されるときに、既存の行の最大 ID 値に追加される値を指定します。</span><span class="sxs-lookup"><span data-stu-id="28a63-135">The **Identity Increment** property specifies the value [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] adds to the greatest existing row identity value as it generates an identity value for a row being inserted.</span></span>  
  
 <span data-ttu-id="28a63-136">**[既定のバインド]**</span><span class="sxs-lookup"><span data-stu-id="28a63-136">**Default Binding**</span></span>  
 <span data-ttu-id="28a63-137">列にバインドされた [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の既定値です。</span><span class="sxs-lookup"><span data-stu-id="28a63-137">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] default bound to the column.</span></span> <span data-ttu-id="28a63-138">既定値がバインドされていない場合、このオプションは空白になります。</span><span class="sxs-lookup"><span data-stu-id="28a63-138">This option is blank if no default is bound.</span></span>  
  
 <span data-ttu-id="28a63-139">**[既定のスキーマ]**</span><span class="sxs-lookup"><span data-stu-id="28a63-139">**Default Schema**</span></span>  
 <span data-ttu-id="28a63-140">参照される列にバインドされた既定値を所有するデータベース スキーマを識別します。</span><span class="sxs-lookup"><span data-stu-id="28a63-140">Identifies the database schema owning the default bound to the referenced column.</span></span> <span data-ttu-id="28a63-141">既定値がバインドされていない場合、このオプションは空白になります。</span><span class="sxs-lookup"><span data-stu-id="28a63-141">This option is blank if no default is bound.</span></span>  
  
 <span data-ttu-id="28a63-142">**Rule**</span><span class="sxs-lookup"><span data-stu-id="28a63-142">**Rule**</span></span>  
 <span data-ttu-id="28a63-143">列にバインドされたデータ整合性制約を識別します。</span><span class="sxs-lookup"><span data-stu-id="28a63-143">Identifies the data integrity constraint that is bound to the column.</span></span> <span data-ttu-id="28a63-144">ルールがバインドされていない場合、このオプションは空白になります。</span><span class="sxs-lookup"><span data-stu-id="28a63-144">This option is blank if no rule is bound.</span></span>  
  
 <span data-ttu-id="28a63-145">**[ルール スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="28a63-145">**Rule Schema**</span></span>  
 <span data-ttu-id="28a63-146">参照される列にバインドされたルールを所有する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベース スキーマを表示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-146">Displays the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database schema that owns the rule bound to the referenced column.</span></span> <span data-ttu-id="28a63-147">ルールがバインドされていない場合、このオプションは空白になります。</span><span class="sxs-lookup"><span data-stu-id="28a63-147">This option is blank if no rule is bound.</span></span>  
  
 <span data-ttu-id="28a63-148">**[データ型]**</span><span class="sxs-lookup"><span data-stu-id="28a63-148">**Length**</span></span>  
 <span data-ttu-id="28a63-149">列によって許容される文字またはバイトの最大数を示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-149">Indicates the maximum number of characters or bytes accepted by the column.</span></span>  
  
 <span data-ttu-id="28a63-150">**Collation**</span><span class="sxs-lookup"><span data-stu-id="28a63-150">**Collation**</span></span>  
 <span data-ttu-id="28a63-151">列の現在の照合順序を表示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-151">Displays the current collation for the column.</span></span> <span data-ttu-id="28a63-152">空白の場合、照合順序プロパティはオブジェクトから継承されます。</span><span class="sxs-lookup"><span data-stu-id="28a63-152">If blank, the collation property is inherited from the object.</span></span>  
  
 <span data-ttu-id="28a63-153">**[数値有効桁数]**</span><span class="sxs-lookup"><span data-stu-id="28a63-153">**Numeric Precision**</span></span>  
 <span data-ttu-id="28a63-154">固定精度の数値データ型における最大桁数を示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-154">Indicates the maximum number of digits in a fixed-precision, numeric data type.</span></span>  
  
 <span data-ttu-id="28a63-155">**[数値の小数点以下桁数]**</span><span class="sxs-lookup"><span data-stu-id="28a63-155">**Numeric Scale**</span></span>  
 <span data-ttu-id="28a63-156">固定精度の数値データ型における小数点以下桁数を示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-156">Indicates the number of digits to the right of the decimal point in a fixed-precision, numeric data type.</span></span>  
  
 <span data-ttu-id="28a63-157">**[XML スキーマ名前空間]**</span><span class="sxs-lookup"><span data-stu-id="28a63-157">**XML Schema Namespace**</span></span>  
 <span data-ttu-id="28a63-158">XML Schema Definition Language (XSD) 検証で XML 列の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="28a63-158">Defines the type of the XML column by way of XML Schema Definition (XSD) Language validation.</span></span>  
  
 <span data-ttu-id="28a63-159">**[XML スキーマ名前空間スキーマ]**</span><span class="sxs-lookup"><span data-stu-id="28a63-159">**XML Schema Namespace schema**</span></span>  
 <span data-ttu-id="28a63-160">XML スキーマ名前空間を所有する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] スキーマです。</span><span class="sxs-lookup"><span data-stu-id="28a63-160">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] schema that owns the XML Schema Namespace.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="28a63-161">一般にスキーマという語にはいくつかの異なる意味があります。</span><span class="sxs-lookup"><span data-stu-id="28a63-161">There are several common but different meanings of the word schema.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="28a63-162">では、データベース オブジェクトを編成する場合にスキーマを使用します。</span><span class="sxs-lookup"><span data-stu-id="28a63-162">uses schema to organize database objects.</span></span> <span data-ttu-id="28a63-163">これは所有権に似ています。</span><span class="sxs-lookup"><span data-stu-id="28a63-163">It is similar to ownership.</span></span> <span data-ttu-id="28a63-164">XML は、スキーマを使用して XML 情報の編成を一連の名前空間に定義します。</span><span class="sxs-lookup"><span data-stu-id="28a63-164">XML uses the schema to define the organization of XML information into a series of namespaces.</span></span> <span data-ttu-id="28a63-165">このスキーマは、XML コードをまとめてグループ化する方法です。</span><span class="sxs-lookup"><span data-stu-id="28a63-165">It is a way to group related XML code together.</span></span>  
  
 <span data-ttu-id="28a63-166">**[スパース]**</span><span class="sxs-lookup"><span data-stu-id="28a63-166">**Is Sparse**</span></span>  
 <span data-ttu-id="28a63-167">列がスパース列であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-167">Indicates whether the column is a sparse column.</span></span> <span data-ttu-id="28a63-168">指定できる値は、 **[True]** および **[False]** です。</span><span class="sxs-lookup"><span data-stu-id="28a63-168">Possible values are **True** and **False**.</span></span> <span data-ttu-id="28a63-169">詳細については、「 [スパース列の使用](use-sparse-columns.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a63-169">For more information, see [Use Sparse Columns](use-sparse-columns.md).</span></span>  
  
 <span data-ttu-id="28a63-170">**[列セット]**</span><span class="sxs-lookup"><span data-stu-id="28a63-170">**Is Column Set**</span></span>  
 <span data-ttu-id="28a63-171">列が列セットであるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-171">Indicates whether the column is a column set.</span></span> <span data-ttu-id="28a63-172">指定できる値は、 **[True]** および **[False]** です。</span><span class="sxs-lookup"><span data-stu-id="28a63-172">Possible values are **True** and **False**.</span></span> <span data-ttu-id="28a63-173">詳細については、「 [列セットの使用](use-column-sets.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a63-173">For more information, see [Use Column Sets](use-column-sets.md).</span></span>  
  
 <span data-ttu-id="28a63-174">**[ANSI PADDING の状態]**</span><span class="sxs-lookup"><span data-stu-id="28a63-174">**ANSI Padding Status**</span></span>  
 <span data-ttu-id="28a63-175">ANSI PADDING が有効かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-175">Indicates whether ANSI padding is on or off.</span></span> <span data-ttu-id="28a63-176">詳細については、「[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a63-176">For more information, see [SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql).</span></span>  
  
 <span data-ttu-id="28a63-177">**[フルテキスト]**</span><span class="sxs-lookup"><span data-stu-id="28a63-177">**Full Text**</span></span>  
 <span data-ttu-id="28a63-178">列がフルテキスト クエリに参加するかどうかを表示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-178">Displays whether the column participates in full-text queries.</span></span>  
  
 <span data-ttu-id="28a63-179">**[統計的セマンティクス]**</span><span class="sxs-lookup"><span data-stu-id="28a63-179">**Statistical Semantics**</span></span>  
 <span data-ttu-id="28a63-180">列に対する統計的セマンティック検索を有効にするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-180">Indicates whether statistical semantic search is enabled for the column.</span></span> <span data-ttu-id="28a63-181">詳細については、「[セマンティック検索 &#40;SQL Server&#41;](../search/semantic-search-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28a63-181">For more information, see [Semantic Search &#40;SQL Server&#41;](../search/semantic-search-sql-server.md).</span></span>  
  
 <span data-ttu-id="28a63-182">**[レプリケーションでは使用しない]**</span><span class="sxs-lookup"><span data-stu-id="28a63-182">**Not For Replication**</span></span>  
 <span data-ttu-id="28a63-183">列をレプリケーションに使用できるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="28a63-183">Indicates whether the column is available for replication.</span></span> <span data-ttu-id="28a63-184">指定できる値は、 **[True]** および **[False]** です。</span><span class="sxs-lookup"><span data-stu-id="28a63-184">Possible values are **True** and **False**.</span></span>  
  
  
