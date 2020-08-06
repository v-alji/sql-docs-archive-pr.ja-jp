---
title: FILESTREAM のサポート | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], SQL Server Native Client
- SQL Server Native Client [FILESTREAM support]
ms.assetid: 1ad3400d-7fcd-40c9-87ae-f5afc61e0374
author: rothja
ms.author: jroth
ms.openlocfilehash: 18e9a002bfb205e2c0807234550998fe48120d20
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87714281"
---
# <a name="filestream-support"></a><span data-ttu-id="aa381-102">FILESTREAM のサポート</span><span class="sxs-lookup"><span data-stu-id="aa381-102">FILESTREAM Support</span></span>
  <span data-ttu-id="aa381-103">FILESTREAM を使用すると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] を経由するか、Windows ファイル システムに直接アクセスすることで、大きなバイナリ値の格納やアクセスが可能になります。</span><span class="sxs-lookup"><span data-stu-id="aa381-103">FILESTREAM provides a way to store and access large binary values, either through [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] or by direct access to the Windows file system.</span></span> <span data-ttu-id="aa381-104">大きなバイナリ値とは、2 ギガバイト (GB) よりも大きい値です。</span><span class="sxs-lookup"><span data-stu-id="aa381-104">A large binary value is a value larger than 2 gigabytes (GB).</span></span> <span data-ttu-id="aa381-105">強化された FILESTREAM のサポートの詳細については、「[FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa381-105">For more information about enhanced FILESTREAM support, see [FILESTREAM &#40;SQL Server&#41;](../../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="aa381-106">データベース接続を開くと、`@@TEXTSIZE` が既定で -1 (無制限) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="aa381-106">When a database connection is opened, `@@TEXTSIZE` will be set to -1 ("unlimited"), by default.</span></span>  
  
 <span data-ttu-id="aa381-107">Windows ファイル システムの API を使用して、FILESTREAM 列にアクセスし、更新することもできます。</span><span class="sxs-lookup"><span data-stu-id="aa381-107">It is also possible to access and update FILESTREAM columns using Windows file system APIs.</span></span>  
  
 <span data-ttu-id="aa381-108">詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa381-108">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="aa381-109">FILESTREAM サポート &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="aa381-109">FILESTREAM Support &#40;OLE DB&#41;</span></span>](../ole-db/filestream-support-ole-db.md)  
  
-   [<span data-ttu-id="aa381-110">FILESTREAM のサポート &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="aa381-110">FILESTREAM Support &#40;ODBC&#41;</span></span>](../odbc/filestream-support-odbc.md)  
  
-   [<span data-ttu-id="aa381-111">OpenSqlFilestream による FILESTREAM データへのアクセス</span><span class="sxs-lookup"><span data-stu-id="aa381-111">Access FILESTREAM Data with OpenSqlFilestream</span></span>](../../blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a><span data-ttu-id="aa381-112">FILESTREAM 列のクエリ</span><span class="sxs-lookup"><span data-stu-id="aa381-112">Querying for FILESTREAM Columns</span></span>  
 <span data-ttu-id="aa381-113">OLE DB のスキーマ行セットでは、列が FILESTREAM 列かどうかは報告されません。</span><span class="sxs-lookup"><span data-stu-id="aa381-113">Schema rowsets in OLE DB will not report whether a column is a FILESTREAM column.</span></span> <span data-ttu-id="aa381-114">また、OLE DB の ITableDefinition を使用して FILESTREAM 列を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="aa381-114">ITableDefinition in OLE DB cannot be used to create a FILESTREAM column.</span></span>  
  
 <span data-ttu-id="aa381-115">ODBC の SQLColumns などのカタログ関数では、列が FILESTREAM 列かどうかは報告されません。</span><span class="sxs-lookup"><span data-stu-id="aa381-115">Catalog functions such as SQLColumns in ODBC will not report whether a column is a FILESTREAM column.</span></span>  
  
 <span data-ttu-id="aa381-116">Filestream 列を作成したり、どの既存の列が FILESTREAM 列であるかを検出したりするには、[列 `is_filestream` カタログ] ビューの列を使用します。 [sys.columns](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="aa381-116">To create FILESTREAM columns or to detect which existing columns are FILESTREAM columns, you can use the `is_filestream` column of the [sys.columns](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="aa381-117">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="aa381-117">The following is an example:</span></span>  
  
```  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a><span data-ttu-id="aa381-118">下位互換性</span><span class="sxs-lookup"><span data-stu-id="aa381-118">Down-Level Compatibility</span></span>  
 <span data-ttu-id="aa381-119">クライアントが、に含まれていたバージョンの Native Client を使用してコンパイルされている場合 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)] 、 `varbinary(max)` 動作はと互換性があり [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="aa381-119">If your client was compiled using the version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client that was included with [!INCLUDE[ssVersion2005](../../../includes/sscurrent-md.md)], `varbinary(max)` behavior will be compatible with [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="aa381-120">返されるデータの最大サイズが 2 GB に制限されます。</span><span class="sxs-lookup"><span data-stu-id="aa381-120">That is, the maximum size of returned data will be limited to 2 GB.</span></span> <span data-ttu-id="aa381-121">戻り値が 2 GB より大きい場合は切り捨てが行われ、"文字列データの右側が切り捨てられました" という警告が返されます。</span><span class="sxs-lookup"><span data-stu-id="aa381-121">For result values larger that 2 GB, truncation will occur and a "string data right truncation" warning will be returned.</span></span>  
  
 <span data-ttu-id="aa381-122">データ型の互換性が 80 に設定されている場合は、クライアントの動作で下位クライアントとの互換性が維持されます。</span><span class="sxs-lookup"><span data-stu-id="aa381-122">When data-type compatibility is set to 80, client behavior will be consistent with down-level client behavior.</span></span>  
  
 <span data-ttu-id="aa381-123">SQLOLEDB または Native Client より前にリリースされたその他のプロバイダーを使用するクライアントで [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] `varbinary(max)` は、がイメージにマップされます。</span><span class="sxs-lookup"><span data-stu-id="aa381-123">For clients that use SQLOLEDB or other providers that were released before the [!INCLUDE[ssVersion2005](../../../includes/ssnoversion-md.md)] Native Client, `varbinary(max)` will be mapped to image.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa381-124">参照</span><span class="sxs-lookup"><span data-stu-id="aa381-124">See Also</span></span>  
 [<span data-ttu-id="aa381-125">SQL Server Native Client の機能</span><span class="sxs-lookup"><span data-stu-id="aa381-125">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
