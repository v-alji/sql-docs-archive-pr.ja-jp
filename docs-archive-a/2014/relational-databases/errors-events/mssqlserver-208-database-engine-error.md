---
title: MSSQLSERVER_208 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 208 (Database Engine error)
ms.assetid: 4b1895f5-3197-4da1-af86-954c93507956
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 97ab3eb220c03c3de0c95251861f3b947890b090
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631988"
---
# <a name="mssqlserver_208"></a><span data-ttu-id="d49fd-102">MSSQLSERVER_208</span><span class="sxs-lookup"><span data-stu-id="d49fd-102">MSSQLSERVER_208</span></span>
    
## <a name="details"></a><span data-ttu-id="d49fd-103">詳細</span><span class="sxs-lookup"><span data-stu-id="d49fd-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d49fd-104">製品名</span><span class="sxs-lookup"><span data-stu-id="d49fd-104">Product Name</span></span>|<span data-ttu-id="d49fd-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d49fd-105">SQL Server</span></span>|  
|<span data-ttu-id="d49fd-106">イベント ID</span><span class="sxs-lookup"><span data-stu-id="d49fd-106">Event ID</span></span>|<span data-ttu-id="d49fd-107">208</span><span class="sxs-lookup"><span data-stu-id="d49fd-107">208</span></span>|  
|<span data-ttu-id="d49fd-108">イベント ソース</span><span class="sxs-lookup"><span data-stu-id="d49fd-108">Event Source</span></span>|<span data-ttu-id="d49fd-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d49fd-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d49fd-110">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="d49fd-110">Component</span></span>|<span data-ttu-id="d49fd-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d49fd-111">SQLEngine</span></span>|  
|<span data-ttu-id="d49fd-112">シンボル名</span><span class="sxs-lookup"><span data-stu-id="d49fd-112">Symbolic Name</span></span>|<span data-ttu-id="d49fd-113">SQ_BADOBJECT</span><span class="sxs-lookup"><span data-stu-id="d49fd-113">SQ_BADOBJECT</span></span>|  
|<span data-ttu-id="d49fd-114">メッセージ テキスト</span><span class="sxs-lookup"><span data-stu-id="d49fd-114">Message Text</span></span>|<span data-ttu-id="d49fd-115">オブジェクト名 '%.\*ls' が無効です。</span><span class="sxs-lookup"><span data-stu-id="d49fd-115">Invalid object name '%.\*ls'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d49fd-116">説明</span><span class="sxs-lookup"><span data-stu-id="d49fd-116">Explanation</span></span>  
 <span data-ttu-id="d49fd-117">指定されたオブジェクトが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="d49fd-117">The specified object cannot be found.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="d49fd-118">考えられる原因</span><span class="sxs-lookup"><span data-stu-id="d49fd-118">Possible Causes</span></span>  
 <span data-ttu-id="d49fd-119">このエラーは次のいずれかの問題が原因で生じている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d49fd-119">This error can be caused by one of the following problems:</span></span>  
  
-   <span data-ttu-id="d49fd-120">オブジェクトが正しく指定されていない。</span><span class="sxs-lookup"><span data-stu-id="d49fd-120">The object is not specified correctly.</span></span>  
  
-   <span data-ttu-id="d49fd-121">現在のデータベースまたは指定されたデータベースにオブジェクトが存在しない。</span><span class="sxs-lookup"><span data-stu-id="d49fd-121">The object does not exist in the current database or in the specified database.</span></span>  
  
-   <span data-ttu-id="d49fd-122">オブジェクトは存在するが、ユーザーからアクセスできない。</span><span class="sxs-lookup"><span data-stu-id="d49fd-122">The object exists, but could not be exposed to the user.</span></span> <span data-ttu-id="d49fd-123">たとえば、オブジェクトに対する権限がユーザーにない場合や、EXECUTE ステートメント内で作成したオブジェクトに EXECUTE ステートメントのスコープ外からアクセスしている場合などが考えられます。</span><span class="sxs-lookup"><span data-stu-id="d49fd-123">For example, the user might not have permissions on the object or the object is created within an EXECUTE statement but accessed outside the scope of the EXECUTE statement.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d49fd-124">ユーザーの操作</span><span class="sxs-lookup"><span data-stu-id="d49fd-124">User Action</span></span>  
 <span data-ttu-id="d49fd-125">次の情報を確認し、必要に応じてステートメントを修正します。</span><span class="sxs-lookup"><span data-stu-id="d49fd-125">Verify the following information and correct the statement as appropriate.</span></span>  
  
-   <span data-ttu-id="d49fd-126">オブジェクト名のスペルが正しいかどうか。</span><span class="sxs-lookup"><span data-stu-id="d49fd-126">The object name is spelled correctly.</span></span>  
  
-   <span data-ttu-id="d49fd-127">現在のデータベース コンテキストが正しいかどうか。</span><span class="sxs-lookup"><span data-stu-id="d49fd-127">The current database context is correct.</span></span> <span data-ttu-id="d49fd-128">オブジェクトのデータベース名を指定していない場合は、現在のデータベースにオブジェクトが存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d49fd-128">If a database name for the object is not specified, the object must exist in the current database.</span></span> <span data-ttu-id="d49fd-129">データベース コンテキストの設定の詳細については、「[USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d49fd-129">For more information about setting the database context, see [USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql).</span></span>  
  
