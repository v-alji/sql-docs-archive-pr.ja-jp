---
title: EKM provider enabled サーバー構成オプション | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- external encryption provider
helpviewer_keywords:
- EKM provider enabled option
ms.assetid: da58ed50-3a13-4172-9065-960559d8f383
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1b44e7f5e0801bb370a98abe79a6ea449c6f7409
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741245"
---
# <a name="ekm-provider-enabled-server-configuration-option"></a><span data-ttu-id="89747-102">EKM provider enabled サーバー構成オプション</span><span class="sxs-lookup"><span data-stu-id="89747-102">EKM provider enabled Server Configuration Option</span></span>
  <span data-ttu-id="89747-103">`EKM provider enabled` オプションは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] での拡張キー管理デバイスのサポートを制御します。</span><span class="sxs-lookup"><span data-stu-id="89747-103">The `EKM provider enabled` option controls Extensible Key Management device support in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="89747-104">既定では、このオプションはオフになっています。</span><span class="sxs-lookup"><span data-stu-id="89747-104">By default this option is off.</span></span>  
  
 <span data-ttu-id="89747-105">この機能を有効または無効にするには、次の `sp_configure` コマンドのいずれかを実行します。</span><span class="sxs-lookup"><span data-stu-id="89747-105">To enable or disable the feature, issue one of the following `sp_configure` commands:</span></span>  
  
```  
/* Enable the external encryption provider option */  
sp_configure 'EKM provider enabled', 1  
/* Disable the external encryption provider option */  
sp_configure 'EKM provider enabled', 0  
```  
  
> [!NOTE]  
>  <span data-ttu-id="89747-106">このオプションは [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のすべてのエディションで有効になっているわけではありません。</span><span class="sxs-lookup"><span data-stu-id="89747-106">This option is not enabled in every edition of [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="89747-107">の各エディションでサポートされる機能の一覧につい [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ては、「 [SQL Server 2014 の各エディションがサポートする機能](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89747-107">For a list of features that are supported by the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89747-108">参照</span><span class="sxs-lookup"><span data-stu-id="89747-108">See Also</span></span>  
 <span data-ttu-id="89747-109">[拡張キー管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md) </span><span class="sxs-lookup"><span data-stu-id="89747-109">[Extensible Key Management &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md) </span></span>  
 <span data-ttu-id="89747-110">[サーバー構成オプション &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="89747-110">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="89747-111">[リソースの利用状況の監視 &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span><span class="sxs-lookup"><span data-stu-id="89747-111">[Monitor Resource Usage &#40;System Monitor&#41;](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md) </span></span>  
 <span data-ttu-id="89747-112">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="89747-112">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="89747-113">RECONFIGURE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="89747-113">RECONFIGURE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/reconfigure-transact-sql)  
  
  
