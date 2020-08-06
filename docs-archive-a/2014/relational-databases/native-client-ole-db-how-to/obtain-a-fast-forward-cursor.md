---
title: FAST_FORWARD カーソルの取得 | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
ms.assetid: 931a28c3-8ea1-45d6-9ca1-2b8388c4d8b0
author: rothja
ms.author: jroth
ms.openlocfilehash: af0f990d2d7115bf3243bedcdde09775001a52e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639940"
---
# <a name="obtain-a-fast_forward-cursor"></a><span data-ttu-id="38bce-102">FAST_FORWARD カーソルの取得</span><span class="sxs-lookup"><span data-stu-id="38bce-102">Obtain a FAST_FORWARD Cursor</span></span>
  <span data-ttu-id="38bce-103">読み取り専用の順方向専用カーソルを取得するには、行セット プロパティ DBPROP_SERVERCURSOR、DBPROP_OTHERINSERT、DBPROP_OTHERUPDATEDELETE、DBPROP_OWNINSERT、および DBPROP_OWNUPDATEDELETE を VARIANT_TRUE に設定します。</span><span class="sxs-lookup"><span data-stu-id="38bce-103">To obtain a forward-only, read-only cursor, set the rowset properties DBPROP_SERVERCURSOR, DBPROP_OTHERINSERT, DBPROP_OTHERUPDATEDELETE, DBPROP_OWNINSERT, and DBPROP_OWNUPDATEDELETE to VARIANT_TRUE.</span></span>  
  
 <span data-ttu-id="38bce-104">完全なサンプル コードには、行セット プロパティを設定して FAST_FORWARD カーソルを取得する方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="38bce-104">A complete sample shows how to set the rowset properties to obtain a FAST_FORWARD cursor.</span></span> <span data-ttu-id="38bce-105">プロパティが設定されると、SELECT ステートメントが実行され、 **AdventureWorks**データベース内の**Vendor**テーブルの**Name**列が取得されて表示されます。</span><span class="sxs-lookup"><span data-stu-id="38bce-105">After the properties are set, a SELECT statement is executed to retrieve and display the **Name** column of the **Purchasing.Vendor** table in the **AdventureWorks** database.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="38bce-106">可能な場合は、Windows 認証を使用します。</span><span class="sxs-lookup"><span data-stu-id="38bce-106">When possible, use Windows Authentication.</span></span> <span data-ttu-id="38bce-107">Windows 認証が使用できない場合は、実行時に資格情報を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="38bce-107">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="38bce-108">資格情報をファイルに保存するのは避けてください。</span><span class="sxs-lookup"><span data-stu-id="38bce-108">Avoid storing credentials in a file.</span></span> <span data-ttu-id="38bce-109">資格情報を保持する必要がある場合は、[Win32 Crypto API](https://go.microsoft.com/fwlink/?LinkId=64532) を使用して暗号化してください。</span><span class="sxs-lookup"><span data-stu-id="38bce-109">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-obtain-fast_forward-cursor"></a><span data-ttu-id="38bce-110">FAST_FORWARD カーソルを取得するには</span><span class="sxs-lookup"><span data-stu-id="38bce-110">To obtain FAST_FORWARD cursor</span></span>  
  
1.  <span data-ttu-id="38bce-111">データ ソースへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="38bce-111">Establish a connection to the data source.</span></span>  
  
2.  <span data-ttu-id="38bce-112">行セット プロパティ DBPROP_SERVERCURSOR、DBPROP_OTHERINSERT、DBPROP_OTHERUPDATEDELETE、DBPROP_OWNINSERT、および DBPROP_OWNUPDATEDELETE を VARIANT_TRUE に設定します。</span><span class="sxs-lookup"><span data-stu-id="38bce-112">Set the rowset properties DBPROP_SERVERCURSOR, DBPROP_OTHERINSERT, DBPROP_OTHERUPDATEDELETE, DBPROP_OWNINSERT, and DBPROP_OWNUPDATEDELETE to VARIANT_TRUE.</span></span>  
  
3.  <span data-ttu-id="38bce-113">コマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="38bce-113">Execute the command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38bce-114">例</span><span class="sxs-lookup"><span data-stu-id="38bce-114">Example</span></span>  
 <span data-ttu-id="38bce-115">このサンプルでは、行セット プロパティを設定して FAST_FORWARD カーソルを取得する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="38bce-115">The following example shows how to set the rowset properties to obtain a FAST_FORWARD cursor.</span></span> <span data-ttu-id="38bce-116">プロパティを設定した後、SELECT ステートメントを実行し、AdventureWorks データベースの Purchasing.Vendor テーブルから Name 列を取得して表示します。</span><span class="sxs-lookup"><span data-stu-id="38bce-116">After the properties are set, a SELECT statement is executed to retrieve and display the Name column of the Purchasing.Vendor table in the AdventureWorks database.</span></span> <span data-ttu-id="38bce-117">このサンプルは IA64 ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="38bce-117">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="38bce-118">このサンプルには AdventureWorks サンプル データベースが必要です。このサンプル データベースは、[Microsoft SQL Server サンプルとコミュニティのプロジェクト](https://go.microsoft.com/fwlink/?LinkID=85384)のホーム ページからダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="38bce-118">This sample requires the AdventureWorks sample database, which you can download from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.</span></span>  
  
 <span data-ttu-id="38bce-119">ole32.lib と oleaut32.lib を使用して次の C++ コード リストをコンパイルし、実行します。</span><span class="sxs-lookup"><span data-stu-id="38bce-119">Compile with ole32.lib oleaut32.lib and execute the following C++ code listing.</span></span> <span data-ttu-id="38bce-120">このアプリケーションは、コンピューターの既定の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="38bce-120">This application connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="38bce-121">一部の Windows オペレーティング システムでは、(localhost) または (local) を実際の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスの名前に変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="38bce-121">On some Windows operating systems, you will need to change (localhost) or (local) to the name of your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="38bce-122">名前付きインスタンスに接続するには、接続文字列を L"(local)" から L"(local)\\\name" に変更します。ここで、name は名前付きインスタンスです。</span><span class="sxs-lookup"><span data-stu-id="38bce-122">To connect to a named instance, change the connection string from L"(local)" to L"(local)\\\name" , where name is the named instance.</span></span> <span data-ttu-id="38bce-123">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express は、既定で名前付きインスタンスとしてインストールされます。</span><span class="sxs-lookup"><span data-stu-id="38bce-123">By default, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Express installs to a named instance.</span></span> <span data-ttu-id="38bce-124">INCLUDE 環境変数に、sqlncli を含むディレクトリが含まれていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="38bce-124">Make sure your INCLUDE environment variable includes the directory that contains sqlncli.h.</span></span>  
  
```  
// compile with: ole32.lib oleaut32.lib  
#define INITGUID  
#define DBINITCONSTANTS  
#define OLEDBVER 0x0250   // to include correct interfaces  
  
#include <windows.h>  
#include <stdio.h>  
#include <oledb.h>  
#include <sqlncli.h>  
#include <oledberr.h>  
  
IDBInitialize* pIDBInitialize = NULL;  
ICommandText* pICommandText = NULL;  
  
// Connect to the server and create a command object.  
int InitializeAndConnect();  
  
// Set the properties to get a FAST_FORWARD cursor.  
int SetRowsetProperties();  
  
// This function executes a command and displays the results.  
int ExecuteAndDisplay();  
  
// Release memory.  
void Cleanup();  
  
int main() {  
   if (InitializeAndConnect() == -1) {  
      // Handle error.  
      printf("Failed to initialize and connect to the server.\n");  
      return -1;  
   }  
  
   // Set the row properties to FAST_FORWARD cursor.  
   if (SetRowsetProperties() == -1) {  
      // Handle error.  
      printf("Failed to set the rowset properties.\n");  
      return -1;  
   }  
  
   // Execute a command and display the results.  
   if (ExecuteAndDisplay() == -1) {  
      // Handle error.  
      printf("Failed to execute a command and display the results.\n");  
      return -1;  
   }  
  
   Cleanup();  
}  
  
int InitializeAndConnect() {  
   HRESULT hr = S_OK;  
  
   IDBProperties* pIDBProperties = NULL;  
   IDBCreateSession* pIDBCreateSession = NULL;  
   IDBCreateCommand* pIDBCreateCommand = NULL;  
  
   DBPROPSET dbPropSet;  
   DBPROP dbProp[4];  
   int iRetVal = 0;  
  
   // Initialize OLE  
   if ( FAILED( hr = OleInitialize( NULL ) ) ) {  
      // Handle errors here.  
      return -1;  
   }  
  
   // Create an instance of Microsoft SQL Server Native Client OLE DB Provider.  
   if ( FAILED( hr =   
      CoCreateInstance(CLSID_SQLNCLI11, NULL, CLSCTX_INPROC_SERVER, IID_IDBProperties, (void **) &pIDBProperties ))) {  
      // Handle errors here.  
      return -1;  
   }  
  
   // Set up the connection properties.  
   dbProp[0].dwPropertyID = DBPROP_INIT_DATASOURCE;  
   dbProp[0].dwOptions = DBPROPOPTIONS_REQUIRED;  
   dbProp[0].colid = DB_NULLID;  
   V_VT(&(dbProp[0].vValue)) = VT_BSTR;  
  
   V_BSTR(&(dbProp[0].vValue)) = SysAllocString( L"(local)" );  
  
   dbProp[1].dwPropertyID = DBPROP_AUTH_INTEGRATED;  
   dbProp[1].dwOptions = DBPROPOPTIONS_REQUIRED;  
   dbProp[1].colid = DB_NULLID;  
   V_VT(&(dbProp[1].vValue)) = VT_BSTR;  
   V_BSTR(&(dbProp[1].vValue)) = SysAllocString( L"SSPI" );  
  
   dbProp[2].dwPropertyID = DBPROP_NULLCOLLATION;  
   dbProp[2].dwOptions = DBPROPOPTIONS_REQUIRED;  
   dbProp[2].colid = DB_NULLID;  
   V_VT(&(dbProp[2].vValue)) = VT_BSTR;  
   V_BSTR(&(dbProp[2].vValue)) = SysAllocString( L"" );  
  
   dbProp[3].dwPropertyID = DBPROP_INIT_CATALOG;  
   dbProp[3].dwOptions = DBPROPOPTIONS_REQUIRED;  
   dbProp[3].colid = DB_NULLID;  
   V_VT(&(dbProp[3].vValue)) = VT_BSTR;  
   V_BSTR(&(dbProp[3].vValue)) = SysAllocString( L"AdventureWorks" );  
  
   dbPropSet.rgProperties = dbProp;  
   dbPropSet.cProperties = 4;  
   dbPropSet.guidPropertySet = DBPROPSET_DBINIT;  
  
   if ( FAILED( hr = pIDBProperties->SetProperties( 1, &dbPropSet ))) {  
      // Handle errors here.  
      iRetVal = -1;  
      goto CLEANUP;  
   }  
  
   SysFreeString( V_BSTR(&(dbProp[0].vValue)) );  
   SysFreeString( V_BSTR(&(dbProp[1].vValue)) );  
   SysFreeString( V_BSTR(&(dbProp[2].vValue)) );  
   SysFreeString( V_BSTR(&(dbProp[3].vValue)) );  
  
   // Get an IDBInitialize interface.  
   if ( FAILED( hr =   
      pIDBProperties->QueryInterface( IID_IDBInitialize, (void **) &pIDBInitialize ))) {  
      // Handle errors here.  
      iRetVal = -1;  
      goto CLEANUP;  
   }  
  
   // Call Initialize.  
   if ( FAILED( hr = pIDBInitialize->Initialize())) {  
      // Handle errors here.  
      iRetVal = -1;  
      goto CLEANUP;  
   }  
  
   // Get a IDBCreateSession interface.  
   if ( FAILED( hr =   
      pIDBInitialize->QueryInterface( IID_IDBCreateSession, (void **) &pIDBCreateSession ))) {  
      // Handle errors here.  
      iRetVal = -1;  
      goto CLEANUP;  
   }  
  
   // Create a session  
   if ( FAILED( hr =   
      pIDBCreateSession->CreateSession( NULL, IID_IDBCreateCommand, (IUnknown **) &pIDBCreateCommand))) {  
      // Handle errors here.  
      iRetVal = -1;  
      goto CLEANUP;  
   }  
  
   // Create a command.  
   if ( FAILED( hr =   
      pIDBCreateCommand->CreateCommand( NULL, IID_ICommandText, (IUnknown **) &pICommandText))) {  
      // Handle errors here.  
      iRetVal = -1;  
      goto CLEANUP;  
   }  
  
CLEANUP:  
   // Release all the objects not needed anymore.  
   pIDBProperties->Release();  
   if ( pIDBCreateSession )  
      pIDBCreateSession->Release();  
   if ( pIDBCreateCommand )  
      pIDBCreateCommand->Release();  
  
   return iRetVal;  
}  
  
int SetRowsetProperties() {  
   HRESULT hr = S_OK;  
   ICommandProperties* pICommandProperties = NULL;  
   DBPROPSET dbPropSet;  
   DBPROP dbProp[5];  
   int iRetVal = 0;  
  
   // Get an ICommandProperties object.  
   if ( FAILED( hr =   
      pICommandText->QueryInterface( IID_ICommandProperties, (void **) &pICommandProperties ))) {  
      // Handle errors here.  
      return -1;  
   }  
  
   // Set up the properties to get a FAST_FORWARD cursor.  
   dbProp[0].dwPropertyID       = DBPROP_SERVERCURSOR;  
   dbProp[0].dwOptions          = DBPROPOPTIONS_REQUIRED;  
   dbProp[0].colid              = DB_NULLID;  
   V_VT(&(dbProp[0].vValue))    = VT_BOOL;  
   V_BOOL(&(dbProp[0].vValue))  = VARIANT_TRUE;  
  
   dbProp[1].dwPropertyID       = DBPROP_OTHERINSERT;  
   dbProp[1].dwOptions          = DBPROPOPTIONS_REQUIRED;  
   dbProp[1].colid              = DB_NULLID;  
   V_VT(&(dbProp[1].vValue))    = VT_BOOL;  
   V_BOOL(&(dbProp[1].vValue))  = VARIANT_TRUE;  
  
   dbProp[2].dwPropertyID       = DBPROP_OTHERUPDATEDELETE;  
   dbProp[2].dwOptions          = DBPROPOPTIONS_REQUIRED;  
   dbProp[2].colid              = DB_NULLID;  
   V_VT(&(dbProp[2].vValue))    = VT_BOOL;  
   V_BOOL(&(dbProp[2].vValue))  = VARIANT_TRUE;  
  
   dbProp[3].dwPropertyID       = DBPROP_OWNINSERT;  
   dbProp[3].dwOptions          = DBPROPOPTIONS_REQUIRED;  
   dbProp[3].colid              = DB_NULLID;  
   V_VT(&(dbProp[3].vValue))    = VT_BOOL;  
   V_BOOL(&(dbProp[3].vValue))  = VARIANT_TRUE;  
  
   dbProp[4].dwPropertyID       = DBPROP_OWNUPDATEDELETE;  
   dbProp[4].dwOptions          = DBPROPOPTIONS_REQUIRED;  
   dbProp[4].colid              = DB_NULLID;  
   V_VT(&(dbProp[4].vValue))    = VT_BOOL;  
   V_BOOL(&(dbProp[4].vValue))  = VARIANT_TRUE;  
  
   dbPropSet.rgProperties       = dbProp;  
   dbPropSet.cProperties        = 5;  
   dbPropSet.guidPropertySet    = DBPROPSET_ROWSET;  
  
   if ( FAILED( hr = pICommandProperties->SetProperties( 1, &dbPropSet))) {  
      // Handle errors here.  
      iRetVal = -1;  
   }  
  
   // Release the ICommandProperties object.  
   pICommandProperties->Release();  
  
   return iRetVal;  
}  
  
int ExecuteAndDisplay() {  
   HRESULT hr = S_OK;  
   IRowset* pIRowset = NULL;  
   IAccessor* pIAccessor = NULL;  
  
   BYTE* pData = NULL;  
   DBCOUNTITEM cRowsObtained = 0;  
   ULONG cCount = 0;  
  
   HROW* pRows = new HROW[10];  
   HACCESSOR hAccessor = 0;  
   DBBINDING Bind[1];  
   int iRetVal = 0;  
  
   if (!pRows)  
      return -1;  
  
   // Set the command text.  
   if ( FAILED( hr = pICommandText->SetCommandText( DBGUID_SQL, L"select Name from Purchasing.Vendor")))  
      // Handle errors and free the memory here.  
      return -1;  
  
   // Execute the command.  
   if ( FAILED( hr = pICommandText->Execute( NULL, IID_IRowset, NULL, NULL, (IUnknown **) &pIRowset )))  
      // Handle errors and free the memory here.  
      return -1;  
  
    // Set up the binding structure for Name (nvarchar(50)).  
    Bind[0].dwPart      = DBPART_VALUE;  
    Bind[0].eParamIO    = DBPARAMIO_NOTPARAM;  
    Bind[0].iOrdinal    = 1;  
    Bind[0].pTypeInfo   = NULL;  
    Bind[0].pObject     = NULL;  
    Bind[0].pBindExt    = NULL;  
    Bind[0].dwFlags     = 0;  
    Bind[0].dwMemOwner  = DBMEMOWNER_CLIENTOWNED;  
    Bind[0].obLength    = 0;  
    Bind[0].obStatus    = 0;  
    Bind[0].obValue     = 0;  
    Bind[0].cbMaxLen    = 102;  
    Bind[0].wType       = DBTYPE_WSTR;  
    Bind[0].bPrecision  = 0;  
    Bind[0].bScale      = 0;  
  
   // Get an IAccessor interface.  
   if ( FAILED( hr = pIRowset->QueryInterface( IID_IAccessor, (void **) &pIAccessor))) {  
      // Handle errors and free the memory here.  
      iRetVal = -1;  
      goto CLEANUP;  
   }  
  
   // Create an accessor.  
   if ( FAILED( hr =   
      pIAccessor->CreateAccessor(  DBACCESSOR_ROWDATA, 1, Bind, 0, &hAccessor, NULL))) {  
      // Handle errors and free the memory here.  
      iRetVal = -1;  
      goto CLEANUP;  
   }  
  
   // Allocate memory for the data.  
   pData = new BYTE[102];  
   if (!(pData /* = new BYTE[102] */ )) {  
      // Handle errors and free the memory here.  
      iRetVal = -1;  
      goto CLEANUP;  
   }  
  
   // Loop through all of the rows.  
   for ( ; ; ) {  
      if (FAILED( hr = pIRowset->GetNextRows( NULL, 0, 10, &cRowsObtained, &pRows))) {  
         // Handle errors and free the memory here.  
         iRetVal = -1;  
         goto CLEANUP;  
      }  
  
      // Make sure some rows were obtained.  
      if (cRowsObtained == 0)  
         break;  
  
      // Get the data for the each of the rows.  
      for ( cCount = 0 ; cCount < cRowsObtained ; cCount++ ) {  
         // Get the row data needed.  
         if ( FAILED( hr = pIRowset->GetData( pRows[cCount], hAccessor, pData ))) {  
            // Handle errors and free the memory here.  
            iRetVal = -1;  
            goto CLEANUP;  
         }  
  
         // Display row data.  
         printf( "%S\n", pData);  
      }  
  
      // Release the rows.  
      if ( FAILED( hr = pIRowset->ReleaseRows(cRowsObtained, pRows, NULL, NULL, NULL ))) {  
         // Handle errors and free the memory here.  
         iRetVal = -1;  
         goto CLEANUP;  
      }  
   }  
  
CLEANUP:  
   // Release memory allocated for the data.  
   delete [] pRows;  
   delete [] pData;  
  
   // Release the HACCESSOR.  
   if (pIAccessor) {  
      pIAccessor->ReleaseAccessor( hAccessor, NULL );  
  
      // Release the IAccessor object.  
      pIAccessor->Release();  
   }  
  
   // Release the rowset.  
   pIRowset->Release();  
  
   return iRetVal;  
}  
  
void Cleanup() {  
   HRESULT hr = S_OK;  
  
   // Release the ICommandText object.  
   pICommandText->Release();  
  
   // Uninitialize the IDBInitialize object.  
   if ( FAILED( hr = pIDBInitialize->Uninitialize())) {  
      // Handle errors here.  
   }  
  
   // Release the IDBInitialize object.  
   pIDBInitialize->Release();  
  
   // Uninitialize OLE.  
   OleUninitialize();  
}  
```  
  
  
