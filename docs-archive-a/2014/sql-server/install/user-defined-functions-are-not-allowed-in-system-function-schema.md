---
title: ユーザー定義関数は system_function_schema | では許可されていません。Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- system functions [SQL Server]
- user-defined functions [SQL Server], system
ms.assetid: 3cb54053-ef65-4558-ae96-8686b6b22f4f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 7242f9fda74288a2b7354ac0550ff4966e05c555
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742761"
---
# <a name="user-defined-functions-are-not-allowed-in-system_function_schema"></a><span data-ttu-id="c98a0-102">system_function_schema でユーザー定義関数が許可されない</span><span class="sxs-lookup"><span data-stu-id="c98a0-102">User-defined functions are not allowed in system_function_schema</span></span>
  <span data-ttu-id="c98a0-103">アップグレードアドバイザーによって、ドキュメントに記載されていないユーザー **system_function_schema**が所有しているユーザー定義関数が検出されました。</span><span class="sxs-lookup"><span data-stu-id="c98a0-103">The Upgrade Advisor detected user-defined functions that are owned by the undocumented user **system_function_schema**.</span></span> <span data-ttu-id="c98a0-104">このユーザーを指定してユーザー定義のシステム関数を作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="c98a0-104">You cannot create a user-defined system function by specifying this user.</span></span> <span data-ttu-id="c98a0-105">**System_function_schema**ユーザー名が存在しません。この名前に関連付けられているユーザー ID (UID = 4) は**sys**スキーマ用に予約されており、内部使用に限定されています。</span><span class="sxs-lookup"><span data-stu-id="c98a0-105">The **system_function_schema** user name does not exist, and the user ID that is associated with this name (UID = 4) is reserved for the **sys** schema and is restricted to internal use only.</span></span>  
  
## <a name="component"></a><span data-ttu-id="c98a0-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="c98a0-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="c98a0-107">説明</span><span class="sxs-lookup"><span data-stu-id="c98a0-107">Description</span></span>  
 <span data-ttu-id="c98a0-108">システム オブジェクトの格納とアクセスが次のように変更されました。</span><span class="sxs-lookup"><span data-stu-id="c98a0-108">System object storage and access has changed in the following ways:</span></span>  
  
-   <span data-ttu-id="c98a0-109">システムオブジェクトは読み取り専用の**リソース**データベースに格納され、システムオブジェクトを直接更新することはできません。</span><span class="sxs-lookup"><span data-stu-id="c98a0-109">System objects are stored in the read-only **Resource** database, and direct system object updates are not permitted.</span></span>  
  
     <span data-ttu-id="c98a0-110">システムオブジェクトは、各データベースの**sys**スキーマに論理的に表示されます。</span><span class="sxs-lookup"><span data-stu-id="c98a0-110">System objects logically appear in the **sys** schema of every database.</span></span> <span data-ttu-id="c98a0-111">これにより、1 つの要素で構成される関数名を指定してデータベースからシステム関数を呼び出す機能が維持されます。</span><span class="sxs-lookup"><span data-stu-id="c98a0-111">This maintains the ability to invoke system functions from any database by specifying a one-part function name.</span></span> <span data-ttu-id="c98a0-112">たとえば、ステートメント `SELECT * FROM fn_helpcollations()` はどのデータベースからでも実行できます。</span><span class="sxs-lookup"><span data-stu-id="c98a0-112">For example, the statement `SELECT * FROM fn_helpcollations()` can be run from any database.</span></span>  
  
-   <span data-ttu-id="c98a0-113">非公開のユーザー **system_function_schema**が削除されました。</span><span class="sxs-lookup"><span data-stu-id="c98a0-113">The undocumented user **system_function_schema** has been removed.</span></span>  
  
-   <span data-ttu-id="c98a0-114">**System_function_schema**に関連付けられたユーザー ID (UID = 4) は**sys**スキーマ用に予約されており、内部使用のみに制限されています。</span><span class="sxs-lookup"><span data-stu-id="c98a0-114">The user ID associated with **system_function_schema** (UID = 4) is reserved for the **sys** schema and is restricted to internal use only.</span></span>  
  
 <span data-ttu-id="c98a0-115">これらの変更によって、ユーザー定義のシステム関数には次の影響があります。</span><span class="sxs-lookup"><span data-stu-id="c98a0-115">These changes have the following effect on user-defined system functions:</span></span>  
  
-   <span data-ttu-id="c98a0-116">**System_function_schema**を参照するデータ定義言語 (DDL) ステートメントは失敗します。</span><span class="sxs-lookup"><span data-stu-id="c98a0-116">Data Definition Language (DDL) statements that reference **system_function_schema** will fail.</span></span> <span data-ttu-id="c98a0-117">たとえば、.. `CREATE FUNCTION system` `function` \_ `schema.fn` \_ `MySystemFunction` .成功しません。</span><span class="sxs-lookup"><span data-stu-id="c98a0-117">For example, the statement `CREATE FUNCTION system`_`function`\_`schema.fn`\_`MySystemFunction` ... will not succeed.</span></span>  
  