-   <span data-ttu-id="d49fd-130">オブジェクトがシステム テーブルに存在するかどうか。</span><span class="sxs-lookup"><span data-stu-id="d49fd-130">The object exists in the system tables.</span></span> <span data-ttu-id="d49fd-131">テーブルやその他のスキーマ スコープ オブジェクトが存在するかどうかを確認するには、**sys.objects** カタログ ビューでクエリします。</span><span class="sxs-lookup"><span data-stu-id="d49fd-131">To verify whether a table or other schema-scoped object exists, query the **sys.objects** catalog view.</span></span> <span data-ttu-id="d49fd-132">オブジェクトがシステム テーブルにない場合、そのオブジェクトは削除されたか、ユーザーにオブジェクト メタデータを表示する権限がないかのいずれかです。</span><span class="sxs-lookup"><span data-stu-id="d49fd-132">If the object is not in the system tables, the object has been deleted, or the user does not have permissions to view the object metadata.</span></span> <span data-ttu-id="d49fd-133">オブジェクト メタデータの表示権限の詳細については、「[メタデータ表示の構成](../security/metadata-visibility-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d49fd-133">For more information about permissions to view object metadata, see [Metadata Visibility Configuration](../security/metadata-visibility-configuration.md).</span></span>  
  
-   <span data-ttu-id="d49fd-134">オブジェクトがユーザーの既定のスキーマに含まれているかどうか。</span><span class="sxs-lookup"><span data-stu-id="d49fd-134">The object is contained in the default schema of the user.</span></span> <span data-ttu-id="d49fd-135">オブジェクトがユーザーの既定のスキーマに含まれていない場合は、*schema_name.object_name* という 2 部構成の形式を使用してオブジェクトを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d49fd-135">If it is not, the object must be specified using the two-part format *schema_name.object_name*.</span></span> <span data-ttu-id="d49fd-136">スカラー値関数は、必ず 2 つ以上の要素で構成される名前を使用して呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d49fd-136">Note that scalar-valued functions must always be invoked by using at least a two-part name.</span></span>  
  
-   <span data-ttu-id="d49fd-137">データベースの照合順序で大文字と小文字が区別されるかどうか。</span><span class="sxs-lookup"><span data-stu-id="d49fd-137">The case sensitivity of the database collation.</span></span>  
  
     <span data-ttu-id="d49fd-138">大文字と小文字が区別される照合順序がデータベースで使用されている場合、オブジェクト名は、大文字と小文字の区別を含め、データベース内のオブジェクトと一致する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d49fd-138">When a database uses a case-sensitive collation, the object name must match the case of the object in the database.</span></span> <span data-ttu-id="d49fd-139">たとえば、大文字と小文字が区別される照合順序を使用しているデータベースでオブジェクトが **MyTable** と指定されている場合、クエリで **mytable** または **Mytable** と指定してそのオブジェクトを参照すると、エラー 208 が返されます。これはオブジェクト名が一致しないためです。</span><span class="sxs-lookup"><span data-stu-id="d49fd-139">For example, when an object is specified as **MyTable** in a database with a case sensitive collation, queries that refer to the object as **mytable** or **Mytable** will cause error 208 to return because the object names do not match.</span></span>  
  
     <span data-ttu-id="d49fd-140">データベースの照合順序を確認するには、次のステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="d49fd-140">You can verify the database collation by running the following statement.</span></span>  
  
    ```  
    SELECT collation_name FROM sys.databases WHERE name = 'database_name';  
    ```  
  
     <span data-ttu-id="d49fd-141">照合順序名に含まれる省略形 CS は、照合順序で大文字と小文字が区別されることを示します。</span><span class="sxs-lookup"><span data-stu-id="d49fd-141">The abbreviation CS in the collation name indicates the collation is case sensitive.</span></span> <span data-ttu-id="d49fd-142">たとえば、Latin1_General_CS_AS は、大文字と小文字およびアクセントが区別される照合順序です。</span><span class="sxs-lookup"><span data-stu-id="d49fd-142">For example, Latin1_General_CS_AS is a case sensitive, accent sensitive collation.</span></span> <span data-ttu-id="d49fd-143">CI は、大文字と小文字が区別されない照合順序であることを示します。</span><span class="sxs-lookup"><span data-stu-id="d49fd-143">CI indicates a case insensitive collation.</span></span>  
  
-   <span data-ttu-id="d49fd-144">ユーザーがオブジェクトへのアクセス権限を持っているかどうか。</span><span class="sxs-lookup"><span data-stu-id="d49fd-144">The user has permission to access the object.</span></span> <span data-ttu-id="d49fd-145">オブジェクトに対するユーザーの権限を確認するには、**Has_Perms_By_Name** システム関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="d49fd-145">To verify the permissions the user has on the object, use the **Has_Perms_By_Name** system function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d49fd-146">参照</span><span class="sxs-lookup"><span data-stu-id="d49fd-146">See Also</span></span>  
 <span data-ttu-id="d49fd-147">[&#40;Transact-sql&#41;を使用する](/sql/t-sql/language-elements/use-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d49fd-147">[USE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/use-transact-sql) </span></span>  
 <span data-ttu-id="d49fd-148">[メタデータ表示の構成](../security/metadata-visibility-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="d49fd-148">[Metadata Visibility Configuration](../security/metadata-visibility-configuration.md) </span></span>  
 [<span data-ttu-id="d49fd-149">HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d49fd-149">HAS_PERMS_BY_NAME &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/has-perms-by-name-transact-sql)  
  
  
