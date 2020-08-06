---
title: テーブル値パラメーターを含むコマンドの実行 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters, executing commands containing
ms.assetid: 7ecba6f6-fe7a-462a-9aa3-d5115b6d4529
author: rothja
ms.author: jroth
ms.openlocfilehash: e3f616b2b9f95ae558e444bcbdae50eae123fa4c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633828"
---
# <a name="executing-commands-containing-table-valued-parameters"></a><span data-ttu-id="a7aa1-102">テーブル値パラメーターを含むコマンドの実行</span><span class="sxs-lookup"><span data-stu-id="a7aa1-102">Executing Commands Containing Table-Valued Parameters</span></span>
  <span data-ttu-id="a7aa1-103">テーブル値パラメーターを含むコマンドを実行するには、次の 2 つのフェーズが必要になります。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-103">Executing a command that contains table-valued parameters requires two phases:</span></span>  
  
1.  <span data-ttu-id="a7aa1-104">パラメーターの型を指定する。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-104">Specify the parameter types.</span></span>  
  
2.  <span data-ttu-id="a7aa1-105">パラメーター データをバインドする。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-105">Bind the parameter data.</span></span>  
  
## <a name="table-valued-parameter-specification"></a><span data-ttu-id="a7aa1-106">テーブル値パラメーターの指定</span><span class="sxs-lookup"><span data-stu-id="a7aa1-106">Table-Valued Parameter Specification</span></span>  
 <span data-ttu-id="a7aa1-107">コンシューマーは、テーブル値パラメーターの型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-107">The consumer can specify the type of the table-valued parameter.</span></span> <span data-ttu-id="a7aa1-108">この情報には、テーブル値パラメーターの型名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-108">This information includes the table-valued parameter type name.</span></span> <span data-ttu-id="a7aa1-109">また、テーブル値パラメーターのユーザー定義テーブル型が接続の現在の既定のスキーマにない場合は、スキーマ名も含まれます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-109">It also includes the schema name, if the user-defined table type for the table-valued parameter is not in the current default schema for the connection.</span></span> <span data-ttu-id="a7aa1-110">サーバーでサポートされているかどうかに応じて、コンシューマーでは、省略可能なメタデータ情報 (列の順序など) を指定したり、特定の列のすべての行に既定値が設定されるよう指定したりすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-110">Depending on server support, the consumer can also specify optional metadata information, such as ordering of columns, and can specify that all rows for particular columns have the default values.</span></span>  
  
 <span data-ttu-id="a7aa1-111">テーブル値パラメーターを指定する目的で、コンシューマーは ISSCommandWithParameter::SetParameterInfo を呼び出し、任意で ISSCommandWithParameters::SetParameterProperties を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-111">To specify a table-valued parameter, the consumer calls ISSCommandWithParameter::SetParameterInfo, and optionally calls ISSCommandWithParameters::SetParameterProperties.</span></span> <span data-ttu-id="a7aa1-112">テーブル値パラメーターの場合、DBPARAMBINDINFO 構造体の *pwszDataSourceType* フィールドの値は DBTYPE_TABLE になります。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-112">For a table-valued parameter, the *pwszDataSourceType* field in the DBPARAMBINDINFO structure has a value of DBTYPE_TABLE.</span></span> <span data-ttu-id="a7aa1-113">*ulParamSize* フィールドには ~0 が設定され、長さが不明であることを示します。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-113">The *ulParamSize* field is set to ~0 to indicate that length is unknown.</span></span> <span data-ttu-id="a7aa1-114">テーブル値パラメーターの特定のプロパティ (スキーマ名、型名、列の順序、既定の列など) は、ISSCommandWithParameters::SetParameterProperties を使用して設定できます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-114">Particular properties for table-valued parameters, such as schema name, type name, column order, and default columns, can be set through ISSCommandWithParameters::SetParameterProperties.</span></span>  
  
