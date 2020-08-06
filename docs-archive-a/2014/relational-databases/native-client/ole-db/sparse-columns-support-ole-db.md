---
title: スパース列のサポート (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: 918574b3-c62e-4937-9e5f-37310dedc8f9
author: rothja
ms.author: jroth
ms.openlocfilehash: 2d40964b3c433b35b5ab9af2637389a022cc3961
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633106"
---
# <a name="sparse-columns-support-ole-db"></a><span data-ttu-id="27399-102">スパース列のサポート (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="27399-102">Sparse Columns Support (OLE DB)</span></span>
  <span data-ttu-id="27399-103">このトピックでは、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB でのスパース列のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="27399-103">This topic provides information about [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB support for sparse columns.</span></span> <span data-ttu-id="27399-104">スパース列の詳細については、「 [SQL Server Native Client でのスパース列のサポート](../features/sparse-columns-support-in-sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27399-104">For more information about sparse columns, see [Sparse Columns Support in SQL Server Native Client](../features/sparse-columns-support-in-sql-server-native-client.md).</span></span> <span data-ttu-id="27399-105">サンプルについては、「[スパース列に対する列およびカタログ メタデータの表示 &#40;OLE DB&#41;](../../native-client-ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27399-105">For a sample, see [Display Column and Catalog Metadata for Sparse Columns &#40;OLE DB&#41;](../../native-client-ole-db-how-to/display-column-and-catalog-metadata-for-sparse-columns-ole-db.md).</span></span>  
  
## <a name="ole-db-statement-metadata"></a><span data-ttu-id="27399-106">OLE DB ステートメント メタデータ</span><span class="sxs-lookup"><span data-stu-id="27399-106">OLE DB Statement Metadata</span></span>  
 <span data-ttu-id="27399-107">[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 以降では、新しい DBCOLUMNFLAGS フラグ値である DBCOLUMNFLAGS_SS_ISCOLUMNSET を使用できます。</span><span class="sxs-lookup"><span data-stu-id="27399-107">Beginning with [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)], a new DBCOLUMNFLAGS flag value, DBCOLUMNFLAGS_SS_ISCOLUMNSET, is available.</span></span> <span data-ttu-id="27399-108">この値は、`column_set` 値である列に対して設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27399-108">This value should be set for columns that are `column_set` values.</span></span> <span data-ttu-id="27399-109">DBCOLUMNFLAGS フラグは、IColumnsInfo::GetColumnsInfo の *dwFlags* パラメーターと、IColumnsRowset::GetColumnsRowset から返される行セットの DBCOLUMN_FLAGS 列を使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="27399-109">The DBCOLUMNFLAGS flag can be retrieved through the *dwFlags* parameter of IColumnsInfo::GetColumnsInfo and the DBCOLUMN_FLAGS column of the rowset returned by IColumnsRowset::GetColumnsRowset.</span></span>  
  
## <a name="ole-db-catalog-metadata"></a><span data-ttu-id="27399-110">OLE DB カタログ メタデータ</span><span class="sxs-lookup"><span data-stu-id="27399-110">OLE DB Catalog Metadata</span></span>  
 <span data-ttu-id="27399-111">DBSCHEMA_COLUMNS に、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 固有の列が 2 つ追加されています。</span><span class="sxs-lookup"><span data-stu-id="27399-111">Two additional [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-specific columns have been added to DBSCHEMA_COLUMNS.</span></span>  
  
|<span data-ttu-id="27399-112">列名</span><span class="sxs-lookup"><span data-stu-id="27399-112">Column name</span></span>|<span data-ttu-id="27399-113">データ型</span><span class="sxs-lookup"><span data-stu-id="27399-113">Data type</span></span>|<span data-ttu-id="27399-114">値およびコメント</span><span class="sxs-lookup"><span data-stu-id="27399-114">Value/comments</span></span>|  
|-----------------|---------------|---------------------|  
|<span data-ttu-id="27399-115">SS_IS_SPARSE</span><span class="sxs-lookup"><span data-stu-id="27399-115">SS_IS_SPARSE</span></span>|<span data-ttu-id="27399-116">DBTYPE_BOOL</span><span class="sxs-lookup"><span data-stu-id="27399-116">DBTYPE_BOOL</span></span>|<span data-ttu-id="27399-117">列がスパース列の場合は VARIANT_TRUE、それ以外の場合は VARIANT_FALSE になります。</span><span class="sxs-lookup"><span data-stu-id="27399-117">If the column is a sparse column, this has the value VARIANT_TRUE; otherwise, VARIANT_FALSE.</span></span>|  
|<span data-ttu-id="27399-118">SS_IS_COLUMN_SET</span><span class="sxs-lookup"><span data-stu-id="27399-118">SS_IS_COLUMN_SET</span></span>|<span data-ttu-id="27399-119">DBTYPE_BOOL</span><span class="sxs-lookup"><span data-stu-id="27399-119">DBTYPE_BOOL</span></span>|<span data-ttu-id="27399-120">列がスパース `column_set` 列の場合は VARIANT_TRUE、それ以外の場合は VARIANT_FALSE になります。</span><span class="sxs-lookup"><span data-stu-id="27399-120">If the column is the sparse `column_set` column, this has the value VARIANT_TRUE; otherwise, VARIANT_FALSE.</span></span>|  
  
 <span data-ttu-id="27399-121">また、2 つのスキーマ行セットが追加されています。</span><span class="sxs-lookup"><span data-stu-id="27399-121">Two additional schema rowsets have also been added.</span></span> <span data-ttu-id="27399-122">これらの行セットは、構造は DBSCHEMA_COLUMNS と同じですが、返される内容が異なります。</span><span class="sxs-lookup"><span data-stu-id="27399-122">These rowsets have the same structure as DBSCHEMA_COLUMNS but return different content.</span></span> <span data-ttu-id="27399-123">DBSCHEMA_COLUMNS_EXTENDED は、スパース列かどうか、`column_set` のメンバーかどうかに関係なく、すべての列を返します。</span><span class="sxs-lookup"><span data-stu-id="27399-123">DBSCHEMA_COLUMNS_EXTENDED returns all columns regardless of `column_set` membership.</span></span> <span data-ttu-id="27399-124">DBSCHEMA_SPARSE_COLUMN_SET は、スパース `column_set` のメンバーである列のみを返します。</span><span class="sxs-lookup"><span data-stu-id="27399-124">DBSCHEMA_SPARSE_COLUMN_SET returns only columns that are members of the sparse `column_set`.</span></span>  
  
## <a name="ole-db-datatypecompatibility-behavior"></a><span data-ttu-id="27399-125">OLE DB DataTypeCompatibility の動作</span><span class="sxs-lookup"><span data-stu-id="27399-125">OLE DB DataTypeCompatibility Behavior</span></span>  
 <span data-ttu-id="27399-126">`DataTypeCompatibility=80` の (接続文字列内での) 動作は、次のように、[!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] クライアントと変わりません。</span><span class="sxs-lookup"><span data-stu-id="27399-126">Behavior with `DataTypeCompatibility=80` (in the connection string) is consistent with a [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] client, as follows:</span></span>  
  
-   <span data-ttu-id="27399-127">新しいスキーマ行セットは表示されず、スキーマ行セットの行セットにそれらのスキーマ行セットの行は含まれません。</span><span class="sxs-lookup"><span data-stu-id="27399-127">The new schema rowsets are not visible, and there are no rows for them in the schema rowsets rowset.</span></span>  
  
-   <span data-ttu-id="27399-128">COLUMNS 行セット内の新しい列は表示されません。</span><span class="sxs-lookup"><span data-stu-id="27399-128">New columns in the COLUMNS rowset are not visible.</span></span>  
  
-   <span data-ttu-id="27399-129">DBCOLUMNFLAGS_SS_ISCOLUMNSET が `column_set` 列に対して設定されません。</span><span class="sxs-lookup"><span data-stu-id="27399-129">DBCOLUMNFLAGS_SS_ISCOLUMNSET is not set for `column_set` columns.</span></span>  
  
-   <span data-ttu-id="27399-130">DBCOMPUTEMODE_NOTCOMPUTED が `column_set` 列に対して設定されます。</span><span class="sxs-lookup"><span data-stu-id="27399-130">DBCOMPUTEMODE_NOTCOMPUTED is set for `column_set` columns.</span></span>  
  
## <a name="ole-db-support-for-sparse-columns"></a><span data-ttu-id="27399-131">OLE DB によるスパース列のサポート</span><span class="sxs-lookup"><span data-stu-id="27399-131">OLE DB Support for Sparse Columns</span></span>  
 <span data-ttu-id="27399-132">スパース列をサポートするために、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client で次の OLE DB インターフェイスが変更されています。</span><span class="sxs-lookup"><span data-stu-id="27399-132">The following OLE DB interfaces were modified in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to support sparse columns:</span></span>  
  
|<span data-ttu-id="27399-133">型またはメンバー関数</span><span class="sxs-lookup"><span data-stu-id="27399-133">Type or member function</span></span>|<span data-ttu-id="27399-134">説明</span><span class="sxs-lookup"><span data-stu-id="27399-134">Description</span></span>|  
|-----------------------------|-----------------|  
|<span data-ttu-id="27399-135">IColumnsInfo::GetColumnsInfo</span><span class="sxs-lookup"><span data-stu-id="27399-135">IColumnsInfo::GetColumnsInfo</span></span>|<span data-ttu-id="27399-136">DwFlags の列に対して DBCOLUMNFLAGS_SS_ISCOLUMNSET 新しい DBCOLUMNFLAGS フラグ値が設定されてい `column_set` ます。 *dwFlags*</span><span class="sxs-lookup"><span data-stu-id="27399-136">A new DBCOLUMNFLAGS flag value DBCOLUMNFLAGS_SS_ISCOLUMNSET is set for `column_set` columns in *dwFlags*.</span></span><br /><br /> <span data-ttu-id="27399-137">DBCOLUMNFLAGS_WRITE が `column_set` 列に対して設定されます。</span><span class="sxs-lookup"><span data-stu-id="27399-137">DBCOLUMNFLAGS_WRITE is set for `column_set` columns.</span></span>|  
|<span data-ttu-id="27399-138">IColumsRowset::GetColumnsRowset</span><span class="sxs-lookup"><span data-stu-id="27399-138">IColumsRowset::GetColumnsRowset</span></span>|<span data-ttu-id="27399-139">DBCOLUMN_FLAGS で、新しい DBCOLUMNFLAGS フラグ値である DBCOLUMNFLAGS_SS_ISCOLUMNSET が `column_set` 列に対して設定されます。</span><span class="sxs-lookup"><span data-stu-id="27399-139">A new DBCOLUMNFLAGS flag value, DBCOLUMNFLAGS_SS_ISCOLUMNSET, is set for `column_set` columns in DBCOLUMN_FLAGS.</span></span><br /><br /> <span data-ttu-id="27399-140">`column_set` 列に対して DBCOLUMN_COMPUTEMODE が DBCOMPUTEMODE_DYNAMIC に設定されます。</span><span class="sxs-lookup"><span data-stu-id="27399-140">DBCOLUMN_COMPUTEMODE is set to DBCOMPUTEMODE_DYNAMIC for `column_set` columns.</span></span>|  
|<span data-ttu-id="27399-141">IDBSchemaRowset::GetSchemaRowset</span><span class="sxs-lookup"><span data-stu-id="27399-141">IDBSchemaRowset::GetSchemaRowset</span></span>|<span data-ttu-id="27399-142">DBSCHEMA_COLUMNS が、SS_IS_COLUMN_SET と SS_IS_SPARSE という 2 つの新しい列を返します。</span><span class="sxs-lookup"><span data-stu-id="27399-142">DBSCHEMA_COLUMNS returns two new columns: SS_IS_COLUMN_SET and SS_IS_SPARSE.</span></span><br /><br /> <span data-ttu-id="27399-143">DBSCHEMA_COLUMNS は、`column_set` のメンバーでない列のみを返します。</span><span class="sxs-lookup"><span data-stu-id="27399-143">DBSCHEMA_COLUMNS returns only columns that are not members of a `column_set`.</span></span><br /><br /> <span data-ttu-id="27399-144">2 つの新しいスキーマ行セットが追加されています。DBSCHEMA_COLUMNS_EXTENDED は、スパース `column_set` のメンバーシップに関係なくすべての列を返します。</span><span class="sxs-lookup"><span data-stu-id="27399-144">Two new schema rowsets have been added: DBSCHEMA_COLUMNS_EXTENDED will return all columns regardless of sparseness of `column_set` membership.</span></span> <span data-ttu-id="27399-145">DBSCHEMA_SPARSE_COLUMN_SET は、`column_set` のメンバーである列のみを返します。</span><span class="sxs-lookup"><span data-stu-id="27399-145">DBSCHEMA_SPARSE_COLUMN_SET returns only columns that are members of a `column_set`.</span></span> <span data-ttu-id="27399-146">これらの新しい行セットの列と制限は DBSCHEMA_COLUMNS と同じです。</span><span class="sxs-lookup"><span data-stu-id="27399-146">These new rowsets have the same columns and restrictions as DBSCHEMA_COLUMNS.</span></span>|  
|<span data-ttu-id="27399-147">IDBSchemaRowset::GetSchemas</span><span class="sxs-lookup"><span data-stu-id="27399-147">IDBSchemaRowset::GetSchemas</span></span>|<span data-ttu-id="27399-148">IDBSchemaRowset::GetSchemas の使用可能なスキーマ行セットの一覧に、新しい行セットである DBSCHEMA_COLUMNS_EXTENDED と DBSCHEMA_SPARSE_COLUMN_SET の GUID が含まれます。</span><span class="sxs-lookup"><span data-stu-id="27399-148">IDBSchemaRowset::GetSchemas includes the GUIDs for the new rowsets DBSCHEMA_COLUMNS_EXTENDED and DBSCHEMA_SPARSE_COLUMN_SET in the list of available schema rowsets.</span></span>|  
|<span data-ttu-id="27399-149">ICommand::Execute</span><span class="sxs-lookup"><span data-stu-id="27399-149">ICommand::Execute</span></span>|<span data-ttu-id="27399-150">**Select \* from** *table*を使用すると、スパースのメンバーではないすべての列と、スパースのメンバーである `column_set` すべての null 以外の列の値を含む XML 列 (存在する場合) が返され `column_set` ます。</span><span class="sxs-lookup"><span data-stu-id="27399-150">If **select \* from** *table* is used, it returns all columns that are not members of the sparse `column_set`, plus an XML column that contains values of all non-null columns that are members of the sparse `column_set`, if present.</span></span>|  
|<span data-ttu-id="27399-151">IOpenRowset::OpenRowset</span><span class="sxs-lookup"><span data-stu-id="27399-151">IOpenRowset::OpenRowset</span></span>|<span data-ttu-id="27399-152">同じテーブルに対して **select\*** クエリを使用すると、IOpenRowset::OpenRowset から ICommand::Execute と同じ列を持つ行セットが返されます。</span><span class="sxs-lookup"><span data-stu-id="27399-152">IOpenRowset::OpenRowset returns a rowset with the same columns as ICommand::Execute, with a **select \*** query on the same table.</span></span>|  
|<span data-ttu-id="27399-153">ITableDefinition</span><span class="sxs-lookup"><span data-stu-id="27399-153">ITableDefinition</span></span>|<span data-ttu-id="27399-154">このインターフェイスには、スパース列や `column_set` 列のための変更はありません。</span><span class="sxs-lookup"><span data-stu-id="27399-154">There is no change to this interface for sparse columns or for `column_set` columns.</span></span> <span data-ttu-id="27399-155">スキーマを変更する必要のあるアプリケーションでは、適切な [!INCLUDE[tsql](../../../includes/tsql-md.md)] を直接実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="27399-155">Applications that have to make schema modifications must execute the appropriate [!INCLUDE[tsql](../../../includes/tsql-md.md)] directly.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27399-156">参照</span><span class="sxs-lookup"><span data-stu-id="27399-156">See Also</span></span>  
 [<span data-ttu-id="27399-157">SQL Server Native Client &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="27399-157">SQL Server Native Client &#40;OLE DB&#41;</span></span>](sql-server-native-client-ole-db.md)  
  
  