---
title: CLR 統合の有効化 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- clr enabled option
- common language runtime [SQL Server], enabling
ms.assetid: eb3e9c64-7486-42e7-baf6-c956fb311a2c
author: rothja
ms.author: jroth
ms.openlocfilehash: d7187906f1376deb81ca7ff4770af7b12b63c022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87720012"
---
# <a name="enabling-clr-integration"></a><span data-ttu-id="59d6a-102">CLR 統合の有効化</span><span class="sxs-lookup"><span data-stu-id="59d6a-102">Enabling CLR Integration</span></span>
  <span data-ttu-id="59d6a-103">CLR (共通言語ランタイム) 統合機能は既定では無効になっているので、CLR 統合を使用して実装されるオブジェクトを使用するには、この機能を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="59d6a-103">The common language runtime (CLR) integration feature is off by default, and must be enabled in order to use objects that are implemented using CLR integration.</span></span> <span data-ttu-id="59d6a-104">CLR 統合を有効にするには、 **sp_configure**ストアドプロシージャの**clr enabled**オプションを使用します。</span><span class="sxs-lookup"><span data-stu-id="59d6a-104">To enable CLR integration, use the **clr enabled** option of the **sp_configure** stored procedure:</span></span>  
  
```  
  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'clr enabled', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
 <span data-ttu-id="59d6a-105">Clr の統合を無効にするには、 **clr enabled**オプションを0に設定します。</span><span class="sxs-lookup"><span data-stu-id="59d6a-105">You can disable CLR integration by setting the **clr enabled** option to 0.</span></span> <span data-ttu-id="59d6a-106">CLR 統合を無効にすると、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ではすべての CLR ルーチンの実行が停止され、すべてのアプリケーション ドメインがアンロードされます。</span><span class="sxs-lookup"><span data-stu-id="59d6a-106">When you disable CLR integration, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] stops executing all CLR routines and unloads all application domains.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59d6a-107">CLR 統合を有効にするには、 **sysadmin**固定サーバーロールおよび**serveradmin**固定サーバーロールのメンバーによって暗黙的に保持される ALTER SETTINGS サーバーレベル権限が必要です。</span><span class="sxs-lookup"><span data-stu-id="59d6a-107">To enable CLR integration, you must have ALTER SETTINGS server level permission, which is implicitly held by members of the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59d6a-108">コンピューターを構成しているメモリ サイズとプロセッサ数が非常に大きい場合、SQL Server の CLR 統合機能をサーバーの起動時に読み込めないことがあります。</span><span class="sxs-lookup"><span data-stu-id="59d6a-108">Computers configured with large amounts of memory and a large number of processors may fail to load the CLR integration feature of SQL Server when starting the server.</span></span> <span data-ttu-id="59d6a-109">この問題に対処するには、 **-gmemory_to_reserve**サービスのスタートアップオプションを使用してサーバーを起動 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] し、十分な大きさのメモリ値を指定します。</span><span class="sxs-lookup"><span data-stu-id="59d6a-109">To address this issue, start the server by using the **-gmemory_to_reserve**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] service startup option, and specify a memory value large enough.</span></span> <span data-ttu-id="59d6a-110">詳細については、「 [データベース エンジン サービスのスタートアップ オプション](../../database-engine/configure-windows/database-engine-service-startup-options.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59d6a-110">For more information, see [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="59d6a-111">簡易プーリングでは、共通言語ランタイム (CLR) の実行はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="59d6a-111">Common language runtime (CLR) execution is not supported under lightweight pooling.</span></span> <span data-ttu-id="59d6a-112">CLR 統合を有効にする前に、簡易プーリングを無効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="59d6a-112">Before enabling CLR integration, you must disable lightweight pooling.</span></span> <span data-ttu-id="59d6a-113">詳細については、「 [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59d6a-113">For more information, see [lightweight pooling Server Configuration Option](../../database-engine/configure-windows/lightweight-pooling-server-configuration-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59d6a-114">参照</span><span class="sxs-lookup"><span data-stu-id="59d6a-114">See Also</span></span>  
 <span data-ttu-id="59d6a-115">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="59d6a-115">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="59d6a-116">[clr enabled サーバー構成オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) </span><span class="sxs-lookup"><span data-stu-id="59d6a-116">[clr enabled Server Configuration Option](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md) </span></span>  
 <span data-ttu-id="59d6a-117">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="59d6a-117">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="59d6a-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="59d6a-118">[GRANT &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-transact-sql) </span></span>  
 [<span data-ttu-id="59d6a-119">サーバーレベルのロール</span><span class="sxs-lookup"><span data-stu-id="59d6a-119">Server-Level Roles</span></span>](../security/authentication-access/server-level-roles.md)  
  
  
