---
title: LocalDB ヘッダーとバージョン情報の SQL Server Express |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
api_location:
- sqluserinstance.dll
ms.assetid: 506b5161-b902-4894-b87b-9192d7b1664a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 138081852cf505b03265fd9c5f39eae6ed2af39b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87645086"
---
# <a name="sql-server-express-localdb-header-and-version-information"></a><span data-ttu-id="da2c3-102">SQL Server Express LocalDB ヘッダーとバージョン情報</span><span class="sxs-lookup"><span data-stu-id="da2c3-102">SQL Server Express LocalDB Header and Version Information</span></span>
  <span data-ttu-id="da2c3-103">SQL Server Express LocalDB インスタンス API には、独立したヘッダー ファイルはありません。LocalDB の関数署名とエラー コードは、SQL Server Native Client ヘッダー ファイル (sqlncli.h) に定義されています。</span><span class="sxs-lookup"><span data-stu-id="da2c3-103">There is no separate header file for the SQL Server Express LocalDB instance API; the LocalDB function signatures and error codes are defined in the SQL Server Native Client header file (sqlncli.h).</span></span> <span data-ttu-id="da2c3-104">LocalDB インスタンス API を使用するには、プロジェクトに sqlncli.h ヘッダー ファイルをインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="da2c3-104">To use the LocalDB instance API, you must include the sqlncli.h header file in your project.</span></span>  
  
## <a name="localdb-versioning"></a><span data-ttu-id="da2c3-105">LocalDB のバージョン管理</span><span class="sxs-lookup"><span data-stu-id="da2c3-105">LocalDB Versioning</span></span>  
 <span data-ttu-id="da2c3-106">LocalDB インストールでは、主要な SQL Server バージョンごとの単一のバイナリ セットを使用します。</span><span class="sxs-lookup"><span data-stu-id="da2c3-106">The LocalDB installation uses a single set of binaries per major SQL Server version.</span></span> <span data-ttu-id="da2c3-107">これらの LocalDB バージョンは維持され、個別にパッチが適用されます。</span><span class="sxs-lookup"><span data-stu-id="da2c3-107">These LocalDB versions are maintained and patched independently.</span></span> <span data-ttu-id="da2c3-108">つまり、ユーザーはどの LocalDB ベースライン リリース (主要な SQL Server バージョン) を使用するのかを指定する必要があるということです。</span><span class="sxs-lookup"><span data-stu-id="da2c3-108">This means that the user has to specify which LocalDB baseline release (that is, major SQL Server version) he or she will be using.</span></span> <span data-ttu-id="da2c3-109">バージョンは **、.NET Framework バージョン**クラスで定義されている標準バージョン形式で指定されます。</span><span class="sxs-lookup"><span data-stu-id="da2c3-109">The version is specified in the standard version format defined by the .NET Framework **System.Version** class:</span></span>  
  
 <span data-ttu-id="da2c3-110">*major.minor[.build[.revision]]*</span><span class="sxs-lookup"><span data-stu-id="da2c3-110">*major.minor[.build[.revision]]*</span></span>  
  
 <span data-ttu-id="da2c3-111">バージョン文字列の最初の2つの数値 (*major*および*minor*) は必須です。</span><span class="sxs-lookup"><span data-stu-id="da2c3-111">The first two numbers in the version string (*major* and *minor*) are mandatory.</span></span> <span data-ttu-id="da2c3-112">バージョン文字列の最後の2つの数値 (*build*と*revision*) は省略可能で、ユーザーがそのままにした場合の既定値は0です。これは、ユーザーが LocalDB バージョン番号として "12.2" だけを指定した場合、ユーザーが "12.2.0.0" を指定したかのように処理されることを意味します。</span><span class="sxs-lookup"><span data-stu-id="da2c3-112">The last two numbers in the version string (*build* and *revision*) are optional and default to zero if the user leaves them out. This means that if the user specifies only "12.2" as the LocalDB version number, it will be treated as if the user specified "12.2.0.0".</span></span>  
  
 <span data-ttu-id="da2c3-113">LocalDB インストールのバージョンは、SQL Server インスタンス レジストリ キーの下の MSSQLServer\CurrentVersion レジストリ キーに定義されます。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="da2c3-113">The version for the LocalDB installation is defined in the MSSQLServer\CurrentVersion registry key under the SQL Server instance registry key, for example:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\MSSQL12E.LOCALDB\ MSSQLServer\CurrentVersion: "CurrentVersion"="12.0.2531.0"  
