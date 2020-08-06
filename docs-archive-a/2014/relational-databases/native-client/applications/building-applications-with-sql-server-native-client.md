---
title: SQL Server Native Client | を使用したアプリケーションの構築Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], building applications
- SQLNCLI, building applications
- applications [SQL Server Native Client]
- SQL Server Native Client, building applications
ms.assetid: 254a2b48-f0e3-43b5-a48d-3d666c2a779f
author: rothja
ms.author: jroth
ms.openlocfilehash: d08fe1042ab1a79f6b48648f5a774b4fbac49ead
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642040"
---
# <a name="building-applications-with-sql-server-native-client"></a><span data-ttu-id="abf7f-102">SQL Server Native Client を使用したアプリケーションのビルド</span><span class="sxs-lookup"><span data-stu-id="abf7f-102">Building Applications with SQL Server Native Client</span></span>
  <span data-ttu-id="abf7f-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ライブラリを使用するアプリケーションを開発する際には、いくつかの課題があります。</span><span class="sxs-lookup"><span data-stu-id="abf7f-103">When developing an application that uses the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client library, there are a number of issues that come into play.</span></span> <span data-ttu-id="abf7f-104">このセクションのトピックでは、MDAC から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client へのアップグレード、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ヘッダー ファイルやライブラリ ファイルの使用など、これらの課題の多くについて説明します。また、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client と併用できるさまざまな接続文字列の概要についても説明します。</span><span class="sxs-lookup"><span data-stu-id="abf7f-104">The topics in this section discuss many of these issues including upgrading from MDAC to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client, using the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files, and an overview of the various connection strings that can be used with [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="abf7f-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="abf7f-105">In This Section</span></span>  
 [<span data-ttu-id="abf7f-106">SQL Server Native Client のインストール</span><span class="sxs-lookup"><span data-stu-id="abf7f-106">Installing SQL Server Native Client</span></span>](installing-sql-server-native-client.md)  
 <span data-ttu-id="abf7f-107">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client をインストールする方法、各種コンポーネントがインストールされる場所、および [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client をアンインストールする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="abf7f-107">Discusses how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client is installed, the locations that various components are installed to, and how to uninstall [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="abf7f-108">SQL Server Native Client のコンポーネント</span><span class="sxs-lookup"><span data-stu-id="abf7f-108">Components of SQL Server Native Client</span></span>](components-of-sql-server-native-client.md)  
 <span data-ttu-id="abf7f-109">ライブラリ ファイル、リソース ファイル、ヘルプ ファイル、ヘッダー ファイルなど、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を構成するコンポーネントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="abf7f-109">Discusses the components that make up [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client including library, resource, help, and header files.</span></span>  
  
 [<span data-ttu-id="abf7f-110">SQL Server Native Client での接続文字列キーワードの使用</span><span class="sxs-lookup"><span data-stu-id="abf7f-110">Using Connection String Keywords with SQL Server Native Client</span></span>](using-connection-string-keywords-with-sql-server-native-client.md)  
 <span data-ttu-id="abf7f-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 経由でデータベースに接続するときに使用できる、さまざまな接続文字列について説明します。</span><span class="sxs-lookup"><span data-stu-id="abf7f-111">Discusses the various types of connection strings that can be used when connecting to a database through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="abf7f-112">SQL Server Native Client ヘッダー ファイルとライブラリ ファイルの使用</span><span class="sxs-lookup"><span data-stu-id="abf7f-112">Using the SQL Server Native Client Header and Library Files</span></span>](using-the-sql-server-native-client-header-and-library-files.md)  
 <span data-ttu-id="abf7f-113">アプリケーション内で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ヘッダー ファイルとライブラリ ファイルを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="abf7f-113">Discusses how to use the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client header and library files within an application.</span></span>  
  
 [<span data-ttu-id="abf7f-114">MDAC から SQL Server Native Client へのアプリケーションの更新</span><span class="sxs-lookup"><span data-stu-id="abf7f-114">Updating an Application to SQL Server Native Client from MDAC</span></span>](updating-an-application-to-sql-server-native-client-from-mdac.md)  
 <span data-ttu-id="abf7f-115">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client と MDAC の違い、および MDAC から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client にアップグレードするときに考慮すべき点について説明します。</span><span class="sxs-lookup"><span data-stu-id="abf7f-115">Discusses the differences between [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and MDAC and issues that should be considered when upgrading from MDAC to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="abf7f-116">SQL Server 2005 Native Client からアプリケーションを更新する</span><span class="sxs-lookup"><span data-stu-id="abf7f-116">Updating an Application from SQL Server 2005 Native Client</span></span>](updating-an-application-from-sql-server-2005-native-client.md)  
 <span data-ttu-id="abf7f-117">[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client から [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] Native Client にアップグレードするときに考慮すべき点について説明します。</span><span class="sxs-lookup"><span data-stu-id="abf7f-117">Discusses issues that should be considered when upgrading from [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] Native Client to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)].</span></span>  
  
 [<span data-ttu-id="abf7f-118">SQL Server Native Client と ADO の併用</span><span class="sxs-lookup"><span data-stu-id="abf7f-118">Using ADO with SQL Server Native Client</span></span>](using-ado-with-sql-server-native-client.md)  
 <span data-ttu-id="abf7f-119">ADO で [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] の機能にアクセスし、それらの機能を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="abf7f-119">Discusses how ADO can use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client to access and use [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] functionality.</span></span>  
  
 [<span data-ttu-id="abf7f-120">SQL Server Native Client のサポート ポリシー</span><span class="sxs-lookup"><span data-stu-id="abf7f-120">Support Policies for SQL Server Native Client</span></span>](support-policies-for-sql-server-native-client.md)  
 <span data-ttu-id="abf7f-121">さまざまなデータ アクセス コンポーネントを、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client の各バージョンで使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="abf7f-121">Discusses how various data-access components can be used with different versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
 [<span data-ttu-id="abf7f-122">SQL Server Native Client を使用した Azure SQL データベースへの接続</span><span class="sxs-lookup"><span data-stu-id="abf7f-122">Connecting to an Azure SQL Database Using SQL Server Native Client</span></span>](connecting-to-a-windows-azure-sql-database-using-sql-server-native-client.md)  
 <span data-ttu-id="abf7f-123">[!INCLUDE[ssSDS](../../../includes/sssds-md.md)] Native Client を使用して [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] に接続する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="abf7f-123">Discusses how to connect to a [!INCLUDE[ssSDS](../../../includes/sssds-md.md)] using [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf7f-124">参照</span><span class="sxs-lookup"><span data-stu-id="abf7f-124">See Also</span></span>  
 <span data-ttu-id="abf7f-125">[SQL Server Native Client プログラミング](../sql-server-native-client-programming.md) </span><span class="sxs-lookup"><span data-stu-id="abf7f-125">[SQL Server Native Client Programming](../sql-server-native-client-programming.md) </span></span>  
 <span data-ttu-id="abf7f-126">[ODBC の操作方法に関するトピック](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span><span class="sxs-lookup"><span data-stu-id="abf7f-126">[ODBC How-to Topics](../../native-client-odbc-how-to/odbc-how-to-topics.md) </span></span>  
 [<span data-ttu-id="abf7f-127">OLE DB の使用法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="abf7f-127">OLE DB How-to Topics</span></span>](../../native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
  
