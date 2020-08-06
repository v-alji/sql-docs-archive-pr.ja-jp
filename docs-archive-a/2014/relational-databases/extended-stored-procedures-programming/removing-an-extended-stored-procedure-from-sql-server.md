---
title: SQL Server | から拡張ストアドプロシージャを削除するMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- deleting extended stored procedures
- removing extended stored procedures
- extended stored procedures [SQL Server], removing
- dropping extended stored procedures
ms.assetid: 7827e574-3f59-4279-9a9b-532582e041cb
author: rothja
ms.author: jroth
ms.openlocfilehash: 284da815de073248669da032c06ddeeb68c697a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87743257"
---
# <a name="removing-an-extended-stored-procedure-from-sql-server"></a><span data-ttu-id="2f27a-102">SQL Server からの拡張ストアド プロシージャの削除</span><span class="sxs-lookup"><span data-stu-id="2f27a-102">Removing an Extended Stored Procedure from SQL Server</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="2f27a-103">代わりに CLR Integration を使用してください。</span><span class="sxs-lookup"><span data-stu-id="2f27a-103">Use CLR Integration instead.</span></span>  
  
 <span data-ttu-id="2f27a-104">ユーザー定義の拡張ストアドプロシージャ DLL 内の各拡張ストアドプロシージャ関数を削除するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム管理者が**sp_dropextendedproc**システムストアドプロシージャを実行して、関数の名前とその関数が存在する DLL の名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f27a-104">To drop each extended stored procedure function in a user-defined extended stored procedure DLL, a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] system administrator must run the **sp_dropextendedproc** system stored procedure, specifying the name of the function and the name of the DLL in which that function resides.</span></span> <span data-ttu-id="2f27a-105">たとえば、次のコマンドは、xp_hello.dll という名前の DLL にある関数**xp_hello**をから削除し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="2f27a-105">For example, this command removes the function **xp_hello**, located in a DLL named xp_hello.dll, from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
```  
sp_dropextendedproc 'xp_hello'  
```  
  
 <span data-ttu-id="2f27a-106">以降で [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] は、 **sp_dropextendedproc**システムの拡張ストアドプロシージャは削除されません。</span><span class="sxs-lookup"><span data-stu-id="2f27a-106">Beginning with [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], **sp_dropextendedproc** does not drop system extended stored procedures.</span></span> <span data-ttu-id="2f27a-107">代わりに、システム管理者は、拡張ストアドプロシージャに対する EXECUTE 権限を**public**ロールに対して拒否する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2f27a-107">Instead, the system administrator should deny EXECUTE permission on the extended stored procedure to the **public** role.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f27a-108">参照</span><span class="sxs-lookup"><span data-stu-id="2f27a-108">See Also</span></span>  
 [<span data-ttu-id="2f27a-109">sp_dropextendedproc &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2f27a-109">sp_dropextendedproc &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-dropextendedproc-transact-sql)  
  
  