## <a name="table-valued-parameter-binding"></a><span data-ttu-id="a7aa1-115">テーブル値パラメーターのバインド</span><span class="sxs-lookup"><span data-stu-id="a7aa1-115">Table-Valued Parameter Binding</span></span>  
 <span data-ttu-id="a7aa1-116">テーブル値パラメーターには、任意の行セット オブジェクトを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-116">A table-valued parameter can be any rowset object.</span></span> <span data-ttu-id="a7aa1-117">プロバイダーは、実行中、このオブジェクトからテーブル値パラメーターを読み取って、サーバーに送信します。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-117">The provider reads from this object while sending table-valued parameters to the server during execution.</span></span>  
  
 <span data-ttu-id="a7aa1-118">テーブル値パラメーターをバインドするために、コンシューマーは IAccessor::CreateAccessor を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-118">To bind the table-valued parameter, the consumer calls IAccessor::CreateAccessor.</span></span> <span data-ttu-id="a7aa1-119">テーブル値パラメーターの DBBINDING 構造体の *wType* フィールドには、DBTYPE_TABLE が設定されます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-119">The *wType* field of the DBBINDING structure for the table-valued parameter is set to DBTYPE_TABLE.</span></span> <span data-ttu-id="a7aa1-120">DBBINDING 構造体の *pObject* メンバーは NULL ではなく、*pObject* の *iid* メンバーは IID_IRowset、またはその他のテーブル値パラメーターの行セット オブジェクト インターフェイスに設定されます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-120">The *pObject* member of the DBBINDING structure is non-NULL, and the *pObject*'s *iid* member is set to IID_IRowset or any other table-valued parameter rowset object interfaces.</span></span> <span data-ttu-id="a7aa1-121">DBBINDING 構造体の残りのフィールドは、ストリームされた BLOB の場合と同じように設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-121">The remaining fields in the DBBINDING structure should be set the same way they are set for streamed BLOBs.</span></span>  
  
 <span data-ttu-id="a7aa1-122">テーブル値パラメーターと、テーブル値パラメーターに関連付けられる行セット オブジェクトのバインドでは、次の制限が適用されます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-122">In the bindings for the table-valued parameter and the rowset object associated with a table-valued parameter, the following restrictions apply:</span></span>  
  
-   <span data-ttu-id="a7aa1-123">テーブル値パラメーターの行セット列データに許容される状態値は DBSTATUS_S_ISNULL と DBSTATUS_S_OK だけです。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-123">The only status values allowed for table-valued parameter rowset column data are DBSTATUS_S_ISNULL and DBSTATUS_S_OK.</span></span> <span data-ttu-id="a7aa1-124">DBSTATUS_S_DEFAULT ではエラーが発生し、バインド状態値が DBSTATUS_E_BADSTATUS に設定されます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-124">DBSTATUS_S_DEFAULT will result in a failure, and the bound status value will be set to DBSTATUS_E_BADSTATUS.</span></span>  
  
-   <span data-ttu-id="a7aa1-125">テーブル値パラメーターは DBSTATUS_S_DEFAULT 状態でマークできます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-125">A table-valued parameter can be marked with the status DBSTATUS_S_DEFAULT.</span></span> <span data-ttu-id="a7aa1-126">有効な値は DBSTATUS_S_DEFAULT と DBSTATUS_S_OK だけです。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-126">The only valid values are DBSTATUS_S_DEFAULT and DBSTATUS_S_OK.</span></span> <span data-ttu-id="a7aa1-127">状態が DBSTATUS_S_DEFAULT に設定された場合、テーブル値パラメーターの値は、空のテーブルに対応します。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-127">When the status is set to DBSTATUS_S_DEFAULT, the value of the table-valued parameter corresponds to an empty table.</span></span>  
  
-   <span data-ttu-id="a7aa1-128">テーブル値パラメーターの読み取り専用列 (ID 列または計算列) は、SSPROP_PARAM_TABLE_DEFAULT_COLUMNS プロパティを使って、既定としてマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-128">Read-only columns in table-valued parameters (identity or computed columns) must be marked as default by using the SSPROP_PARAM_TABLE_DEFAULT_COLUMNS property.</span></span> <span data-ttu-id="a7aa1-129">既定値を持つ列も、特定のテーブル値パラメーターの列のデータ値用に既定値を使用できるように、SSPROP_PARAM_TABLE_DEFAULT_COLUMNS プロパティで、既定としてマークする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-129">Columns that have a default value must also be marked as default through SSPROP_PARAM_TABLE_DEFAULT_COLUMNS property to allow the default value to be used for the column's data values for a particular table-valued parameter.</span></span> <span data-ttu-id="a7aa1-130">既定としてマークされた列にバインドされたデータ値は、プロバイダーによって無視されます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-130">The provider will ignore the data values bound for the columns marked as default.</span></span>  
  
-   <span data-ttu-id="a7aa1-131">SSPROP_PARAM_TABLE_DEFAULT も設定されない限り、データは、DBPROP_COL_AUTOINCREMENT または SSPROP_COL_COMPUTED が設定された列を想定して、サーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="a7aa1-131">Data will be sent to the server for columns with DBPROP_COL_AUTOINCREMENT or SSPROP_COL_COMPUTED, unless SSPROP_PARAM_TABLE_DEFAULT is also set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7aa1-132">参照</span><span class="sxs-lookup"><span data-stu-id="a7aa1-132">See Also</span></span>  
 <span data-ttu-id="a7aa1-133">[テーブル値パラメーター &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="a7aa1-133">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="a7aa1-134">テーブル値パラメーターの使用 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="a7aa1-134">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
