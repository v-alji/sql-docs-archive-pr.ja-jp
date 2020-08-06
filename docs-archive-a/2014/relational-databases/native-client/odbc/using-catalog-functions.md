---
title: カタログ関数の使用 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC, functions
- SQLLinkedCatalogs function
- SQL Server Native Client ODBC driver, catalog functions
- SQLLinkedServers function
- catalog functions [ODBC]
- functions [ODBC]
ms.assetid: 7773fb2e-06b5-4c4b-88e9-0ad9132ad273
author: rothja
ms.author: jroth
ms.openlocfilehash: 6cac35e658343f606c1953f265c752335c70d81f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644441"
---
# <a name="using-catalog-functions"></a><span data-ttu-id="0433c-102">カタログ関数の使用</span><span class="sxs-lookup"><span data-stu-id="0433c-102">Using Catalog Functions</span></span>
  <span data-ttu-id="0433c-103">どのようなデータベースであっても、その構造は、データベースに格納されたデータを保持するような構造になっています。</span><span class="sxs-lookup"><span data-stu-id="0433c-103">All databases have a structure containing the data stored in the database.</span></span> <span data-ttu-id="0433c-104">この構造の定義は、権限などその他の情報と共にカタログに保存されます。カタログは、システム テーブルのセットとして実装され、データ辞書と呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="0433c-104">A definition of this structure, along with other information such as permissions, is stored in a catalog (implemented as a set of system tables), also known as a data dictionary.</span></span>  
  
 <span data-ttu-id="0433c-105">Native Client ODBC ドライバーを使用すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] アプリケーションは odbc カタログ関数を呼び出すことによってデータベース構造を決定できます。</span><span class="sxs-lookup"><span data-stu-id="0433c-105">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver enables an application to determine the database structure through calls to ODBC catalog functions.</span></span> <span data-ttu-id="0433c-106">カタログ関数は情報を結果セットとして返す関数で、カタログのシステム テーブルをクエリするカタログ ストアド プロシージャを使用して実装されます。</span><span class="sxs-lookup"><span data-stu-id="0433c-106">Catalog functions return information in result sets and are implemented using catalog stored procedures to query the system tables in the catalog.</span></span> <span data-ttu-id="0433c-107">たとえば、アプリケーションが、システム上のすべてのテーブルに関する情報を含む結果セット、または特定のテーブルが持つすべての列に関する情報を含む結果セットを要求するとします。</span><span class="sxs-lookup"><span data-stu-id="0433c-107">For example, an application might request a result set containing information about all the tables on the system or all the columns in a particular table.</span></span> <span data-ttu-id="0433c-108">この場合、標準の ODBC カタログ関数を使用して、アプリケーションが接続している [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] からカタログ情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="0433c-108">The standard ODBC catalog functions are used to get catalog information from the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to which the application connected.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="0433c-109">は分散クエリをサポートします。分散クエリは、1 つのクエリで複数の異種 OLE DB データ ソースのデータにアクセスするクエリです。</span><span class="sxs-lookup"><span data-stu-id="0433c-109">supports distributed queries in which data from multiple, heterogeneous OLE DB data sources is accessed in a single query.</span></span> <span data-ttu-id="0433c-110">リモートの OLE DB データ ソースへアクセスするための方法として、目的のデータ ソースをリンク サーバーとして定義する方法があります。</span><span class="sxs-lookup"><span data-stu-id="0433c-110">One of the methods of accessing a remote OLE DB data source is to define the data source as a linked server.</span></span> <span data-ttu-id="0433c-111">これを行うには、 [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)を使用します。</span><span class="sxs-lookup"><span data-stu-id="0433c-111">This can be done by using [sp_addlinkedserver](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql).</span></span> <span data-ttu-id="0433c-112">リンク サーバーを定義すると、このサーバーのオブジェクトを次のような 4 部構成の名前を使用して Transact-SQL ステートメントで参照できるようになります。</span><span class="sxs-lookup"><span data-stu-id="0433c-112">After the linked server has been defined, objects in that server can be referenced in Transact-SQL statements by using a four-part name:</span></span>  
  
 <span data-ttu-id="0433c-113">*object_name を linked_server_name*します。</span><span class="sxs-lookup"><span data-stu-id="0433c-113">*linked_server_name.catalog.schema.object_name*.</span></span>  
  
 <span data-ttu-id="0433c-114">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーでは、リンク サーバーからのカタログ情報の取得に役立つ、次の 2 つのドライバー固有の関数をサポートします。</span><span class="sxs-lookup"><span data-stu-id="0433c-114">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports two driver-specific functions that help get catalog information from linked servers:</span></span>  
  
