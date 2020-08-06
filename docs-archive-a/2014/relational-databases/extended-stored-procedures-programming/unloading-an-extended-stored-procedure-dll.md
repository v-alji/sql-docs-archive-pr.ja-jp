---
title: 拡張ストアドプロシージャ DLL のアンロード |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], unloading
- unloading extended stored procedures
ms.assetid: 4c75ab14-af54-4965-b376-8d75d385c941
author: rothja
ms.author: jroth
ms.openlocfilehash: 7bd4855390e95d949ab769d6567d6f106959dcde
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631024"
---
# <a name="unloading-an-extended-stored-procedure-dll"></a><span data-ttu-id="2395e-102">拡張ストアド プロシージャ DLL のアンロード</span><span class="sxs-lookup"><span data-stu-id="2395e-102">Unloading an Extended Stored Procedure DLL</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="2395e-103">代わりに CLR Integration を使用してください。</span><span class="sxs-lookup"><span data-stu-id="2395e-103">Use CLR Integration instead.</span></span>  
  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="2395e-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]dll のいずれかの関数が呼び出されるとすぐに、拡張ストアドプロシージャ DLL を読み込みます。</span><span class="sxs-lookup"><span data-stu-id="2395e-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] loads an extended stored procedure DLL as soon as a call is made to one of the functions of the DLL.</span></span> <span data-ttu-id="2395e-105">DLL がロードされた状態は、サーバーがシャットダウンするか、DBCC ステートメントを使用してシステム管理者によってアンロードされるまで、維持されます。</span><span class="sxs-lookup"><span data-stu-id="2395e-105">The DLL remains loaded until the server is shut down or until the system administrator uses the DBCC statement to unload it.</span></span> <span data-ttu-id="2395e-106">たとえば、次のコマンドは、 **xp_hello.dll**をアンロードします。これにより、システム管理者は、サーバーをシャットダウンすることなく、このファイルの新しいバージョンをディレクトリにコピーできます。</span><span class="sxs-lookup"><span data-stu-id="2395e-106">For example, this command unloads the **xp_hello.dll**, allowing the system administrator to copy a newer version of this file to the directory without shutting down the server:</span></span>  
  
```  
DBCC xp_hello(FREE)  
```  
  
## <a name="see-also"></a><span data-ttu-id="2395e-107">参照</span><span class="sxs-lookup"><span data-stu-id="2395e-107">See Also</span></span>  
 [<span data-ttu-id="2395e-108">DBCC dllname &#40;FREE&#41; &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="2395e-108">DBCC dllname &#40;FREE&#41; &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-dllname-free-transact-sql)  
  
  
