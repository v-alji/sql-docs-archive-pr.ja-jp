---
title: SQL Server 2014 | の管理ツール機能における重大な変更Microsoft Docs
ms.custom: ''
ms.date: 11/27/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: 3ff3fad8-b569-4516-bd58-5a3efeb537e2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0487b6ab0958e0b83d4e8e34be507b5b3211ac87
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87642342"
---
# <a name="breaking-changes-to-management-tools-features-in-sql-server-2014"></a><span data-ttu-id="24089-102">SQL Server 2014 の管理ツール機能における重大な変更</span><span class="sxs-lookup"><span data-stu-id="24089-102">Breaking Changes to Management Tools Features in SQL Server 2014</span></span>
  <span data-ttu-id="24089-103">このトピックでは、管理ツール機能における重大な変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="24089-103">This topic describes breaking changes to management tools features.</span></span> <span data-ttu-id="24089-104">これらの変更によって、以前のバージョンの [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]に基づくアプリケーション、スクリプト、または機能が使用できなくなる場合があります。</span><span class="sxs-lookup"><span data-stu-id="24089-104">These changes might break applications, scripts, or functionalities that are based on earlier versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="24089-105">この問題は、アップグレードするときに発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="24089-105">You might encounter these issues when you upgrade.</span></span> <span data-ttu-id="24089-106">詳細については、「 [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24089-106">For more information, see [Use Upgrade Advisor to Prepare for Upgrades](../../2014/sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).</span></span>  
  
## <a name="breaking-changes-in-sssql14"></a><span data-ttu-id="24089-107">[!INCLUDE[ssSQL14](../includes/sssql14-md.md)] における重大な変更</span><span class="sxs-lookup"><span data-stu-id="24089-107">Breaking Changes in [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]</span></span>  
 <span data-ttu-id="24089-108">今後、情報が追加されていきます。</span><span class="sxs-lookup"><span data-stu-id="24089-108">Information to come later.</span></span>  
  
## <a name="breaking-changes-in-sssql11"></a><span data-ttu-id="24089-109">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] における重大な変更</span><span class="sxs-lookup"><span data-stu-id="24089-109">Breaking Changes in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
  
### <a name="you-cannot-use-sssql11-management-tools-to-create-a-utility-control-point-on-a-sskilimanjaro-instance-of-sql-server"></a><span data-ttu-id="24089-110">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] 管理ツールを使用して、SQL Server の [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] インスタンスにユーティリティ コントロール ポイントを作成することはできない</span><span class="sxs-lookup"><span data-stu-id="24089-110">You cannot use [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] Management Tools to create a utility control point on a [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] instance of SQL Server</span></span>  
 <span data-ttu-id="24089-111">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)]のインスタンスにユーティリティ コントロール ポイントを作成するには、 [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 管理ツールを使用してください。</span><span class="sxs-lookup"><span data-stu-id="24089-111">To create a utility control point on an instance of [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)], use [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] Management Tools.</span></span>  
  
### <a name="smo-has-been-reversioned-in-sssql11"></a><span data-ttu-id="24089-112">[!INCLUDE[ssSQL11](../includes/sssql11-md.md)] では SMO のバージョンが再設定されている</span><span class="sxs-lookup"><span data-stu-id="24089-112">SMO has been reversioned in [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]</span></span>  
 <span data-ttu-id="24089-113">[!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] 以前のバージョンの SMO で開発されたコードを [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] でビルドするには、若干の変更が必要になることがあります。</span><span class="sxs-lookup"><span data-stu-id="24089-113">Code developed with SMO from [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] or earlier versions might not build against [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] without minor modifications.</span></span> <span data-ttu-id="24089-114">旧バージョンとの互換性については、「 [SMO の旧バージョンとの互換性](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24089-114">For more information, see [Backward Compatibility in SMO](../relational-databases/server-management-objects-smo/backward-compatibility-in-smo.md).</span></span>  

## <a name="breaking-changes-in-sql-server-2005"></a><a name="previous-versions"></a><span data-ttu-id="24089-115">SQL Server 2005 での重大な変更</span><span class="sxs-lookup"><span data-stu-id="24089-115">Breaking Changes in SQL Server 2005</span></span>  

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a><span data-ttu-id="24089-116">参照</span><span class="sxs-lookup"><span data-stu-id="24089-116">See Also</span></span>  
 [<span data-ttu-id="24089-117">旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="24089-117">Backward Compatibility</span></span>](../../2014/getting-started/backward-compatibility.md)  
 [<span data-ttu-id="24089-118">SQL Server 2014 の管理ツール機能における重大な変更についての詳細</span><span class="sxs-lookup"><span data-stu-id="24089-118">More about Breaking Changes to Management Tools Features in SQL Server 2014</span></span>](breaking-changes-to-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)  
  
  