-   <span data-ttu-id="0433c-115">**SQLLinkedServers**</span><span class="sxs-lookup"><span data-stu-id="0433c-115">**SQLLinkedServers**</span></span>  
  
     <span data-ttu-id="0433c-116">ローカルサーバーに定義されているリンクサーバーの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="0433c-116">Returns a list of the linked servers defined to the local server.</span></span>  
  
-   <span data-ttu-id="0433c-117">**SQLLinkedCatalogs**</span><span class="sxs-lookup"><span data-stu-id="0433c-117">**SQLLinkedCatalogs**</span></span>  
  
     <span data-ttu-id="0433c-118">リンク サーバーに含まれるカタログの一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="0433c-118">Returns a list of the catalogs contained in a linked server.</span></span>  
  
 <span data-ttu-id="0433c-119">リンクサーバー名とカタログ名を指定すると、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native CLIENT ODBC ドライバーは、 _linked_server_name_の2部構成の名前を使用してカタログから情報を取得することをサポートし**ます。** 次の ODBC カタログ関数の*CatalogName*の_カタログ_。</span><span class="sxs-lookup"><span data-stu-id="0433c-119">After you have a linked server name and a catalog name, the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports getting information from the catalog by using a two-part name of _linked_server_name_**.**_catalog_ for *CatalogName* on the following ODBC catalog functions:</span></span>  
  
-   <span data-ttu-id="0433c-120">**SQLColumnPrivileges**</span><span class="sxs-lookup"><span data-stu-id="0433c-120">**SQLColumnPrivileges**</span></span>  
  
-   <span data-ttu-id="0433c-121">**SQLColumns**</span><span class="sxs-lookup"><span data-stu-id="0433c-121">**SQLColumns**</span></span>  
  
-   <span data-ttu-id="0433c-122">**SQLPrimaryKeys**</span><span class="sxs-lookup"><span data-stu-id="0433c-122">**SQLPrimaryKeys**</span></span>  
  
-   <span data-ttu-id="0433c-123">**SQLStatistics**</span><span class="sxs-lookup"><span data-stu-id="0433c-123">**SQLStatistics**</span></span>  
  
-   <span data-ttu-id="0433c-124">**SQLTablePrivileges**</span><span class="sxs-lookup"><span data-stu-id="0433c-124">**SQLTablePrivileges**</span></span>  
  
-   <span data-ttu-id="0433c-125">**SQLTables**</span><span class="sxs-lookup"><span data-stu-id="0433c-125">**SQLTables**</span></span>  
  
 <span data-ttu-id="0433c-126">2部構成の_linked_server_name_**。**_カタログ_は、 [SQLForeignKeys](../../native-client-odbc-api/sqlforeignkeys.md)上の*FKCatalogName*および*PKCatalogName*でもサポートされています。</span><span class="sxs-lookup"><span data-stu-id="0433c-126">The two-part _linked_server_name_**.**_catalog_ is also supported for *FKCatalogName* and *PKCatalogName* on [SQLForeignKeys](../../native-client-odbc-api/sqlforeignkeys.md).</span></span>  
  
 <span data-ttu-id="0433c-127">SQLLinkedServers と SQLLinkedCatalogs を使用する場合は、次のファイルが必要です。</span><span class="sxs-lookup"><span data-stu-id="0433c-127">Using SQLLinkedServers and SQLLinkedCatalogs requires the following files:</span></span>  
  
