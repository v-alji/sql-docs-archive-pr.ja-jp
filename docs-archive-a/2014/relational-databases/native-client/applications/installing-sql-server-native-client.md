---
title: SQL Server Native Client のインストール |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client, uninstalling
- SQLNCLI, installing
- SQLNCLI, uninstalling
- Setup [SQL Server Native Client]
- uninstalling SQL Server Native Client
- data access [SQL Server Native Client], uninstalling SQL Server Native Client
- installing SQL Server Native Client
- SQL Server Native Client, installing
- data access [SQL Server Native Client], installing SQL Server Native Client
- removing SQL Server Native Client
ms.assetid: c6abeab2-0052-49c9-be79-cfbc50bff5c1
author: rothja
ms.author: jroth
ms.openlocfilehash: 86a30924dc6dfc0b5b4f4dc176f0186d8f35b2f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642039"
---
# <a name="installing-sql-server-native-client"></a><span data-ttu-id="591b8-102">SQL Server Native Client のインストール</span><span class="sxs-lookup"><span data-stu-id="591b8-102">Installing SQL Server Native Client</span></span>
  <span data-ttu-id="591b8-103">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 は、のインストール時にインストールされ [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="591b8-103">Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 is installed when you install [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="591b8-104">[!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client は存在しません。</span><span class="sxs-lookup"><span data-stu-id="591b8-104">There is no [!INCLUDE[ssSQL14](../../../includes/sssql14-md.md)] Native Client.</span></span> <span data-ttu-id="591b8-105">詳細については、「 [SQL Server Native Client の新機能](../sql-server-native-client.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="591b8-105">For more information, see [What's New in SQL Server Native Client](../sql-server-native-client.md).</span></span> <span data-ttu-id="591b8-106">また、SQL Server 2012 Feature Pack web ページから sqlncli.msi を取得することもできます。</span><span class="sxs-lookup"><span data-stu-id="591b8-106">You can also get sqlncli.msi from the SQL Server 2012 Feature Pack web page.</span></span> <span data-ttu-id="591b8-107">SQL Server Native Client の最新バージョンをダウンロードするには、Microsoft にアクセスしてください。 [SQL Server。。2012 SP2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=43339)。</span><span class="sxs-lookup"><span data-stu-id="591b8-107">To download the most recent version of the SQL Server Native Client, go to [Microsoft?? SQL Server?? 2012 SP2 Feature Pack](https://www.microsoft.com/download/details.aspx?id=43339).</span></span> <span data-ttu-id="591b8-108">SQL Server 2012 より前のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native client もコンピューターにインストールされている場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] native client 11.0 は以前のバージョンとサイドバイサイドでインストールされます。</span><span class="sxs-lookup"><span data-stu-id="591b8-108">If a previous version of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client earlier than SQL Server 2012 is also installed on the computer, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 11.0 will be installed side-by-side with the earlier version.</span></span>  
  
 <span data-ttu-id="591b8-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client のファイル (sqlncli11.dll、sqlnclir11.rll、および s11ch_sqlncli.chm) は、次の場所にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="591b8-109">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client files (sqlncli11.dll, sqlnclir11.rll, and s11ch_sqlncli.chm) are installed to the following location:</span></span>  
  
 `%SYSTEMROOT%\system32\`  
  
> [!NOTE]  
>  <span data-ttu-id="591b8-110">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーと [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーのすべてのレジストリ設定は、インストール処理の一環として適切に行われます。</span><span class="sxs-lookup"><span data-stu-id="591b8-110">All appropriate registry settings for the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver are made as part of the installation process.</span></span>  
  
 <span data-ttu-id="591b8-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ヘッダー ファイルとライブラリ ファイル (sqlncli.h と sqlncli11.lib) は、次の場所にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="591b8-111">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files (sqlncli.h and sqlncli11.lib) are installed in the following location:</span></span>  
  
 `%PROGRAMFILES%\Microsoft SQL Server\110\SDK`  
  
 <span data-ttu-id="591b8-112">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client をインストールの一部としてインストールすることに加えて、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sqlncli.msi という再配布可能なインストールプログラムもあります。これは、の [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] インストールディスクにあり `%CD%\Setup\` ます。</span><span class="sxs-lookup"><span data-stu-id="591b8-112">In addition to installing [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client as part of the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation, there is also a redistributable installation program named sqlncli.msi, which can be found on the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] installation disk in the following location: `%CD%\Setup\`.</span></span>  
  
 <span data-ttu-id="591b8-113">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client は、sqlncli.msi を使用して配布できます。</span><span class="sxs-lookup"><span data-stu-id="591b8-113">You can distribute [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client through sqlncli.msi.</span></span> <span data-ttu-id="591b8-114">アプリケーションを配置する場合は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client をインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="591b8-114">You might have to install [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client when you deploy an application.</span></span> <span data-ttu-id="591b8-115">チェイナーとブートストラップのテクノロジを使用すると、ユーザーが 1 回のインストール手順に従うだけで複数のパッケージをまとめてインストールできるようになります。</span><span class="sxs-lookup"><span data-stu-id="591b8-115">One way to install multiple packages in what seems to the user to be a single installation is to use chainer and bootstrapper technology.</span></span> <span data-ttu-id="591b8-116">詳細については、「[Visual Studio 2005 用のカスタム ブートストラップ パッケージの作成](https://go.microsoft.com/fwlink/?LinkId=115667)」および「[カスタムの必須コンポーネントの追加](https://go.microsoft.com/fwlink/?LinkId=115668)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="591b8-116">For more information, see [Authoring a Custom Bootstrapper Package for Visual Studio 2005](https://go.microsoft.com/fwlink/?LinkId=115667) and [Adding Custom Prerequisites](https://go.microsoft.com/fwlink/?LinkId=115668).</span></span>  
  
 <span data-ttu-id="591b8-117">x64 バージョンと Itanium バージョンの sqlncli.msi では、32 ビット バージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client もインストールされます。</span><span class="sxs-lookup"><span data-stu-id="591b8-117">The x64 and Itanium versions of sqlncli.msi also install the 32-bit version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="591b8-118">アプリケーションが、開発時に使用したものとは異なるプラットフォームを対象としている場合、Microsoft ダウンロード センターから x64、Itanium、および x86 用のバージョンの sqlncli.msi をダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="591b8-118">If your application targets a platform other than the one it was developed on, you can download versions of sqlncli.msi for x64, Itanium, and x86 from the Microsoft Download Center.</span></span>  
  
 <span data-ttu-id="591b8-119">sqlncli.msi を呼び出すと、既定ではクライアント コンポーネントだけがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="591b8-119">When you invoke sqlncli.msi, only the client components are installed by default.</span></span> <span data-ttu-id="591b8-120">クライアントコンポーネントは、Native Client を使用して開発されたアプリケーションの実行をサポートするファイルです [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="591b8-120">The client components are files that support running an application that was developed using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="591b8-121">SDK コンポーネントもインストールするには、コマンド ラインで `ADDLOCAL=All` を指定します。</span><span class="sxs-lookup"><span data-stu-id="591b8-121">To also install the SDK components, specify `ADDLOCAL=All` on the command line.</span></span> <span data-ttu-id="591b8-122">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="591b8-122">For example:</span></span>  
  
 `msiexec /i sqlncli.msi ADDLOCAL=ALL APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
## <a name="silent-install"></a><span data-ttu-id="591b8-123">サイレント インストール</span><span class="sxs-lookup"><span data-stu-id="591b8-123">Silent Install</span></span>  
 <span data-ttu-id="591b8-124">msiexec で /passive、/qn、/qb、または /qr オプションを指定する場合、IACCEPTSQLNCLILICENSETERMS=YES も指定して、使用許諾契約の条件に同意することを明示的に指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="591b8-124">If you use the /passive, /qn, /qb, or /qr option with msiexec, you must also specify IACCEPTSQLNCLILICENSETERMS=YES, to explicitly indicate that you accept the terms of the end user license.</span></span> <span data-ttu-id="591b8-125">このオプションは、すべて大文字で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="591b8-125">This option must be specified in all capital letters.</span></span>  
  
## <a name="uninstalling-sql-server-native-client"></a><span data-ttu-id="591b8-126">SQL Server Native Client のアンインストール</span><span class="sxs-lookup"><span data-stu-id="591b8-126">Uninstalling SQL Server Native Client</span></span>  
 <span data-ttu-id="591b8-127">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]サーバーやツールなどのアプリケーション [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] は、native client に依存しているため [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 、すべての [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 依存アプリケーションがアンインストールされるまでは、native client をアンインストールしないことが重要です。</span><span class="sxs-lookup"><span data-stu-id="591b8-127">Because applications such as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] server and the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] tools depend on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, it is important not to uninstall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client until all dependent applications are uninstalled.</span></span> <span data-ttu-id="591b8-128">アプリケーションが Native Client に依存しているという警告がユーザーに提供されるようにするには、次のように [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] MSI で APPGUID インストールオプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="591b8-128">To provider users with a warning that your application depends on [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, use the APPGUID install option in your MSI, as follows:</span></span>  
  
 `msiexec /i sqlncli.msi APPGUID={0CC618CE-F36A-415E-84B4-FB1BFF6967E1}`  
  
 <span data-ttu-id="591b8-129">APPGUID に渡す値は、特定の製品コードです。</span><span class="sxs-lookup"><span data-stu-id="591b8-129">The value passed to APPGUID is your specific product code.</span></span> <span data-ttu-id="591b8-130">Microsoft インストーラーを使用してアプリケーションのセットアップ プログラムをバンドルするときは、製品コードを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="591b8-130">A product code must be created when using Microsoft Installer to bundle your application setup program.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="591b8-131">参照</span><span class="sxs-lookup"><span data-stu-id="591b8-131">See Also</span></span>  
 <span data-ttu-id="591b8-132">[SQL Server Native Client を使用したアプリケーションの構築](installing-sql-server-native-client.md) </span><span class="sxs-lookup"><span data-stu-id="591b8-132">[Building Applications with SQL Server Native Client](installing-sql-server-native-client.md) </span></span>  
 [<span data-ttu-id="591b8-133">インストール方法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="591b8-133">Installation How-to Topics</span></span>](../../../sql-server/install/installation-how-to-topics.md)  
  
  