-   <span data-ttu-id="c98a0-118">にアップグレードした後 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 、 **system_function_schema**によって所有されている既存のオブジェクトは、 **master**データベースの**sys**スキーマにのみ格納されます。</span><span class="sxs-lookup"><span data-stu-id="c98a0-118">After you upgrade to [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], existing objects that are owned by **system_function_schema** are contained only in the **sys** schema of the **master** database.</span></span> <span data-ttu-id="c98a0-119">システムオブジェクトは変更できないので、 **master**データベースからこれらの関数を変更したり削除したりすることはできません。</span><span class="sxs-lookup"><span data-stu-id="c98a0-119">Because system objects cannot be modified, these functions can never be changed or dropped from the **master** database.</span></span> <span data-ttu-id="c98a0-120">また、これらの関数は、1 つの要素だけで構成される関数名を指定して他のデータベースから呼び出すこともできません。</span><span class="sxs-lookup"><span data-stu-id="c98a0-120">Additionally, these functions cannot be invoked from other databases by specifying only a one-part function name.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="c98a0-121">修正措置</span><span class="sxs-lookup"><span data-stu-id="c98a0-121">Corrective Action</span></span>  
 <span data-ttu-id="c98a0-122">アップグレードする前に、以下の作業を完了してください。</span><span class="sxs-lookup"><span data-stu-id="c98a0-122">Before you upgrade , complete the following tasks:</span></span>  
  
1.  <span data-ttu-id="c98a0-123">**Sp_changeobjectowner**システムストアドプロシージャを使用して、既存のユーザー定義関数の所有権を**dbo**に変更します。</span><span class="sxs-lookup"><span data-stu-id="c98a0-123">Change the ownership of existing user-defined functions to **dbo** by using the **sp_changeobjectowner** system stored procedure.</span></span>  
  
2.  <span data-ttu-id="c98a0-124">プレフィックス 'fn_' を使用しないように関数名を変更することを検討します。</span><span class="sxs-lookup"><span data-stu-id="c98a0-124">Consider renaming the function so that is does not use the prefix 'fn_'.</span></span> <span data-ttu-id="c98a0-125">これにより、現在または今後のシステム関数で名前の競合が発生するのを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="c98a0-125">This will avoid potential name conflicts with current or future system functions.</span></span>  
  
3.  <span data-ttu-id="c98a0-126">変更した関数のコピーを、その関数を使用するすべてのデータベースに追加します。</span><span class="sxs-lookup"><span data-stu-id="c98a0-126">Add a copy of the modified functions in every database that uses them.</span></span>  
  
4.  <span data-ttu-id="c98a0-127">ユーザー定義関数 DDL ステートメントが含まれているすべてのスクリプトで、 **system_function_schema**への参照を**dbo**に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="c98a0-127">Replace references to **system_function_schema** with **dbo** in all scripts that contain user-defined function DDL statements.</span></span>  
  
5.  <span data-ttu-id="c98a0-128">2部構成の名前 dbo を使用するようにこれらの関数を呼び出すスクリプトを変更し**ます。**_function_name_、または3つの部分で構成される名前_database_name_**です。** dbo.*function_name*。</span><span class="sxs-lookup"><span data-stu-id="c98a0-128">Modify scripts that invoke these functions to use either the two-part name dbo **.**_function_name_, or the three-part name _database_name_**.** dbo.*function_name*.</span></span>  
  
 <span data-ttu-id="c98a0-129">詳細については、SQL Server オンライン ブックの次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="c98a0-129">For more information, see the following topics in SQL Server Books Online:</span></span>  
  
-   <span data-ttu-id="c98a0-130">"sp_changeobjectowner"</span><span class="sxs-lookup"><span data-stu-id="c98a0-130">"sp_changeobjectowner"</span></span>  
  
-   <span data-ttu-id="c98a0-131">"ユーザーとスキーマの分離"</span><span class="sxs-lookup"><span data-stu-id="c98a0-131">"User-schema Separation"</span></span>  
  
-   <span data-ttu-id="c98a0-132">Resource データベース</span><span class="sxs-lookup"><span data-stu-id="c98a0-132">"Resource Database"</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c98a0-133">参照</span><span class="sxs-lookup"><span data-stu-id="c98a0-133">See Also</span></span>  
 <span data-ttu-id="c98a0-134">[SQL Server 2014 Upgrade Advisor &#91;新しい&#93;](sql-server-2014-upgrade-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="c98a0-134">[SQL Server 2014 Upgrade Advisor &#91;new&#93;](sql-server-2014-upgrade-advisor.md) </span></span>  
 <span data-ttu-id="c98a0-135">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="c98a0-135">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 <span data-ttu-id="c98a0-136">[システムオブジェクトを変更するステートメントを削除します。](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md) </span><span class="sxs-lookup"><span data-stu-id="c98a0-136">[Remove statements that modify system objects](../../../2014/sql-server/install/remove-statements-that-modify-system-objects.md) </span></span>  
 [<span data-ttu-id="c98a0-137">システム オブジェクトを破棄するステートメントを削除する</span><span class="sxs-lookup"><span data-stu-id="c98a0-137">Remove statements that drop system objects</span></span>](../../../2014/sql-server/install/remove-statements-that-drop-system-objects.md)  
  
  