```  
  
 <span data-ttu-id="da2c3-114">同じ 1 台のワークステーション上で複数の LocalDB バージョンが同時にサポートされます。</span><span class="sxs-lookup"><span data-stu-id="da2c3-114">Multiple LocalDB versions on the same workstation are supported side-by-side.</span></span> <span data-ttu-id="da2c3-115">ただし、ユーザーコードは、常にローカルコンピューター上で使用可能な最新の**Sqluserinstance.dll** DLL を使用して LocalDB インスタンスに接続します。</span><span class="sxs-lookup"><span data-stu-id="da2c3-115">However, user code always uses the latest available **SQLUserInstance** DLL on the local computer to connect to LocalDB instances.</span></span>  
  
## <a name="locating-the-sqluserinstance-dll"></a><span data-ttu-id="da2c3-116">SQLUserInstance DLL の検索</span><span class="sxs-lookup"><span data-stu-id="da2c3-116">Locating the SQLUserInstance DLL</span></span>  
 <span data-ttu-id="da2c3-117">クライアントプロバイダーは、 **Sqluserinstance.dll** DLL を検索するために、次のレジストリキーを使用します。</span><span class="sxs-lookup"><span data-stu-id="da2c3-117">To locate the **SQLUserInstance** DLL, the client provider uses the following registry key:</span></span>  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions]  
```  
  
 <span data-ttu-id="da2c3-118">このキーの下に、キーのリストがあります。このコンピューターにインストールされている LocalDB のバージョンごとに 1 つのキーがあります。</span><span class="sxs-lookup"><span data-stu-id="da2c3-118">Under this key there is a list of keys, one for each version of LocalDB installed on the computer.</span></span> <span data-ttu-id="da2c3-119">これらの各キーには、という形式で LocalDB バージョン番号が付けられてい *\<major-version>* ます。*\<minor-version>*</span><span class="sxs-lookup"><span data-stu-id="da2c3-119">Each of these keys is named with the LocalDB version number in the format *\<major-version>*.*\<minor-version>*</span></span> <span data-ttu-id="da2c3-120">(たとえば、のキー [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] は12.0 という名前です)。</span><span class="sxs-lookup"><span data-stu-id="da2c3-120">(for example, the key for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] is named 12.0).</span></span> <span data-ttu-id="da2c3-121">各バージョン キーの下に、`InstanceAPIPath` の名前と値のペアが 1 つあります。このペアは、そのバージョンでインストールされた SQLUserInstance.dll ファイルの絶対パスを定義します。</span><span class="sxs-lookup"><span data-stu-id="da2c3-121">Under each version key there is an `InstanceAPIPath` name-value pair that defines the full path to the SQLUserInstance.dll file installed with that version.</span></span> <span data-ttu-id="da2c3-122">次に、LocalDB バージョン 11.0 と 12.0 がインストールされたコンピューターのレジストリ エントリの例を示します。</span><span class="sxs-lookup"><span data-stu-id="da2c3-122">The following example shows the registry entries for a computer that has LocalDB versions 11.0 and 12.0 installed:</span></span>  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"]  
```  
  
 <span data-ttu-id="da2c3-123">クライアントプロバイダーは、インストールされているすべてのバージョンの最新バージョンを検索し、関連付けられている値から**Sqluserinstance.dll** DLL ファイルを読み込みます `InstanceAPIPath` 。</span><span class="sxs-lookup"><span data-stu-id="da2c3-123">The client provider must find the latest version among all installed versions and load the **SQLUserInstance** DLL file from the associated `InstanceAPIPath` value.</span></span>  
  
### <a name="wow64-mode-on-64-bit-windows"></a><span data-ttu-id="da2c3-124">64 ビット版 Windows 上の WOW64 モード</span><span class="sxs-lookup"><span data-stu-id="da2c3-124">WOW64 Mode on 64-bit Windows</span></span>  
 <span data-ttu-id="da2c3-125">LocalDB の 64 ビット インストールには、追加のレジストリ キー セットがあるため、Windows-32-on-Windows-64 (WOW64) モードで実行される 32 ビット版アプリケーションで LocalDB を使用することができます。</span><span class="sxs-lookup"><span data-stu-id="da2c3-125">64-bit installations of LocalDB will have an additional set of registry keys to allow 32-bit applications running in Windows-32-on-Windows-64 (WOW64) mode to use LocalDB.</span></span> <span data-ttu-id="da2c3-126">具体的には、64 ビット版 Windows では、LocalDB MSI が次のレジストリ キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="da2c3-126">Specifically, on 64-bit Windows, the LocalDB MSI will create the following registry keys:</span></span>  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wow6432Node\Microsoft SQL Server Local DB\Installed Versions\12.0]  
"InstanceAPIPath"="C:\\Program Files (x86)\\Microsoft SQL Server\\120\\LocalDB\\Binn\\SqlUserInstance.dll"]  
  
```  
  
 <span data-ttu-id="da2c3-127">64ビットのプログラムキーを読み取ると、 `Installed Versions` 64 ビットバージョンの**sqluserinstance.dll** DLL を指す値が表示されます。一方、32ビットプログラム (WOW64 モードでは、64ビットの Windows で実行されている) は `Installed Versions` 、hive の下にあるキーに自動的にリダイレクトされ `Wow6432Node` ます。</span><span class="sxs-lookup"><span data-stu-id="da2c3-127">64-bit programs reading the `Installed Versions` key will see values pointing to 64-bit versions of the **SQLUserInstance** DLL, while 32-bit programs (running on 64-bit Windows in WOW64 mode) will be automatically redirected to an `Installed Versions` key located under the `Wow6432Node` hive.</span></span> <span data-ttu-id="da2c3-128">このキーには、 **Sqluserinstance.dll** DLL の32ビットバージョンをポイントする値が含まれています。</span><span class="sxs-lookup"><span data-stu-id="da2c3-128">This key contains values pointing to 32-bit versions of the **SQLUserInstance** DLL.</span></span>  
  
