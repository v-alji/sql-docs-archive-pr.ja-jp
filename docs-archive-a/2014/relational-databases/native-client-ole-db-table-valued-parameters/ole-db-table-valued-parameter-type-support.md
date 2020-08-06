---
title: OLE DB テーブル値パラメーターの型のサポート | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (OLE DB), API support (OLE DB)
ms.assetid: 147036a0-260e-4f81-8b3b-89209e023a32
author: rothja
ms.author: jroth
ms.openlocfilehash: 48d5fd780b2eaa2fc18e39071d3b10fde897b82c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634481"
---
# <a name="ole-db-table-valued-parameter-type-support"></a><span data-ttu-id="15ffd-102">OLE DB テーブル値パラメーターの型のサポート</span><span class="sxs-lookup"><span data-stu-id="15ffd-102">OLE DB Table-Valued Parameter Type Support</span></span>
  <span data-ttu-id="15ffd-103">このトピックでは、テーブル値パラメーターに対する OLE DB 型のサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="15ffd-103">This topic describes OLE DB type support for table-value parameters.</span></span>  
  
## <a name="table-valued-parameter-rowset-object"></a><span data-ttu-id="15ffd-104">テーブル値パラメーターの行セット オブジェクト</span><span class="sxs-lookup"><span data-stu-id="15ffd-104">Table-Valued Parameter Rowset Object</span></span>  
 <span data-ttu-id="15ffd-105">テーブル値パラメーターの特殊な行セット オブジェクトを作成できます。</span><span class="sxs-lookup"><span data-stu-id="15ffd-105">You can create a specialized rowset object for table-valued parameters.</span></span> <span data-ttu-id="15ffd-106">テーブル値パラメーターの行セット オブジェクトを作成するには、ITableDefinitionWithConstraints::CreateTableWithConstraints または IOpenRowset::OpenRowset を使用します。</span><span class="sxs-lookup"><span data-stu-id="15ffd-106">You create the table-valued parameter rowset object by using ITableDefinitionWithConstraints::CreateTableWithConstraints or IOpenRowset::OpenRowset.</span></span> <span data-ttu-id="15ffd-107">そのためには、*pTableID* パラメーターの *eKind* メンバーに DBKIND_GUID_NAME を設定し、CLSID_ROWSET_INMEMORY を *guid* メンバーとして指定します。</span><span class="sxs-lookup"><span data-stu-id="15ffd-107">To do this, set the *eKind* member of the *pTableID* parameter to DBKIND_GUID_NAME, and provide the CLSID_ROWSET_INMEMORY as the *guid* member.</span></span> <span data-ttu-id="15ffd-108">テーブル値パラメーターのサーバーの型名は、IOpenRowset::OpenRowset の使用時に *pTableID* の *pwszName* メンバーに指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="15ffd-108">The server type name for the table-valued parameter must be specified in the *pwszName* member of *pTableID* when using IOpenRowset::OpenRowset.</span></span> <span data-ttu-id="15ffd-109">テーブル値パラメーターの行セット オブジェクトは、標準の SQL Server Native Client OLE DB プロバイダー オブジェクトと同様に動作します。</span><span class="sxs-lookup"><span data-stu-id="15ffd-109">The table-valued parameter rowset object behaves like a regular SQL Server Native Client OLE DB Provider object.</span></span>  
  
```  
const GUID CLSID_ROWSET_TVP =   
{0xc7ef28d5, 0x7bee, 0x443f, {0x86, 0xda, 0xe3, 0x98, 0x4f, 0xcd, 0x4d, 0xf9}};  
  
CoType RowsetTVP  
{  
[mandatory] interface IAccessor;  
[mandatory] interface IColumnsInfo;  
[mandatory] interface IConvertType;  
[mandatory] interface IRowset;  
[mandatory] interface IRowsetInfo;  
[optional]  interface IColumnsRowset;  
[optional]  interface IRowsetChange;  
[optional]  interface ISupportErrorInfo;  
};  
```  
  
## <a name="dbtype_table"></a><span data-ttu-id="15ffd-110">DBTYPE_TABLE</span><span class="sxs-lookup"><span data-stu-id="15ffd-110">DBTYPE_TABLE</span></span>  
 <span data-ttu-id="15ffd-111">新しい型 DBTYPE_TABLE はテーブル型を表します。</span><span class="sxs-lookup"><span data-stu-id="15ffd-111">A new type, DBTYPE_TABLE, represents a table type.</span></span> <span data-ttu-id="15ffd-112">この型は、DBTYPE を必要とするさまざまな OLE DB インターフェイスのテーブル値パラメーターを示します。</span><span class="sxs-lookup"><span data-stu-id="15ffd-112">This type specifies table-valued parameters in various OLE DB interfaces where a DBTYPE is required.</span></span>  
  