-   <span data-ttu-id="0433c-128">sqlncli.h</span><span class="sxs-lookup"><span data-stu-id="0433c-128">sqlncli.h</span></span>  
  
     <span data-ttu-id="0433c-129">リンク サーバーのカタログ関数の関数プロトタイプと定数定義を含むファイルです。</span><span class="sxs-lookup"><span data-stu-id="0433c-129">Includes function prototypes and constant definitions for the linked server catalog functions.</span></span> <span data-ttu-id="0433c-130">sqlncli.h を ODBC アプリケーションにインクルードし、アプリケーションのコンパイル時にはこのファイルをインクルード パスに配置しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="0433c-130">sqlncli.h must be included in the ODBC application and must be in the include path when the application is compiled.</span></span>  
  
-   <span data-ttu-id="0433c-131">sqlncli11.lib</span><span class="sxs-lookup"><span data-stu-id="0433c-131">sqlncli11.lib</span></span>  
  
     <span data-ttu-id="0433c-132">リンカーのライブラリ パスに存在し、リンクされるファイルとして指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0433c-132">Must be in the library path of the linker and specified as a file to be linked.</span></span> <span data-ttu-id="0433c-133">sqlncli11.lib は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに付属しています。</span><span class="sxs-lookup"><span data-stu-id="0433c-133">sqlncli11.lib is distributed with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
-   <span data-ttu-id="0433c-134">sqlncli11.dll</span><span class="sxs-lookup"><span data-stu-id="0433c-134">sqlncli11.dll</span></span>  
  
     <span data-ttu-id="0433c-135">実行時に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0433c-135">Must be present at execution time.</span></span> <span data-ttu-id="0433c-136">sqlncli11.dll は、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーに付属しています。</span><span class="sxs-lookup"><span data-stu-id="0433c-136">sqlncli11.dll is distributed with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0433c-137">参照</span><span class="sxs-lookup"><span data-stu-id="0433c-137">See Also</span></span>  
 <span data-ttu-id="0433c-138">[SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="0433c-138">[SQL Server Native Client &#40;ODBC&#41;](sql-server-native-client-odbc.md) </span></span>  
 <span data-ttu-id="0433c-139">[SQLColumnPrivileges](../../native-client-odbc-api/sqlcolumnprivileges.md) </span><span class="sxs-lookup"><span data-stu-id="0433c-139">[SQLColumnPrivileges](../../native-client-odbc-api/sqlcolumnprivileges.md) </span></span>  
 <span data-ttu-id="0433c-140">[SQLColumns](../../native-client-odbc-api/sqlcolumns.md) </span><span class="sxs-lookup"><span data-stu-id="0433c-140">[SQLColumns](../../native-client-odbc-api/sqlcolumns.md) </span></span>  
 <span data-ttu-id="0433c-141">[SQLPrimaryKeys](../../native-client-odbc-api/sqlprimarykeys.md) </span><span class="sxs-lookup"><span data-stu-id="0433c-141">[SQLPrimaryKeys](../../native-client-odbc-api/sqlprimarykeys.md) </span></span>  
 <span data-ttu-id="0433c-142">[SQLTablePrivileges](../../native-client-odbc-api/sqltableprivileges.md) </span><span class="sxs-lookup"><span data-stu-id="0433c-142">[SQLTablePrivileges](../../native-client-odbc-api/sqltableprivileges.md) </span></span>  
 <span data-ttu-id="0433c-143">[SQLTables](../../native-client-odbc-api/sqltables.md) </span><span class="sxs-lookup"><span data-stu-id="0433c-143">[SQLTables](../../native-client-odbc-api/sqltables.md) </span></span>  
 [<span data-ttu-id="0433c-144">SQLStatistics</span><span class="sxs-lookup"><span data-stu-id="0433c-144">SQLStatistics</span></span>](../../statistics/statistics.md)  
  
  
