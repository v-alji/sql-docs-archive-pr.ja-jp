---
title: データ ソースへの接続の確立 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data sources [SQL Server Native Client]
- connections [SQL Server Native Client]
- SQL Server Native Client OLE DB provider, data source connections
- CoCreateInstance method
- OLE DB data sources [SQL Server Native Client]
ms.assetid: 7ebd1394-cc8d-4bcf-92f3-c374a26e7ba0
author: rothja
ms.author: jroth
ms.openlocfilehash: f88454339ee932c38655819cce475ab52d79975f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643797"
---
# <a name="establishing-a-connection-to-a-data-source"></a><span data-ttu-id="2b29c-102">データ ソースへの接続の確立</span><span class="sxs-lookup"><span data-stu-id="2b29c-102">Establishing a Connection to a Data Source</span></span>
  <span data-ttu-id="2b29c-103">コンシューマーは、Native Client OLE DB プロバイダーにアクセスするために、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] まず**CoCreateInstance**メソッドを呼び出すことによって、データソースオブジェクトのインスタンスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2b29c-103">To access the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the consumer must first create an instance of a data source object by calling the **CoCreateInstance** method.</span></span> <span data-ttu-id="2b29c-104">一意のクラス ID (CLSID) で、各 OLE DB プロバイダーが識別されます。</span><span class="sxs-lookup"><span data-stu-id="2b29c-104">A unique class identifier (CLSID) identifies each OLE DB provider.</span></span> <span data-ttu-id="2b29c-105">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB プロバイダーの場合、クラス識別子は CLSID_SQLNCLI10 です。</span><span class="sxs-lookup"><span data-stu-id="2b29c-105">For the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, the class identifier is CLSID_SQLNCLI10.</span></span> <span data-ttu-id="2b29c-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]参照する SQLNCLI に使用されている Native Client OLE DB プロバイダーに解決されるシンボル SQLNCLI_CLSID を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="2b29c-106">You can also use the symbol SQLNCLI_CLSID that will resolve to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider that is used in the sqlncli.h that you reference.</span></span>  
  
 <span data-ttu-id="2b29c-107">データ ソース オブジェクトは、**IDBProperties** インターフェイスを公開します。コンシューマーは、このインターフェイスを使用して、サーバー名、データベース名、ユーザー ID、パスワードなどの基本的な認証情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="2b29c-107">The data source object exposes the **IDBProperties** interface, which the consumer uses to provide basic authentication information such as server name, database name, user ID, and password.</span></span> <span data-ttu-id="2b29c-108">**IDBProperties::SetProperties** メソッドが呼び出されて、これらのプロパティが設定されます。</span><span class="sxs-lookup"><span data-stu-id="2b29c-108">The **IDBProperties::SetProperties** method is called to set these properties.</span></span>  
  
 <span data-ttu-id="2b29c-109">同じコンピューター上で複数の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが実行されている場合、サーバー名を ServerName\InstanceName のように指定します。</span><span class="sxs-lookup"><span data-stu-id="2b29c-109">If there are multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] running on the computer, the server name is specified as ServerName\InstanceName.</span></span>  
  
 <span data-ttu-id="2b29c-110">データ ソース オブジェクトは、**IDBInitialize** インターフェイスも公開します。</span><span class="sxs-lookup"><span data-stu-id="2b29c-110">The data source object also exposes the **IDBInitialize** interface.</span></span> <span data-ttu-id="2b29c-111">プロパティを設定した後、**IDBInitialize::Initialize** メソッドを呼び出して、データ ソースへの接続を確立します。</span><span class="sxs-lookup"><span data-stu-id="2b29c-111">After the properties are set, connection to the data source is established by calling the **IDBInitialize::Initialize** method.</span></span> <span data-ttu-id="2b29c-112">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="2b29c-112">For example:</span></span>  
  
