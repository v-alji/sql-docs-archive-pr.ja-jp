---
title: SMO オブジェクトモデル |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- object models [SMO]
- SMO [SQL Server], object model
- SQL Server Management Objects, object model
ms.assetid: bd6e59b6-ca46-42c0-adb2-c9d64cf6e00b
author: stevestein
ms.author: sstein
ms.openlocfilehash: c973e381a6cc7de44a0072d012147271eaa609ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87711861"
---
# <a name="smo-object-model"></a><span data-ttu-id="347a3-102">SMO オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="347a3-102">SMO Object Model</span></span>
  <span data-ttu-id="347a3-103">SMO オブジェクト モデルは、オブジェクトの階層で構成されています。</span><span class="sxs-lookup"><span data-stu-id="347a3-103">The SMO object model is made up of a hierarchy of objects.</span></span> <span data-ttu-id="347a3-104"><xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトはトップ レベル オブジェクトであるため、すべてのインスタンス クラス オブジェクトは <xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトの下位に位置します。</span><span class="sxs-lookup"><span data-stu-id="347a3-104">The <xref:Microsoft.SqlServer.Management.Smo.Server> object is the top level object and all instance class objects reside under the <xref:Microsoft.SqlServer.Management.Smo.Server> object.</span></span>  
  
 <span data-ttu-id="347a3-105"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> クラスは、個別のオブジェクト階層を持ったトップ レベル クラスです。</span><span class="sxs-lookup"><span data-stu-id="347a3-105">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> class is a top level class with a separate object hierarchy.</span></span> <span data-ttu-id="347a3-106"><xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer>オブジェクトは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] WMI プロバイダーを通じて使用できるサービスとネットワーク設定を表します。</span><span class="sxs-lookup"><span data-stu-id="347a3-106">The <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> object represents [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services and network settings available through the WMI Provider.</span></span>  
  
 <span data-ttu-id="347a3-107"><xref:Microsoft.SqlServer.Management.Smo.Server> オブジェクトおよび <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> オブジェクトに加え、<xref:Microsoft.SqlServer.Management.Smo.Transfer>、<xref:Microsoft.SqlServer.Management.Smo.Backup>、<xref:Microsoft.SqlServer.Management.Smo.Restore> など、タスクや操作を表す複数のユーティリティ クラスがあります。</span><span class="sxs-lookup"><span data-stu-id="347a3-107">Besides the <xref:Microsoft.SqlServer.Management.Smo.Server> and <xref:Microsoft.SqlServer.Management.Smo.Wmi.ManagedComputer> objects, there are several utility classes that represent tasks or operations, such as <xref:Microsoft.SqlServer.Management.Smo.Transfer>, <xref:Microsoft.SqlServer.Management.Smo.Backup>, or <xref:Microsoft.SqlServer.Management.Smo.Restore></span></span>  
  
 <span data-ttu-id="347a3-108">SMO オブジェクト モデルは、複数の名前空間で構成されています。</span><span class="sxs-lookup"><span data-stu-id="347a3-108">The SMO object model is made up of several namespaces.</span></span> <span data-ttu-id="347a3-109">詳細については、「[SMO 名前空間](smo-object-model-namespaces.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="347a3-109">For more information, see [SMO Namespaces](smo-object-model-namespaces.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="347a3-110">参照</span><span class="sxs-lookup"><span data-stu-id="347a3-110">See Also</span></span>  
 <span data-ttu-id="347a3-111">[SMO オブジェクトモデルの図](smo-object-model-diagram.md) </span><span class="sxs-lookup"><span data-stu-id="347a3-111">[SMO Object Model Diagram](smo-object-model-diagram.md) </span></span>  
 <span data-ttu-id="347a3-112">[SMO 名前空間](smo-object-model-namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="347a3-112">[SMO Namespaces](smo-object-model-namespaces.md) </span></span>  
 [<span data-ttu-id="347a3-113">構成管理用の WMI プロバイダーの概念</span><span class="sxs-lookup"><span data-stu-id="347a3-113">WMI Provider for Configuration Management Concepts</span></span>](../wmi-provider-configuration/wmi-provider-for-configuration-management.md)  
  
  
