---
title: Ole Automation Procedures サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- Ole Automation Procedures option
ms.assetid: e8982e05-4984-4406-9760-285e8c028ddf
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d34615ce1f808c1015c9c3d312a38a67dba291b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87712362"
---
# <a name="ole-automation-procedures-server-configuration-option"></a><span data-ttu-id="2e035-102">Ole Automation Procedures サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="2e035-102">Ole Automation Procedures Server Configuration Option</span></span>
  <span data-ttu-id="2e035-103">`Ole Automation Procedures` オプションは、[!INCLUDE[tsql](../../includes/tsql-md.md)] バッチ内で OLE オートメーション オブジェクトをインスタンス化するかどうかを指定するために使用します。</span><span class="sxs-lookup"><span data-stu-id="2e035-103">Use the `Ole Automation Procedures` option to specify whether OLE Automation objects can be instantiated within [!INCLUDE[tsql](../../includes/tsql-md.md)] batches.</span></span> <span data-ttu-id="2e035-104">このオプションは、ポリシー ベースの管理または **sp_configure** ストアド プロシージャを使用して構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="2e035-104">This option can also be configured using the Policy-Based Management or the **sp_configure** stored procedure.</span></span> <span data-ttu-id="2e035-105">詳細については、「 [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e035-105">For more information, see [Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md).</span></span>  
  
 <span data-ttu-id="2e035-106">`Ole Automation Procedures` オプションに設定できる値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="2e035-106">The `Ole Automation Procedures` option can be set to the following values.</span></span>  
  
 <span data-ttu-id="2e035-107">0</span><span class="sxs-lookup"><span data-stu-id="2e035-107">0</span></span>  
 <span data-ttu-id="2e035-108">OLE オートメーション プロシージャを無効にします。</span><span class="sxs-lookup"><span data-stu-id="2e035-108">OLE Automation Procedures are disabled.</span></span> <span data-ttu-id="2e035-109">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の新しいインスタンスの既定値です。</span><span class="sxs-lookup"><span data-stu-id="2e035-109">Default for new instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="2e035-110">1</span><span class="sxs-lookup"><span data-stu-id="2e035-110">1</span></span>  
 <span data-ttu-id="2e035-111">OLE オートメーション プロシージャを有効にします。</span><span class="sxs-lookup"><span data-stu-id="2e035-111">OLE Automation Procedures are enabled.</span></span>  
  
 <span data-ttu-id="2e035-112">OLE オートメーション プロシージャが有効である場合、 **sp_OACreate** を呼び出すと OLE 共有実行環境が開始します。</span><span class="sxs-lookup"><span data-stu-id="2e035-112">When OLE Automation Procedures are enabled, a call to **sp_OACreate** will start the OLE shared execution environment.</span></span>  
  
 <span data-ttu-id="2e035-113">オプションの現在の値を `Ole Automation Procedures` 表示および変更するには、 **sp_configure**システムストアドプロシージャを使用します。</span><span class="sxs-lookup"><span data-stu-id="2e035-113">The current value of the `Ole Automation Procedures` option can be viewed and changed by using the **sp_configure** system stored procedure.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="2e035-114">例</span><span class="sxs-lookup"><span data-stu-id="2e035-114">Examples</span></span>  
 <span data-ttu-id="2e035-115">OLE オートメーション プロシージャの現在の設定を確認する方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="2e035-115">The following example shows how to view the current setting of OLE Automation procedures.</span></span>  
  
```  
EXEC sp_configure 'Ole Automation Procedures';  
GO  
```  
  
 <span data-ttu-id="2e035-116">OLE オートメーション プロシージャを有効にする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="2e035-116">The following example shows how to enable OLE Automation procedures.</span></span>  
  
```  
sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE;  
GO  
sp_configure 'Ole Automation Procedures', 1;  
GO  
RECONFIGURE;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="2e035-117">参照</span><span class="sxs-lookup"><span data-stu-id="2e035-117">See Also</span></span>  
 <span data-ttu-id="2e035-118">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e035-118">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 <span data-ttu-id="2e035-119">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2e035-119">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="2e035-120">[セキュリティ構成](../../relational-databases/security/surface-area-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="2e035-120">[Surface Area Configuration](../../relational-databases/security/surface-area-configuration.md) </span></span>  
 [<span data-ttu-id="2e035-121">サーバー構成オプション &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2e035-121">Server Configuration Options &#40;SQL Server&#41;</span></span>](server-configuration-options-sql-server.md)  
  
  
