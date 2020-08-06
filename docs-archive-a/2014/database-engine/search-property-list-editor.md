---
title: 検索プロパティリストエディター |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.searchpropertylisteditor.f1
ms.assetid: 0f3ced6e-0dfd-49fc-b175-82378c3d668e
author: rothja
ms.author: jroth
ms.openlocfilehash: 6c68ec986e2c6f4f53dfec7f188ba2a120532ae4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87639632"
---
# <a name="search-property-list-editor"></a><span data-ttu-id="a84fa-102">検索プロパティ リスト エディター</span><span class="sxs-lookup"><span data-stu-id="a84fa-102">Search Property List Editor</span></span>
  <span data-ttu-id="a84fa-103">このダイアログ ボックスを使用すると、検索プロパティ リストの検索プロパティを追加または削除できます。</span><span class="sxs-lookup"><span data-stu-id="a84fa-103">Use this dialog box to add or delete search properties in a search property list.</span></span>  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a><span data-ttu-id="a84fa-104">SQL Server Management Studio を使用した検索プロパティ リストの管理</span><span class="sxs-lookup"><span data-stu-id="a84fa-104">To Use SQL Server Management Studio to Manage Search Property Lists</span></span>  
 <span data-ttu-id="a84fa-105">検索プロパティリストを作成、表示、または削除する方法、およびプロパティ検索用にフルテキストインデックスを構成する方法については、「検索[プロパティリストを使用したドキュメントプロパティの検索](../relational-databases/search/search-document-properties-with-search-property-lists.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a84fa-105">For information about how to create, view, or delete a search property list, and about how to configure a full-text index for property searching, see [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="a84fa-106">Options</span><span class="sxs-lookup"><span data-stu-id="a84fa-106">Options</span></span>  
 <span data-ttu-id="a84fa-107">**プロパティ名**</span><span class="sxs-lookup"><span data-stu-id="a84fa-107">**Property Name**</span></span>  
 <span data-ttu-id="a84fa-108">フルテキスト クエリのプロパティを識別するために使用される名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a84fa-108">Specify the name to be used to identify the property in full-text queries.</span></span> <span data-ttu-id="a84fa-109">プロパティ名の内部にはスペースを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="a84fa-109">A property name can contain internal spaces.</span></span> <span data-ttu-id="a84fa-110">**プロパティ名** の長さは最大 256 文字です。</span><span class="sxs-lookup"><span data-stu-id="a84fa-110">The maximum length of **Property Name** is 256 characters.</span></span> <span data-ttu-id="a84fa-111">この名前は "作成者" や "ホーム アドレス" などのわかりやすい名前、または、Windows の正規のプロパティ名 (`System.Author` または `System.Contact.HomeAddress` など) にすることができます。</span><span class="sxs-lookup"><span data-stu-id="a84fa-111">This name can be a user-friendly name, such as "Author" or "Home Address", or it can be the Windows canonical name of the property, such as `System.Author` or `System.Contact.HomeAddress`.</span></span> <span data-ttu-id="a84fa-112">**プロパティ名** は、プロパティ セット内でプロパティを一意に識別する名前である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a84fa-112">**Property Name** must uniquely identify the property within the property set.</span></span>  
  
 <span data-ttu-id="a84fa-113">開発者は、このプロパティ名を使って [CONTAINS](/sql/t-sql/queries/contains-transact-sql) 述語のプロパティを識別します。</span><span class="sxs-lookup"><span data-stu-id="a84fa-113">Developers use the property name to identify the property in the [CONTAINS](/sql/t-sql/queries/contains-transact-sql) predicate.</span></span> <span data-ttu-id="a84fa-114">したがって、プロパティを追加する場合は、そのプロパティの意味を明確に表す名前を指定することが重要です。</span><span class="sxs-lookup"><span data-stu-id="a84fa-114">Therefore, when adding a property it is important to specify a value that meaningfully represents the property.</span></span>  
  
 <span data-ttu-id="a84fa-115">**[プロパティ セット GUID]**</span><span class="sxs-lookup"><span data-stu-id="a84fa-115">**Property Set GUID**</span></span>  
 <span data-ttu-id="a84fa-116">プロパティが属するプロパティ セットの識別子を指定します。</span><span class="sxs-lookup"><span data-stu-id="a84fa-116">Specify the identifier of the property set to which the property belongs.</span></span> <span data-ttu-id="a84fa-117">これはグローバル一意識別子 (GUID) です。</span><span class="sxs-lookup"><span data-stu-id="a84fa-117">This is a globally unique identifier (GUID).</span></span> <span data-ttu-id="a84fa-118">プロパティ セットは論理的に関連するプロパティのグループです。</span><span class="sxs-lookup"><span data-stu-id="a84fa-118">A property set is a group of logically related properties.</span></span> <span data-ttu-id="a84fa-119">この値の取得に関する情報については、このトピックの「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a84fa-119">For information about obtaining this value, see "Remarks," later in this topic.</span></span>  
  
 <span data-ttu-id="a84fa-120">**[プロパティの整数の ID]**</span><span class="sxs-lookup"><span data-stu-id="a84fa-120">**Property Int ID**</span></span>  
 <span data-ttu-id="a84fa-121">プロパティのプロパティ整数識別子を指定します。</span><span class="sxs-lookup"><span data-stu-id="a84fa-121">Specify the property integer identifier of the property.</span></span> <span data-ttu-id="a84fa-122">このあらかじめ割り当てられた値は、プロパティ セット内で一意の正の整数です。</span><span class="sxs-lookup"><span data-stu-id="a84fa-122">This pre-assigned value is a positive integer that is unique within the property set.</span></span> <span data-ttu-id="a84fa-123">この値の取得に関する情報については、このトピックの「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a84fa-123">For information about obtaining this value, see "Remarks," later in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a84fa-124">文字列識別子を使用するドキュメント プロパティはフルテキスト検索でサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a84fa-124">Document properties that use string identifiers are not supported by full-text search.</span></span>  
  
 <span data-ttu-id="a84fa-125">**プロパティの説明**</span><span class="sxs-lookup"><span data-stu-id="a84fa-125">**Property Description**</span></span>  
 <span data-ttu-id="a84fa-126">必要に応じてプロパティの説明を指定します。</span><span class="sxs-lookup"><span data-stu-id="a84fa-126">Optionally, specify a description of the property.</span></span> <span data-ttu-id="a84fa-127">これは最大 512 文字までの文字列です。</span><span class="sxs-lookup"><span data-stu-id="a84fa-127">This is a string of up to 512 characters.</span></span> <span data-ttu-id="a84fa-128">説明には、たとえばプロパティのプロパティ セットに関する情報、または名前からはその内容がわかりにくいプロパティに関する情報などが含まれる場合があります。</span><span class="sxs-lookup"><span data-stu-id="a84fa-128">For example, a description could contain information about the property set of the property or information about a property that is not evident from its name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a84fa-129">解説</span><span class="sxs-lookup"><span data-stu-id="a84fa-129">Remarks</span></span>  
 <span data-ttu-id="a84fa-130">検索プロパティ リストに検索プロパティを追加するには、プロパティが属するプロパティ セットのグローバル一意識別子 (GUID) とプロパティのプロパティ整数識別子を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a84fa-130">To add a search property to a search property list, you must specify the globally unique identifier (GUID) of the property set to which the property belongs and the property integer identifier of the property.</span></span> <span data-ttu-id="a84fa-131">これらの識別子の組み合わせが、検索プロパティ リスト内で一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a84fa-131">A given combination of these must be unique in a given search property list.</span></span> <span data-ttu-id="a84fa-132">既存の組み合わせを追加しようとすると、操作が失敗しエラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="a84fa-132">If you try to add an existing combination, the operation fails and issues an error.</span></span> <span data-ttu-id="a84fa-133">つまり、1 つの名前は 1 つのプロパティに対してのみ構成できます。</span><span class="sxs-lookup"><span data-stu-id="a84fa-133">This means that you can configure only one name for a given property.</span></span>  
  
 <span data-ttu-id="a84fa-134">このプロパティの説明は省略できます。</span><span class="sxs-lookup"><span data-stu-id="a84fa-134">The property description is optional.</span></span>  
  
 <span data-ttu-id="a84fa-135">**フルテキスト インデックスのための検索プロパティ リストを構成するには**</span><span class="sxs-lookup"><span data-stu-id="a84fa-135">**To configure a search property list for a full-text index**</span></span>  
  
-   [<span data-ttu-id="a84fa-136">検索プロパティ リストを使用したドキュメント プロパティの検索</span><span class="sxs-lookup"><span data-stu-id="a84fa-136">Search Document Properties with Search Property Lists</span></span>](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
## <a name="permissions"></a><span data-ttu-id="a84fa-137">アクセス許可</span><span class="sxs-lookup"><span data-stu-id="a84fa-137">Permissions</span></span>  
 <span data-ttu-id="a84fa-138">「 [ALTER SEARCH PROPERTY LIST &#40;transact-sql&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a84fa-138">See [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a84fa-139">参照</span><span class="sxs-lookup"><span data-stu-id="a84fa-139">See Also</span></span>  
 <span data-ttu-id="a84fa-140">[ALTER SEARCH PROPERTY LIST &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a84fa-140">[ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql) </span></span>  
 <span data-ttu-id="a84fa-141">[検索プロパティリストを使用したドキュメントプロパティの検索](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span><span class="sxs-lookup"><span data-stu-id="a84fa-141">[Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md) </span></span>  
 [<span data-ttu-id="a84fa-142">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a84fa-142">sys.registered_search_property_lists &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  
