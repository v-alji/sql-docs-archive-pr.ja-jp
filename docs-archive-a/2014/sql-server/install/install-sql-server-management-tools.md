---
title: SQL Server 管理ツールのインストール |Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Tools
ms.assetid: af68d59a-a04d-4f23-9967-ad4ee2e63381
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 39a7ed6d859c6bbbb63e938cc7127958082737dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643128"
---
# <a name="install-sql-server-management-tools"></a><span data-ttu-id="782e7-102">SQL Server 管理ツールのインストール</span><span class="sxs-lookup"><span data-stu-id="782e7-102">Install SQL Server Management Tools</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="782e7-103">管理ツールには、次のコンポーネントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="782e7-103">Management tools include the following components:</span></span>  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]  
  
-   [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="782e7-104">データベース チューニング アドバイザー</span><span class="sxs-lookup"><span data-stu-id="782e7-104">Database Tuning Advisor</span></span>  
  
-   <span data-ttu-id="782e7-105">sqlcmd.exe や osql.exe などのコマンド プロンプト ツール</span><span class="sxs-lookup"><span data-stu-id="782e7-105">Command prompt tools, such as sqlcmd.exe and osql.exe.</span></span>  
  
-   [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]<span data-ttu-id="782e7-106">[!INCLUDE[msCoName](../../includes/msconame-md.md)]アドイン[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]</span><span class="sxs-lookup"><span data-stu-id="782e7-106">add-ins to [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]</span></span>  
  
 <span data-ttu-id="782e7-107">[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インストール時の別個のオプションです。</span><span class="sxs-lookup"><span data-stu-id="782e7-107">Note that [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] is a separate option during [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installation.</span></span>  
  
 <span data-ttu-id="782e7-108">コンピューターにインストールされている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] または [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] のインスタンス数にかかわらず、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 管理ツールは 1 つのみインストールされます。</span><span class="sxs-lookup"><span data-stu-id="782e7-108">Regardless of how many instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], or [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] are installed on a computer, only one copy of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Management Tools will be installed.</span></span>  
  
 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]<span data-ttu-id="782e7-109">管理ツールは、以前のバージョンの管理ツールと同じコンピューター上でサイドバイサイドで実行でき [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="782e7-109">Management Tools can run side-by-side on the same computer with earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Management Tools.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="782e7-110">参照</span><span class="sxs-lookup"><span data-stu-id="782e7-110">See Also</span></span>  
 <span data-ttu-id="782e7-111">[SQL Server 2014 の各エディションがサポートする機能](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span><span class="sxs-lookup"><span data-stu-id="782e7-111">[Features Supported by the Editions of SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md) </span></span>  
 <span data-ttu-id="782e7-112">[SQL Server 2014 のエディションとコンポーネント](../editions-and-components-of-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="782e7-112">[Editions and Components of SQL Server 2014](../editions-and-components-of-sql-server-2016.md) </span></span>  
 <span data-ttu-id="782e7-113">[インストールウィザード &#40;セットアップから SQL Server 2014 をインストール&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) </span><span class="sxs-lookup"><span data-stu-id="782e7-113">[Install SQL Server 2014 from the Installation Wizard &#40;Setup&#41;](../../database-engine/install-windows/install-sql-server-from-the-installation-wizard-setup.md) </span></span>  
 [<span data-ttu-id="782e7-114">インストールウィザード &#40;セットアップを使用して SQL Server 2014 にアップグレード&#41;</span><span class="sxs-lookup"><span data-stu-id="782e7-114">Upgrade to SQL Server 2014 Using the Installation Wizard &#40;Setup&#41;</span></span>](../../database-engine/install-windows/upgrade-sql-server-using-the-installation-wizard-setup.md)  
  
  
