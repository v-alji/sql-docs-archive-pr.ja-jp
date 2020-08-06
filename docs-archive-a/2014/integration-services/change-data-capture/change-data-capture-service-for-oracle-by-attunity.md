---
title: Attunity の Change Data Capture Service for Oracle | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 22ec8a5c-9550-4d38-8a4a-485ec3e53ea8
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 68e68e9edd91bd1d0c718b32e29c3b29f74778c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87641824"
---
# <a name="change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="93784-102">Attunity の Change Data Capture Service for Oracle</span><span class="sxs-lookup"><span data-stu-id="93784-102">Change Data Capture Service for Oracle by Attunity</span></span>
  <span data-ttu-id="93784-103">CDC Service for Oracle は、Oracle トランザクション ログをスキャンして目的の Oracle テーブルに対する変更を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 変更テーブルにキャプチャする Windows サービスです。</span><span class="sxs-lookup"><span data-stu-id="93784-103">The CDC Service for Oracle is a Windows service that scans Oracle transaction logs and captures changes to Oracle tables of interest into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] change tables.</span></span> <span data-ttu-id="93784-104">Oracle からキャプチャされた変更が格納される SQL 変更テーブルは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のネイティブの変更データ キャプチャ機能で使用される変更テーブルと同じ種類のテーブルです。</span><span class="sxs-lookup"><span data-stu-id="93784-104">The SQL change tables where the changes captured from Oracle are stored are the same type of change tables used in the native [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Change Data Capture feature.</span></span> <span data-ttu-id="93784-105">そのため、このような変更も、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに対して行われた変更を使用する場合と同様に簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="93784-105">This makes consuming these changes as easy as consuming changes made to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases.</span></span>  
  
## <a name="installation"></a><span data-ttu-id="93784-106">インストール</span><span class="sxs-lookup"><span data-stu-id="93784-106">Installation</span></span>  
 <span data-ttu-id="93784-107">CDC Service for Oracle は、キャプチャするソース Oracle データベースと、対象の CDC データベースが存在する対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにアクセスできる、サポートされているすべての Windows コンピューターにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="93784-107">The CDC Service for Oracle can be installed on any supported Windows computer with access to the source Oracle database(s) being captured and the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance where the target CDC database resides.</span></span> <span data-ttu-id="93784-108">CDC Service では、Oracle データベースまたは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースのローカル インストールは必要なく、サポートされるクライアントのみが必要です。</span><span class="sxs-lookup"><span data-stu-id="93784-108">The CDC Service does not need a local installation of the Oracle database or the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database, only their supported clients.</span></span> <span data-ttu-id="93784-109">必要なデータベース コンポーネントのインストール場所の詳細については、「 **データベースの前提条件** 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93784-109">For information about where to install the required database components, see **Database Prerequisites** in this topic.</span></span>  
  
 <span data-ttu-id="93784-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC Service for Oracle をインストールすると、サービス構成 UI とサービス プログラムが選択した場所に配置されます。</span><span class="sxs-lookup"><span data-stu-id="93784-110">The installation of the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CDC Service for Oracle places the service configuration UI and the service program in the selected location.</span></span> <span data-ttu-id="93784-111">CDC Service for Oracle は、Oracle CDC Service 構成コンソールを使用して個別に構成します。</span><span class="sxs-lookup"><span data-stu-id="93784-111">The CDC Service for Oracle is configured separately using the Oracle CDC Service Configuration Console.</span></span> <span data-ttu-id="93784-112">Oracle CDC Service の構成の詳細については、「 [Change Data Capture Service for Oracle by Attunity の F1 ヘルプ](change-data-capture-service-for-oracle-by-attunity-f1-help.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93784-112">For more information on configuring the Oracle CDC Service, see [Change Data Capture Service for Oracle by Attunity F1 Help](change-data-capture-service-for-oracle-by-attunity-f1-help.md).</span></span>  
  
 <span data-ttu-id="93784-113">CDC Service for Oracle をインストールするには、SQL Server のインストールメディアから手動で**AttunityOracleCdcService.msi**を実行します。</span><span class="sxs-lookup"><span data-stu-id="93784-113">To install the CDC Service for Oracle, manually run **AttunityOracleCdcService.msi** from the SQL Server installation media.</span></span> <span data-ttu-id="93784-114">X86 および x64 用のインストールパッケージは、SQL Server インストールメディアの \*\*.\Tools\AttunityCDCOracle \\ \*\*にあります。</span><span class="sxs-lookup"><span data-stu-id="93784-114">Installation packages for x86 and x64 are located in **.\Tools\AttunityCDCOracle\\** on the SQL Server installation media.</span></span>  
  
 <span data-ttu-id="93784-115">CDC Service for Oracle は、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client がインストールされたサポートされているすべての Windows コンピューターにインストールできます。対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がインストールされている同じコンピューターにインストールする必要はありません。</span><span class="sxs-lookup"><span data-stu-id="93784-115">The CDC Service for Oracle can be installed on any supported Windows computer where the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client is installed; it does not need to be installed on the same computer where the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed.</span></span>  
  
## <a name="supported-windows-environments"></a><span data-ttu-id="93784-116">サポートされている Windows 環境</span><span class="sxs-lookup"><span data-stu-id="93784-116">Supported Windows Environments</span></span>  
 <span data-ttu-id="93784-117">Change Data Capture Service for Oracle by Attunity は、次の Windows 環境で実行できます。</span><span class="sxs-lookup"><span data-stu-id="93784-117">The Change Data Capture Service for Oracle by Attunity can run in the following Windows environments:</span></span>  
  
-   <span data-ttu-id="93784-118">Windows 8</span><span class="sxs-lookup"><span data-stu-id="93784-118">Windows 8</span></span>  
  
-   <span data-ttu-id="93784-119">Windows 7 32 ビット (x86) および 64 ビット (x64)</span><span class="sxs-lookup"><span data-stu-id="93784-119">Windows 7 32-bit (x86) and 64-bit (x64)</span></span>  
  
-   <span data-ttu-id="93784-120">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="93784-120">Windows Server 2012</span></span>  
  
-   <span data-ttu-id="93784-121">Windows Server 2008 R2 Service Pack 1</span><span class="sxs-lookup"><span data-stu-id="93784-121">Windows Server 2008 R2 with Service Pack 1</span></span>  
  
-   <span data-ttu-id="93784-122">Windows Server 2008 Service Pack 2 (32 ビット (x86) および 64 ビット (x64))</span><span class="sxs-lookup"><span data-stu-id="93784-122">Windows Server 2008 32-bit (x86) and 64-bit (x64) with Service Pack 2</span></span>  
  
## <a name="database-prerequisites"></a><span data-ttu-id="93784-123">データベースの前提条件</span><span class="sxs-lookup"><span data-stu-id="93784-123">Database Prerequisites</span></span>  
 <span data-ttu-id="93784-124">CDC Service for Oracle を使用するには、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle ソフトウェアをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="93784-124">To work with the CDC Service for Oracle you must install the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Native Client Oracle software.</span></span> <span data-ttu-id="93784-125">これは、Oracle CDC Service をインストールする前に Oracle から入手してインストールする必要がある必須ソフトウェアです。</span><span class="sxs-lookup"><span data-stu-id="93784-125">This is a prerequisite that should be obtained from Oracle and installed before installing the Oracle CDC Service.</span></span> <span data-ttu-id="93784-126">さらに、SQL Server セットアップを使用して SQL Server ODBC クライアントをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="93784-126">Additionally, you need to install the SQL Server ODBC Client using SQL Server Setup.</span></span>  
  
 <span data-ttu-id="93784-127">CDC Service for Oracle では、次のバージョンがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="93784-127">The CDC Service for Oracle supports the following versions:</span></span>  
  
### <a name="source-oracle-database"></a><span data-ttu-id="93784-128">ソース Oracle データベース</span><span class="sxs-lookup"><span data-stu-id="93784-128">Source Oracle Database</span></span>  
  
-   <span data-ttu-id="93784-129">Oracle Database 11x、すべてのバージョン</span><span class="sxs-lookup"><span data-stu-id="93784-129">Oracle Database 11x, any version</span></span>  
  
-   <span data-ttu-id="93784-130">Oracle Database 10x、すべてのバージョン</span><span class="sxs-lookup"><span data-stu-id="93784-130">Oracle Database 10x, any version</span></span>  
  
### <a name="target-sql-server-database"></a><span data-ttu-id="93784-131">対象の SQL Server データベース</span><span class="sxs-lookup"><span data-stu-id="93784-131">Target SQL Server Database</span></span>  
 <span data-ttu-id="93784-132">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="93784-132">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="running-the-installation-program"></a><span data-ttu-id="93784-133">インストール プログラムの実行</span><span class="sxs-lookup"><span data-stu-id="93784-133">Running the Installation Program</span></span>  
 <span data-ttu-id="93784-134">CDC Service for Oracle をインストールするには、使用している Windows プラットフォーム (32/64 ビット) 用のインストール ウィザードを開き、画面の指示に従います。</span><span class="sxs-lookup"><span data-stu-id="93784-134">To install the CDC Service for Oracle, open the installation wizard for the Windows platform you are using (32/64-bit) and follow the directions on the screen.</span></span>  
  
## <a name="uninstalling-change-data-capture-service-for-oracle-by-attunity"></a><span data-ttu-id="93784-135">Change Data Capture Service for Oracle by Attunity のアンインストール</span><span class="sxs-lookup"><span data-stu-id="93784-135">Uninstalling Change Data Capture Service for Oracle by Attunity</span></span>  
 <span data-ttu-id="93784-136">CDC Service for Oracle をアンインストールするには、コントロール パネルの [プログラムと機能] を使用します。</span><span class="sxs-lookup"><span data-stu-id="93784-136">You uninstall the CDC Service for Oracle using Control Panel, Programs and Features.</span></span>  
  
 <span data-ttu-id="93784-137">CDC Service をアンインストールしても、作成した [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースは削除されません。</span><span class="sxs-lookup"><span data-stu-id="93784-137">Uninstalling the CDC Service does not delete the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases created.</span></span> <span data-ttu-id="93784-138">ツールを完全に削除するには、使用していた対象の [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで作成した MSXDBCDC データベースと特定の CDC データベースを削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="93784-138">For complete removal of the tool, you must remove the MSXDBCDC database and the specific CDC databases that were created in the target [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance you worked with.</span></span>  
  
 <span data-ttu-id="93784-139">CDC Service ソフトウェアをアンインストールしてから別のコンピューターにインストールする場合は、次の定義を指定するだけで済みます。</span><span class="sxs-lookup"><span data-stu-id="93784-139">If you uninstall the CDC Service software from one machine and install it on another computer, you only need to provide the following definitions:</span></span>  
  
-   <span data-ttu-id="93784-140">サービス アカウント</span><span class="sxs-lookup"><span data-stu-id="93784-140">Service account</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="93784-141">の接続文字列と資格情報</span><span class="sxs-lookup"><span data-stu-id="93784-141">connect string and credentials</span></span>  
  
-   <span data-ttu-id="93784-142">マスター パスワード</span><span class="sxs-lookup"><span data-stu-id="93784-142">The master password</span></span>  
  
 <span data-ttu-id="93784-143">他のすべての定義は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に格納されており、別のコンピューター上の以前のインストール環境から取得できます。</span><span class="sxs-lookup"><span data-stu-id="93784-143">All the other definitions are stored in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and are available from the previous installation on another computer.</span></span>  
  
## <a name="in-this-documentation"></a><span data-ttu-id="93784-144">このドキュメントの内容</span><span class="sxs-lookup"><span data-stu-id="93784-144">In This Documentation</span></span>  
  
-   [<span data-ttu-id="93784-145">Change Data Capture Service for Oracle by Attunity のシステム アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="93784-145">Change Data Capture Service for Oracle by Attunity System Architecture</span></span>](change-data-capture-service-for-oracle-by-attunity-system-architecture.md)  
  
-   [<span data-ttu-id="93784-146">Oracle CDC Service</span><span class="sxs-lookup"><span data-stu-id="93784-146">The Oracle CDC Service</span></span>](the-oracle-cdc-service.md)  
  
-   [<span data-ttu-id="93784-147">Change Data Capture Service for Oracle by Attunity の F1 ヘルプ</span><span class="sxs-lookup"><span data-stu-id="93784-147">Change Data Capture Service for Oracle by Attunity F1 Help</span></span>](change-data-capture-service-for-oracle-by-attunity-f1-help.md)  
  
-   [<span data-ttu-id="93784-148">Change Data Capture Service for Oracle by Attunity 操作ガイド</span><span class="sxs-lookup"><span data-stu-id="93784-148">Change Data Capture Service for Oracle by Attunity How to Guide</span></span>](change-data-capture-service-for-oracle-by-attunity-how-to-guide.md)  
  
## <a name="see-also"></a><span data-ttu-id="93784-149">参照</span><span class="sxs-lookup"><span data-stu-id="93784-149">See Also</span></span>  
 [<span data-ttu-id="93784-150">Oracle CDC Service の使用</span><span class="sxs-lookup"><span data-stu-id="93784-150">Working with the Oracle CDC Service</span></span>](working-with-the-oracle-cdc-service.md)  
  
  
