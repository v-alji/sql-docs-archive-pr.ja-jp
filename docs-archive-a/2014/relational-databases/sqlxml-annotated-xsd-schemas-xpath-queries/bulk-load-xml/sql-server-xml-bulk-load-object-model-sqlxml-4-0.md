---
title: SQL Server XML 一括読み込みオブジェクトモデル (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- bulk load [SQLXML], object model
- ErrorLogFile property
- SGDropTables property
- SGUseID property
- KeepNulls property
- ConnectionCommand property
- SchemaGen property
- XMLFragment property
- SQLXMLBulkLoad object
- ForceTableLock property
- CheckConstraints property
- BulkLoad property
- TempFilePath property
- IgnoreDuplicateKeys property
- Transaction property
- KeepIdentity property
- ConnectionString property
- FireTriggers property
- Execute method
- XML Bulk Load [SQLXML], object model
ms.assetid: a9efbbde-ed2b-4929-acc1-261acaaed19d
author: rothja
ms.author: jroth
ms.openlocfilehash: 364515afaea17ce403f8eb38cb10bbe6003dfe2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711810"
---
# <a name="sql-server-xml-bulk-load-object-model-sqlxml-40"></a><span data-ttu-id="b58ed-102">SQL Server XML 一括読み込みオブジェクト モデル (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="b58ed-102">SQL Server XML Bulk Load Object Model (SQLXML 4.0)</span></span>
  <span data-ttu-id="b58ed-103">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML 一括読み込みオブジェクトモデルは、SQLXMLBulkLoad オブジェクトで構成されています。</span><span class="sxs-lookup"><span data-stu-id="b58ed-103">The Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] XML Bulk Load object model consists of the SQLXMLBulkLoad object.</span></span> <span data-ttu-id="b58ed-104">このオブジェクトでは、次のメソッドとプロパティがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-104">This object supports the following methods and properties.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b58ed-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b58ed-105">Methods</span></span>  
 <span data-ttu-id="b58ed-106">実行</span><span class="sxs-lookup"><span data-stu-id="b58ed-106">Execute</span></span>  
 <span data-ttu-id="b58ed-107">パラメーターとして渡されるスキーマ ファイルとデータ ファイル (またはストリーム) を使用して、データの一括読み込みを行います。</span><span class="sxs-lookup"><span data-stu-id="b58ed-107">Bulk loads the data by using the schema file and data file (or stream) that are provided as parameters.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b58ed-108">Properties</span><span class="sxs-lookup"><span data-stu-id="b58ed-108">Properties</span></span>  
 <span data-ttu-id="b58ed-109">BulkLoad</span><span class="sxs-lookup"><span data-stu-id="b58ed-109">BulkLoad</span></span>  
 <span data-ttu-id="b58ed-110">一括読み込みを実行するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-110">Specifies whether a Bulk Load should be performed.</span></span> <span data-ttu-id="b58ed-111">このプロパティは、スキーマのみを生成する場合に便利です (以降の SchemaGen、SGDropTables、SGUseID の各プロパティを参照してください)。一括読み込みは実行されません。</span><span class="sxs-lookup"><span data-stu-id="b58ed-111">This property is useful if you want to generate only the schemas (see the SchemaGen, SGDropTables, and SGUseID properties that follow) and not perform a bulk load.</span></span> <span data-ttu-id="b58ed-112">このプロパティはブール値をとります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-112">This is a Boolean property.</span></span> <span data-ttu-id="b58ed-113">このプロパティを TRUE に設定すると、XML 一括読み込みが行われます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-113">When the property is set to TRUE, XML Bulk Load executes.</span></span> <span data-ttu-id="b58ed-114">FALSE に設定すると、XML 一括読み込みは行われません。</span><span class="sxs-lookup"><span data-stu-id="b58ed-114">When it is set to FALSE, XML Bulk Load does not execute.</span></span>  
  
 <span data-ttu-id="b58ed-115">既定値は TRUE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-115">The default value is TRUE.</span></span>  
  
 <span data-ttu-id="b58ed-116">CheckConstraints</span><span class="sxs-lookup"><span data-stu-id="b58ed-116">CheckConstraints</span></span>  
 <span data-ttu-id="b58ed-117">一括読み込みで列にデータを挿入するときに、列に指定されている制約 (列間の主キー/外部キーのリレーションシップによる制約など) をチェックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-117">Specifies whether the constraints (such as constraints due to the primary key/foreign key relationship among columns) that are specified on the column should be checked when XML Bulk Load inserts data into the columns.</span></span> <span data-ttu-id="b58ed-118">このプロパティはブール値をとります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-118">This is a Boolean property.</span></span>  
  
 <span data-ttu-id="b58ed-119">このプロパティを TRUE に設定すると、XML 一括読み込みで挿入される値ごとに制約がチェックされ、制約違反があるとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-119">When the property is set to TRUE, XML Bulk Load checks the constraints for each value inserted (which means that a constraint violation results in an error).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b58ed-120">このプロパティを FALSE のままにしておくには、対象テーブルに対する**ALTER TABLE**権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-120">To leave this property as FALSE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="b58ed-121">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b58ed-121">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="b58ed-122">既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-122">The default value is FALSE.</span></span> <span data-ttu-id="b58ed-123">FALSE に設定した場合、XML 一括読み込みでは挿入操作中、制約が無視されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-123">When it is set to FALSE, XML Bulk Load ignores the constraints during an insert operation.</span></span> <span data-ttu-id="b58ed-124">現在の実装では、マッピング スキーマの主キーと外部キーのリレーションシップの順序でテーブルを定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-124">In the current implementation, you must define the tables in the order of primary key and foreign key relationships in the mapping schema.</span></span> <span data-ttu-id="b58ed-125">つまり、主キーが設定されているテーブルは、外部キーが設定されている対応テーブルよりも前に定義する必要があります。このように定義しない場合、XML 一括読み込みは失敗します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-125">That is, a table with a primary key must be defined before the corresponding table with the foreign key; otherwise, XML Bulk Load fails.</span></span>  
  
 <span data-ttu-id="b58ed-126">ID 配布が実行されている場合は、このオプションは適用されず、制約チェックはオンのままになる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b58ed-126">Note that if ID Propagation is being done, then this option does not apply and constraint checking will be left on.</span></span> <span data-ttu-id="b58ed-127">これに該当するのは、親が ID フィールドで、その値が生成時に子に指定されるリレーションシップが定義されており、かつ `KeepIdentity=False` の場合です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-127">This occurs when `KeepIdentity=False` and there is a relationship defined where the parent is an identity field and the value is given to the child as it is generated.</span></span>  
  
 <span data-ttu-id="b58ed-128">ConnectionCommand</span><span class="sxs-lookup"><span data-stu-id="b58ed-128">ConnectionCommand</span></span>  
 <span data-ttu-id="b58ed-129">XML 一括読み込みで使用する既存の接続オブジェクト (ADO や ICommand コマンドオブジェクトなど) を識別します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-129">Identifies an existing connection object (for example, the ADO or ICommand command object) that XML Bulk Load should use.</span></span> <span data-ttu-id="b58ed-130">ConnectionString プロパティを使用して接続文字列を指定する代わりに、ConnectionCommand プロパティを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-130">You can use the ConnectionCommand property instead of specifying a connection string with the ConnectionString property.</span></span> <span data-ttu-id="b58ed-131">ConnectionCommand を使用する場合は、Transaction プロパティを TRUE に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-131">The Transaction property must be set to TRUE if you use ConnectionCommand.</span></span>  
  
 <span data-ttu-id="b58ed-132">ConnectionString プロパティと ConnectionCommand プロパティの両方を使用する場合、XML 一括読み込みでは最後に指定したプロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-132">If you use both the ConnectionString and ConnectionCommand properties, XML Bulk Load uses the last specified property.</span></span>  
  
 <span data-ttu-id="b58ed-133">既定値は NULL です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-133">The default value is NULL.</span></span>  
  
 <span data-ttu-id="b58ed-134">ConnectionString</span><span class="sxs-lookup"><span data-stu-id="b58ed-134">ConnectionString</span></span>  
 <span data-ttu-id="b58ed-135">データベース インスタンスへの接続の確立に必要な情報を提供する OLE DB 接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-135">Identifies the OLE DB connection string that provides the necessary information to establish a connection to an instance of the database.</span></span> <span data-ttu-id="b58ed-136">ConnectionString プロパティと ConnectionCommand プロパティの両方を使用する場合、XML 一括読み込みでは最後に指定したプロパティが使用されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-136">If you use both the ConnectionString and ConnectionCommand properties, XML Bulk Load uses the last specified property.</span></span>  
  
 <span data-ttu-id="b58ed-137">既定値は NULL です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-137">The default value is NULL.</span></span>  
  
 <span data-ttu-id="b58ed-138">ErrorLogFile</span><span class="sxs-lookup"><span data-stu-id="b58ed-138">ErrorLogFile</span></span>  
 <span data-ttu-id="b58ed-139">XML 一括読み込みでエラーとメッセージを記録するログ ファイル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-139">Specifies the file name into which the XML Bulk Load logs errors and messages.</span></span> <span data-ttu-id="b58ed-140">既定値は空文字列で、この場合ログは記録されません。</span><span class="sxs-lookup"><span data-stu-id="b58ed-140">The default is an empty string, in which case no logging takes place.</span></span>  
  
 <span data-ttu-id="b58ed-141">FireTriggers</span><span class="sxs-lookup"><span data-stu-id="b58ed-141">FireTriggers</span></span>  
 <span data-ttu-id="b58ed-142">一括読み込み操作中に、対象テーブルに定義されているトリガーを起動するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-142">Specifies if triggers defined on target tables should fire during the Bulk Load operation.</span></span> <span data-ttu-id="b58ed-143">既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-143">The default is FALSE.</span></span>  
  
 <span data-ttu-id="b58ed-144">TRUE に設定した場合は、挿入操作中、トリガーが通常どおり起動されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-144">When set to TRUE, triggers will fire as per normal during insert operations.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b58ed-145">このプロパティを FALSE のままにしておくには、対象テーブルに対する**ALTER TABLE**権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-145">To leave this property as FALSE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="b58ed-146">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b58ed-146">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="b58ed-147">ID 配布が実行されている場合は、このオプションは適用されず、トリガーはオンのままになる点に注意してください。</span><span class="sxs-lookup"><span data-stu-id="b58ed-147">Note that if ID Propagation is being done, then this option does not apply and triggers will be left on.</span></span> <span data-ttu-id="b58ed-148">これに該当するのは、親が ID フィールドで、その値が生成時に子に指定されるリレーションシップが定義されており、かつ `KeepIdentity=False` の場合です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-148">This occurs when `KeepIdentity=False` and there is a relationship defined where the parent is an identity field and the value is given to the child as it is generated.</span></span>  
  
 <span data-ttu-id="b58ed-149">ForceTableLock</span><span class="sxs-lookup"><span data-stu-id="b58ed-149">ForceTableLock</span></span>  
 <span data-ttu-id="b58ed-150">XML 一括読み込みでデータをコピーするテーブルを、一括読み込み中にロックするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-150">Specifies whether the tables into which XML Bulk Load copies data should be locked for the duration of the Bulk Load.</span></span> <span data-ttu-id="b58ed-151">このプロパティはブール値をとります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-151">This is a Boolean property.</span></span> <span data-ttu-id="b58ed-152">このプロパティを TRUE に設定すると、XML 一括読み込み中、テーブルはロックされます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-152">When the property is set to TRUE, XML Bulk Load acquires table locks for the duration of the Bulk Load.</span></span> <span data-ttu-id="b58ed-153">FALSE に設定すると、XML 一括読み込みでテーブルにレコードが挿入されるときに、毎回テーブルがロックされます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-153">When it is set to FALSE, XML Bulk Load acquires a table lock each time it inserts a record into a table.</span></span>  
  
 <span data-ttu-id="b58ed-154">既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-154">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b58ed-155">IgnoreDuplicateKeys</span><span class="sxs-lookup"><span data-stu-id="b58ed-155">IgnoreDuplicateKeys</span></span>  
 <span data-ttu-id="b58ed-156">キー列に挿入される値が重複している場合の動作を指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-156">Specifies what to do if an attempt is made to insert duplicate values in a key column.</span></span> <span data-ttu-id="b58ed-157">このプロパティが TRUE に設定されている状態で、キー列に挿入されるレコードの値が重複している場合、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではそのレコードは挿入されません。</span><span class="sxs-lookup"><span data-stu-id="b58ed-157">If this property is set to TRUE and an attempt is made to insert a record with a duplicate value in a key column, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not insert that record.</span></span> <span data-ttu-id="b58ed-158">しかし、その後に続くレコードは挿入されるので、一括読み込み操作は失敗しません。</span><span class="sxs-lookup"><span data-stu-id="b58ed-158">But it does insert the subsequent record; thus, the Bulk Load operation does not fail.</span></span> <span data-ttu-id="b58ed-159">このプロパティを FALSE に設定すると、キー列に挿入される値が重複している場合、一括読み込みは失敗します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-159">If this property is set to FALSE, Bulk Load fails when an attempt is made to insert a duplicate value in a key column.</span></span>  
  
 <span data-ttu-id="b58ed-160">IgnoreDuplicateKeys プロパティが TRUE に設定されている場合、テーブルに挿入されたすべてのレコードに対して COMMIT ステートメントが発行されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-160">When the IgnoreDuplicateKeys property is set to TRUE, a COMMIT statement is issued for every record inserted in the table.</span></span> <span data-ttu-id="b58ed-161">このため、パフォーマンスが低下します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-161">This slows down the performance.</span></span> <span data-ttu-id="b58ed-162">トランザクションの動作はファイルを使用して実装されるので、プロパティは、Transaction プロパティが FALSE に設定されている場合にのみ TRUE に設定できます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-162">The property can be set to TRUE only when the Transaction property is set to FALSE, because the transactional behavior is implemented using files.</span></span>  
  
 <span data-ttu-id="b58ed-163">既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-163">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b58ed-164">KeepIdentity</span><span class="sxs-lookup"><span data-stu-id="b58ed-164">KeepIdentity</span></span>  
 <span data-ttu-id="b58ed-165">ソース ファイルにある ID 型列値の取り扱い方法を指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-165">Specifies how to deal with the values for an Identity type column in the source file.</span></span> <span data-ttu-id="b58ed-166">このプロパティはブール値をとります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-166">This is a Boolean property.</span></span> <span data-ttu-id="b58ed-167">このプロパティを TRUE に設定すると、XML 一括読み込みでは、ソース ファイルで指定されている値が ID 列に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-167">When the property is set to TRUE, XML Bulk Load assigns the values that are specified in the source file to the identity column.</span></span> <span data-ttu-id="b58ed-168">このプロパティを FALSE に設定すると、一括読み込み操作では、ソースで指定されている ID 列値は無視されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-168">When the property is set to FALSE, the bulk-load operation ignores the identity-column values that are specified in the source.</span></span> <span data-ttu-id="b58ed-169">この場合、ID 列値は [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] によって割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-169">In this case, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assigns a value to the identity column.</span></span>  
  
 <span data-ttu-id="b58ed-170">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] で生成される値が ID 列に格納される場合に、一括読み込みでこの列を参照する外部キー列も読み込まれる場合、一括読み込みではこれらの ID 値が外部キー列に適切に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-170">If the Bulk Load involves a column that is a foreign key referring to an identity column in which [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]-generated values are stored, Bulk Load appropriately propagates these identity values to the foreign key column.</span></span>  
  
 <span data-ttu-id="b58ed-171">このプロパティの値は、一括読み込みの対象となるすべての列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-171">The value of this property applies to all columns involved in the bulk load.</span></span> <span data-ttu-id="b58ed-172">既定値は TRUE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-172">The default value is TRUE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b58ed-173">このプロパティを TRUE のままにするには、対象テーブルに対する**ALTER TABLE**権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-173">To leave this property as TRUE, you must have **ALTER TABLE** permissions on target tables.</span></span> <span data-ttu-id="b58ed-174">この権限がない場合は、値を FALSE に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-174">Otherwise, it must be set to a value of FALSE.</span></span> <span data-ttu-id="b58ed-175">詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b58ed-175">For more information, see [ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql).</span></span>  
  
 <span data-ttu-id="b58ed-176">KeepNulls</span><span class="sxs-lookup"><span data-stu-id="b58ed-176">KeepNulls</span></span>  
 <span data-ttu-id="b58ed-177">列に対応する属性または子要素が XML ドキュメントに見つからない場合に、その列に使用する値を指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-177">Specifies what value to use for a column that is missing a corresponding attribute or child element in the XML document.</span></span> <span data-ttu-id="b58ed-178">このプロパティはブール値をとります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-178">This is a Boolean property.</span></span> <span data-ttu-id="b58ed-179">このプロパティを TRUE に設定すると、XML 一括読み込みでは列に NULL 値が割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-179">When the property is set to TRUE, XML Bulk Load assigns a null value to the column.</span></span> <span data-ttu-id="b58ed-180">サーバーで列の既定値が設定されている場合でも、その既定値は割り当てられません。</span><span class="sxs-lookup"><span data-stu-id="b58ed-180">It does not assign the column's default value, if any, as set on the server.</span></span> <span data-ttu-id="b58ed-181">このプロパティの値は、一括読み込みの対象となるすべての列に適用されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-181">The value of this property applies to all columns involved in the bulk load.</span></span>  
  
 <span data-ttu-id="b58ed-182">既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-182">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b58ed-183">SchemaGen</span><span class="sxs-lookup"><span data-stu-id="b58ed-183">SchemaGen</span></span>  
 <span data-ttu-id="b58ed-184">一括読み込み操作の前に、必要なテーブルを作成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-184">Specifies whether to create the required tables before performing a Bulk Load operation.</span></span> <span data-ttu-id="b58ed-185">このプロパティはブール値をとります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-185">This is a Boolean property.</span></span> <span data-ttu-id="b58ed-186">このプロパティを TRUE に設定すると、マッピング スキーマで指定されているテーブルが作成されます (データベースは存在している必要があります)。</span><span class="sxs-lookup"><span data-stu-id="b58ed-186">If this property is set to TRUE, the tables identified in the mapping schema are created (the database must exist).</span></span> <span data-ttu-id="b58ed-187">データベース内に1つ以上のテーブルが既に存在する場合、SGDropTables プロパティは、これらの既存のテーブルを削除して再作成するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-187">If one or more of the tables already exist in the database, the SGDropTables property determines whether these preexisting tables are to be dropped and re-created.</span></span>  
  
 <span data-ttu-id="b58ed-188">SchemaGen プロパティの既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-188">The default value for the SchemaGen property is FALSE.</span></span> <span data-ttu-id="b58ed-189">SchemaGen では、新しく作成されたテーブルに PRIMARY KEY 制約は作成されません。</span><span class="sxs-lookup"><span data-stu-id="b58ed-189">SchemaGen does not create PRIMARY KEY constraints on the newly created tables.</span></span> <span data-ttu-id="b58ed-190">ただし、SchemaGen では、 `sql:relationship` マッピングスキーマで一致する注釈と注釈が見つかる場合 `sql:key-fields` や、キーフィールドが1つの列で構成されている場合、データベースに外部キー制約が作成されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-190">SchemaGen does, however, create FOREIGN KEY constraints in the database if it can find matching `sql:relationship` and `sql:key-fields` annotations in the mapping schema and if the key field consists of a single column.</span></span>  
  
 <span data-ttu-id="b58ed-191">SchemaGen プロパティを TRUE に設定すると、XML 一括読み込みでは次のことが行われることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="b58ed-191">Note that if you set the SchemaGen property to TRUE, XML Bulk Load does the following:</span></span>  
  
