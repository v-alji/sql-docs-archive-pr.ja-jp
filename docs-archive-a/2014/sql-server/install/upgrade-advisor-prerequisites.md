---
title: アップグレードアドバイザーの前提条件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- installing Upgrade Advisor
- requirements [Upgrade Advisor]
- software [Upgrade Advisor]
- system requirements [Upgrade Advisor]
- Setup [Upgrade Advisor]
- SQL Server Upgrade Advisor, prerequisites
- prerequisites [Upgrade Advisor]
- Upgrade Advisor [SQL Server], prerequisites
ms.assetid: d21a39e5-5f81-4096-a7dd-f244e4779992
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 41c97cf585d1768c7aebeec2613ee8744cb220da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640376"
---
# <a name="upgrade-advisor-prerequisites"></a><span data-ttu-id="4b9c3-102">アップグレード アドバイザーの前提条件</span><span class="sxs-lookup"><span data-stu-id="4b9c3-102">Upgrade Advisor Prerequisites</span></span>
  <span data-ttu-id="4b9c3-103">ここでは、アップグレード アドバイザーに関するソフトウェアの必要条件について説明します。</span><span class="sxs-lookup"><span data-stu-id="4b9c3-103">This topic describes the software requirements for Upgrade Advisor.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4b9c3-104">前提条件</span><span class="sxs-lookup"><span data-stu-id="4b9c3-104">Prerequisites</span></span>  
 <span data-ttu-id="4b9c3-105">アップグレード アドバイザーのインストールと実行の前提条件は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4b9c3-105">The prerequisites for installing and running Upgrade Advisor are as follows:</span></span>  
  
-   [!INCLUDE[wiprlhext](../../includes/wiprlhext-md.md)] <span data-ttu-id="4b9c3-106">SP1、[!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] SP2 以降、Windows 7、または [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2。</span><span class="sxs-lookup"><span data-stu-id="4b9c3-106">SP1, [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] beginning with SP2, Windows 7, or [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] R2.</span></span>  
  
-   <span data-ttu-id="4b9c3-107">Windows インストーラー 4.5。</span><span class="sxs-lookup"><span data-stu-id="4b9c3-107">Windows Installer 4.5.</span></span> <span data-ttu-id="4b9c3-108">[Windows インストーラー Web サイト](https://www.microsoft.com/download/details.aspx?id=8483)から Windows インストーラーをインストールできます。</span><span class="sxs-lookup"><span data-stu-id="4b9c3-108">You can install Windows Installer from the [Windows Installer Web site](https://www.microsoft.com/download/details.aspx?id=8483).</span></span>  
  
-   <span data-ttu-id="4b9c3-109">[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] (.NET Framework 4 以降)。</span><span class="sxs-lookup"><span data-stu-id="4b9c3-109">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)], beginning with .NET Framework 4.</span></span> <span data-ttu-id="4b9c3-110">は、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 製品メディア、 [SDK、再頒布可能パッケージ、Service Pack ダウンロード Web サイト](https://go.microsoft.com/fwlink/?LinkId=48882)で入手できます。</span><span class="sxs-lookup"><span data-stu-id="4b9c3-110">The [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] is available on the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] product media, and from the [SDK, redistributable, and service pack download Web site](https://go.microsoft.com/fwlink/?LinkId=48882).</span></span>  
  
    -   <span data-ttu-id="4b9c3-111">[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] メディアから .NET Framework 4 をインストールするには、ディスク ドライブのルートに移動します。</span><span class="sxs-lookup"><span data-stu-id="4b9c3-111">To install the .NET Framework 4 from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] media, locate the root of the disk drive.</span></span> <span data-ttu-id="4b9c3-112">次に、redist フォルダー、DotNetFrameworks フォルダーの順にダブルクリックし、dotNetFx40_Full_x86_x64.exe (32 ビットおよび 64 ビット オペレーティング システム用) を実行します。</span><span class="sxs-lookup"><span data-stu-id="4b9c3-112">Then double-click the \redist folder, double-click the DotNetFrameworks folder, and run dotNetFx40_Full_x86_x64.exe (for both 32-bit and 64-bit operating systems).</span></span>  
  
-   <span data-ttu-id="4b9c3-113">[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Scriptdom はアップグレードアドバイザーをインストールするための前提条件で [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] あり、アップグレードアドバイザーのセットアップではインストールされません。</span><span class="sxs-lookup"><span data-stu-id="4b9c3-113">The [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom is a prerequisite for installing [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Upgrade Advisor, and is not installed by Upgrade Advisor Setup.</span></span> <span data-ttu-id="4b9c3-114">セットアップでは、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[tsql](../../includes/tsql-md.md)] Feature Pack から scriptdom をダウンロードしてインストールする必要があり [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ます。</span><span class="sxs-lookup"><span data-stu-id="4b9c3-114">The Setup requires you to download and install the [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] ScriptDom from the [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Feature Pack.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b9c3-115">参照</span><span class="sxs-lookup"><span data-stu-id="4b9c3-115">See Also</span></span>  
 [<span data-ttu-id="4b9c3-116">アップグレード アドバイザーをインストールする方法</span><span class="sxs-lookup"><span data-stu-id="4b9c3-116">How to: Install Upgrade Advisor</span></span>](../../../2014/sql-server/install/how-to-install-upgrade-advisor.md)  
  
  
