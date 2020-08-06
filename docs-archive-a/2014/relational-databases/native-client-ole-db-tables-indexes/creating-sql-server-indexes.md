---
title: SQL Server インデックスの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- CreateIndex function
- constraints [OLE DB]
- SQL Server Native Client OLE DB provider, indexes
- indexes [OLE DB]
- adding indexes
ms.assetid: 6239d440-2818-4b98-bb79-732dced41952
author: rothja
ms.author: jroth
ms.openlocfilehash: 3693355eec7a290c03658c10db500161aa52062d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739786"
---
# <a name="creating-sql-server-indexes"></a><span data-ttu-id="03a22-102">SQL Server インデックスの作成</span><span class="sxs-lookup"><span data-stu-id="03a22-102">Creating SQL Server Indexes</span></span>
  <span data-ttu-id="03a22-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **Iindexdefinition:: createindex**関数を公開します。これにより、コンシューマーはテーブルに新しいインデックスを定義でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="03a22-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **IIndexDefinition::CreateIndex** function, allowing consumers to define new indexes on [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tables.</span></span>  
  
 <span data-ttu-id="03a22-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、インデックスまたは制約としてテーブルインデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-104">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates table indexes as either indexes or constraints.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="03a22-105">では、制約を作成する権限がテーブルの所有者、データベースの所有者、および特定の管理ロールのメンバーに許可されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-105">gives constraint-creation privilege to the table owner, database owner, and members of certain administrative roles.</span></span> <span data-ttu-id="03a22-106">テーブルにインデックスを作成できるのは、既定では、テーブルの所有者だけです。</span><span class="sxs-lookup"><span data-stu-id="03a22-106">By default, only the table owner can create an index on a table.</span></span> <span data-ttu-id="03a22-107">したがって、**CreateIndex** が成功するか失敗するかは、アプリケーション ユーザーのアクセス権だけでなく、作成するインデックスの種類によっても異なります。</span><span class="sxs-lookup"><span data-stu-id="03a22-107">Therefore, the success or failure of **CreateIndex** depends not only on the application user's access rights but also on the type of index created.</span></span>  
  
 <span data-ttu-id="03a22-108">コンシューマーは、*pTableID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列としてテーブル名を指定します。</span><span class="sxs-lookup"><span data-stu-id="03a22-108">Consumers specify the table name as a Unicode character string in the *pwszName* member of the *uName* union in the *pTableID* parameter.</span></span> <span data-ttu-id="03a22-109">*pTableID* の *eKind* メンバーを DBKIND_NAME にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="03a22-109">The *eKind* member of *pTableID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="03a22-110">*PIndexID*パラメーターには NULL を指定できます。 NULL の場合は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーによってインデックスの一意の名前が作成されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-110">The *pIndexID* parameter can be NULL, and if it is, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider creates a unique name for the index.</span></span> <span data-ttu-id="03a22-111">*ppIndexID* パラメーターに DBID への有効なポインターを指定することで、インデックスの名前をキャプチャできます。</span><span class="sxs-lookup"><span data-stu-id="03a22-111">The consumer can capture the name of the index by specifying a valid pointer to a DBID in the *ppIndexID* parameter.</span></span>  
  
 <span data-ttu-id="03a22-112">インデックス名は、*pIndexID* パラメーターの *uName* 共用体の *pwszName* メンバーに Unicode 文字列で指定できます。</span><span class="sxs-lookup"><span data-stu-id="03a22-112">The consumer can specify the index name as a Unicode character string in the *pwszName* member of the *uName* union of the *pIndexID* parameter.</span></span> <span data-ttu-id="03a22-113">*pIndexID* の *eKind* メンバーを DBKIND_NAME にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="03a22-113">The *eKind* member of *pIndexID* must be DBKIND_NAME.</span></span>  
  
 <span data-ttu-id="03a22-114">コンシューマーは、インデックスに参加する列または複数の列を名前で指定します。</span><span class="sxs-lookup"><span data-stu-id="03a22-114">The consumer specifies the column or columns participating in the index by name.</span></span> <span data-ttu-id="03a22-115">**CreateIndex** で使用する DBINDEXCOLUMNDESC 構造体ごとに、*pColumnID* の *eKind* メンバーを DBKIND_NAME にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="03a22-115">For each DBINDEXCOLUMNDESC structure used in **CreateIndex**, the *eKind* member of the *pColumnID* must be DBKIND_NAME.</span></span> <span data-ttu-id="03a22-116">列の名前は、*pColumnID* の *uName* 共用体の *pwszName* メンバーに Unicode 文字列で指定します。</span><span class="sxs-lookup"><span data-stu-id="03a22-116">The name of the column is specified as a Unicode character string in the *pwszName* member of the *uName* union in the *pColumnID*.</span></span>  
  
 <span data-ttu-id="03a22-117">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーで、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インデックス内の値に対する昇順の並べ替えをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="03a22-117">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support ascending order on values in the index.</span></span> <span data-ttu-id="03a22-118">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]コンシューマーが DBINDEXCOLUMNDESC 構造体の DBINDEX_COL_ORDER_DESC を指定している場合、Native Client OLE DB プロバイダーは E_INVALIDARG を返します。</span><span class="sxs-lookup"><span data-stu-id="03a22-118">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider returns E_INVALIDARG if the consumer specifies DBINDEX_COL_ORDER_DESC in any DBINDEXCOLUMNDESC structure.</span></span>  
  
 <span data-ttu-id="03a22-119">**CreateIndex** では、インデックスのプロパティが次のように解釈されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-119">**CreateIndex** interprets index properties as follows.</span></span>  
  
