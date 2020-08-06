---
title: SQL Server インストールの新機能 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- installing SQL Server, what's new
- SQL Server, what's new
- SQL Server, installing
ms.assetid: c8642a96-3a09-4ec7-a9c3-c539147e6330
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d34085e320cd8ca0b82d382d6d49eaa303086114
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640351"
---
# <a name="what39s-new-in-sql-server-installation"></a><span data-ttu-id="c8907-102">SQL Server インストールの新機能</span><span class="sxs-lookup"><span data-stu-id="c8907-102">What&#39;s New in SQL Server Installation</span></span>
  <span data-ttu-id="c8907-103">Windows Vista は、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] のサポート対象のオペレーティング システムではありません。</span><span class="sxs-lookup"><span data-stu-id="c8907-103">Windows Vista is not a supported operating system for [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)].</span></span> <span data-ttu-id="c8907-104">Service Pack 1 は、[!INCLUDE[win7](../../includes/win7-md.md)] および [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] の各オペレーティング システムの場合の最小要件として残されています。</span><span class="sxs-lookup"><span data-stu-id="c8907-104">Service Pack 1 remains as the minimum requirement for [!INCLUDE[win7](../../includes/win7-md.md)] and [!INCLUDE[winserver2008r2](../../includes/winserver2008r2-md.md)] operating systems.</span></span> <span data-ttu-id="c8907-105">オペレーティングシステムの要件の詳細については、「 [SQL Server 2014 をインストールするためのハードウェアおよびソフトウェアの要件](hardware-and-software-requirements-for-installing-sql-server.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8907-105">For more information on operating system requirements, see [Hardware and Software Requirements for Installing SQL Server 2014](hardware-and-software-requirements-for-installing-sql-server.md).</span></span>  
  
 <span data-ttu-id="c8907-106">[!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] のインストール時には、抽出されたパッケージを保存するディレクトリを指定するように求められます。</span><span class="sxs-lookup"><span data-stu-id="c8907-106">Installation of [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] will prompt you to specify the directory to save the extracted package.</span></span> <span data-ttu-id="c8907-107">場所が入力されていない場合、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、既定でコンピューターのシステム ドライブが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c8907-107">If no location is entered, [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] will default to the computer's system drive.</span></span> <span data-ttu-id="c8907-108">抽出されたファイルは、 [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] のインストールが完了した後も残ります。</span><span class="sxs-lookup"><span data-stu-id="c8907-108">The extracted files will remain after [!INCLUDE[ssExpCurrent](../../includes/ssexpcurrent-md.md)] installation is complete.</span></span>  
  
 <span data-ttu-id="c8907-109">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、SysPrep は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のすべてのインストールでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c8907-109">In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], SysPrep is supported for all installations of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c8907-110">現在、SysPrep はフェールオーバー クラスターのインストールをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c8907-110">SysPrep now supports failover cluster installations.</span></span> <span data-ttu-id="c8907-111">詳細については、「 [sysprep を使用して SQL Server をインストールする場合の考慮事項](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)」および「 [Sysprep を使用した SQL Server 2014 のインストール](../../database-engine/install-windows/install-sql-server-using-sysprep.md)</span><span class="sxs-lookup"><span data-stu-id="c8907-111">For more information, see [Considerations for Installing SQL Server Using SysPrep](../../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md) and [Install SQL Server 2014 Using SysPrep](../../database-engine/install-windows/install-sql-server-using-sysprep.md).</span></span>  
  
 <span data-ttu-id="c8907-112">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] からのアップグレードはサポートされていますが、並列使用はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c8907-112">Upgrade from [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] is supported, but side-by-side is not supported.</span></span> <span data-ttu-id="c8907-113">[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] の [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]サポートに関する詳細については、「 [サポートされているバージョンとエディションのアップグレード](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c8907-113">For more information about [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] support in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], see [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md).</span></span>  
  
 <span data-ttu-id="c8907-114">[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]以降では、Standard Edition のデータベース エンジンのメモリ領域は 128 GB です。</span><span class="sxs-lookup"><span data-stu-id="c8907-114">Beginning in [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], the database engine in the Standard edition has a memory capacity of 128 GB.</span></span> <span data-ttu-id="c8907-115">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] では、Standard Edition のデータベース エンジンのメモリ領域は 64 GB でした。</span><span class="sxs-lookup"><span data-stu-id="c8907-115">In [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], the database engine in the Standard edition had a memory capacity of 64 GB.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8907-116">参照</span><span class="sxs-lookup"><span data-stu-id="c8907-116">See Also</span></span>  
 <span data-ttu-id="c8907-117">[SQL Server 2014 の新機能](../what-s-new-in-sql-server-2016.md) </span><span class="sxs-lookup"><span data-stu-id="c8907-117">[What's New in SQL Server 2014](../what-s-new-in-sql-server-2016.md) </span></span>  
 <span data-ttu-id="c8907-118">[SQL Server 2014 の製品仕様](../../../2014/getting-started/sql-server-2014-product-specifications.md) </span><span class="sxs-lookup"><span data-stu-id="c8907-118">[Product Specifications for SQL Server 2014](../../../2014/getting-started/sql-server-2014-product-specifications.md) </span></span>  
 <span data-ttu-id="c8907-119">[SQL Server のインストール計画](../../../2014/sql-server/install/planning-a-sql-server-installation.md) </span><span class="sxs-lookup"><span data-stu-id="c8907-119">[Planning a SQL Server Installation](../../../2014/sql-server/install/planning-a-sql-server-installation.md) </span></span>  
 [<span data-ttu-id="c8907-120">SQL Server 2014 のインストールに必要なハードウェアおよびソフトウェア</span><span class="sxs-lookup"><span data-stu-id="c8907-120">Hardware and Software Requirements for Installing SQL Server 2014</span></span>](hardware-and-software-requirements-for-installing-sql-server.md)  
  
  
