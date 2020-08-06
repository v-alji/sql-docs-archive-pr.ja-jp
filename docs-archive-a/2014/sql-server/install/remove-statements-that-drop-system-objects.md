---
title: システムオブジェクトを削除するステートメントを削除する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- drop system objects [SQL Server]
ms.assetid: cdfc3c50-c801-4039-a4bf-b35f876f1c61
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d9e8fbfd4a436e87cee413d95468ccf5dd36b9dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631498"
---
# <a name="remove-statements-that-drop-system-objects"></a><span data-ttu-id="8a92c-102">システム オブジェクトを破棄するステートメントを削除する</span><span class="sxs-lookup"><span data-stu-id="8a92c-102">Remove statements that drop system objects</span></span>
  <span data-ttu-id="8a92c-103">アップグレード アドバイザーによって、システム オブジェクトを削除するステートメントが検出されました。</span><span class="sxs-lookup"><span data-stu-id="8a92c-103">Upgrade Advisor detected statements that drop system objects.</span></span> <span data-ttu-id="8a92c-104">拡張ストアドプロシージャを含むシステムオブジェクトは、読み取り専用の**リソース**データベース (mssqlsystemresource.mdf) に配置され、削除することはできません。</span><span class="sxs-lookup"><span data-stu-id="8a92c-104">System objects, including extended stored procedures, are deployed in the read-only **resource** database (mssqlsystemresource) and cannot be dropped.</span></span> <span data-ttu-id="8a92c-105">システム オブジェクトに対する EXECUTE 権限を禁止または拒否するように、アプリケーションを変更します。</span><span class="sxs-lookup"><span data-stu-id="8a92c-105">Modify your applications to either revoke or deny EXECUTE permission on system objects.</span></span>  
  
## <a name="component"></a><span data-ttu-id="8a92c-106">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="8a92c-106">Component</span></span>  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a><span data-ttu-id="8a92c-107">説明</span><span class="sxs-lookup"><span data-stu-id="8a92c-107">Description</span></span>  
 <span data-ttu-id="8a92c-108">DROP TABLE、DROP PROCEDURE、 **sp_dropextendedproc**などのステートメントを使用してシステムオブジェクトを削除することはできません。これらのオブジェクトは読み取り専用の**リソース**データベースに配置されているためです。</span><span class="sxs-lookup"><span data-stu-id="8a92c-108">Statements such as DROP TABLE, DROP PROCEDURE, and **sp_dropextendedproc** cannot be used to remove system objects, because these objects are deployed in the read-only **resource** database.</span></span>  
  
## <a name="corrective-action"></a><span data-ttu-id="8a92c-109">修正措置</span><span class="sxs-lookup"><span data-stu-id="8a92c-109">Corrective Action</span></span>  
 <span data-ttu-id="8a92c-110">アプリケーションからシステム オブジェクトの削除を試行するすべてのステートメントを削除します。</span><span class="sxs-lookup"><span data-stu-id="8a92c-110">Remove all statements that try to drop system objects from your applications.</span></span> <span data-ttu-id="8a92c-111">システム オブジェクトに対する EXECUTE 権限を禁止または拒否するように、アプリケーションを変更します。</span><span class="sxs-lookup"><span data-stu-id="8a92c-111">Modify your applications to either revoke or deny EXECUTE permission on system objects.</span></span> <span data-ttu-id="8a92c-112">または、セキュリティ構成 (SAC) ツールを使用して、システム オブジェクトの一部を無効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="8a92c-112">Alternatively, you can use the Surface Area Configuration (SAC) tool to disable some of these objects.</span></span> <span data-ttu-id="8a92c-113">たとえば、 **xp_cmdshell**の拡張ストアドプロシージャは、SAC ツールを使用して無効または有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="8a92c-113">For example, the **xp_cmdshell** extended stored procedure can be disabled or enabled using the SAC tool.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a92c-114">参照</span><span class="sxs-lookup"><span data-stu-id="8a92c-114">See Also</span></span>  
 <span data-ttu-id="8a92c-115">[データベースエンジンのアップグレードに関する問題](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span><span class="sxs-lookup"><span data-stu-id="8a92c-115">[Database Engine Upgrade Issues](../../../2014/sql-server/install/database-engine-upgrade-issues.md) </span></span>  
 [<span data-ttu-id="8a92c-116">SQL Server 2014 Upgrade Advisor &#91;新しい&#93;</span><span class="sxs-lookup"><span data-stu-id="8a92c-116">SQL Server 2014 Upgrade Advisor &#91;new&#93;</span></span>](sql-server-2014-upgrade-advisor.md)  
  
  
