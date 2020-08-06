---
title: DDL トリガーの実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- DDL triggers, implementing
ms.assetid: f44e5340-1d18-40e9-828e-0ffcca091ae3
author: rothja
ms.author: jroth
ms.openlocfilehash: 110e69aca31df75d4b4d7a732de5c58556bd3e24
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87644884"
---
# <a name="implement-ddl-triggers"></a><span data-ttu-id="22e3b-102">DDL トリガーの実装</span><span class="sxs-lookup"><span data-stu-id="22e3b-102">Implement DDL Triggers</span></span>
  <span data-ttu-id="22e3b-103">ここでは、DDL トリガーの作成、DDL トリガーの変更、および DDL トリガーの無効化または削除に役立つ情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="22e3b-103">This topic provides information to help you create DDL triggers, modify DDL triggers, and disable or drop DDL triggers.</span></span>  
  
## <a name="creating-ddl-triggers"></a><span data-ttu-id="22e3b-104">DDL トリガーの作成</span><span class="sxs-lookup"><span data-stu-id="22e3b-104">Creating DDL Triggers</span></span>  
 <span data-ttu-id="22e3b-105">[!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER ステートメントを使用することにより、DDL トリガーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="22e3b-105">DDL triggers are created by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE TRIGGER statement for DDL triggers.</span></span>  
  
 <span data-ttu-id="22e3b-106">**DDL トリガーを作成するには**</span><span class="sxs-lookup"><span data-stu-id="22e3b-106">**To create a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="22e3b-107">CREATE TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="22e3b-107">CREATE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-trigger-transact-sql)  
  
> [!IMPORTANT]  
>  <span data-ttu-id="22e3b-108">今後のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、トリガーを使用して結果セットを返す機能が削除される予定です。</span><span class="sxs-lookup"><span data-stu-id="22e3b-108">The ability to return result sets from triggers will be removed in a future version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="22e3b-109">結果セットを返すトリガーは、それと連動するように設計されていないアプリケーションでは予期しない動作を起こすことがあります。</span><span class="sxs-lookup"><span data-stu-id="22e3b-109">Triggers that return result sets may cause unexpected behavior in applications that are not designed to work with them.</span></span> <span data-ttu-id="22e3b-110">新しい開発作業では、トリガーを使用して結果セットを返すことを避け、現在この方法を使用しているアプリケーションについては変更を検討してください。</span><span class="sxs-lookup"><span data-stu-id="22e3b-110">Avoid returning result sets from triggers in new development work, and plan to modify applications that currently do this.</span></span> <span data-ttu-id="22e3b-111">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]でトリガーを使用して結果セットを返さないようにするには、 [disallow results from triggers](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md) オプションを 1 に設定します。</span><span class="sxs-lookup"><span data-stu-id="22e3b-111">To prevent triggers from returning result sets in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], set the [disallow results from triggers Option](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md) to 1.</span></span> <span data-ttu-id="22e3b-112">今後のバージョンの [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]では、このオプションの既定の設定は 1 になります。</span><span class="sxs-lookup"><span data-stu-id="22e3b-112">The default setting of this option will be 1 in a future version of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="modifying-ddl-triggers"></a><span data-ttu-id="22e3b-113">DDL トリガーの変更</span><span class="sxs-lookup"><span data-stu-id="22e3b-113">Modifying DDL Triggers</span></span>  
 <span data-ttu-id="22e3b-114">DDL トリガーの定義を変更する必要がある場合は、トリガーを削除してから作成し直すか、または既存のトリガーの再定義を行います。</span><span class="sxs-lookup"><span data-stu-id="22e3b-114">If you have to modify the definition of a DDL trigger, you can either drop and re-create the trigger or redefine the existing trigger in a single step.</span></span>  
  
 <span data-ttu-id="22e3b-115">DDL トリガーで参照されるオブジェクトの名前を変更する際には、新しい名前が反映されるようにトリガーを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="22e3b-115">If you change the name of an object that is referenced by a DDL trigger, you must modify the trigger so that its text reflects the new name.</span></span> <span data-ttu-id="22e3b-116">したがって、オブジェクトの名前を変更する前に、まずオブジェクトの依存関係を表示して、オブジェクト名の変更により影響を受けるトリガーがあるかどうかを確認してください。</span><span class="sxs-lookup"><span data-stu-id="22e3b-116">Therefore, before renaming an object, display the dependencies of the object first to determine whether any triggers are affected by the proposed change.</span></span>  
  
 <span data-ttu-id="22e3b-117">トリガーは、定義が暗号化されるように変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="22e3b-117">A trigger can also be modified to encrypt its definition.</span></span>  
  
 <span data-ttu-id="22e3b-118">**トリガーを変更するには**</span><span class="sxs-lookup"><span data-stu-id="22e3b-118">**To modify a trigger**</span></span>  
  