```  
#define DBTYPE_TABLE (143)  
```  
  
 <span data-ttu-id="15ffd-113">DBTYPE_TABLE の形式は、DBTYPE_IUNKNOWN と同じです。</span><span class="sxs-lookup"><span data-stu-id="15ffd-113">DBTYPE_TABLE has the same format as DBTYPE_IUNKNOWN.</span></span> <span data-ttu-id="15ffd-114">これは、データ バッファー内のオブジェクトへのポインターです。</span><span class="sxs-lookup"><span data-stu-id="15ffd-114">It is a pointer to an object in the data buffer.</span></span> <span data-ttu-id="15ffd-115">バインドでの完全な指定のため、コンシューマーは、行セット オブジェクト インターフェイス (IID_IRowset) の 1 つに *iid* を設定して、DBOBJECT バッファーをいっぱいにします。</span><span class="sxs-lookup"><span data-stu-id="15ffd-115">For complete specification in the bindings, the consumer fills up the DBOBJECT buffer, with *iid* set to one of the rowset object interfaces (IID_IRowset).</span></span> <span data-ttu-id="15ffd-116">DBOBJECT がバインドで指定されない場合は、IID_IRowset が想定されます。</span><span class="sxs-lookup"><span data-stu-id="15ffd-116">If no DBOBJECT is specified in the bindings, IID_IRowset will be assumed.</span></span>  
  
 <span data-ttu-id="15ffd-117">DBTYPE_TABLE とその他の型との間の変換はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="15ffd-117">Conversions to and from DBTYPE_TABLE for any other types are not supported.</span></span> <span data-ttu-id="15ffd-118">IConvertType::CanConvert は、DBTYPE_TABLE から DBTYPE_TABLE への変換以外の要求に対するサポートされない変換について、S_FALSE を返します。</span><span class="sxs-lookup"><span data-stu-id="15ffd-118">IConvertType::CanConvert will return S_FALSE for unsupported conversion for any request other than DBTYPE_TABLE to DBTYPE_TABLE conversion.</span></span> <span data-ttu-id="15ffd-119">これは、Command オブジェクトの DBCONVERTFLAGS_PARAMETER を想定します。</span><span class="sxs-lookup"><span data-stu-id="15ffd-119">This assumes DBCONVERTFLAGS_PARAMETER on the Command object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="15ffd-120">メソッド</span><span class="sxs-lookup"><span data-stu-id="15ffd-120">Methods</span></span>  
 <span data-ttu-id="15ffd-121">テーブル値パラメーターをサポートする OLE DB メソッドの詳細については、「[OLE DB テーブル値パラメーターの型のサポート (メソッド)](ole-db-table-valued-parameter-type-support-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15ffd-121">For information about OLE DB methods that support table-valued parameters, see [OLE DB Table-Valued Parameter Type Support &#40;Methods&#41;](ole-db-table-valued-parameter-type-support-methods.md).</span></span>  
  
## <a name="properties"></a><span data-ttu-id="15ffd-122">Properties</span><span class="sxs-lookup"><span data-stu-id="15ffd-122">Properties</span></span>  
 <span data-ttu-id="15ffd-123">テーブル値パラメーターをサポートする OLE DB プロパティの詳細については、「[OLE DB テーブル値パラメーターの型のサポート (プロパティ)](ole-db-table-valued-parameter-type-support-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15ffd-123">For information about OLE DB properties that support table-valued parameters, see [OLE DB Table-Valued Parameter Type Support &#40;Properties&#41;](ole-db-table-valued-parameter-type-support-properties.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ffd-124">参照</span><span class="sxs-lookup"><span data-stu-id="15ffd-124">See Also</span></span>  
 <span data-ttu-id="15ffd-125">[テーブル値パラメーター &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span><span class="sxs-lookup"><span data-stu-id="15ffd-125">[Table-Valued Parameters &#40;OLE DB&#41;](table-valued-parameters-ole-db.md) </span></span>  
 [<span data-ttu-id="15ffd-126">テーブル値パラメーターの使用 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="15ffd-126">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-how-to/use-table-valued-parameters-ole-db.md)  
  
  
