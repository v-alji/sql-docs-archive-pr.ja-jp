---
title: SQL Server にインストールされている拡張ストアドプロシージャに対してクエリを実行する |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], querying
ms.assetid: e02348e6-dba6-438a-98b6-684244bb034d
author: rothja
ms.author: jroth
ms.openlocfilehash: 3f44db9053ad18c3a6902a30aaab4f81610c5a8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87633855"
---
# <a name="querying-extended-stored-procedures-installed-in-sql-server"></a><span data-ttu-id="0a8fd-102">SQL Server にインストールされた拡張ストアド プロシージャの照会</span><span class="sxs-lookup"><span data-stu-id="0a8fd-102">Querying Extended Stored Procedures Installed in SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)]<span data-ttu-id="0a8fd-103">代わりに CLR Integration をご使用ください。</span><span class="sxs-lookup"><span data-stu-id="0a8fd-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="0a8fd-104">認証されたユーザーは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **sp_helpextendedproc**システムプロシージャを実行することによって、現在定義されている拡張ストアドプロシージャと、それぞれが属している DLL の名前を表示できます。</span><span class="sxs-lookup"><span data-stu-id="0a8fd-104">A [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] authenticated user can display the currently defined extended stored procedures and the name of the DLL to which each belongs by running the **sp_helpextendedproc** system procedure.</span></span> <span data-ttu-id="0a8fd-105">たとえば、次の例では、 **xp_hello**が属している DLL が返されます。</span><span class="sxs-lookup"><span data-stu-id="0a8fd-105">For example, the following example returns the DLL to which **xp_hello** belongs:</span></span>  
  
```  
sp_helpextendedproc 'xp_hello'  
```  
  
 <span data-ttu-id="0a8fd-106">拡張ストアドプロシージャを指定せずに**sp_helpextendedproc**を実行すると、すべての拡張ストアドプロシージャとその dll が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0a8fd-106">If **sp_helpextendedproc** is executed without specifying an extended stored procedure, all the extended stored procedures and their DLLs are displayed.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0a8fd-107">ログインしたユーザーが所有しているか、権限を持っている拡張ストアド プロシージャの情報だけが返されます。</span><span class="sxs-lookup"><span data-stu-id="0a8fd-107">Information will be returned for only those extended stored procedures that the logged in user owns or has permissions to.</span></span> <span data-ttu-id="0a8fd-108">すべての拡張ストアドプロシージャの情報を表示できるのは、 **sysadmin**固定サーバーロールのメンバーと、 **db_owner**、 **db_securityadmin**、および**db_ddladmin**の固定データベースロールのメンバーだけです。</span><span class="sxs-lookup"><span data-stu-id="0a8fd-108">Only members of the **sysadmin** fixed server role and the **db_owner**, **db_securityadmin**, and the **db_ddladmin** fixed database roles can view information for all extended stored procedures.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a8fd-109">参照</span><span class="sxs-lookup"><span data-stu-id="0a8fd-109">See Also</span></span>  
 <span data-ttu-id="0a8fd-110">[sp_helpextendedproc &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a8fd-110">[sp_helpextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpextendedproc-transact-sql) </span></span>  
 <span data-ttu-id="0a8fd-111">[sp_addextendedproc &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0a8fd-111">[sp_addextendedproc &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addextendedproc-transact-sql) </span></span>  
 [<span data-ttu-id="0a8fd-112">sp_dropextendedproc &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0a8fd-112">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