|<span data-ttu-id="03a22-120">プロパティ ID</span><span class="sxs-lookup"><span data-stu-id="03a22-120">Property ID</span></span>|<span data-ttu-id="03a22-121">説明</span><span class="sxs-lookup"><span data-stu-id="03a22-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="03a22-122">DBPROP_INDEX_AUTOUPDATE</span><span class="sxs-lookup"><span data-stu-id="03a22-122">DBPROP_INDEX_AUTOUPDATE</span></span>|<span data-ttu-id="03a22-123">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="03a22-123">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="03a22-124">既定値: なし</span><span class="sxs-lookup"><span data-stu-id="03a22-124">Default: None</span></span><br /><br /> <span data-ttu-id="03a22-125">説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、このプロパティをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="03a22-125">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="03a22-126">**CreateIndex** でこのプロパティの設定を試みると、戻り値として DB_S_ERRORSOCCURRED が返されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-126">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="03a22-127">プロパティ構造体の *dwStatus* メンバーには、DBPROPSTATUS_BADVALUE が示されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-127">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="03a22-128">DBPROP_INDEX_CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="03a22-128">DBPROP_INDEX_CLUSTERED</span></span>|<span data-ttu-id="03a22-129">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="03a22-129">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="03a22-130">既定値はVARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="03a22-130">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="03a22-131">説明 : インデックスのクラスター化を制御します。</span><span class="sxs-lookup"><span data-stu-id="03a22-131">Description: Controls index clustering.</span></span><br /><br /> <span data-ttu-id="03a22-132">VARIANT_TRUE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、テーブルにクラスター化インデックスを作成しようとし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="03a22-132">VARIANT_TRUE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider attempts to create a clustered index on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="03a22-133">では、どのテーブルでもクラスター化インデックスは 1 つしかサポートされません。</span><span class="sxs-lookup"><span data-stu-id="03a22-133">supports at most one clustered index on any table.</span></span><br /><br /> <span data-ttu-id="03a22-134">VARIANT_FALSE: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、テーブルに非クラスター化インデックスを作成しようとし [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="03a22-134">VARIANT_FALSE: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider attempts to create a nonclustered index on the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table.</span></span>|  
|<span data-ttu-id="03a22-135">DBPROP_INDEX_FILLFACTOR</span><span class="sxs-lookup"><span data-stu-id="03a22-135">DBPROP_INDEX_FILLFACTOR</span></span>|<span data-ttu-id="03a22-136">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="03a22-136">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="03a22-137">既定値: 0</span><span class="sxs-lookup"><span data-stu-id="03a22-137">Default: 0</span></span><br /><br /> <span data-ttu-id="03a22-138">説明 : インデックス ページの格納に使用する割合を指定します。</span><span class="sxs-lookup"><span data-stu-id="03a22-138">Description: Specifies the percentage of an index page used for storage.</span></span> <span data-ttu-id="03a22-139">詳細については、「 [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03a22-139">For more information, see [CREATE INDEX](/sql/t-sql/statements/create-index-transact-sql).</span></span><br /><br /> <span data-ttu-id="03a22-140">バリアントの型は VT_I4 です。</span><span class="sxs-lookup"><span data-stu-id="03a22-140">The type of the variant is VT_I4.</span></span> <span data-ttu-id="03a22-141">値は 1 ～ 100 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="03a22-141">The value must be greater than or equal to 1 and less than or equal to 100.</span></span>|  
|<span data-ttu-id="03a22-142">DBPROP_INDEX_INITIALIZE</span><span class="sxs-lookup"><span data-stu-id="03a22-142">DBPROP_INDEX_INITIALIZE</span></span>|<span data-ttu-id="03a22-143">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="03a22-143">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="03a22-144">既定値: なし</span><span class="sxs-lookup"><span data-stu-id="03a22-144">Default: None</span></span><br /><br /> <span data-ttu-id="03a22-145">説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、このプロパティをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="03a22-145">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="03a22-146">**CreateIndex** でこのプロパティの設定を試みると、戻り値として DB_S_ERRORSOCCURRED が返されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-146">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="03a22-147">プロパティ構造体の *dwStatus* メンバーには、DBPROPSTATUS_BADVALUE が示されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-147">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="03a22-148">DBPROP_INDEX_NULLCOLLATION</span><span class="sxs-lookup"><span data-stu-id="03a22-148">DBPROP_INDEX_NULLCOLLATION</span></span>|<span data-ttu-id="03a22-149">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="03a22-149">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="03a22-150">既定値: なし</span><span class="sxs-lookup"><span data-stu-id="03a22-150">Default: None</span></span><br /><br /> <span data-ttu-id="03a22-151">説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、このプロパティをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="03a22-151">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="03a22-152">**CreateIndex** でこのプロパティの設定を試みると、戻り値として DB_S_ERRORSOCCURRED が返されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-152">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="03a22-153">プロパティ構造体の *dwStatus* メンバーには、DBPROPSTATUS_BADVALUE が示されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-153">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="03a22-154">DBPROP_INDEX_NULLS</span><span class="sxs-lookup"><span data-stu-id="03a22-154">DBPROP_INDEX_NULLS</span></span>|<span data-ttu-id="03a22-155">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="03a22-155">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="03a22-156">既定値: なし</span><span class="sxs-lookup"><span data-stu-id="03a22-156">Default: None</span></span><br /><br /> <span data-ttu-id="03a22-157">説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、このプロパティをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="03a22-157">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="03a22-158">**CreateIndex** でこのプロパティの設定を試みると、戻り値として DB_S_ERRORSOCCURRED が返されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-158">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="03a22-159">プロパティ構造体の *dwStatus* メンバーには、DBPROPSTATUS_BADVALUE が示されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-159">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="03a22-160">DBPROP_INDEX_PRIMARYKEY</span><span class="sxs-lookup"><span data-stu-id="03a22-160">DBPROP_INDEX_PRIMARYKEY</span></span>|<span data-ttu-id="03a22-161">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="03a22-161">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="03a22-162">既定値 : VARIANT_FALSE&lt;br&gt;&lt;/br&gt;説明 : 参照整合性 (PRIMARY KEY 制約) としてインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03a22-162">Default: VARIANT_FALSE Description: Creates the index as a referential integrity, PRIMARY KEY constraint.</span></span><br /><br /> <span data-ttu-id="03a22-163">VARIANT_TRUE: インデックスは、テーブルの PRIMARY KEY 制約をサポートするために作成されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-163">VARIANT_TRUE: The index is created to support the PRIMARY KEY constraint of the table.</span></span> <span data-ttu-id="03a22-164">列には NULL 値を許容しないでください。</span><span class="sxs-lookup"><span data-stu-id="03a22-164">The columns must be nonnullable.</span></span><br /><br /> <span data-ttu-id="03a22-165">VARIANT_FALSE: インデックスは、テーブル内の行値の PRIMARY KEY 制約としては使用されません。</span><span class="sxs-lookup"><span data-stu-id="03a22-165">VARIANT_FALSE: The index is not used as a PRIMARY KEY constraint for row values in the table.</span></span>|  
|<span data-ttu-id="03a22-166">DBPROP_INDEX_SORTBOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="03a22-166">DBPROP_INDEX_SORTBOOKMARKS</span></span>|<span data-ttu-id="03a22-167">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="03a22-167">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="03a22-168">既定値: なし</span><span class="sxs-lookup"><span data-stu-id="03a22-168">Default: None</span></span><br /><br /> <span data-ttu-id="03a22-169">説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、このプロパティをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="03a22-169">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="03a22-170">**CreateIndex** でこのプロパティの設定を試みると、戻り値として DB_S_ERRORSOCCURRED が返されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-170">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="03a22-171">プロパティ構造体の *dwStatus* メンバーには、DBPROPSTATUS_BADVALUE が示されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-171">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="03a22-172">DBPROP_INDEX_TEMPINDEX</span><span class="sxs-lookup"><span data-stu-id="03a22-172">DBPROP_INDEX_TEMPINDEX</span></span>|<span data-ttu-id="03a22-173">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="03a22-173">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="03a22-174">既定値: なし</span><span class="sxs-lookup"><span data-stu-id="03a22-174">Default: None</span></span><br /><br /> <span data-ttu-id="03a22-175">説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、このプロパティをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="03a22-175">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="03a22-176">**CreateIndex** でこのプロパティの設定を試みると、戻り値として DB_S_ERRORSOCCURRED が返されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-176">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="03a22-177">プロパティ構造体の *dwStatus* メンバーには、DBPROPSTATUS_BADVALUE が示されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-177">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="03a22-178">DBPROP_INDEX_TYPE</span><span class="sxs-lookup"><span data-stu-id="03a22-178">DBPROP_INDEX_TYPE</span></span>|<span data-ttu-id="03a22-179">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="03a22-179">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="03a22-180">既定値: なし</span><span class="sxs-lookup"><span data-stu-id="03a22-180">Default: None</span></span><br /><br /> <span data-ttu-id="03a22-181">説明: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、このプロパティをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="03a22-181">Description: The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider does not support this property.</span></span> <span data-ttu-id="03a22-182">**CreateIndex** でこのプロパティの設定を試みると、戻り値として DB_S_ERRORSOCCURRED が返されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-182">Attempts to set the property in **CreateIndex** cause a DB_S_ERRORSOCCURRED return value.</span></span> <span data-ttu-id="03a22-183">プロパティ構造体の *dwStatus* メンバーには、DBPROPSTATUS_BADVALUE が示されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-183">The *dwStatus* member of the property structure indicates DBPROPSTATUS_BADVALUE.</span></span>|  
|<span data-ttu-id="03a22-184">DBPROP_INDEX_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="03a22-184">DBPROP_INDEX_UNIQUE</span></span>|<span data-ttu-id="03a22-185">R/W:読み取り/書き込み</span><span class="sxs-lookup"><span data-stu-id="03a22-185">R/W: Read/write</span></span><br /><br /> <span data-ttu-id="03a22-186">既定値はVARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="03a22-186">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="03a22-187">説明 : インデックスに参加する列または複数の列に、UNIQUE 制約としてインデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03a22-187">Description: Creates the index as a UNIQUE constraint on the participating column or columns.</span></span><br /><br /> <span data-ttu-id="03a22-188">VARIANT_TRUE: インデックスを使用して、テーブル内の行値を一意に制約します。</span><span class="sxs-lookup"><span data-stu-id="03a22-188">VARIANT_TRUE: The index is used to uniquely constrain row values in the table.</span></span><br /><br /> <span data-ttu-id="03a22-189">VARIANT_FALSE: インデックスでは、行値が一意に制約されません。</span><span class="sxs-lookup"><span data-stu-id="03a22-189">VARIANT_FALSE: The index does not uniquely constrain row values.</span></span>|  
  
 <span data-ttu-id="03a22-190">プロバイダー固有のプロパティセット DBPROPSET_SQLSERVERINDEX では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが、次のデータソース情報プロパティを定義します。</span><span class="sxs-lookup"><span data-stu-id="03a22-190">In the provider-specific property set DBPROPSET_SQLSERVERINDEX, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider defines the following data source information property.</span></span>  
  
|<span data-ttu-id="03a22-191">プロパティ ID</span><span class="sxs-lookup"><span data-stu-id="03a22-191">Property ID</span></span>|<span data-ttu-id="03a22-192">説明</span><span class="sxs-lookup"><span data-stu-id="03a22-192">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="03a22-193">SSPROP_INDEX_XML</span><span class="sxs-lookup"><span data-stu-id="03a22-193">SSPROP_INDEX_XML</span></span>|<span data-ttu-id="03a22-194">型 : VT_BOOL (R/W)</span><span class="sxs-lookup"><span data-stu-id="03a22-194">Type: VT_BOOL (R/W)</span></span><br /><br /> <span data-ttu-id="03a22-195">既定値はVARIANT_FALSE</span><span class="sxs-lookup"><span data-stu-id="03a22-195">Default: VARIANT_FALSE</span></span><br /><br /> <span data-ttu-id="03a22-196">説明 : IIndexDefinition::CreateIndex のときに、このプロパティの値に VARIANT_TRUE を指定すると、インデックス対象の列に対応するプライマリ XML インデックスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="03a22-196">Description: When this property is specified with a value of VARIANT_TRUE with IIndexDefinition::CreateIndex, it results in a primary xml index being created corresponding to the column being indexed.</span></span> <span data-ttu-id="03a22-197">このプロパティが VARIANT_TRUE の場合、cIndexColumnDescs を 1 にする必要があります。それ以外の値を指定するとエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="03a22-197">If this property is VARIANT_TRUE, cIndexColumnDescs should be 1, otherwise it is an error.</span></span>|  
  
 <span data-ttu-id="03a22-198">次の例では、主キー インデックスを作成します。</span><span class="sxs-lookup"><span data-stu-id="03a22-198">This example creates a primary key index:</span></span>  
  
```  
// This CREATE TABLE statement shows the referential integrity and   
// PRIMARY KEY constraint on the OrderDetails table that will be created   
// by the following example code.  
//  
// CREATE TABLE OrderDetails  
// (  
//    OrderID      int      NOT NULL  
//    ProductID   int      NOT NULL  
//        CONSTRAINT PK_OrderDetails  
//        PRIMARY KEY CLUSTERED (OrderID, ProductID),  
//    UnitPrice   money      NOT NULL,  
//    Quantity   int      NOT NULL,  
//    Discount   decimal(2,2)   NOT NULL  
//        DEFAULT 0  
// )  
//  
HRESULT CreatePrimaryKey  
    (  
    IIndexDefinition* pIIndexDefinition  
    )  
    {  
    HRESULT             hr = S_OK;  
  
    DBID                dbidTable;  
    DBID                dbidIndex;  
    const ULONG         nCols = 2;  
    ULONG               nCol;  
    const ULONG         nProps = 2;  
    ULONG               nProp;  
  
    DBINDEXCOLUMNDESC   dbidxcoldesc[nCols];  
    DBPROP              dbpropIndex[nProps];  
    DBPROPSET           dbpropset;  
  
    DBID*               pdbidIndexOut = NULL;  
  
    // Set up identifiers for the table and index.  
    dbidTable.eKind = DBKIND_NAME;  
    dbidTable.uName.pwszName = L"OrderDetails";  
  
    dbidIndex.eKind = DBKIND_NAME;  
    dbidIndex.uName.pwszName = L"PK_OrderDetails";  
  
    // Set up column identifiers.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        dbidxcoldesc[nCol].pColumnID = new DBID;  
        dbidxcoldesc[nCol].pColumnID->eKind = DBKIND_NAME;  
  
        dbidxcoldesc[nCol].eIndexColOrder = DBINDEX_COL_ORDER_ASC;  
        }  
    dbidxcoldesc[0].pColumnID->uName.pwszName = L"OrderID";  
    dbidxcoldesc[1].pColumnID->uName.pwszName = L"ProductID";  
  
    // Set properties for the index. The index is clustered,  
    // PRIMARY KEY.  
    for (nProp = 0; nProp < nProps; nProp++)  
        {  
        dbpropIndex[nProp].dwOptions = DBPROPOPTIONS_REQUIRED;  
        dbpropIndex[nProp].colid = DB_NULLID;  
  
        VariantInit(&(dbpropIndex[nProp].vValue));  
  
        dbpropIndex[nProp].vValue.vt = VT_BOOL;  
        }  
    dbpropIndex[0].dwPropertyID = DBPROP_INDEX_CLUSTERED;  
    dbpropIndex[0].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropIndex[1].dwPropertyID = DBPROP_INDEX_PRIMARYKEY;  
    dbpropIndex[1].vValue.boolVal = VARIANT_TRUE;  
  
    dbpropset.rgProperties = dbpropIndex;  
    dbpropset.cProperties = nProps;  
    dbpropset.guidPropertySet = DBPROPSET_INDEX;  
  
    hr = pIIndexDefinition->CreateIndex(&dbidTable, &dbidIndex, nCols,  
        dbidxcoldesc, 1, &dbpropset, &pdbidIndexOut);  
  
    // Clean up dynamically allocated DBIDs.  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        delete dbidxcoldesc[nCol].pColumnID;  
        }  
  
    return (hr);  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="03a22-199">参照</span><span class="sxs-lookup"><span data-stu-id="03a22-199">See Also</span></span>  
 [<span data-ttu-id="03a22-200">テーブルとインデックス</span><span class="sxs-lookup"><span data-stu-id="03a22-200">Tables and Indexes</span></span>](../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
  
