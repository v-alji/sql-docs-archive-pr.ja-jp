---
title: IBCPSession2::BCPSetBulkMode | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- BCPSetBulkMode function
ms.assetid: babba19f-e67b-450c-b0e6-523a0f9d23ab
author: rothja
ms.author: jroth
ms.openlocfilehash: 9605ff9b8effde1b4a77ba0d8554c719a8a8d1e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644461"
---
# <a name="ibcpsession2bcpsetbulkmode"></a><span data-ttu-id="fca8a-102">IBCPSession2::BCPSetBulkMode</span><span class="sxs-lookup"><span data-stu-id="fca8a-102">IBCPSession2::BCPSetBulkMode</span></span>
  <span data-ttu-id="fca8a-103">IBCPSession2::BCPSetBulkMode には、列形式を指定するために [IBCPSession::BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md) の代替手段が用意されています。</span><span class="sxs-lookup"><span data-stu-id="fca8a-103">IBCPSession2::BCPSetBulkMode provides an alternative to [IBCPSession::BCPColFmt &#40;OLE DB&#41;](ibcpsession-bcpcolfmt-ole-db.md) for specifying the column format.</span></span> <span data-ttu-id="fca8a-104">個々の列形式属性を設定する IBCPSession::BCPColFmt とは異なり、IBCPSession2::BCPSetBulkMode では、すべての属性を設定します。</span><span class="sxs-lookup"><span data-stu-id="fca8a-104">Unlike IBCPSession::BCPColFmt, which sets individual column format attributes, IBCPSession2::BCPSetBulkMode sets all attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fca8a-105">構文</span><span class="sxs-lookup"><span data-stu-id="fca8a-105">Syntax</span></span>  
  
```  
  
HRESULT BCPSetBulkMode (  
      int property,  
   void * pField,  
   int cbField,  
   void * pRow,  
   int cbRow  
);  
```  
  
## <a name="arguments"></a><span data-ttu-id="fca8a-106">引数</span><span class="sxs-lookup"><span data-stu-id="fca8a-106">Arguments</span></span>  
 <span data-ttu-id="fca8a-107">*property*</span><span class="sxs-lookup"><span data-stu-id="fca8a-107">*property*</span></span>  
 <span data-ttu-id="fca8a-108">BYTE 型の定数です。</span><span class="sxs-lookup"><span data-stu-id="fca8a-108">A constant of type BYTE.</span></span> <span data-ttu-id="fca8a-109">定数の一覧については、「解説」の表を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fca8a-109">See the table in the Remarks section for a list of the constants.</span></span>  
  
 <span data-ttu-id="fca8a-110">*pField*</span><span class="sxs-lookup"><span data-stu-id="fca8a-110">*pField*</span></span>  
 <span data-ttu-id="fca8a-111">フィールド ターミネータ値を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="fca8a-111">The pointer to the field terminator value.</span></span>  
  
 <span data-ttu-id="fca8a-112">cbField</span><span class="sxs-lookup"><span data-stu-id="fca8a-112">cbField</span></span>  
 <span data-ttu-id="fca8a-113">フィールド ターミネータ値の長さです (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="fca8a-113">The length in bytes of the field terminator value.</span></span>  
  
 <span data-ttu-id="fca8a-114">pRow</span><span class="sxs-lookup"><span data-stu-id="fca8a-114">pRow</span></span>  
 <span data-ttu-id="fca8a-115">行ターミネータ値を指すポインターです。</span><span class="sxs-lookup"><span data-stu-id="fca8a-115">The pointer to the row terminator value.</span></span>  
  
 <span data-ttu-id="fca8a-116">cbRow</span><span class="sxs-lookup"><span data-stu-id="fca8a-116">cbRow</span></span>  
 <span data-ttu-id="fca8a-117">行ターミネータ値の長さです (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="fca8a-117">The length in bytes of the row terminator value.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="fca8a-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="fca8a-118">Returns</span></span>  
 <span data-ttu-id="fca8a-119">IBCPSession2::BCPSetBulkMode では、次のいずれかを返すことができます。</span><span class="sxs-lookup"><span data-stu-id="fca8a-119">IBCPSession2::BCPSetBulkMode can return one of the following:</span></span>  
  
|||  
|-|-|  
|`S_OK`|<span data-ttu-id="fca8a-120">メソッドが成功しました。</span><span class="sxs-lookup"><span data-stu-id="fca8a-120">The method succeeded.</span></span>|  
|`E_FAIL`|<span data-ttu-id="fca8a-121">プロバイダー固有のエラーが発生しました。詳細を確認するには、ISQLServerErrorInfo インターフェイスを使用してください。</span><span class="sxs-lookup"><span data-stu-id="fca8a-121">A provider specific error occurred, for detailed information use the ISQLServerErrorInfo interface.</span></span>|  
|`E_UNEXPECTED`|<span data-ttu-id="fca8a-122">メソッドの呼び出しが予期されませんでした。</span><span class="sxs-lookup"><span data-stu-id="fca8a-122">The call to the method was unexpected.</span></span> <span data-ttu-id="fca8a-123">たとえば、 `IBCPSession2::BCPInit` IBCPSession2:: BCPSetBulkMode を呼び出す前に、メソッドが呼び出されませんでした。</span><span class="sxs-lookup"><span data-stu-id="fca8a-123">For example, the `IBCPSession2::BCPInit` method was not called before calling IBCPSession2::BCPSetBulkMode.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="fca8a-124">引数が無効です。</span><span class="sxs-lookup"><span data-stu-id="fca8a-124">The argument was invalid.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="fca8a-125">メモリ不足エラー。</span><span class="sxs-lookup"><span data-stu-id="fca8a-125">Out of memory error.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fca8a-126">解説</span><span class="sxs-lookup"><span data-stu-id="fca8a-126">Remarks</span></span>  
 <span data-ttu-id="fca8a-127">IBCPSession2::BCPSetBulkMode を使用して、クエリまたはテーブルを一括コピーできます。</span><span class="sxs-lookup"><span data-stu-id="fca8a-127">IBCPSession2::BCPSetBulkMode can be used to bulk copy out of either a query or a table.</span></span> <span data-ttu-id="fca8a-128">IBCPSession2::BCPSetBulkMode を使用してクエリ ステートメントを一括コピー出力する場合は、`IBCPSession::BCPControl(BCP_OPTIONS_HINTS, ...)` を呼び出してクエリ ステートメントを指定する前に、これを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="fca8a-128">When IBCPSession2::BCPSetBulkMode is used to bulk copy out of a query statement, it must be called before calling `IBCPSession::BCPControl(BCP_OPTIONS_HINTS, ...)` to specify the query statement.</span></span>  
  
 <span data-ttu-id="fca8a-129">RPC 呼び出し構文とバッチ クエリ構文 (`{rpc func};SELECT * from Tbl` など) を 1 つのコマンド テキスト内で組み合わせて使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="fca8a-129">You should avoid combining RPC call syntax with batch query syntax (`{rpc func};SELECT * from Tbl`, for example) in a single command text.</span></span>  <span data-ttu-id="fca8a-130">ICommandPrepare::Prepare からエラーが返され、メタデータを取得できなくなるためです。</span><span class="sxs-lookup"><span data-stu-id="fca8a-130">This will cause ICommandPrepare::Prepare to return an error and prevent you from retrieving metadata.</span></span> <span data-ttu-id="fca8a-131">ストアド プロシージャの実行とバッチ クエリを 1 つのコマンド テキストで組み合わせて使用する必要がある場合は、ODBC CALL 構文 (`{call func}; SELECT * from Tbl` など) を使用します。</span><span class="sxs-lookup"><span data-stu-id="fca8a-131">Use ODBC CALL syntax (`{call func}; SELECT * from Tbl`, for example) if you need to combine stored procedure execution and batch query in a single command text.</span></span>  
  
 <span data-ttu-id="fca8a-132">*property* パラメーターとして使用できる定数の一覧を次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="fca8a-132">The following table lists the constants for the *property* parameter.</span></span>  
  
|<span data-ttu-id="fca8a-133">プロパティ</span><span class="sxs-lookup"><span data-stu-id="fca8a-133">Property</span></span>|<span data-ttu-id="fca8a-134">説明</span><span class="sxs-lookup"><span data-stu-id="fca8a-134">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="fca8a-135">BCP_OUT_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="fca8a-135">BCP_OUT_CHARACTER_MODE</span></span>|<span data-ttu-id="fca8a-136">文字出力モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="fca8a-136">Specifies character output mode.</span></span><br /><br /> <span data-ttu-id="fca8a-137">BCP.EXE の-c オプション、および*Euserdatatype*プロパティがに設定された IBCPSession:: BCPColFmt に対応し `BCP_TYPE_SQLCHARACTER` ます。</span><span class="sxs-lookup"><span data-stu-id="fca8a-137">Corresponds to the -c option in BCP.EXE, and to IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLCHARACTER`.</span></span>|  
|<span data-ttu-id="fca8a-138">BCP_OUT_WIDE_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="fca8a-138">BCP_OUT_WIDE_CHARACTER_MODE</span></span>|<span data-ttu-id="fca8a-139">Unicode 出力モードを指定します。</span><span class="sxs-lookup"><span data-stu-id="fca8a-139">Specifies Unicode output mode.</span></span><br /><br /> <span data-ttu-id="fca8a-140">BCP.EXE の-w オプションと*Euserdatatype*プロパティがに設定された IBCPSession:: BCPColFmt に対応し `BCP_TYPE_SQLNCHAR` ます。</span><span class="sxs-lookup"><span data-stu-id="fca8a-140">Corresponds to the -w option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLNCHAR`.</span></span>|  
|<span data-ttu-id="fca8a-141">BCP_OUT_NATIVE_TEXT_MODE</span><span class="sxs-lookup"><span data-stu-id="fca8a-141">BCP_OUT_NATIVE_TEXT_MODE</span></span>|<span data-ttu-id="fca8a-142">文字型以外にネイティブ型を指定し、文字型に Unicode を指定します。</span><span class="sxs-lookup"><span data-stu-id="fca8a-142">Specifies native types for non-character types and Unicode for character types.</span></span><br /><br /> <span data-ttu-id="fca8a-143">列の型が文字列の場合、または文字列でない場合は、 *Euserdatatype*プロパティをに設定して、BCP.EXE の-N オプションと IBCPSession:: BCPColFmt に対応し `BCP_TYPE_SQLNCHAR` `BCP_TYPE_DEFAULT` ます。</span><span class="sxs-lookup"><span data-stu-id="fca8a-143">Corresponds to the -N option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_SQLNCHAR` if the column type is a string or `BCP_TYPE_DEFAULT` if not a string.</span></span>|  
|<span data-ttu-id="fca8a-144">BCP_OUT_NATIVE_MODE</span><span class="sxs-lookup"><span data-stu-id="fca8a-144">BCP_OUT_NATIVE_MODE</span></span>|<span data-ttu-id="fca8a-145">ネイティブ データベース型を指定します。</span><span class="sxs-lookup"><span data-stu-id="fca8a-145">Specifies native database types.</span></span><br /><br /> <span data-ttu-id="fca8a-146">BCP.EXE の-n オプションと、 *Euserdatatype*プロパティがに設定された IBCPSession:: BCPColFmt に対応し `BCP_TYPE_DEFAULT` ます。</span><span class="sxs-lookup"><span data-stu-id="fca8a-146">Corresponds to the -n option in BCP.EXE and IBCPSession::BCPColFmt with *eUserDataType* property set to `BCP_TYPE_DEFAULT`.</span></span>|  
  
 <span data-ttu-id="fca8a-147">IBCPSession::BCPControl と IBCPSession2::BCPSetBulkMode は、IBCPSession2::BCPSetBulkMode と競合しない IBCPSession::BCPControl オプションに対して呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="fca8a-147">You can call IBCPSession::BCPControl and IBCPSession2::BCPSetBulkMode for IBCPSession::BCPControl options that do not conflict with IBCPSession2::BCPSetBulkMode.</span></span> <span data-ttu-id="fca8a-148">たとえば、 `BCP_OPTION_FIRST` および IBCPSession2:: BCPSetBulkMode を使用して、IBCPSession:: BCPControl を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="fca8a-148">For example, you can call IBCPSession::BCPControl with `BCP_OPTION_FIRST` and IBCPSession2::BCPSetBulkMode.</span></span>  
  
 <span data-ttu-id="fca8a-149">`BCP_OPTION_TEXTFILE`と IBCPSession2:: BCPSetBulkMode を使用して IBCPSession:: BCPControl を呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="fca8a-149">You cannot call IBCPSession::BCPControl with `BCP_OPTION_TEXTFILE` and IBCPSession2::BCPSetBulkMode.</span></span>  
  
 <span data-ttu-id="fca8a-150">IBCPSession::BCPColFmt、IBCPSession::BCPControl、および IBCPSession::BCPReadFmt が含まれる関数呼び出しのシーケンスを使用して IBCPSession2::BCPSetBulkMode を呼び出そうとすると、関数呼び出しの 1 つでシーケンス エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="fca8a-150">If you attempt to call IBCPSession2::BCPSetBulkMode with a sequence of function calls that includes IBCPSession::BCPColFmt, IBCPSession::BCPControl, and IBCPSession::BCPReadFmt, one of the function calls will return a sequence error failure.</span></span> <span data-ttu-id="fca8a-151">このエラーを解決するには、IBCPSession::BCPInit を呼び出して設定をリセットし、最初からやり直してください。</span><span class="sxs-lookup"><span data-stu-id="fca8a-151">If you choose to correct the failure, call IBCPSession::BCPInit to reset the settings and start over.</span></span>  
  
 <span data-ttu-id="fca8a-152">次の表に、関数のシーケンス エラーが発生する関数呼び出しの例をいくつか示します。</span><span class="sxs-lookup"><span data-stu-id="fca8a-152">The following table presents some examples of function calls that result in a function sequence error:</span></span>  
  
 <span data-ttu-id="fca8a-153">呼び出しシーケンス</span><span class="sxs-lookup"><span data-stu-id="fca8a-153">Call sequence</span></span>  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_IN);  
BCPSetBulkMode();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPReadFmt();  
```  
  
```  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPSetBulkMode();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPSetBulkMode();  
BCPColFmt();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPReadFmt();  
BCPColFmt();  
```  
  
```  
BCPInit(NULL, "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetBulkMode();  
BCPControl(BCP_OPTION_HINTS, "select ...");  
BCPReadFmt();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPColumns();  
```  
  
```  
BCPInit("table", "dataFile", "errorFile", BCP_DIRECTION_OUT);  
BCPControl(BCP_OPTION_DELAYREADFMT, true);  
BCPSetColFmt();  
```  
  
## <a name="example"></a><span data-ttu-id="fca8a-154">例</span><span class="sxs-lookup"><span data-stu-id="fca8a-154">Example</span></span>  
 <span data-ttu-id="fca8a-155">次のサンプルでは、IBCPSession2::BCPSetBulkMode の異なる設定を使用して、4 つのファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="fca8a-155">The following sample creates four files using different settings of IBCPSession2::BCPSetBulkMode.</span></span>  
  
```  
  
// compile with: sqlncli11.lib oleaut32.lib ole32.lib  
  
#include <stdio.h>  
#include "sqlncli.h"  
  
IDBInitialize*  g_pIDBInitialize = NULL;  
IBCPSession2 * g_pIBcpSession = NULL;  
class COLEDBPropSet : public DBPROPSET {  
public:  
   COLEDBPropSet() {  
      rgProperties = NULL;  
      cProperties = 0;  
   };  
   COLEDBPropSet(const GUID& guid) {  
      rgProperties = NULL;  
      cProperties = 0;  
      guidPropertySet = guid;  
   };  
   ~COLEDBPropSet() {  
      for ( ULONG i = 0 ; i < cProperties ; i++ )  
         VariantClear(&rgProperties[i].vValue);  
      CoTaskMemFree(rgProperties);  
   }  
   void SetGUID(const GUID& guid) {  
      guidPropertySet = guid;  
   };  
   bool AddProperty(DWORD dwPropertyID, bool bValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BOOL;  
      rgProperties[cProperties].vValue.boolVal = (bValue) ? VARIANT_TRUE : VARIANT_FALSE;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID, long nValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID  = dwPropertyID;  
      rgProperties[cProperties].vValue.vt     = VT_I4;  
      rgProperties[cProperties].vValue.lVal   = nValue;  
      cProperties++;  
      return true;  
   };  
   bool AddProperty(DWORD dwPropertyID,LPCWSTR szValue) {  
      if (!Add())  
         return false;  
      rgProperties[cProperties].dwPropertyID = dwPropertyID;  
      rgProperties[cProperties].vValue.vt = VT_BSTR;  
      rgProperties[cProperties].vValue.bstrVal = SysAllocString(szValue);  
      cProperties++;  
      return true;  
   };  
   bool Add() {  
      DBPROP* p = (DBPROP*)CoTaskMemRealloc(rgProperties, (cProperties + 1) * sizeof(DBPROP));  
      if (p != NULL) {  
         rgProperties = p;  
         rgProperties[cProperties].dwOptions = DBPROPOPTIONS_REQUIRED;  
         rgProperties[cProperties].colid = DB_NULLID;  
         rgProperties[cProperties].vValue.vt = VT_EMPTY;  
         return true;  
      }  
      else  
         return false;  
   };  
};  
  
void OLEDBCleanUp() {  
   if (g_pIDBInitialize) {  
      g_pIDBInitialize->Release();  
      g_pIDBInitialize = NULL;  
   }  
   if (g_pIBcpSession) {  
      g_pIBcpSession->Release();  
      g_pIBcpSession = NULL;  
   }  
}  
  
BOOL MakeOLEDBConnect(LPWSTR  pServer) {  
   BOOL ret = true;  
   IDBProperties * pIDBProperties = NULL;  
   IDBCreateSession * pIDBCreateSession = NULL;  
   COLEDBPropSet PropSet(DBPROPSET_DBINIT);  
   COLEDBPropSet BcpProperty(DBPROPSET_SQLSERVERDATASOURCE);  
   try {  
      HRESULT hr = CoInitializeEx(NULL,COINIT_MULTITHREADED);   
      hr = CoCreateInstance(SQLNCLI_CLSID, NULL, CLSCTX_INPROC_SERVER, IID_IDBInitialize, (LPVOID *)&g_pIDBInitialize);  
      if (FAILED(hr)) {  
         printf("CoCreateInstance failed\n");  
         return false;  
      }  
      PropSet.AddProperty(DBPROP_INIT_DATASOURCE, (LPWSTR)pServer);  
      PropSet.AddProperty(DBPROP_AUTH_INTEGRATED, L"SSPI");  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBProperties, (void**) &pIDBProperties);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->QueryInterface(IID_IDBProperties...) failed\n");  
         throw false;  
      }  
      hr = pIDBProperties->SetProperties(1, &PropSet);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties(...) failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->Initialize();  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->Initialize() failed\n");  
         throw false;  
      }  
      BcpProperty.AddProperty(SSPROP_ENABLEFASTLOAD, true);  
      BcpProperty.AddProperty(SSPROP_ENABLEBULKCOPY, true);  
      hr = pIDBProperties->SetProperties(1, &BcpProperty);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->->SetProperties() for bcp failed\n");  
         throw false;  
      }  
      hr = g_pIDBInitialize->QueryInterface(IID_IDBCreateSession, (void**) &pIDBCreateSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBInitialize->QueryInterface(IID_IDBCreateSession..) failed\n");  
         throw false;  
      }  
  
      hr = pIDBCreateSession->CreateSession(NULL, IID_IBCPSession2, (IUnknown**) &g_pIBcpSession);  
      if (FAILED(hr)) {  
         printf("g_pIDBCreateSession->CreateSession() failed\n");  
         throw false;  
      }  
   }  
   catch(...) {  
      ret = false;  
   }  
   if (pIDBProperties)  
      pIDBProperties->Release();  
   if (pIDBCreateSession)  
      pIDBCreateSession->Release();  
   return ret;  
}  
  
BOOL BCPSetBulkMode(LPWSTR pszServer, LPTSTR pszQureryOut, char BCPType, LPWSTR pszDataFile) {  
   HRESULThr;  
   if (!MakeOLEDBConnect(pszServer))  
      return false;  
   hr = g_pIBcpSession->BCPInit(NULL, pszDataFile, NULL, BCP_DIRECTION_OUT );   // bcp init for queryout  
   if (FAILED(hr)) {  
      printf("BCP init failed\n");  
      OLEDBCleanUp();  
      return false;  
   }  
   // setbulkmode  
   char ColTerm[] = "\t";  
   char RowTerm[] = "\r\n";  
   wchar_t wColTerm[] = L"\t";  
   wchar_t wRowTerm[] = L"\r\n";  
   BYTE * pColTerm = NULL;  
   int cbColTerm = NULL;  
   BYTE * pRowTerm = 0;  
   int cbRowTerm = 0;  
   int bulkmode = -1;  
  
   if(BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if(BCPType == 'w') {   // bcp -w  
         pColTerm = (BYTE*)wColTerm;  
         pRowTerm = (BYTE*)wRowTerm;  
         cbColTerm = 2;  
         cbRowTerm = 4;  
         bulkmode = BCP_OUT_WIDE_CHARACTER_MODE;  
      }  
      else  
         if (BCPType == 'n')   // bcp -n  
            bulkmode = BCP_OUT_NATIVE_MODE;  
         else  
            if (BCPType == 'N')   // bcp -n  
               bulkmode = BCP_OUT_NATIVE_TEXT_MODE;  
            else {  
               printf("unknown bcp mode\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            hr = g_pIBcpSession->BCPSetBulkMode(bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (FAILED(hr)) {  
               printf("BCPSetBulkMode failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
  
            // set queryout TSQL statement  
            hr = g_pIBcpSession->BCPControl(BCP_OPTION_HINTS, pszQureryOut);  
            if (FAILED(hr)) {  
               printf("BCPControl failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBROWCOUNT nRowsInserted = 0;  
            hr = g_pIBcpSession->BCPExec(&nRowsInserted);  
            if (FAILED(hr)) {  
               printf("BCPExec failed\n");  
               OLEDBCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            OLEDBCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', L"bcpc.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', L"bcpw.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', L"bcpn.dat");  
   BCPSetBulkMode(L"localhost", TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', L"bcp_N.dat");  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="fca8a-156">参照</span><span class="sxs-lookup"><span data-stu-id="fca8a-156">See Also</span></span>  
 [<span data-ttu-id="fca8a-157">IBCPSession2 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="fca8a-157">IBCPSession2 &#40;OLE DB&#41;</span></span>](ibcpsession2-ole-db.md)  
  
  