```  
CoCreateInstance(CLSID_SQLNCLI10,   
                 NULL,   
                 CLSCTX_INPROC_SERVER,  
                 IID_IDBInitialize,   
                 (void **) &pIDBInitialize)  
```  
  
 <span data-ttu-id="2b29c-113">この**CoCreateInstance**への呼び出しによって、CLSID_SQLNCLI10 (オブジェクトの作成に使用されるデータとコードに関連付けられた CSLID) に関連付けられたクラスの1つのオブジェクトが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2b29c-113">This call to **CoCreateInstance** creates a single object of the class associated with CLSID_SQLNCLI10 (CSLID associated with the data and code that will be used to create the object).</span></span> <span data-ttu-id="2b29c-114">IID_IDBInitialize は、オブジェクトとの通信に使われるインターフェイス (**IDBInitialize**) の ID への参照です。</span><span class="sxs-lookup"><span data-stu-id="2b29c-114">IID_IDBInitialize is a reference to the identifier of the interface (**IDBInitialize**) to be used to communicate with the object.</span></span>  
  
 <span data-ttu-id="2b29c-115">次に、データ ソースへの接続を初期化し、確立する関数の例を示します。</span><span class="sxs-lookup"><span data-stu-id="2b29c-115">The following is a sample function that initializes and establishes a connection to the data source.</span></span>  
  
```  
void InitializeAndEstablishConnection() {  
   // Initialize the COM library.  
   CoInitialize(NULL);  
  
   // Obtain access to the SQL Server Native Client OLE DB provider.  
   hr = CoCreateInstance(CLSID_SQLNCLI10,   
                         NULL,   
                         CLSCTX_INPROC_SERVER,  
                         IID_IDBInitialize,   
                         (void **) &pIDBInitialize);  
   // Initialize property values needed to establish connection.  
   for (i = 0 ; i < 4 ; i++)   
      VariantInit(&InitProperties[i].vValue);  
  
   // Server name.  
   // See DBPROP structure for more information on InitProperties  
   InitProperties[0].dwPropertyID  = DBPROP_INIT_DATASOURCE;  
   InitProperties[0].vValue.vt    = VT_BSTR;  
   InitProperties[0].vValue.bstrVal=   
                     SysAllocString(L"Server");  
   InitProperties[0].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[0].colid       = DB_NULLID;  
  
   // Database.  
   InitProperties[1].dwPropertyID  = DBPROP_INIT_CATALOG;  
   InitProperties[1].vValue.vt    = VT_BSTR;  
   InitProperties[1].vValue.bstrVal= SysAllocString(L"database");  
   InitProperties[1].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[1].colid       = DB_NULLID;  
  
   // Username (login).  
   InitProperties[2].dwPropertyID  = DBPROP_AUTH_INTEGRATED;  
   InitProperties[2].vValue.vt    = VT_BSTR;  
   InitProperties[2].vValue.bstrVal= SysAllocString(L"SSPI");  
   InitProperties[2].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[2].colid       = DB_NULLID;  
   InitProperties[3].dwOptions    = DBPROPOPTIONS_REQUIRED;  
   InitProperties[3].colid       = DB_NULLID;  
  
   // Construct the DBPROPSET structure(rgInitPropSet). The   
   // DBPROPSET structure is used to pass an array of DBPROP   
   // structures (InitProperties) to the SetProperties method.  
   rgInitPropSet[0].guidPropertySet = DBPROPSET_DBINIT;  
   rgInitPropSet[0].cProperties   = 4;  
   rgInitPropSet[0].rgProperties   = InitProperties;  
  
   // Set initialization properties.  
   hr = pIDBInitialize->QueryInterface(IID_IDBProperties,   
                           (void **)&pIDBProperties);  
   hr = pIDBProperties->SetProperties(1, rgInitPropSet);   
   pIDBProperties->Release();  
  
   // Now establish the connection to the data source.  
   pIDBInitialize->Initialize();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="2b29c-116">参照</span><span class="sxs-lookup"><span data-stu-id="2b29c-116">See Also</span></span>  
 [<span data-ttu-id="2b29c-117">SQL Server Native Client OLE DB プロバイダー アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="2b29c-117">Creating a SQL Server Native Client OLE DB Provider Application</span></span>](creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
  
