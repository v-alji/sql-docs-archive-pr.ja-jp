---
title: MSSQLSERVER_2501 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2501 (Database Engine error)
ms.assetid: 895aafe3-a4e7-4ed8-acc5-93be76ef3664
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 200997dcfe7bf8a5933b9fce492daabd5baffd04
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87718183"
---
# <a name="mssqlserver_2501"></a><span data-ttu-id="8d96c-102">MSSQLSERVER_2501</span><span class="sxs-lookup"><span data-stu-id="8d96c-102">MSSQLSERVER_2501</span></span>
    
## <a name="details"></a><span data-ttu-id="8d96c-103">詳細</span><span class="sxs-lookup"><span data-stu-id="8d96c-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8d96c-104">製品名</span><span class="sxs-lookup"><span data-stu-id="8d96c-104">Product Name</span></span>|<span data-ttu-id="8d96c-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8d96c-105">SQL Server</span></span>|  
|<span data-ttu-id="8d96c-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="8d96c-106">Event ID</span></span>|<span data-ttu-id="8d96c-107">2501</span><span class="sxs-lookup"><span data-stu-id="8d96c-107">2501</span></span>|  
|<span data-ttu-id="8d96c-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="8d96c-108">Event Source</span></span>|<span data-ttu-id="8d96c-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8d96c-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8d96c-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8d96c-110">Component</span></span>|<span data-ttu-id="8d96c-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8d96c-111">SQLEngine</span></span>|  
|<span data-ttu-id="8d96c-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="8d96c-112">Symbolic Name</span></span>|<span data-ttu-id="8d96c-113">DBCC_NO_SUCH_TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8d96c-113">DBCC_NO_SUCH_TABLE_NAME</span></span>|  
|<span data-ttu-id="8d96c-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="8d96c-114">Message Text</span></span>|<span data-ttu-id="8d96c-115">'NAME' という名前のテーブルまたはオブジェクトが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="8d96c-115">Cannot find a table or object with the name 'NAME'.</span></span> <span data-ttu-id="8d96c-116">システム カタログを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8d96c-116">Check the system catalog.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8d96c-117">説明</span><span class="sxs-lookup"><span data-stu-id="8d96c-117">Explanation</span></span>  
 <span data-ttu-id="8d96c-118">指定されたオブジェクトが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="8d96c-118">The specified object cannot be found.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="8d96c-119">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="8d96c-119">Possible Causes</span></span>  
 <span data-ttu-id="8d96c-120">このエラーは次のいずれかの問題が原因で生じている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="8d96c-120">This error can be caused by one of the following problems:</span></span>  
  
-   <span data-ttu-id="8d96c-121">オブジェクトが正しく指定されていない。</span><span class="sxs-lookup"><span data-stu-id="8d96c-121">The object is not specified correctly.</span></span>  
  
-   <span data-ttu-id="8d96c-122">オブジェクトが存在しないか、ステートメントが使用しようとする前に削除された。</span><span class="sxs-lookup"><span data-stu-id="8d96c-122">The object does not exist, or the object was dropped before a statement tried to use it.</span></span>  
  
-   <span data-ttu-id="8d96c-123">オブジェクトは存在するが、ユーザーからアクセスできない。</span><span class="sxs-lookup"><span data-stu-id="8d96c-123">The object might exist, but could not be exposed to the user.</span></span> <span data-ttu-id="8d96c-124">たとえば、オブジェクトに対する権限がユーザーにない場合や、オブジェクトがユーザーからは見えない内部テーブルである場合などが考えられます。</span><span class="sxs-lookup"><span data-stu-id="8d96c-124">For example, the user might not have permissions on the object, or the object is an internal table that could not be seen by a user.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8d96c-125">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="8d96c-125">User Action</span></span>  
  
-   <span data-ttu-id="8d96c-126">現在のデータベース コンテキストが正しいことを確認します。</span><span class="sxs-lookup"><span data-stu-id="8d96c-126">Verify the current database context is correct.</span></span> <span data-ttu-id="8d96c-127">詳細については、「[USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d96c-127">For more information, see [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).</span></span>  
  
-   <span data-ttu-id="8d96c-128">テーブルまたはオブジェクトの名前が正しく入力されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="8d96c-128">Verify that the table or object name is spelled correctly.</span></span>  
  
-   <span data-ttu-id="8d96c-129">オブジェクトが含まれているスキーマの名前を確認します。</span><span class="sxs-lookup"><span data-stu-id="8d96c-129">Verify the schema name that contains the object.</span></span> <span data-ttu-id="8d96c-130">オブジェクトが既定の (**dbo**) スキーマ以外のスキーマに属している場合は、*schema_name.object_name* という 2 部構成の形式を使用してテーブルやオブジェクトの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="8d96c-130">If the object belongs to a schema other than the default (**dbo**) schema, you must specify the table or object name by using the two-part format *schema_name.object_name*.</span></span>  
  
-   <span data-ttu-id="8d96c-131">オブジェクトがシステム テーブルに存在することを確認します。</span><span class="sxs-lookup"><span data-stu-id="8d96c-131">Verify that the object exists in the system tables.</span></span> <span data-ttu-id="8d96c-132">テーブルやその他のスキーマ スコープ オブジェクトが存在するかどうかを確認するには、[sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) カタログ ビューでクエリします。</span><span class="sxs-lookup"><span data-stu-id="8d96c-132">To verify whether a table or other schema-scoped object exists, query the [sys.objects](/sql/relational-databases/system-catalog-views/sys-objects-transact-sql) catalog view.</span></span> <span data-ttu-id="8d96c-133">オブジェクトがシステム テーブルにない場合、そのオブジェクトは削除されたか、ユーザーにオブジェクト メタデータを表示する権限がないかのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="8d96c-133">If the object is not in the system tables, the object has been deleted, or the user does not have permissions to view the object metadata.</span></span> <span data-ttu-id="8d96c-134">オブジェクト メタデータの表示方法の詳細については、「[メタデータ表示の構成](../security/metadata-visibility-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8d96c-134">For more information about how to view object metadata, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d96c-135">参照</span><span class="sxs-lookup"><span data-stu-id="8d96c-135">See Also</span></span>  
 [<span data-ttu-id="8d96c-136">カタログ ビュー &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8d96c-136">Catalog Views &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/catalog-views-transact-sql)  
  
  