-   <span data-ttu-id="b58ed-192">要素名と属性名から、必要なテーブルを作成します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-192">Creates the necessary tables from the element and attribute names.</span></span> <span data-ttu-id="b58ed-193">このため、スキーマでは要素と属性に [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の予約語を使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="b58ed-193">Therefore, it is important that you do not use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] reserved words for element and attribute names in the schema.</span></span>  
  
-   <span data-ttu-id="b58ed-194">[Xml データ型](/sql/t-sql/xml/xml-transact-sql)の形式で、 [sql: overflow フィールド](annotation-interpretation-sql-overflow-field.md)を使用して指定された任意の列のオーバーフローデータを返します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-194">Returns overflow data for any column designated using the [sql:overflow-field](annotation-interpretation-sql-overflow-field.md) in [xml data type](/sql/t-sql/xml/xml-transact-sql) format.</span></span>  
  
 <span data-ttu-id="b58ed-195">SGDropTables</span><span class="sxs-lookup"><span data-stu-id="b58ed-195">SGDropTables</span></span>  
 <span data-ttu-id="b58ed-196">既存のテーブルを削除し、再作成するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-196">Specifies whether existing tables should be dropped and re-created.</span></span> <span data-ttu-id="b58ed-197">このプロパティは、SchemaGen プロパティが TRUE に設定されている場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-197">You use this property when the SchemaGen property is set to TRUE.</span></span> <span data-ttu-id="b58ed-198">SGDropTables が FALSE の場合は、既存のテーブルが保持されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-198">If SGDropTables is FALSE, the existing tables are retained.</span></span> <span data-ttu-id="b58ed-199">このプロパティが TRUE の場合、既存のテーブルは削除され再作成されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-199">When this property is TRUE, the existing tables are deleted and re-created.</span></span>  
  
 <span data-ttu-id="b58ed-200">既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-200">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b58ed-201">SGUseID</span><span class="sxs-lookup"><span data-stu-id="b58ed-201">SGUseID</span></span>  
 <span data-ttu-id="b58ed-202">`id` 型として指定されているマッピング スキーマの属性を、テーブル作成時の PRIMARY KEY 制約の作成に使用できるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-202">Specifies whether the attribute in the mapping schema that is identified as `id` type can be used in creating a PRIMARY KEY constraint when the table is created.</span></span> <span data-ttu-id="b58ed-203">このプロパティは、SchemaGen プロパティが TRUE に設定されている場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-203">Use this property when the SchemaGen property is set to TRUE.</span></span> <span data-ttu-id="b58ed-204">SGUseID が TRUE の場合、SchemaGen ユーティリティは、 `dt:type="id"` が主キー列として指定されている属性を使用し、テーブルの作成時に適切な PRIMARY key 制約を追加します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-204">If SGUseID is TRUE, the SchemaGen utility uses an attribute for which `dt:type="id"` is specified as the primary key column and adds the appropriate PRIMARY KEY constraint when creating the table.</span></span>  
  
 <span data-ttu-id="b58ed-205">既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-205">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b58ed-206">TempFilePath</span><span class="sxs-lookup"><span data-stu-id="b58ed-206">TempFilePath</span></span>  
 <span data-ttu-id="b58ed-207">XML 一括読み込みで、読み込んだデータ用の一時ファイルを作成するファイル パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-207">Specifies the file path where XML Bulk Load creates the temporary files for a transacted bulk load.</span></span> <span data-ttu-id="b58ed-208">(このプロパティは、Transaction プロパティが TRUE に設定されている場合にのみ役立ちます)。[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]XML 一括読み込みに使用するアカウントにこのパスへのアクセス権があることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-208">(This property is useful only when the Transaction property is set to TRUE.) You must ensure that the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] account that is used for XML Bulk Load has access to this path.</span></span> <span data-ttu-id="b58ed-209">このプロパティを設定しない場合、XML 一括読み込みでは、TEMP 環境変数で指定された場所に一時ファイルが格納されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-209">If this property is not set, XML Bulk Load stores the temporary files in the location that is specified in the TEMP environment variable.</span></span>  
  
 <span data-ttu-id="b58ed-210">トランザクション</span><span class="sxs-lookup"><span data-stu-id="b58ed-210">Transaction</span></span>  
 <span data-ttu-id="b58ed-211">一括読み込みをトランザクションとして実行するよう指定します。この場合、一括読み込みが失敗するとロールバックが実行されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-211">Specifies whether the Bulk Load should be done as a transaction, in which case the rollback is guaranteed if the Bulk Load fails.</span></span> <span data-ttu-id="b58ed-212">このプロパティはブール値をとります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-212">This is a Boolean property.</span></span> <span data-ttu-id="b58ed-213">このプロパティを TRUE に設定すると、一括読み込みはトランザクション コンテキストで実行されます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-213">If the property is set to TRUE, the Bulk Load occurs in a transactional context.</span></span> <span data-ttu-id="b58ed-214">TempFilePath プロパティは、Transaction が TRUE に設定されている場合にのみ役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b58ed-214">The TempFilePath property is useful only when Transaction is set to TRUE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b58ed-215">バイナリデータ (たとえば、bin. hex, bin. base64 XML データ型) をバイナリ、image データ型に読み込んでいる場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Transaction プロパティを FALSE に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-215">If you are loading binary data (such as the bin.hex, bin.base64 XML data types to the binary, image [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types), the Transaction property must be set to FALSE.</span></span>  
  
 <span data-ttu-id="b58ed-216">既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-216">The default value is FALSE.</span></span>  
  
 <span data-ttu-id="b58ed-217">XMLFragment</span><span class="sxs-lookup"><span data-stu-id="b58ed-217">XMLFragment</span></span>  
 <span data-ttu-id="b58ed-218">ソース データが XML フラグメントであるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="b58ed-218">Specifies whether the source data is an XML fragment.</span></span> <span data-ttu-id="b58ed-219">XML フラグメントとは、最上位 (ルート) 要素のない、単一の XML ドキュメントです。</span><span class="sxs-lookup"><span data-stu-id="b58ed-219">An XML fragment is an XML document with no single, top-level (root) element.</span></span> <span data-ttu-id="b58ed-220">このプロパティはブール値をとります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-220">This is a Boolean property.</span></span> <span data-ttu-id="b58ed-221">ソース ファイルに XML フラグメントが含まれている場合は、このプロパティを TRUE に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b58ed-221">This property must be set to TRUE if the source file consists of an XML fragment.</span></span>  
  
 <span data-ttu-id="b58ed-222">既定値は FALSE です。</span><span class="sxs-lookup"><span data-stu-id="b58ed-222">The default value is FALSE.</span></span>  
  
  