-   [<span data-ttu-id="22e3b-119">ALTER TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="22e3b-119">ALTER TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-trigger-transact-sql)  
  
 <span data-ttu-id="22e3b-120">**トリガーの依存関係を表示するには**</span><span class="sxs-lookup"><span data-stu-id="22e3b-120">**To view the dependencies of a trigger**</span></span>  
  
-   [<span data-ttu-id="22e3b-121">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="22e3b-121">sys.sql_expression_dependencies &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql)  
  
-   [<span data-ttu-id="22e3b-122">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="22e3b-122">sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql)  
  
-   [<span data-ttu-id="22e3b-123">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="22e3b-123">sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql)  
  
## <a name="disabling-and-dropping-ddl-triggers"></a><span data-ttu-id="22e3b-124">DDL トリガーの無効化と削除</span><span class="sxs-lookup"><span data-stu-id="22e3b-124">Disabling and Dropping DDL Triggers</span></span>  
 <span data-ttu-id="22e3b-125">DDL トリガーが不要になった場合は、そのトリガーを無効にするかまたは削除できます。</span><span class="sxs-lookup"><span data-stu-id="22e3b-125">When a DDL trigger is no longer needed, you can disable it or delete it.</span></span>  
  
 <span data-ttu-id="22e3b-126">DDL トリガーを無効にしても削除はされません。</span><span class="sxs-lookup"><span data-stu-id="22e3b-126">Disabling a DDL trigger does not drop it.</span></span> <span data-ttu-id="22e3b-127">オブジェクトとして現在のデータベースに残りますが、</span><span class="sxs-lookup"><span data-stu-id="22e3b-127">The trigger still exists as an object in the current database.</span></span> <span data-ttu-id="22e3b-128">トリガーがプログラムされた [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを実行しても、トリガーは起動しません。</span><span class="sxs-lookup"><span data-stu-id="22e3b-128">However, the trigger will not fire when any [!INCLUDE[tsql](../../includes/tsql-md.md)] statements on which it was programmed are run.</span></span> <span data-ttu-id="22e3b-129">無効になった DDL トリガーは、再度有効にできます。</span><span class="sxs-lookup"><span data-stu-id="22e3b-129">DDL triggers that are disabled can be reenabled.</span></span> <span data-ttu-id="22e3b-130">トリガーを有効にすると、最初に作成したときと同じ方法でトリガーが起動されます。</span><span class="sxs-lookup"><span data-stu-id="22e3b-130">Enabling a DDL trigger causes it to fire in the same way the trigger did when it was originally created.</span></span> <span data-ttu-id="22e3b-131">DDL トリガーが作成されると、既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="22e3b-131">When DDL triggers are created, they are enabled by default.</span></span>  
  
 <span data-ttu-id="22e3b-132">DDL トリガーを削除すると、現在のデータベースから削除されます。</span><span class="sxs-lookup"><span data-stu-id="22e3b-132">When a DDL trigger is deleted, it is dropped from the current database.</span></span> <span data-ttu-id="22e3b-133">DDL トリガーのスコープが設定されているオブジェクトやデータには影響しません。</span><span class="sxs-lookup"><span data-stu-id="22e3b-133">Any objects or data upon which the DDL trigger is scoped are not affected.</span></span>  
  
 <span data-ttu-id="22e3b-134">**DDL トリガーを無効にするには**</span><span class="sxs-lookup"><span data-stu-id="22e3b-134">**To disable a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="22e3b-135">DISABLE TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="22e3b-135">DISABLE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/disable-trigger-transact-sql)  
  
-   [<span data-ttu-id="22e3b-136">ALTER TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="22e3b-136">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
 <span data-ttu-id="22e3b-137">**DDL トリガーを有効にするには**</span><span class="sxs-lookup"><span data-stu-id="22e3b-137">**To enable a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="22e3b-138">ENABLE TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="22e3b-138">ENABLE TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/enable-trigger-transact-sql)  
  
-   [<span data-ttu-id="22e3b-139">ALTER TABLE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="22e3b-139">ALTER TABLE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-table-transact-sql)  
  
 <span data-ttu-id="22e3b-140">**DDL トリガーを削除するには**</span><span class="sxs-lookup"><span data-stu-id="22e3b-140">**To delete a DDL trigger**</span></span>  
  
-   [<span data-ttu-id="22e3b-141">DROP TRIGGER &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="22e3b-141">DROP TRIGGER &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-trigger-transact-sql)  
  
  
