---
title: 大きな値の型の使用 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- large value data types
- SQLNCLI, large value types
- SQL Server Native Client, large value types
- data access [SQL Server Native Client], large value types
- SQL Server Native Client ODBC driver, large value data types
- SQL Server Native Client OLE DB provider, large value data types
ms.assetid: 4a58b05c-8848-44bb-8704-f9f409efa5af
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a2e93ee36eb4bfadf18c5b78f552380d1c94266
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643284"
---
# <a name="using-large-value-types"></a><span data-ttu-id="a4df0-102">大きな値をとるデータ型の使用</span><span class="sxs-lookup"><span data-stu-id="a4df0-102">Using Large Value Types</span></span>
  <span data-ttu-id="a4df0-103">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] より前のバージョンでは、大きな値をとるデータ型を使用して作業する場合に特別な処理が必要でした。</span><span class="sxs-lookup"><span data-stu-id="a4df0-103">Before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], working with large value data types required special handling.</span></span> <span data-ttu-id="a4df0-104">大きな値のデータ型とは、最大行サイズの 8 KB を超えるデータ型のことです。</span><span class="sxs-lookup"><span data-stu-id="a4df0-104">Large value data types are those that exceed the maximum row size of 8 KB.</span></span> [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]<span data-ttu-id="a4df0-105">では、 **varchar**、 **nvarchar** 、および**varbinary**データ型の**max**指定子が導入され、2 ^ 31-1 バイトの大きさの値を格納できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a4df0-105">introduced a **max** specifier for **varchar**, **nvarchar** and **varbinary** data types to allow storage of values as large as 2^31 -1 bytes.</span></span> <span data-ttu-id="a4df0-106">テーブルの列と変数では [!INCLUDE[tsql](../../../includes/tsql-md.md)] 、 **varchar (max)**、 **nvarchar (max)** 、または**varbinary (max)** データ型を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-106">Table columns and [!INCLUDE[tsql](../../../includes/tsql-md.md)] variables may specify **varchar(max)**, **nvarchar(max)** or **varbinary(max)** data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4df0-107">大きな値をとるデータ型は、最大サイズを 1 ～ 8 KB に制限できます。また、サイズを無制限にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-107">Large value data types can have a maximum size between 1 and 8 KB, or they can be specified as unlimited.</span></span>  
  
 <span data-ttu-id="a4df0-108">以前は、**text**、**ntext**、**image** などの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データ型のみにこのようなサイズを指定できました。</span><span class="sxs-lookup"><span data-stu-id="a4df0-108">Previously, only [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] data types such as **text**, **ntext** and **image** could attain such lengths.</span></span> <span data-ttu-id="a4df0-109">**Varchar**、 **nvarchar** 、および**varbinary**の**max**指定子は、これらのデータ型を冗長化しました。</span><span class="sxs-lookup"><span data-stu-id="a4df0-109">The **max** specifier for **varchar**, **nvarchar** and **varbinary** made these data types redundant.</span></span> <span data-ttu-id="a4df0-110">ただし、これらの大きなデータ型も引き続き使用できるので、OLE DB や ODBC データ アクセス コンポーネントに対する大部分のインターフェイスは変更されません。</span><span class="sxs-lookup"><span data-stu-id="a4df0-110">However, because long data types are still available, most of the interfaces to the OLE DB and ODBC data access components will remain the same.</span></span> <span data-ttu-id="a4df0-111">以前のリリースとの互換性を維持するために、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーの DBCOLUMNFLAGS_ISLONG フラグと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーの SQL_LONGVARCHAR はこれまでどおり使用されます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-111">For backward compatibility with prior releases, the DBCOLUMNFLAGS_ISLONG flag in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider, and the SQL_LONGVARCHAR in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver remain in use.</span></span> <span data-ttu-id="a4df0-112">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以降用に作成されたプロバイダーやドライバーでは、最大長を無制限に設定する場合、新しいデータ型に対して、DBCOLUMNFLAGS_ISLONG や SQL_LONGVARCHAR といった表現を引き続き使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-112">Providers and drivers written against [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and later continue to use these terms for the new types when set to unlimited maximum length.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4df0-113">**varchar(max)** データ型、**nvarchar(max)** データ型、**varbinary(max)** データ型を、ストアド プロシージャの入力パラメーターの型や出力パラメーターの型、または関数の戻り値の型として指定したり、[CAST と CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql) の各関数に指定することもできます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-113">You can also specify **varchar(max)**, **nvarchar(max)**, and **varbinary(max)** data types as input and output parameter types of stored procedures, function return types, or in [CAST and CONVERT](/sql/t-sql/functions/cast-and-convert-transact-sql) functions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a4df0-114">データをレプリケートする場合は、 [max text repl size サーバー構成オプション](../../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md)を-1 に構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4df0-114">If replicating data you may need to configure the [max text repl size server configuration option](../../../database-engine/configure-windows/configure-the-max-text-repl-size-server-configuration-option.md) to -1.</span></span>  
  
## <a name="sql-server-native-client-ole-db-provider"></a><span data-ttu-id="a4df0-115">SQL Server Native Client OLE DB プロバイダー</span><span class="sxs-lookup"><span data-stu-id="a4df0-115">SQL Server Native Client OLE DB Provider</span></span>  
 <span data-ttu-id="a4df0-116">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーは、 **varchar (max)**、 **varbinary (max)**、および**nvarchar (max)** 型をそれぞれ DBTYPE_STR、DBTYPE_BYTES、および DBTYPE_WSTR として公開します。</span><span class="sxs-lookup"><span data-stu-id="a4df0-116">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes the **varchar(max)**, **varbinary(max)**, and **nvarchar(max)** types as DBTYPE_STR, DBTYPE_BYTES, and DBTYPE_WSTR, respectively.</span></span>  
  
 <span data-ttu-id="a4df0-117">**max** のサイズが無制限に設定されている列の **varchar(max)** データ型、**varbinary(max)** データ型、**nvarchar(max)** データ型は、列のデータ型を返す主要な OLE DB スキーマ行セットやインターフェイスでは ISLONG で表されます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-117">The data types **varchar(max)**, **varbinary(max)**, and **nvarchar(max)** in columns with the **max** size set to unlimited are represented as an ISLONG through the core OLE DB schema rowsets and interfaces returning column data types.</span></span>  
  
 <span data-ttu-id="a4df0-118">コマンド オブジェクトの **IAccessor** の実装は、DBTYPE_IUNKNOWN としてバインドできるように変更されています。</span><span class="sxs-lookup"><span data-stu-id="a4df0-118">The command object's **IAccessor** implementation has been changed to allow binding as DBTYPE_IUNKNOWN.</span></span> <span data-ttu-id="a4df0-119">コンシューマーが DBTYPE_IUNKNOWN を指定し、*pObject* を NULL に設定すると、プロバイダーからコンシューマーに **ISequentialStream** インターフェイスが返されます。これにより、コンシューマーは **varchar(max)** データ、**nvarchar(max)** データ、または **varbinary(max)** データを出力変数からストリームできます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-119">If the consumer specifies DBTYPE_IUNKNOWN and sets *pObject* to null, the provider will return the **ISequentialStream** interface to the consumer so that the consumer can stream **varchar(max)**, **nvarchar(max)**, or **varbinary(max)** data out of output variables.</span></span>  
  
 <span data-ttu-id="a4df0-120">ストリーミングされる出力パラメーターの値は、すべての結果行の後に返されます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-120">Streamed output parameter values are returned after any result rows.</span></span> <span data-ttu-id="a4df0-121">アプリケーションが、返される出力パラメーター値をすべて使用しないうちに **IMultipleResults::GetResult** を呼び出して次の結果セットに移動しようとすると、DB_E_OBJECTOPEN が返されます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-121">If the application attempts to move on to the next result set by calling **IMultipleResults::GetResult** without consuming all the returned output parameter values, DB_E_OBJECTOPEN will be returned.</span></span>  
  
 <span data-ttu-id="a4df0-122">ストリーミングをサポートするために、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、可変長パラメーターに順番にアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4df0-122">In order to support streaming, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider requires variable length parameters to be accessed in sequential order.</span></span> <span data-ttu-id="a4df0-123">つまり、**varchar(max)** 列、**nvarchchar(max)** 列、**varbinary(max)** 列や出力パラメーターを DBTYPE_IUNKNOWN. にバインドするときは必ず、DBPROP_ACCESSORDER を DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS または DBPROPVAL_AO_SEQUENTIAL のいずれかに設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4df0-123">This means that DBPROP_ACCESSORDER must be set to either DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS or DBPROPVAL_AO_SEQUENTIAL whenever **varchar(max)**, **nvarchchar(max)**, or **varbinary(max)** columns or output parameters are bound to DBTYPE_IUNKNOWN.</span></span> <span data-ttu-id="a4df0-124">このアクセス順序の制限に従わないと、**IRowset::GetData** への呼び出しは DBSTATUS_E_UNAVAILABLE で失敗します。</span><span class="sxs-lookup"><span data-stu-id="a4df0-124">Calls to **IRowset::GetData** will fail with DBSTATUS_E_UNAVAILABLE if this access order restriction is not adhered to.</span></span> <span data-ttu-id="a4df0-125">DBTYPE_IUNKNOWN を使用する出力バインドがない場合は、この制限は適用されません。</span><span class="sxs-lookup"><span data-stu-id="a4df0-125">This restriction does not apply when there are no output bindings using DBTYPE_IUNKNOWN.</span></span>  
  
 <span data-ttu-id="a4df0-126">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーでは、大きな値のデータ型の DBTYPE_IUNKNOWN として出力パラメーターをバインドすることもできます。これにより、ストアドプロシージャがクライアントに DBTYPE_IUNKNOWN として公開される戻り値として大きな値の型を返すシナリオが容易になります。</span><span class="sxs-lookup"><span data-stu-id="a4df0-126">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider also supports binding output parameters as DBTYPE_IUNKNOWN for large value data types to facilitate scenarios where a stored procedure returns large value types as return values that are exposed as DBTYPE_IUNKNOWN to the client.</span></span>  
  
 <span data-ttu-id="a4df0-127">このようなデータ型を使用して作業するために、アプリケーションでは次のような操作を行えます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-127">To work with these types, an application has the following options:</span></span>  
  
-   <span data-ttu-id="a4df0-128">列の基本型にバインド可能な型としてバインドします (たとえば nvarchar(max) の場合は、nvarchar にバインド可能な型としてバインドします)。</span><span class="sxs-lookup"><span data-stu-id="a4df0-128">Bind as a type that has supported bindings with the base type of the column (eg for nvarchar(max), bind as a type that can be bound to nvarchar).</span></span> <span data-ttu-id="a4df0-129">以前よりも大きな値を格納できるようになりましたが、バッファーのサイズが十分でない場合は、基本型に応じて値が切り捨てられます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-129">If the buffer is not big enough truncation will occur, exactly as for the base type, albeit that larger values are now available.</span></span>  
  
-   <span data-ttu-id="a4df0-130">列の基本型に変換可能な型としてバインドし、DBTYPE_BYREF も指定します。</span><span class="sxs-lookup"><span data-stu-id="a4df0-130">Bind as a type that has supported conversions with the base type of the column and also specify DBTYPE_BYREF.</span></span>  
  
-   <span data-ttu-id="a4df0-131">DBTYPE_IUNKNOWN としてバインドし、ストリーミングを使用します。</span><span class="sxs-lookup"><span data-stu-id="a4df0-131">Bind as DBTYPE_IUNKNOWN and use streaming.</span></span>  
  
 <span data-ttu-id="a4df0-132">列の最大サイズを報告するときに、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは次のことを報告します。</span><span class="sxs-lookup"><span data-stu-id="a4df0-132">When reporting the maximum size of a column, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider will report:</span></span>  
  
-   <span data-ttu-id="a4df0-133">定義された最大サイズ。たとえば、 **varchar (** 2000) 列の場合は2000です **。**</span><span class="sxs-lookup"><span data-stu-id="a4df0-133">The defined maximum size, which for example, is 2000 for a **varchar(** 2000 **)** column, or</span></span>  
  
-   <span data-ttu-id="a4df0-134">**varchar(max)** 列が 0 に等しい場合の値、"無制限"。</span><span class="sxs-lookup"><span data-stu-id="a4df0-134">The value "unlimited" which in the case of a **varchar(max)** column equals ~0.</span></span> <span data-ttu-id="a4df0-135">この値は、DBCOLUMN_COLUMNSIZE メタデータのプロパティに設定されます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-135">This value is set for the DBCOLUMN_COLUMNSIZE metadata property.</span></span>  
  
 <span data-ttu-id="a4df0-136">標準の変換規則が **varchar(max)** 列に適用されます。つまり、**varchar(** 2000 **)** 列で有効なすべての変換は、**varchar(max)** 列でも有効です。</span><span class="sxs-lookup"><span data-stu-id="a4df0-136">The standard conversion rules will apply to a **varchar(max)** column, meaning that any conversion that is valid for a **varchar(** 2000 **)** column will also be valid for a **varchar(max)** column.</span></span> <span data-ttu-id="a4df0-137">**nvarchar(max)** 列と **varbinary(max)** 列についても同じことが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="a4df0-137">The same is true for **nvarchar(max)** and **varbinary(max)** columns.</span></span>  
  
 <span data-ttu-id="a4df0-138">大きな値をとるデータ型を取得するとき最も効果的な方法は、DBTYPE_IUNKNOWN としてバインドし、行セット プロパティ DBPROP_ACCESSORDER を DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS に設定することです。</span><span class="sxs-lookup"><span data-stu-id="a4df0-138">When retrieving large value types, the most efficient approach is to bind as DBTYPE_IUNKNOWN and set the rowset property DBPROP_ACCESSORDER to DBPROPVAL_AO_SEQUENTIALSTORAGEOBJECTS.</span></span> <span data-ttu-id="a4df0-139">これにより、次の例で示すように、値が中間バッファーなしでネットワークから直接ストリーミングされます。</span><span class="sxs-lookup"><span data-stu-id="a4df0-139">This will cause the value to be streamed directly from the network with no intermediate buffering, as in the following example:</span></span>  
  
```  
#define UNICODE  
#define _UNICODE  
#define DBINITCONSTANTS  
#define INITGUID  
#define OLEDBVER 0x0250  // To include the correct interfaces.  
  
#include <stdio.h>  
#include <tchar.h>  
#include <stddef.h>  
#include <iostream>  
  
using std::cout;  
using std::endl;  
  
#include <windows.h>  
  
#include <oledb.h>  
#include "sqlncli.h"  
#include <oledberr.h>  
  
#define CHKHR_GOTO(hr, errMsg, Label) \  
   if (FAILED(hr)) \  
   { \  
      cout << errMsg << endl; \  
      goto Label; \  
   }  
  
#define MAX_COL_SIZE 8000  
  
// ROUNDUP on all platforms pointers must be aligned properly.  
#define ROUNDUP_AMOUNT 8  
#define ROUNDUP_(size,amount) (((ULONG)(size)+((amount)-1))&~((amount)-1))  
#define ROUNDUP(size) ROUNDUP_(size, ROUNDUP_AMOUNT)  
  
HRESULT InitializeAndEstablishConnection(IDBInitialize** ppIDBInitialize);  
void UnInitializeConnection(IDBInitialize* pIDBInitialize);  
HRESULT CreateAndSetCommand(IDBInitialize* pIDBInitialize, ICommandText** ppICommandText);  
HRESULT ProcessResultSet(IRowset* pIRowset);  
  
void DisplayTime()  
{  
   SYSTEMTIME st;  
   GetSystemTime(&st);  
   cout<< st.wHour << ":" << st.wMinute << ":" << st.wSecond << "." << st.wMilliseconds << endl;  
}  
  
void main()  
{  
   HRESULT hr;  
   IDBInitialize* pIDBInitialize = NULL;  
   ICommandText* pICommandText = NULL;  
   IMultipleResults* pIMultipleResults = NULL;  
   IRowset* pIRowset = NULL;  
  
   hr = InitializeAndEstablishConnection(&pIDBInitialize);  
   CHKHR_GOTO(hr, L"Failed to establish connection.", _ExitMain);  
  
   hr = CreateAndSetCommand(pIDBInitialize, &pICommandText);  
   CHKHR_GOTO(hr, L"Failed to set up command object.", _ExitMain);  
  
   DisplayTime();  
  
   hr = pICommandText->Execute(NULL,   
      IID_IMultipleResults,   
      NULL,   
      NULL,   
     (IUnknown **) &pIMultipleResults);  
  
   CHKHR_GOTO(hr, L"Failed to execute command.", _ExitMain);  
  
   while (1)  
   {  
      hr = pIMultipleResults->GetResult(  
         NULL,   
         DBRESULTFLAG_DEFAULT,   
         IID_IRowset,   
         NULL,   
         (IUnknown**)&pIRowset);  
  
   CHKHR_GOTO(hr, L"Failed to obtain a results from MR object.", _ExitMain);  
  
   if (hr == DB_S_NORESULT)  
      break;  
  
      if (pIRowset)  
      {  
         hr = ProcessResultSet(pIRowset);   
         CHKHR_GOTO(hr, L"Failed to process the current Rowset.", _ExitMain);  
  
         pIRowset->Release();  
         pIRowset = NULL;  
      }  
   }  
  
   DisplayTime();  
  
_ExitMain:  
  
   if (pIRowset)  
   {  
      pIRowset->Release();  
      pIRowset = NULL;  
   }  
  
   if (pIMultipleResults)  
   {  
      pIMultipleResults->Release();  
      pIMultipleResults = NULL;  
   }  
  
   if (pICommandText)  
   {  
      pICommandText->Release();  
      pICommandText = NULL;  
   }  
  
   UnInitializeConnection(pIDBInitialize);  
   return;  
};  
  
HRESULT InitializeAndEstablishConnection(IDBInitialize** ppIDBInitialize)  
{  
   HRESULT hr;  
   IDBInitialize* pIDBInitialize = NULL;  
   IDBProperties* pIDBProperties = NULL;  
  
   const int NUM_DBINIT_PROPS = 3;  
   const wchar_t* const g_wszServer = L".";  
   const wchar_t* const g_wszCatalog = L"AdventureWorks";  
   const wchar_t* const g_wszSecurity = L"SSPI";  
  
   DBPROPSET rgdbPropSetInit[1];  
   DBPROP rgdbPropInit [NUM_DBINIT_PROPS];  
  
   *ppIDBInitialize = NULL;  
   hr = CoInitialize(NULL);  
   CHKHR_GOTO(hr, L"Failed to initialize COM.", _ExitInitialize);  
  
   hr = CoCreateInstance(CLSID_SQLNCLI11,   
      NULL,   
      CLSCTX_INPROC_SERVER,  
      IID_IDBInitialize,   
      (void**)&pIDBInitialize);  
  
   CHKHR_GOTO(hr, L"Failed to create SQLNCLI11 DataSource object.", _ExitInitialize);  
  
   for(int idxProp = 0; idxProp < NUM_DBINIT_PROPS; idxProp++)   
   {  
      VariantInit(&rgdbPropInit[idxProp].vValue);  
   }  
  
   rgdbPropInit[0].dwPropertyID = DBPROP_INIT_DATASOURCE;  
   rgdbPropInit[0].vValue.vt = VT_BSTR;  
   rgdbPropInit[0].vValue.bstrVal= SysAllocString(g_wszServer);  
   rgdbPropInit[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[0].colid = DB_NULLID;  
  
   if (rgdbPropInit[0].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropInit[1].dwPropertyID = DBPROP_INIT_CATALOG;  
   rgdbPropInit[1].vValue.vt = VT_BSTR;  
   rgdbPropInit[1].vValue.bstrVal= SysAllocString(g_wszCatalog);  
   rgdbPropInit[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[1].colid = DB_NULLID;  
  
   if (rgdbPropInit[1].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropInit[2].dwPropertyID = DBPROP_AUTH_INTEGRATED;  
   rgdbPropInit[2].vValue.vt = VT_BSTR;  
   rgdbPropInit[2].vValue.bstrVal= SysAllocString(g_wszSecurity);  
   rgdbPropInit[2].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgdbPropInit[2].colid = DB_NULLID;  
  
   if (rgdbPropInit[2].vValue.bstrVal == NULL)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitInitialize;  
   }  
  
   rgdbPropSetInit[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgdbPropSetInit[0].cProperties = NUM_DBINIT_PROPS;  
   rgdbPropSetInit[0].rgProperties = rgdbPropInit;  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties, (void **)&pIDBProperties);  
   CHKHR_GOTO(hr, L"Failed to QI DataSource object for IDBProperties.", _ExitInitialize);  
  
   hr = pIDBProperties->SetProperties(1, rgdbPropSetInit);   
   CHKHR_GOTO(hr, L"Failed to set DataSource object Properties.", _ExitInitialize);  
  
   pIDBProperties->Release();  
   pIDBProperties = NULL;  
  
   hr = pIDBInitialize->Initialize();  
   CHKHR_GOTO(hr, L"Failed to establish connection with the server.", _ExitInitialize);  
  
_ExitInitialize:  
  
   if (pIDBProperties)  
   {  
      pIDBProperties->Release();  
      pIDBProperties = NULL;  
   }  
  
   if (FAILED(hr))  
   {  
      if (pIDBInitialize)  
      {  
         pIDBInitialize->Release();  
         pIDBInitialize = NULL;  
      }  
   }  
  
   *ppIDBInitialize = pIDBInitialize;  
   return hr;  
}  
  
void UnInitializeConnection(IDBInitialize* pIDBInitialize)  
{  
   if (pIDBInitialize)  
   {  
      pIDBInitialize->Uninitialize();  
      pIDBInitialize->Release();  
      pIDBInitialize = NULL;  
   }  
   CoUninitialize();  
}  
  
HRESULT CreateAndSetCommand(IDBInitialize* pIDBInitialize, ICommandText** ppICommandText)  
{  
   HRESULT hr;  
   IDBCreateSession* pIDBCreateSession = NULL;  
   IDBCreateCommand* pIDBCreateCommand = NULL;  
   ICommandText* pICommandText = NULL;  
   ICommandProperties* pICommandProperties = NULL;  
   DBPROPSET rgCmdPropSet[1];  
   DBPROP rgCmdProperties[1];  
  
const wchar_t* const g_wCmdString = L"declare @x xml, @y nvarchar(max); select @x = (SELECT * FROM Sales.SalesOrderHeader FOR XML AUTO); select @x;";  
  
   *ppICommandText = NULL;  
  
   if (!pIDBInitialize)  
   {  
      hr = E_FAIL;  
      goto _ExitCreateAndSetCommand;  
   }  
  
   hr = pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void**) &pIDBCreateSession);  
   CHKHR_GOTO(hr, L"Failed to obtain IDBCreateSession interface from DSO.", _ExitCreateAndSetCommand);  
  
   hr = pIDBCreateSession->CreateSession(  
      NULL,   
      IID_IDBCreateCommand,   
      (IUnknown**) &pIDBCreateCommand);  
  
   CHKHR_GOTO(hr, L"Failed to Create a Session for command execution.", _ExitCreateAndSetCommand);  
  
   hr = pIDBCreateCommand->CreateCommand(  
      NULL,   
      IID_ICommandText,   
      (IUnknown**)&pICommandText);  
  
   CHKHR_GOTO(hr, L"Failed to Create a Command object.", _ExitCreateAndSetCommand);  
  
   hr = pICommandText->SetCommandText(DBGUID_DBSQL, g_wCmdString);  
   CHKHR_GOTO(hr, L"Failed to Set Command Text.", _ExitCreateAndSetCommand);  
  
   hr = pICommandText->QueryInterface(IID_ICommandProperties, (void**) &pICommandProperties);  
   CHKHR_GOTO(hr, L"Failed to obtain ICommandProperties interface from the command object.", _ExitCreateAndSetCommand);  
  
   rgCmdProperties[0].dwPropertyID = DBPROP_ACCESSORDER;  
   rgCmdProperties[0].vValue.vt = VT_I4;  
   rgCmdProperties[0].vValue.lVal = DBPROPVAL_AO_SEQUENTIAL;  
   rgCmdProperties[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   rgCmdProperties[0].colid = DB_NULLID;  
  
   rgCmdPropSet[0].guidPropertySet = DBPROPSET_ROWSET;  
   rgCmdPropSet[0].cProperties = 1;  
   rgCmdPropSet[0].rgProperties = rgCmdProperties;  
  
   hr = pICommandProperties->SetProperties(1, rgCmdPropSet);   
   CHKHR_GOTO(hr, L"Failed to Set Command object Properties.", _ExitCreateAndSetCommand);  
  
_ExitCreateAndSetCommand:  
  
   if (pICommandProperties)  
   {  
      pICommandProperties->Release();  
      pICommandProperties = NULL;  
   }  
  
   if (pIDBCreateCommand)  
   {  
      pIDBCreateCommand->Release();  
      pIDBCreateCommand = NULL;  
   }  
  
   if (pIDBCreateSession)  
   {  
      pIDBCreateSession->Release();  
      pIDBCreateSession = NULL;  
   }  
  
   if (FAILED(hr))  
   {  
      if (pICommandText)  
      {  
         pICommandText->Release();  
         pICommandText = NULL;  
      }  
   }  
  
   *ppICommandText = pICommandText;  
   return hr;  
}  
  
HRESULT ProcessResultSet(IRowset* pIRowset)  
{  
   HRESULT hr;  
  
   IColumnsInfo* pIColumnsInfo = NULL;  
   DBCOLUMNINFO* pDBColumnInfo = NULL;  
   ULONG lNumCols = 0;  
   wchar_t* pStringsBuffer = NULL;  
  
   DBBINDING* pBindings = NULL;  
   DBOBJECT dbobj;  
   ULONG idxBinding;  
   IAccessor* pIAccessor = NULL;  
   HACCESSOR hAccessor = DB_NULL_HACCESSOR;  
   HROW hRows[1] = {DB_NULL_HROW};  
   HROW* pRow = &hRows[0];  
   BYTE* pBuffer = NULL;  
  
   ULONG lNumRowsRetrieved;  
   DBLENGTH dwOffset = 0;  
  
   hr = pIRowset->QueryInterface(IID_IColumnsInfo, (void **)&pIColumnsInfo);  
   CHKHR_GOTO(hr, L"Failed to QI Rowset for IColumnsInfo.", _ExitProcessResultSet);  
  
   hr = pIColumnsInfo->GetColumnInfo(&lNumCols, &pDBColumnInfo, &pStringsBuffer);  
   CHKHR_GOTO(hr, L"Failed to obtain Column Information.", _ExitProcessResultSet);  
  
   pBindings = new DBBINDING[lNumCols];  
  
   if (!pBindings)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitProcessResultSet;  
   }  
  
   memset(pBindings, 0, sizeof(DBBINDING) * lNumCols);  
  
   dbobj.dwFlags = STGM_READ;  
   dbobj.iid = IID_ISequentialStream;  
  
   for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)   
   {  
      pBindings[idxBinding].iOrdinal = idxBinding + 1;  
      pBindings[idxBinding].obStatus = dwOffset;  
      pBindings[idxBinding].obLength = dwOffset + sizeof(DBSTATUS);  
      pBindings[idxBinding].obValue = dwOffset + sizeof(DBSTATUS) + sizeof(DBLENGTH);  
  
      pBindings[idxBinding].pTypeInfo = NULL;  
      pBindings[idxBinding].pBindExt = NULL;  
      pBindings[idxBinding].dwPart = DBPART_VALUE | DBPART_LENGTH | DBPART_STATUS;  
      pBindings[idxBinding].dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
      pBindings[idxBinding].eParamIO = DBPARAMIO_NOTPARAM;  
      pBindings[idxBinding].bPrecision = pDBColumnInfo[idxBinding].bPrecision;  
      pBindings[idxBinding].bScale = pDBColumnInfo[idxBinding].bScale;  
  
      pBindings[idxBinding].cbMaxLen = 0;  
      pBindings[idxBinding].wType = DBTYPE_WSTR;  
  
   // Determine the maximum number of bytes required in our buffer to  
   // contain the Unicode string representation of the provider's native  
   // data type, including room for the NULL-termination character  
   switch( pDBColumnInfo[idxBinding].wType )  
   {  
      case DBTYPE_NULL:  
      case DBTYPE_EMPTY:  
      case DBTYPE_I1:  
      case DBTYPE_I2:  
      case DBTYPE_I4:  
      case DBTYPE_UI1:  
      case DBTYPE_UI2:  
      case DBTYPE_UI4:  
      case DBTYPE_R4:  
      case DBTYPE_BOOL:  
      case DBTYPE_I8:  
      case DBTYPE_UI8:  
      case DBTYPE_R8:  
      case DBTYPE_CY:  
      case DBTYPE_ERROR:  
      // When the above types are converted to a string, they  
      // will all fit into 25 characters, so use that plus space  
      // for the NULL-terminator.  
  
      pBindings[idxBinding].cbMaxLen = (25 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_DECIMAL:  
      case DBTYPE_NUMERIC:  
      case DBTYPE_DATE:  
      case DBTYPE_DBDATE:  
      case DBTYPE_DBTIMESTAMP:  
      case DBTYPE_GUID:  
      // Converted to a string, the above types will all fit into  
      // 50 characters, so use that plus space for the terminator.  
  
      pBindings[idxBinding].cbMaxLen = (50 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_BYTES:  
      // In converting DBTYPE_BYTES to a string, each byte  
      // becomes two characters (e.g. 0xFF -> "FF"), so we  
      // will use double the maximum size of the column plus  
      // include space for the NULL-terminator.  
  
      pBindings[idxBinding].cbMaxLen = (pDBColumnInfo[idxBinding].ulColumnSize * 2 + 1) * sizeof(WCHAR);  
      break;  
  
      case DBTYPE_STR:  
      case DBTYPE_WSTR:  
      case DBTYPE_BSTR:  
      // Going from a string to our string representation,  
      // we can just take the maximum size of the column,  
      // a count of characters, and include space for the  
      // terminator, which is not included in the column size.  
  
      pBindings[idxBinding].cbMaxLen = (pDBColumnInfo[idxBinding].ulColumnSize + 1) * sizeof(WCHAR);  
      break;  
  
      default:  
      // For any other type, we will simply use our maximum  
      // column buffer size, since the display size of these  
      // columns may be variable (e.g. DBTYPE_VARIANT) or  
      // unknown (e.g. provider-specific types).  
      pBindings[idxBinding].cbMaxLen = MAX_COL_SIZE;  
      break;  
   }  
  
   // If the provider's native data type for this column is  
   // DBTYPE_IUNKNOWN or this is a BLOB column and the user  
   // has requested that we bind BLOB columns as ISequentialStream  
   // objects, bind this column as an ISequentialStream object if  
   // the provider supports our creating another ISequentialStream  
   // binding.  
   if(pDBColumnInfo[idxBinding].dwFlags & DBCOLUMNFLAGS_ISLONG)  
   {  
      pBindings[idxBinding].wType = DBTYPE_IUNKNOWN;  
  
      pBindings[idxBinding].cbMaxLen = sizeof(ISequentialStream*);  
  
      pBindings[idxBinding].pObject = (DBOBJECT *)CoTaskMemAlloc(sizeof(DBOBJECT));  
  
      if (!pBindings[idxBinding].pObject)  
      {  
         hr = E_OUTOFMEMORY;  
         goto _ExitProcessResultSet;  
      }  
  
      // Direct the provider to create an ISequentialStream  
      // object over the data for this column.  
      pBindings[idxBinding].pObject->iid = IID_ISequentialStream;  
  
      // We want read access on the ISequentialStream  
      // object that the provider will create for us  
      pBindings[idxBinding].pObject->dwFlags = STGM_READ;  
      }  
  
      // Ensure that the bound maximum length is no more than the  
      // maximum column size in bytes that we've defined.  
      pBindings[idxBinding].cbMaxLen = min(pBindings[idxBinding].cbMaxLen, MAX_COL_SIZE);  
  
      // Update the offset past the end of this column's data, so  
      // that the next column will begin in the correct place in  
      // the buffer.  
      dwOffset = pBindings[idxBinding].cbMaxLen + pBindings[idxBinding].obValue;  
  
      // Ensure that the data for the next column will be correctly  
      // aligned for all platforms, or, if we're done with columns,  
      // that if we allocate space for multiple rows that the data  
      // for every row is correctly aligned.  
      dwOffset = ROUNDUP(dwOffset);  
   }  
  
   hr = pIRowset->QueryInterface(IID_IAccessor, (void **) &pIAccessor);  
   CHKHR_GOTO(hr, L"Failed to obtain Accessor interface", _ExitProcessResultSet);  
  
   hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA,  
      lNumCols,  
      pBindings,  
      0,  
      &hAccessor,  
      NULL);  
  
   CHKHR_GOTO(hr, L"Failed to create Accessor", _ExitProcessResultSet);  
   for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)   
   {  
      cout << pDBColumnInfo[idxBinding].pwszName << endl;  
   }  
  
   lNumRowsRetrieved = 0;  
  
   hr = pIRowset->GetNextRows(  
      NULL,  
      0,  
      1,  
      &lNumRowsRetrieved,  
      &pRow);  
  
   CHKHR_GOTO(hr, L"Failed to fetch a row from the rowset", _ExitProcessResultSet);  
  
   pBuffer = new BYTE[sizeof(DBSTATUS) + sizeof(DBLENGTH) + sizeof(IUnknown*)];  
  
   if (!pBuffer)  
   {  
      hr = E_OUTOFMEMORY;  
      goto _ExitProcessResultSet;  
   }  
  
   while(lNumRowsRetrieved && hr != DB_S_ENDOFROWSET)   
   {  
      memset(pBuffer, 0, sizeof(DBSTATUS) + sizeof(DBLENGTH) + sizeof(IUnknown*));  
  
      hr = pIRowset->GetData(hRows[0], hAccessor, pBuffer);  
      CHKHR_GOTO(hr, L"Failed to obtain row data", _ExitProcessResultSet);  
  
      for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)  
      {  
         if (pBindings[idxBinding].wType == DBTYPE_IUNKNOWN)  
         {  
            BYTE pbBuff[3000];  
            ULONG cbNeeded = sizeof(pbBuff)/sizeof(BYTE);  
            ULONG cbRead;  
            ULONG cbReadTotal = 0;  
            ISequentialStream* pISequentialStream = NULL;  
  
            IUnknown* pIUnknown = *((IUnknown**)(pBuffer + pBindings[idxBinding].obValue));  
            pIUnknown->QueryInterface(IID_ISequentialStream, (void**)&pISequentialStream);  
  
            do  
            {  
               hr = pISequentialStream->Read(pbBuff, cbNeeded, &cbRead);  
               cbReadTotal += cbRead;  
            }  
            while (SUCCEEDED(hr) && hr != S_FALSE && cbRead == cbNeeded);  
  
               cout << "Total Bytes Read: " << cbReadTotal << endl;  
  
               pISequentialStream->Release();  
               pISequentialStream = NULL;  
               pIUnknown->Release();  
               pIUnknown = NULL;  
            }  
         }  
  
         pIRowset->ReleaseRows(1, pRow, NULL, NULL, NULL);  
  
         hr = pIRowset->GetNextRows(NULL,  
            0,  
            1,  
            &lNumRowsRetrieved,  
            &pRow);  
  
         CHKHR_GOTO(hr, L"Failed to fetch a row from the rowset.", _ExitProcessResultSet);  
   }  
  
_ExitProcessResultSet:  
  
   pIRowset->ReleaseRows(1, pRow, NULL, NULL, NULL);  
   delete [] pBuffer;  
  
   if (pIAccessor)  
   {  
      if (hAccessor != DB_NULL_HACCESSOR)  
      {  
         pIAccessor->ReleaseAccessor(hAccessor, NULL);  
      }  
  
      pIAccessor->Release();  
      pIAccessor = NULL;  
   }  
  
   if (pBindings)  
   {  
      for (idxBinding = 0; idxBinding < lNumCols; idxBinding++)  
      {  
         if (pBindings[idxBinding].pObject)  
         CoTaskMemFree(pBindings[idxBinding].pObject);  
      }  
   }  
  
   delete [] pBindings;  
  
   CoTaskMemFree(pDBColumnInfo);  
   CoTaskMemFree(pStringsBuffer);  
  
   if (pIColumnsInfo)  
   {  
      pIColumnsInfo->Release();  
      pIColumnsInfo = NULL;  
   }  
  
   return hr;  
}  
```  
  
 <span data-ttu-id="a4df0-140">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーが大きな値のデータ型を公開する方法の詳細については、「 [BLOB と OLE オブジェクト](../../native-client-ole-db-blobs/blobs-and-ole-objects.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4df0-140">For more information about how the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider exposes large value data types, see [BLOBs and OLE Objects](../../native-client-ole-db-blobs/blobs-and-ole-objects.md).</span></span>  
  
## <a name="sql-server-native-client-odbc-driver"></a><span data-ttu-id="a4df0-141">SQL Server Native Client ODBC ドライバー</span><span class="sxs-lookup"><span data-stu-id="a4df0-141">SQL Server Native Client ODBC Driver</span></span>  
 <span data-ttu-id="a4df0-142">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT odbc ドライバーでは、ODBC SQL データ型を受け取ったり返したりする ODBC API 関数で、 **varchar (max)**、 **varbinary (max)** 、および**nvarchar (max)** 型を SQL_VARCHAR、SQL_VARBINARY、および SQL_WVARCHAR として公開しています。</span><span class="sxs-lookup"><span data-stu-id="a4df0-142">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver exposes the **varchar(max)**, **varbinary(max)** and **nvarchar(max)** types as SQL_VARCHAR, SQL_VARBINARY, and SQL_WVARCHAR in ODBC API functions that accept or return ODBC SQL data types.</span></span>  
  
 <span data-ttu-id="a4df0-143">ドライバーでは、列の最大サイズを報告するときに次のいずれかを報告します。</span><span class="sxs-lookup"><span data-stu-id="a4df0-143">When reporting the maximum size of a column, the driver will report either:</span></span>  
  
-   <span data-ttu-id="a4df0-144">定義された最大サイズ。たとえば、 **varchar (2000)** 列の場合は2000です。</span><span class="sxs-lookup"><span data-stu-id="a4df0-144">The defined maximum size, which for example, is 2000 for a **varchar(2000)** column, or</span></span>  
  
-   <span data-ttu-id="a4df0-145">**Varchar (max)** 列の場合、"無制限" の値は0と等しくなります。</span><span class="sxs-lookup"><span data-stu-id="a4df0-145">The value "unlimited" which in the case of a **varchar(max)** column equals 0.</span></span>  
  
 <span data-ttu-id="a4df0-146">標準変換規則は**varchar (max)** 列に適用されます。つまり **、varchar (2000\*\*\*\*)** 列に対して有効な変換は、 **varchar (max)** 列に対しても有効になります。</span><span class="sxs-lookup"><span data-stu-id="a4df0-146">The standard conversion rules apply to a **varchar(max)** column, meaning that any conversion that is valid for a **varchar(** 2000 **)** column will also be valid for a **varchar(max)** column.</span></span> <span data-ttu-id="a4df0-147">**nvarchar(max)** 列と **varbinary(max)** 列についても同じことが当てはまります。</span><span class="sxs-lookup"><span data-stu-id="a4df0-147">The same is true for **nvarchar(max)** and **varbinary(max)** columns.</span></span>  
  
 <span data-ttu-id="a4df0-148">次に、大きな値データ型を使用して作業するために機能強化された ODBC API 関数の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="a4df0-148">The following is a list of the ODBC API functions that have been enhanced to work with large value data types:</span></span>  
  
-   [<span data-ttu-id="a4df0-149">SQLBindCol</span><span class="sxs-lookup"><span data-stu-id="a4df0-149">SQLBindCol</span></span>](../../native-client-odbc-api/sqlbindcol.md)  
  
-   [<span data-ttu-id="a4df0-150">SQLBindParameter</span><span class="sxs-lookup"><span data-stu-id="a4df0-150">SQLBindParameter</span></span>](../../native-client-odbc-api/sqlbindparameter.md)  
  
-   [<span data-ttu-id="a4df0-151">SQLColAttribute</span><span class="sxs-lookup"><span data-stu-id="a4df0-151">SQLColAttribute</span></span>](../../native-client-odbc-api/sqlcolattribute.md)  
  
-   [<span data-ttu-id="a4df0-152">SQLColumns</span><span class="sxs-lookup"><span data-stu-id="a4df0-152">SQLColumns</span></span>](../../native-client-odbc-api/sqlcolumns.md)  
  
-   [<span data-ttu-id="a4df0-153">SQLDescribeCol</span><span class="sxs-lookup"><span data-stu-id="a4df0-153">SQLDescribeCol</span></span>](../../native-client-odbc-api/sqldescribecol.md)  
  
-   [<span data-ttu-id="a4df0-154">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="a4df0-154">SQLDescribeParam</span></span>](../../native-client-odbc-api/sqldescribeparam.md)  
  
-   [<span data-ttu-id="a4df0-155">SQLGetData</span><span class="sxs-lookup"><span data-stu-id="a4df0-155">SQLGetData</span></span>](../../native-client-odbc-api/sqlgetdata.md)  
  
-   [<span data-ttu-id="a4df0-156">SQLGetTypeInfo</span><span class="sxs-lookup"><span data-stu-id="a4df0-156">SQLGetTypeInfo</span></span>](../../native-client-odbc-api/sqlgettypeinfo.md)  
  
## <a name="see-also"></a><span data-ttu-id="a4df0-157">参照</span><span class="sxs-lookup"><span data-stu-id="a4df0-157">See Also</span></span>  
 [<span data-ttu-id="a4df0-158">SQL Server Native Client の機能</span><span class="sxs-lookup"><span data-stu-id="a4df0-158">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
