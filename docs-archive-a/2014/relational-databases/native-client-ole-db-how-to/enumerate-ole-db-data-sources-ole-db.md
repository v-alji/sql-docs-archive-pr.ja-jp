---
title: OLE DB データ ソースの列挙 (OLE DB) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [OLE DB]
ms.assetid: ba240060-3237-4fb8-b2fb-b87fda2b1e7a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1173feef8de657c43563b40bec763f81d630014e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87739864"
---
# <a name="enumerate-ole-db-data-sources-ole-db"></a><span data-ttu-id="fbe56-102">OLE DB データ ソースの列挙 (OLE DB)</span><span class="sxs-lookup"><span data-stu-id="fbe56-102">Enumerate OLE DB Data Sources (OLE DB)</span></span>
  <span data-ttu-id="fbe56-103">このサンプルでは、列挙子オブジェクトを使用して、使用可能なデータ ソースを一覧表示する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-103">This sample shows how to use the enumerator object to list the data sources available.</span></span>  
  
 <span data-ttu-id="fbe56-104">SQLOLEDB 列挙子に表示されるデータソースを一覧表示するために、コンシューマーは[isourcesrowset を:: GetSourcesRowset](https://go.microsoft.com/fwlink/?LinkId=120312)メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-104">To list the data sources visible to the SQLOLEDB enumerator, the consumer calls the [ISourcesRowset::GetSourcesRowset](https://go.microsoft.com/fwlink/?LinkId=120312) method.</span></span> <span data-ttu-id="fbe56-105">このメソッドは、現在表示されているデータ ソースに関する情報の行セットを返します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-105">This method returns a rowset of information about the currently visible data sources.</span></span>  
  
 <span data-ttu-id="fbe56-106">使用しているネットワーク ライブラリに応じて、適切なドメインでデータ ソースが検索されます。</span><span class="sxs-lookup"><span data-stu-id="fbe56-106">Depending on the network library used, the appropriate domain is searched for the data sources.</span></span> <span data-ttu-id="fbe56-107">名前付きパイプの場合は、クライアントがログオンしたドメインになります。</span><span class="sxs-lookup"><span data-stu-id="fbe56-107">For named pipes, it is the domain to which the client is logged on.</span></span> <span data-ttu-id="fbe56-108">AppleTalk の場合は、既定のゾーンになります。</span><span class="sxs-lookup"><span data-stu-id="fbe56-108">For AppleTalk, it is the default zone.</span></span> <span data-ttu-id="fbe56-109">SPX/IPX の場合は、バインダリ内にある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールの一覧になります。</span><span class="sxs-lookup"><span data-stu-id="fbe56-109">For SPX/IPX, it is the list of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations found in the bindery.</span></span> <span data-ttu-id="fbe56-110">Banyan VINES の場合は、ローカル ネットワークにある [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインストールになります。</span><span class="sxs-lookup"><span data-stu-id="fbe56-110">For Banyan VINES, it is the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installations found on the local network.</span></span> <span data-ttu-id="fbe56-111">マルチプロトコルと TCP/IP ソケットはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="fbe56-111">Multiprotocol and TCP/IP sockets are not supported.</span></span>  
  
 <span data-ttu-id="fbe56-112">サーバーのオンとオフが切り替わると、これらのドメインで情報を更新するのに数分かかる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fbe56-112">When the server is turned off or on, it can take few minutes to update the information in these domains.</span></span>  
  
 <span data-ttu-id="fbe56-113">このサンプルには AdventureWorks サンプル データベースが必要です。このサンプル データベースは、[Microsoft SQL Server サンプルとコミュニティのプロジェクト](https://go.microsoft.com/fwlink/?LinkID=85384)のホーム ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="fbe56-113">This sample requires the AdventureWorks sample database, which you can download from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="fbe56-114">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-114">When possible, use Windows Authentication.</span></span> <span data-ttu-id="fbe56-115">Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="fbe56-115">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="fbe56-116">資格情報をファイルに保存するのは避けてください。</span><span class="sxs-lookup"><span data-stu-id="fbe56-116">Avoid storing credentials in a file.</span></span> <span data-ttu-id="fbe56-117">資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="fbe56-117">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-enumerate-ole-db-data-sources"></a><span data-ttu-id="fbe56-118">OLE DB データ ソースを列挙するには</span><span class="sxs-lookup"><span data-stu-id="fbe56-118">To enumerate OLE DB data sources</span></span>  
  
1.  <span data-ttu-id="fbe56-119">`ISourceRowset::GetSourcesRowset` を呼び出して、ソースの行セットを取得します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-119">Retrieve the source rowset by calling `ISourceRowset::GetSourcesRowset`.</span></span>  
  
2.  <span data-ttu-id="fbe56-120">`GetColumnInfo::IColumnInfo` を呼び出して、列挙子の行セットの説明を検索します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-120">Find the description of the enumerators rowset by calling `GetColumnInfo::IColumnInfo`.</span></span>  
  
3.  <span data-ttu-id="fbe56-121">列情報からバインド構造体を作成します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-121">Create the binding structures from the column information.</span></span>  
  
4.  <span data-ttu-id="fbe56-122">`IAccessor::CreateAccessor` を呼び出して、行セットのアクセサーを作成します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-122">Create the rowset accessor by calling `IAccessor::CreateAccessor`.</span></span>  
  
5.  <span data-ttu-id="fbe56-123">`IRowset::GetNextRows` を呼び出して行をフェッチします。</span><span class="sxs-lookup"><span data-stu-id="fbe56-123">Fetch the rows by calling `IRowset::GetNextRows`.</span></span>  
  
6.  <span data-ttu-id="fbe56-124">`IRowset::GetData` を呼び出して、行の行セットのコピーからデータを取得し、そのデータを処理します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-124">Retrieve data from the rowset's copy of the row by calling `IRowset::GetData`, and process it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbe56-125">例</span><span class="sxs-lookup"><span data-stu-id="fbe56-125">Example</span></span>  
 <span data-ttu-id="fbe56-126">ole32.lib を使用して次の C++ コード リストをコンパイルし、実行します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-126">Compile with ole32.lib and execute the following C++ code listing.</span></span> <span data-ttu-id="fbe56-127">このアプリケーションは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-127">This application connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="fbe56-128">一部の Windows オペレーティング システムでは、(localhost) または (local) を実際の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="fbe56-128">On some Windows operating systems, you will need to change (localhost) or (local) to the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="fbe56-129">名前付きインスタンスに接続するには、接続文字列を L"(local)" から L"(local)\\\name" に変更します。ここで、name は名前付きインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="fbe56-129">To connect to a named instance, change the connection string from L"(local)" to L"(local)\\\name" , where name is the named instance.</span></span> <span data-ttu-id="fbe56-130">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="fbe56-130">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express installs to a named instance.</span></span> <span data-ttu-id="fbe56-131">INCLUDE 環境変数に、sqlncli を含むディレクトリが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="fbe56-131">Make sure your INCLUDE environment variable includes the directory that contains sqlncli.h.</span></span>  
  
```  
// compile with: ole32.lib  
#define UNICODE  
#define _UNICODE  
#define DBINITCONSTANTS  
#define INITGUID  
#define OLEDBVER 0x0250   // to include correct interfaces  
  
#include <windows.h>  
#include <stddef.h>  
#include <oledb.h>  
#include <oledberr.h>  
#include <sqlncli.h>  
#include <stdio.h>  
  
#define NUMROWS_CHUNK  5  
  
// AdjustLen supports binding on four-byte boundaries.  
_inline DBLENGTH AdjustLen(DBLENGTH cb) {   
   return ( (cb + 3) & ~3 );  
}  
  
// Get the characteristics of the rowset (the IColumnsInfo interface).  
HRESULT GetColumnInfo ( IRowset* pIRowset,   
                        DBORDINAL* pnCols,   
                        DBCOLUMNINFO** ppColumnsInfo,  
                        OLECHAR** ppColumnStrings ) {  
   IColumnsInfo* pIColumnsInfo;  
   HRESULT hr;  
  
   *pnCols = 0;  
   if (FAILED(pIRowset->QueryInterface(IID_IColumnsInfo, (void**) &pIColumnsInfo)))  
      return (E_FAIL);  
  
   hr = pIColumnsInfo->GetColumnInfo(pnCols, ppColumnsInfo, ppColumnStrings);  
  
   if (FAILED(hr)) {}   /* Process error */   
  
   pIColumnsInfo->Release();  
   return (hr);  
}  
  
// Create binding structures from column information. Binding structures  
// will be used to create an accessor that allows row value retrieval.  
void CreateDBBindings ( DBORDINAL nCols,   
                        DBCOLUMNINFO* pColumnsInfo,   
                        DBBINDING** ppDBBindings,  
                        BYTE** ppRowValues ) {  
   ULONG nCol;  
   DBLENGTH cbRow = 0;  
   DBLENGTH cbCol;  
   DBBINDING* pDBBindings;  
   BYTE* pRowValues;  
  
   pDBBindings = new DBBINDING[nCols];  
   if (!(pDBBindings /* = new DBBINDING[nCols] */ ))  
      return;  
  
   for ( nCol = 0 ; nCol < nCols ; nCol++ ) {  
      pDBBindings[nCol].iOrdinal = nCol + 1;  
      pDBBindings[nCol].pTypeInfo = NULL;  
      pDBBindings[nCol].pObject = NULL;  
      pDBBindings[nCol].pBindExt = NULL;  
      pDBBindings[nCol].dwPart = DBPART_VALUE;  
      pDBBindings[nCol].dwMemOwner = DBMEMOWNER_CLIENTOWNED;  
      pDBBindings[nCol].eParamIO = DBPARAMIO_NOTPARAM;  
      pDBBindings[nCol].dwFlags = 0;  
      pDBBindings[nCol].wType = pColumnsInfo[nCol].wType;  
      pDBBindings[nCol].bPrecision = pColumnsInfo[nCol].bPrecision;  
      pDBBindings[nCol].bScale = pColumnsInfo[nCol].bScale;  
  
      cbCol = pColumnsInfo[nCol].ulColumnSize;  
  
      switch (pColumnsInfo[nCol].wType) {  
      case DBTYPE_STR: {  
            cbCol += 1;  
            break;  
         }  
  
      case DBTYPE_WSTR: {  
            cbCol = (cbCol + 1) * sizeof(WCHAR);  
            break;  
         }  
  
      default:  
         break;  
      }  
  
      pDBBindings[nCol].obValue = cbRow;  
      pDBBindings[nCol].cbMaxLen = cbCol;  
      cbRow += AdjustLen(cbCol);  
   }  
  
   pRowValues = new BYTE[cbRow];  
   *ppDBBindings = pDBBindings;  
   *ppRowValues = pRowValues;  
}  
  
int main() {  
   ISourcesRowset* pISourceRowset = NULL;      
   IRowset* pIRowset = NULL;          
   IAccessor* pIAccessor = NULL;  
   DBBINDING* pDBBindings = NULL;              
  
   HROW* pRows = new HROW[500];      
   HACCESSOR hAccessorRetrieve = NULL;          
   ULONG DSSeqNumber = 0;  
  
   HRESULT hr;  
   DBORDINAL nCols;  
   DBCOLUMNINFO* pColumnsInfo = NULL;  
   OLECHAR* pColumnStrings = NULL;  
   DBBINDSTATUS* pDBBindStatus = NULL;  
  
   BYTE* pRowValues = NULL;  
   DBCOUNTITEM cRowsObtained;  
   ULONG iRow;  
   char* pMultiByte = NULL;  
   short* psSourceType = NULL;  
   BYTE* pDatasource = NULL;  
  
   if (!pRows)  
      return (0);  
  
   // Initialize COM library.  
   CoInitialize(NULL);  
  
   // Initialize the enumerator.  
   if (FAILED(CoCreateInstance(CLSID_SQLNCLI11_ENUMERATOR,   
                               NULL,  
                               CLSCTX_INPROC_SERVER,   
                               IID_ISourcesRowset,   
                               (void**)&pISourceRowset))) {  
      // Process error.  
      return TRUE;  
   }  
  
   // Retrieve the source rowset.  
   hr = pISourceRowset->GetSourcesRowset(NULL, IID_IRowset, 0, NULL, (IUnknown**)&pIRowset);  
  
   pISourceRowset->Release();  
   if (FAILED(hr)) {  
      // Process error.  
      return TRUE;  
   }  
  
   // Get the description of the enumerator's rowset.  
   if (FAILED(hr = GetColumnInfo(pIRowset, &nCols, &pColumnsInfo, &pColumnStrings))) {  
      // Process error.  
      goto SAFE_EXIT;  
   }  
  
   // Create the binding structures.  
   CreateDBBindings(nCols, pColumnsInfo, &pDBBindings, &pRowValues);  
   pDBBindStatus = new DBBINDSTATUS[nCols];  
  
   if (sizeof(TCHAR) != sizeof(WCHAR))  
      pMultiByte = new char[pDBBindings[0].cbMaxLen];  
  
   if (FAILED(pIRowset->QueryInterface(IID_IAccessor, (void**)&pIAccessor))) {  
      // Process error.  
      goto SAFE_EXIT;  
   }  
  
   // Create the rowset accessor.  
   if (FAILED(hr = pIAccessor->CreateAccessor(DBACCESSOR_ROWDATA,   
                                              nCols,  
                                              pDBBindings,   
                                              0,   
                                              &hAccessorRetrieve,   
                                              pDBBindStatus))) {  
      // Process error.  
      goto SAFE_EXIT;  
   }  
  
   // Process all the rows, NUMROWS_CHUNK rows at a time.  
   while (SUCCEEDED(hr)) {  
      hr = pIRowset->GetNextRows(NULL, 0, NUMROWS_CHUNK, &cRowsObtained, &pRows);  
      if( FAILED(hr)) {  
         // process error  
      }  
      if (cRowsObtained == 0 || FAILED(hr))  
         break;  
  
      for (iRow = 0 ; iRow < cRowsObtained ; iRow++) {  
         // Get the rowset data.  
         if (SUCCEEDED(hr = pIRowset->GetData(pRows[iRow], hAccessorRetrieve, pRowValues))) {  
            psSourceType = (short *)(pRowValues + pDBBindings[3].obValue);  
  
            if (*psSourceType == DBSOURCETYPE_DATASOURCE) {  
               DSSeqNumber = DSSeqNumber + 1;   // Data source counter.  
               pDatasource = (pRowValues + pDBBindings[0].obValue);  
  
               if ( sizeof(TCHAR) != sizeof(WCHAR) ) {  
                  WideCharToMultiByte(CP_ACP,   
                                      0,  
                                      (WCHAR*)pDatasource,   
                                      -1,   
                                      pMultiByte,  
                                      static_cast<int>(pDBBindings[0].cbMaxLen),   
                                      NULL,   
                                      NULL);  
  
                  printf( "DataSource# %d\tName: %S\n",   
                          DSSeqNumber,   
                          (WCHAR *) pMultiByte );  
               }  
               else {  
                  printf( "DataSource# %d\tName: %S\n",   
                          DSSeqNumber,   
                          (WCHAR *) pDatasource );  
               }  
            }  
         }  
      }  
      pIRowset->ReleaseRows(cRowsObtained, pRows, NULL, NULL, NULL);  
   }  
  
   // Release COM library.  
   CoUninitialize();  
  
SAFE_EXIT:  
   // Do the clean-up.  
   return TRUE;  
}  
```  
  
  