## <a name="using-localdb_define_proxy_functions"></a><span data-ttu-id="da2c3-129">LOCALDB_DEFINE_PROXY_FUNCTIONS の使用</span><span class="sxs-lookup"><span data-stu-id="da2c3-129">Using LOCALDB_DEFINE_PROXY_FUNCTIONS</span></span>  
 <span data-ttu-id="da2c3-130">LocalDB インスタンス API は、 **Sqluserinstance.dll** DLL の検出と読み込みを自動化する LOCALDB_DEFINE_PROXY_FUNCTIONS という名前の定数を定義します。</span><span class="sxs-lookup"><span data-stu-id="da2c3-130">The LocalDB instance API defines a constant named LOCALDB_DEFINE_PROXY_FUNCTIONS that automates the discovery and loading of the **SqlUserInstance** DLL.</span></span>  
  
 <span data-ttu-id="da2c3-131">この定数によって有効化されるコードのセクションにより、各 LocalDB API のプロキシが実装されます。</span><span class="sxs-lookup"><span data-stu-id="da2c3-131">The section of code enabled by this constant provides an implementation of proxies for each of the LocalDB APIs.</span></span> <span data-ttu-id="da2c3-132">プロキシの実装では、共通の関数を使用して、インストールされている最新の**Sqluserinstance.dll** DLL 内のエントリポイントにバインドしてから、要求を転送します。</span><span class="sxs-lookup"><span data-stu-id="da2c3-132">The proxy implementations use a common function to bind to entry points in the latest installed **SqlUserInstance** DLL, and then forward the requests.</span></span>  
  
 <span data-ttu-id="da2c3-133">プロキシ関数が有効化されるのは、定数 LOCALDB_DEFINE_PROXY_FUNCTIONS がユーザー コードで定義された後に、sqlncli.h ファイルがインクルードされた場合だけです。</span><span class="sxs-lookup"><span data-stu-id="da2c3-133">The proxy functions are enabled only if the constant LOCALDB_DEFINE_PROXY_FUNCTIONS is defined in the user code before including the sqlncli.h file.</span></span> <span data-ttu-id="da2c3-134">この定数は、すべての API エントリ ポイントの外部関数名を定義するので、1 つのソース モジュール (.cpp ファイル) だけに定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="da2c3-134">The constant should be defined in only one source module (.cpp file) because it defines external function names for all of the API entry points.</span></span> <span data-ttu-id="da2c3-135">この定数により、各 LocalDB API のプロキシが実装されます。</span><span class="sxs-lookup"><span data-stu-id="da2c3-135">It provides an implementation of proxies for each of the LocalDB APIs.</span></span>  
  
 <span data-ttu-id="da2c3-136">次のコード例では、ネイティブの C++ コードのマクロを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="da2c3-136">The following code example shows how to use the macro from the native C++ code:</span></span>  
  
```  
// Define the LOCALDB_DEFINE_PROXY_FUNCTIONS constant to enable the LocalDB proxy functions   
// The #define has to take place BEFORE the API header file (sqlncli.h) is included  
#define LOCALDB_DEFINE_PROXY_FUNCTIONS  
#include <sqlncli.h>  
...  
HRESULT hr = S_OK;  
  
// Create LocalDB instance by calling the create API proxy function included by macro  
if (FAILED(hr = LocalDBCreateInstance( L"12.0", L"name", 0)))  
{  
...  
}  
...  
  
```  
  
  
