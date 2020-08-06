---
title: 検索用フィルターの構成と管理 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], filters
- filters [full-text search]
ms.assetid: 7ccf2ee0-9854-4253-8cca-1faed43b7095
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e9a57c95226a9b277cfb718b40b5d0525b1f8eb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643753"
---
# <a name="configure-and-manage-filters-for-search"></a><span data-ttu-id="3f6b3-102">検索用フィルターの構成と管理</span><span class="sxs-lookup"><span data-stu-id="3f6b3-102">Configure and Manage Filters for Search</span></span>
  <span data-ttu-id="3f6b3-103">`varbinary`、`varbinary(max)`、`image`、または `xml` データ型列のドキュメントにインデックスを作成するには、追加の処理が必要です。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-103">Indexing documents in an `varbinary`, `varbinary(max)`, `image`, or `xml` data type column requires extra processing.</span></span> <span data-ttu-id="3f6b3-104">この処理はフィルターによって実行します。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-104">This processing must be performed by a filter.</span></span> <span data-ttu-id="3f6b3-105">フィルターは、ドキュメントから (フォーマットを解除して) 文字情報を抽出します。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-105">The filter extracts the textual information from the document (removing the formatting).</span></span> <span data-ttu-id="3f6b3-106">次に、テーブル列に関連付けられている言語のワード ブレーカー コンポーネントにテキストを送ります。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-106">The filter then sends the text to the word-breaker component for the language associated with the table column.</span></span>  
  
 <span data-ttu-id="3f6b3-107">フィルターは、ドキュメント型 (.doc、.pdf、.xls、.xml など) に固有です。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-107">A given filter is specific to a given document type (.doc, .pdf, .xls, .xml, and so forth).</span></span> <span data-ttu-id="3f6b3-108">これらのフィルターは IFilter インターフェイスを実装しています。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-108">These filters implement the IFilter interface.</span></span> <span data-ttu-id="3f6b3-109">ドキュメント型の一覧を参照するには、 [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) カタログ ビューに対してクエリを実行してください。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-109">For more information about these document types, query the [sys.fulltext_document_types](/sql/relational-databases/system-catalog-views/sys-fulltext-document-types-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="3f6b3-110">バイナリ ドキュメントは、単一の `varbinary(max)` 列または `image` 列に格納できます。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-110">Binary documents can be stored in a single `varbinary(max)` or `image` column.</span></span> <span data-ttu-id="3f6b3-111">各ドキュメントについて、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] はファイル拡張子を基に正しいフィルターを選択します。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-111">For each document, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] chooses the correct filter based on the file extension.</span></span> <span data-ttu-id="3f6b3-112">ファイルが `varbinary(max)` 列または `image` 列に格納されている場合にはファイル拡張子が表示されないため、ファイル拡張子 (.doc、.xls、.pdf など) を型列と呼ばれるテーブル内の別の列に格納する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-112">Because the file extension is not visible when the file is stored in a `varbinary(max)` or `image` column, the file extension (.doc, .xls,  .pdf, and so forth) must be stored in a separate column in the table, called a type column.</span></span> <span data-ttu-id="3f6b3-113">この型列は、任意の文字ベースのデータ型で、文書ファイルの拡張子 (たとえば [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word 文書の場合は .doc) を格納します。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-113">This type column can be of any character-based data type and contains the document file extension, such as .doc for a [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Word document.</span></span> <span data-ttu-id="3f6b3-114">の**document**テーブルでは、 [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] **document**列は型で、 `varbinary(max)` 型列**fileextension**は型 `nvarchar(8)` です。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-114">In the **Document** table in [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)], the **Document** column is of type `varbinary(max)`, and the type column, **FileExtension**, is of type `nvarchar(8)`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3f6b3-115">フィルターは、実装によっては、親オブジェクトに埋め込まれたオブジェクトを処理できます。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-115">A filter might be able to handle objects embedded in the parent object, depending on its implementation.</span></span> <span data-ttu-id="3f6b3-116">ただし、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、フィルターが他のオブジェクトへのリンクをたどるように構成されていません。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-116">However, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] does not configure filters to follow links to other objects.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="3f6b3-117">では、独自の XML フィルターと HTML フィルターがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-117">installs its own XML and HTML filters.</span></span> <span data-ttu-id="3f6b3-118">さらに、オペレーティング システムに既にインストールされている [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 専用形式 (.doc、.xdoc、.ppt など) のフィルターもすべて  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]によって読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-118">In addition, any filters for [!INCLUDE[msCoName](../../../includes/msconame-md.md)] proprietary formats (.doc, .xdoc, .ppt and so on) that are already installed on the operating system are also loaded by  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="3f6b3-119">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]のインスタンスに現在読み込まれているフィルターを確認するには、次のように [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) ストアド プロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-119">To identify the filters that are currently loaded on an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], use the [sp_help_fulltext_system_components](/sql/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql) stored procedure, as follows:</span></span>  
  
```  
EXEC sp_help_fulltext_system_components 'filter';   
```  
  
 <span data-ttu-id="3f6b3-120">ただし、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 形式以外のフィルターを使用するには、事前にこれらのフィルターをサーバー インスタンスに読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-120">Before you can use filters for non [!INCLUDE[msCoName](../../../includes/msconame-md.md)] formats, however, you must manually load them into the server instance.</span></span> <span data-ttu-id="3f6b3-121">追加のフィルターのインストールの詳細については、「 [登録済みのフィルターおよびワード ブレーカーの表示または変更](view-or-change-registered-filters-and-word-breakers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f6b3-121">For information about installing additional filters, see [View or Change Registered Filters and Word Breakers](view-or-change-registered-filters-and-word-breakers.md).</span></span>  
  
 <span data-ttu-id="3f6b3-122">**既存のフルテキスト インデックスの型列を表示するには**</span><span class="sxs-lookup"><span data-stu-id="3f6b3-122">**To view the type column in an existing full-text index**</span></span>  
  
-   [<span data-ttu-id="3f6b3-123">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="3f6b3-123">sys.fulltext_index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="3f6b3-124">参照</span><span class="sxs-lookup"><span data-stu-id="3f6b3-124">See Also</span></span>  
 <span data-ttu-id="3f6b3-125">[fulltext_index_columns &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="3f6b3-125">[sys.fulltext_index_columns &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-index-columns-transact-sql) </span></span>  
 [<span data-ttu-id="3f6b3-126">FILESTREAM と SQL Server のその他の機能との互換性</span><span class="sxs-lookup"><span data-stu-id="3f6b3-126">FILESTREAM Compatibility with Other SQL Server Features</span></span>](../blob/filestream-compatibility-with-other-sql-server-features.md)  
  
  
