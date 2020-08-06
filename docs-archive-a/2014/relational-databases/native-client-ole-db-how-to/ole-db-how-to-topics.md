---
title: OLE DB の使用法に関するトピック | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, how-to topics
ms.assetid: fbfab1b0-433d-497e-ae07-9b21a5c6903c
author: rothja
ms.author: jroth
ms.openlocfilehash: 006962c1a28cc4a21f3e2efaa63b45b0871e208f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639937"
---
# <a name="ole-db-how-to-topics"></a><span data-ttu-id="349bd-102">OLE DB の使用法に関するトピック</span><span class="sxs-lookup"><span data-stu-id="349bd-102">OLE DB How-to Topics</span></span>
  <span data-ttu-id="349bd-103">Native Client OLE DB プロバイダーを使用するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] サーバーへの接続を作成し、コマンドを実行して結果を処理する方法を理解する必要があります。</span><span class="sxs-lookup"><span data-stu-id="349bd-103">To use the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider, you have to understand how to make a connection to the server, execute the command, and process the results.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="349bd-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="349bd-104">In This Section</span></span>  
  
-   [<span data-ttu-id="349bd-105">結果を処理する方法に関するトピック &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-105">Processing Results How-to Topics &#40;OLE DB&#41;</span></span>](results/processing-results-how-to-topics-ole-db.md)  
  
-   [<span data-ttu-id="349bd-106">大きなデータの設定 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-106">Set Large Data &#40;OLE DB&#41;</span></span>](set-large-data-ole-db.md)  
  
-   [<span data-ttu-id="349bd-107">OLE DB データ ソースの列挙 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-107">Enumerate OLE DB Data Sources &#40;OLE DB&#41;</span></span>](enumerate-ole-db-data-sources-ole-db.md)  
  
-   [<span data-ttu-id="349bd-108">IRowsetFastLoad を使用したデータの一括コピー &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-108">Bulk Copy Data Using IRowsetFastLoad &#40;OLE DB&#41;</span></span>](../native-client-ole-db-interfaces/irowsetfastload-ole-db.md)  
  
-   [<span data-ttu-id="349bd-109">FAST_FORWARD カーソルの取得</span><span class="sxs-lookup"><span data-stu-id="349bd-109">Obtain a FAST_FORWARD Cursor</span></span>](obtain-a-fast-forward-cursor.md)  
  
-   [<span data-ttu-id="349bd-110">ブックマークを使用した行の取得 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-110">Retrieve Rows Using Bookmarks &#40;OLE DB&#41;</span></span>](retrieve-rows-using-bookmarks-ole-db.md)  
  
-   [<span data-ttu-id="349bd-111">IRow::GetColumns &#40;または IRow::Open&#41; と ISequentialStream を使用した列のフェッチ</span><span class="sxs-lookup"><span data-stu-id="349bd-111">Fetch Columns Using IRow::GetColumns &#40;or IRow::Open&#41; and ISequentialStream</span></span>](fetch-columns-using-irow-getcolumns-or-irow-open-and-isequentialstream.md)  
  
-   [<span data-ttu-id="349bd-112">IRow::GetColumns を使用した列のフェッチ &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-112">Fetch Columns Using IRow::GetColumns &#40;OLE DB&#41;</span></span>](fetch-columns-using-irow-getcolumns-ole-db.md)  
  
-   [<span data-ttu-id="349bd-113">SQL Server 認証のユーザー パスワードの変更 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-113">Change a SQL Server Authentication User Password &#40;OLE DB&#41;</span></span>](change-a-sql-server-authentication-user-password-ole-db.md)  
  
-   [<span data-ttu-id="349bd-114">強化された日付/時刻機能の使用 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-114">Use Enhanced Date and Time Features &#40;OLE DB&#41;</span></span>](use-enhanced-date-and-time-features-ole-db.md)  
  
-   [<span data-ttu-id="349bd-115">FILESTREAM と OLE DB</span><span class="sxs-lookup"><span data-stu-id="349bd-115">Filestream and OLE DB</span></span>](filestream/filestream-and-ole-db.md)  
  
-   [<span data-ttu-id="349bd-116">IROWSETFASTLOAD と ISEQUENTIALSTREAM を使用した SQL SERVER への BLOB データの送信 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-116">Send BLOB Data to SQL SERVER Using IROWSETFASTLOAD and ISEQUENTIALSTREAM &#40;OLE DB&#41;</span></span>](send-blob-data-to-sql-server-using-irowsetfastload-and-isequentialstream-ole-db.md)  
  
-   [<span data-ttu-id="349bd-117">大きな CLR UDT の使用 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-117">Use Large CLR UDTs &#40;OLE DB&#41;</span></span>](use-large-clr-udts-ole-db.md)  
  
-   [<span data-ttu-id="349bd-118">スパース列に対する列およびカタログ メタデータの表示 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-118">Display Column and Catalog Metadata for Sparse Columns &#40;OLE DB&#41;</span></span>](display-column-and-catalog-metadata-for-sparse-columns-ole-db.md)  
  
-   [<span data-ttu-id="349bd-119">統合 Kerberos 認証 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-119">Integrated Kerberos Authentication &#40;OLE DB&#41;</span></span>](integrated-kerberos-authentication-ole-db.md)  
  
-   [<span data-ttu-id="349bd-120">テーブル値パラメーターの使用 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="349bd-120">Use Table-Valued Parameters &#40;OLE DB&#41;</span></span>](../native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)  
  
## <a name="see-also"></a><span data-ttu-id="349bd-121">参照</span><span class="sxs-lookup"><span data-stu-id="349bd-121">See Also</span></span>  
 [<span data-ttu-id="349bd-122">SQL Server Native Client プログラミング</span><span class="sxs-lookup"><span data-stu-id="349bd-122">SQL Server Native Client Programming</span></span>](../native-client/sql-server-native-client-programming.md)  
  
  
