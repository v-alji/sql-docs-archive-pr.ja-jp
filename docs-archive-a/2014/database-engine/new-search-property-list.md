---
title: 新しい検索プロパティリスト |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.newsearchpropertylist.f1
ms.assetid: ffca78e9-8608-4b15-bd38-b2d78da4247a
author: rothja
ms.author: jroth
ms.openlocfilehash: 48c9e475b380d5f0c7310e33717f261c38acbbd4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644616"
---
# <a name="new-search-property-list"></a><span data-ttu-id="c07e0-102">新しい検索プロパティ リスト</span><span class="sxs-lookup"><span data-stu-id="c07e0-102">New Search Property List</span></span>
  <span data-ttu-id="c07e0-103">このダイアログ ボックスを使用すると、検索プロパティ リストを作成できます。</span><span class="sxs-lookup"><span data-stu-id="c07e0-103">Use this dialog box to create a search property list.</span></span>  
  
## <a name="options"></a><span data-ttu-id="c07e0-104">Options</span><span class="sxs-lookup"><span data-stu-id="c07e0-104">Options</span></span>  
 <span data-ttu-id="c07e0-105">**[検索プロパティ リスト名]**</span><span class="sxs-lookup"><span data-stu-id="c07e0-105">**Search property list name**</span></span>  
 <span data-ttu-id="c07e0-106">検索プロパティ リストの名前を入力します。</span><span class="sxs-lookup"><span data-stu-id="c07e0-106">Enter the name of the search property list.</span></span>  
  
 <span data-ttu-id="c07e0-107">**所有者**</span><span class="sxs-lookup"><span data-stu-id="c07e0-107">**Owner**</span></span>  
 <span data-ttu-id="c07e0-108">検索プロパティ リストの所有者を指定します。</span><span class="sxs-lookup"><span data-stu-id="c07e0-108">Specify the owner of the search property list.</span></span> <span data-ttu-id="c07e0-109">自分自身 (現在のユーザー) に所有権を割り当てる場合は、このフィールドを空のままにします。</span><span class="sxs-lookup"><span data-stu-id="c07e0-109">If you want ownership to be assigned to yourself, that is, to the current user, leave this field empty.</span></span> <span data-ttu-id="c07e0-110">別のユーザーを指定するには、参照ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c07e0-110">To specify a different user, click the browse button.</span></span>  
  
### <a name="create-search-property-list-options"></a><span data-ttu-id="c07e0-111">検索プロパティ リストの作成オプション</span><span class="sxs-lookup"><span data-stu-id="c07e0-111">Create Search Property List Options</span></span>  
 <span data-ttu-id="c07e0-112">以下のいずれかのオプションをクリックします。</span><span class="sxs-lookup"><span data-stu-id="c07e0-112">Click one of the following options:</span></span>  
  
 <span data-ttu-id="c07e0-113">**[空の検索プロパティ リストを作成する]**</span><span class="sxs-lookup"><span data-stu-id="c07e0-113">**Create an empty search property list**</span></span>  
 <span data-ttu-id="c07e0-114">プロパティが指定されていない検索プロパティ リストを作成します。</span><span class="sxs-lookup"><span data-stu-id="c07e0-114">Creates a search property list without any properties.</span></span>  
  
 <span data-ttu-id="c07e0-115">**[既存の検索プロパティ リストから作成する]**</span><span class="sxs-lookup"><span data-stu-id="c07e0-115">**Create from an existing search property list**</span></span>  
 <span data-ttu-id="c07e0-116">既存の検索のプロパティ リストのプロパティを新しいプロパティ リストにコピーします。</span><span class="sxs-lookup"><span data-stu-id="c07e0-116">Copies the properties of an existing search property list into the new property list.</span></span> <span data-ttu-id="c07e0-117">検索プロパティ リストはデータベース オブジェクトであるため、コピーするプロパティ リストを含むデータベースを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c07e0-117">Search property lists are database objects, so you must specify the database that contains the property list that you want to copy.</span></span>  
  
 <span data-ttu-id="c07e0-118">**ソースデータベース**</span><span class="sxs-lookup"><span data-stu-id="c07e0-118">**Source database**</span></span>  
 <span data-ttu-id="c07e0-119">既存の検索プロパティ リストが属しているデータベースの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="c07e0-119">Specify the name of the database to which the existing search property list belongs.</span></span> <span data-ttu-id="c07e0-120">既定では、現在のデータベースが選択されています。</span><span class="sxs-lookup"><span data-stu-id="c07e0-120">The current database is selected by default.</span></span> <span data-ttu-id="c07e0-121">現在の接続がそのデータベース内のユーザー ID に関連付けられている場合、必要に応じて、リスト ボックスを使用して別のデータベースを選択することができます。</span><span class="sxs-lookup"><span data-stu-id="c07e0-121">Optionally, you can use the list box to select another database, if your current connection is associated with a user ID in that database.</span></span>  
  
 <span data-ttu-id="c07e0-122">**[基になる検索プロパティ リスト]**</span><span class="sxs-lookup"><span data-stu-id="c07e0-122">**Source search property list**</span></span>  
 <span data-ttu-id="c07e0-123">選択したデータベースに属している既存の検索プロパティ リストの名前を選択します。</span><span class="sxs-lookup"><span data-stu-id="c07e0-123">Select the name of an existing search property list from those belonging to the selected database.</span></span>  
  
## <a name="permissions"></a><span data-ttu-id="c07e0-124">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="c07e0-124">Permissions</span></span>  
 <span data-ttu-id="c07e0-125">「 [CREATE SEARCH PROPERTY LIST &#40;transact-sql&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c07e0-125">See [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql).</span></span>  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a><span data-ttu-id="c07e0-126">SQL Server Management Studio を使用した検索プロパティ リストの管理</span><span class="sxs-lookup"><span data-stu-id="c07e0-126">To Use SQL Server Management Studio to Manage Search Property Lists</span></span>  
 <span data-ttu-id="c07e0-127">検索プロパティ リストを作成、表示、変更、または削除する方法、およびプロパティ検索用にフルテキスト インデックスを構成する方法については、「 [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c07e0-127">For information about how to create, view, change, or delete a search property list, and about how to configure a full-text index for property searching, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07e0-128">参照</span><span class="sxs-lookup"><span data-stu-id="c07e0-128">See Also</span></span>  
 <span data-ttu-id="c07e0-129">[Transact-sql&#41;&#40;の検索プロパティリストの作成](/sql/t-sql/statements/create-search-property-list-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c07e0-129">[CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql) </span></span>  
 <span data-ttu-id="c07e0-130">[検索プロパティリストを使用したドキュメントプロパティの検索](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="c07e0-130">[Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="c07e0-131">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c07e0-131">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
