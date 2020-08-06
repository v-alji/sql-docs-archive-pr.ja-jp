---
title: アプリケーションドメインと CLR 統合のセキュリティ |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: reference
helpviewer_keywords:
- security [CLR integration]
- application domains [CLR integration]
ms.assetid: 54ee904e-e21a-4ee7-b4ad-a6f6f71bd473
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 85d6e66b1d51cc9d7c5829b8e83c510bea750e2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87634006"
---
# <a name="application-domains-and-clr-integration-security"></a><span data-ttu-id="a4719-102">アプリケーション ドメインと CLR 統合のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="a4719-102">Application Domains and CLR Integration Security</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a4719-103">は、同じアプリケーション ドメインの同じ所有者に属するアセンブリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="a4719-103">loads assemblies belonging to the same owner in the same application domain.</span></span> <span data-ttu-id="a4719-104">一連のアセンブリが同じアプリケーション ドメインで実行されるので、.NET Framework リフレクション アプリケーション プログラミング インターフェイスやその他の手段を使用して、実行時にアセンブリを相互に検出することができ、遅延バインディングの形式で呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="a4719-104">By virtue of a set of assemblies running in the same application domain, assemblies are able to discover each other at execution time using the.NET Framework reflection application programming interfaces or other means, and can call into them in late-bound fashion.</span></span> <span data-ttu-id="a4719-105">このような呼び出しは同じ所有者に属するアセンブリに対して行われるので、これらの呼び出しに対して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 権限はチェックされません。</span><span class="sxs-lookup"><span data-stu-id="a4719-105">Because such calls are occurring against assemblies belonging to the same owner, there are no [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permissions checked for these calls.</span></span> <span data-ttu-id="a4719-106">アプリケーション ドメインでのアセンブリの配置方法は、主に、スケーラビリティ、セキュリティ、および分離の実現を目標に設計されていますが、この設計は今後のリリースで変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="a4719-106">The placement scheme of assemblies in application domains is designed primarily to achieve scalability, security, and isolation goals, and can potentially change in future releases.</span></span> <span data-ttu-id="a4719-107">したがって、遅延バインディング メカニズムを使用して同じアプリケーション ドメインのアセンブリを検出する方法に依存しないでください。</span><span class="sxs-lookup"><span data-stu-id="a4719-107">Hence, you should not rely on finding assemblies in the same application domain through late-bound mechanisms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4719-108">参照</span><span class="sxs-lookup"><span data-stu-id="a4719-108">See Also</span></span>  
 [<span data-ttu-id="a4719-109">CLR 統合のセキュリティ</span><span class="sxs-lookup"><span data-stu-id="a4719-109">CLR Integration Security</span></span>](../../relational-databases/clr-integration/security/clr-integration-security.md)  
  
  
