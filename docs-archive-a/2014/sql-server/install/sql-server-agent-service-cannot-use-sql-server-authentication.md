---
title: SQL Server エージェントサービスは SQL Server Authentication | を使用できませんMicrosoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- authentication [SQL Server Agent]
- SQL Server Authentication [SQL Server Agent]
ms.assetid: c39f3ec3-fc2c-4c12-940f-60d8d3d17660
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 32188b1c47168aefbca914fa15f71850df716153
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642517"
---
# <a name="sql-server-agent-service-cannot-use-sql-server-authentication"></a><span data-ttu-id="a96c6-102">SQL Server エージェント サービスで SQL Server 認証を使用できない</span><span class="sxs-lookup"><span data-stu-id="a96c6-102">SQL Server Agent Service cannot use SQL Server Authentication</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a96c6-103">エージェント サービスから [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続する場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントは Windows 認証のみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="a96c6-103">Agent only supports Windows Authentication when the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service connects to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
## <a name="component"></a><span data-ttu-id="a96c6-104">コンポーネント</span><span class="sxs-lookup"><span data-stu-id="a96c6-104">Component</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a96c6-105">エージェント</span><span class="sxs-lookup"><span data-stu-id="a96c6-105">Agent</span></span>  
  
## <a name="description"></a><span data-ttu-id="a96c6-106">説明</span><span class="sxs-lookup"><span data-stu-id="a96c6-106">Description</span></span>  
 <span data-ttu-id="a96c6-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービスは、Windows 認証を使用してデータベースにログオンすることのみできます。</span><span class="sxs-lookup"><span data-stu-id="a96c6-107">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service can only log on to the database using Windows Authentication.</span></span> <span data-ttu-id="a96c6-108">つまり、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザーである必要があります。</span><span class="sxs-lookup"><span data-stu-id="a96c6-108">This means that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent service account must be a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] user.</span></span>  
  
 <span data-ttu-id="a96c6-109">詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オンライン ブックの「SQL Server エージェントのセキュリティ管理」および「[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントのセキュリティの実装」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a96c6-109">For more information, see the topics "Security for Automatic Administration" and "Implementing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent Security" in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a96c6-110">参照</span><span class="sxs-lookup"><span data-stu-id="a96c6-110">See Also</span></span>  
 [<span data-ttu-id="a96c6-111">SQL Server エージェントのアップグレードに関する問題</span><span class="sxs-lookup"><span data-stu-id="a96c6-111">SQL Server Agent Upgrade Issues</span></span>](../../../2014/sql-server/install/sql-server-agent-upgrade-issues.md)  
  
  
