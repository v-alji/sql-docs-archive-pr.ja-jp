---
title: SMO | の旧バージョンとの互換性Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
ms.assetid: 2f986436-aaf2-4eaf-9809-df849d97d4fb
author: stevestein
ms.author: sstein
ms.openlocfilehash: 73b6f4eebccf23850ccf08ec95ccb59dbc5c6293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640879"
---
# <a name="backward-compatibility-in-smo"></a><span data-ttu-id="9dcc1-102">SMO の旧バージョンとの互換性</span><span class="sxs-lookup"><span data-stu-id="9dcc1-102">Backward Compatibility in SMO</span></span>
  <span data-ttu-id="9dcc1-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の以前のバージョンを使用して記述されている SMO アプリケーションは、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の SMO を使用して再コンパイルできます。</span><span class="sxs-lookup"><span data-stu-id="9dcc1-103">SMO applications that were written using previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be recompiled by using SMO in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="migrating-smo-applications"></a><span data-ttu-id="9dcc1-104">SMO アプリケーションの移行</span><span class="sxs-lookup"><span data-stu-id="9dcc1-104">Migrating SMO Applications</span></span>  
 <span data-ttu-id="9dcc1-105">古いバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の SMO dll への参照は削除し、[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] で提供される新しい SMO dll への参照を含める必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dcc1-105">References to SMO dlls in older versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be removed, and references to the new SMO dlls that are provided with [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] must be included.</span></span>  
  
 <span data-ttu-id="9dcc1-106">少なくとも、以下の参照を設定してください。</span><span class="sxs-lookup"><span data-stu-id="9dcc1-106">Minimally, you would reference the following:</span></span>  
  
-   <span data-ttu-id="9dcc1-107">Microsoft.SqlServer.ConnectionInfo</span><span class="sxs-lookup"><span data-stu-id="9dcc1-107">Microsoft.SqlServer.ConnectionInfo</span></span>  
  
-   <span data-ttu-id="9dcc1-108">Microsoft.SqlServer.Smo</span><span class="sxs-lookup"><span data-stu-id="9dcc1-108">Microsoft.SqlServer.Smo</span></span>  
  
-   <span data-ttu-id="9dcc1-109">Microsoft.SqlServer.Management.Sdk.Sfc</span><span class="sxs-lookup"><span data-stu-id="9dcc1-109">Microsoft.SqlServer.Management.Sdk.Sfc</span></span>  
  
 <span data-ttu-id="9dcc1-110">これらのファイルは、接続クラス、SMO ユーティリティ クラス、および基盤クラスのために必要です。</span><span class="sxs-lookup"><span data-stu-id="9dcc1-110">These files are required for connection classes, SMO utility classes, and foundation classes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9dcc1-111">SmoEnum.dll は削除されたため、この dll への参照は SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] プロジェクトから削除する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dcc1-111">SmoEnum.dll has been removed so references to it must be removed from the SMO [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] project.</span></span>  
  
 <span data-ttu-id="9dcc1-112">名前空間も変更されたため、以下のものを使ってください。</span><span class="sxs-lookup"><span data-stu-id="9dcc1-112">The namespaces have also changed, so you can use the following:</span></span>  
  
##### <a name="for-visual-c"></a><span data-ttu-id="9dcc1-113">Visual C# 用</span><span class="sxs-lookup"><span data-stu-id="9dcc1-113">For Visual C#</span></span>  
  
```  
using Microsoft.SqlServer.Management.Smo;  
using Microsoft.SqlServer.Management.Common;  
```  
  
##### <a name="for-visual-basic"></a><span data-ttu-id="9dcc1-114">Visual Basic 用</span><span class="sxs-lookup"><span data-stu-id="9dcc1-114">For Visual Basic</span></span>  
  
```  
Imports Microsoft.SqlServer.Management.Smo  
Imports Microsoft.SqlServer.Management.Common  
```  
  
 <span data-ttu-id="9dcc1-115">コードで `Server.GetSqlSmoObject(Urn)` のような Urn 機能が使われている場合は、Microsoft.SqlServer.Management.Sdk.Sfc 名前空間へのリンクを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9dcc1-115">If your code uses Urn functionality, such as `Server.GetSqlSmoObject(Urn)`, you must link to the Microsoft.SqlServer.Management.Sdk.Sfc namespace.</span></span>  
  
 <span data-ttu-id="9dcc1-116">コードで Transfer オブジェクトを直接使用している場合は、Microsoft.SqlServer.Management.SmoExtended 名前空間へのリンクが必要になります。</span><span class="sxs-lookup"><span data-stu-id="9dcc1-116">If your code uses the Transfer object directly, you will have to link to the Microsoft.SqlServer.Management.SmoExtended namespace.</span></span>  
  
 <span data-ttu-id="9dcc1-117">コードを移行するときに、コードの修正が必要になる場合があります。</span><span class="sxs-lookup"><span data-stu-id="9dcc1-117">When you migrate code, you might have to modify the code.</span></span> <span data-ttu-id="9dcc1-118">これは、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ではいくつかの [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 機能および [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 機能が非推奨とされているためです。</span><span class="sxs-lookup"><span data-stu-id="9dcc1-118">This is because several [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] and [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] features have been deprecated in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9dcc1-119">非推奨の機能の詳細については、オンラインブックの「 [SQL Server 2014 の非推奨のデータベースエンジン機能](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md)」を参照してください [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9dcc1-119">For more information about deprecated features, see [Deprecated Database Engine Features in SQL Server 2014](../../database-engine/deprecated-database-engine-features-in-sql-server-2016.md) in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] Books Online.</span></span>  
  
  
