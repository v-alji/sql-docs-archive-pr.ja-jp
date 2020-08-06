---
title: レポートサーバーの複数インスタンス配置における URL 予約 (SSRS Configuration Manager) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- URL reservations
ms.assetid: f67c83c0-1f74-42bb-bfc1-e50c38152d3d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d2e51813ca2c85d089864dc5d2516e21ed975de4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87631644"
---
# <a name="url-reservations-for-multi-instance-report-server-deployments--ssrs-configuration-manager"></a><span data-ttu-id="5d4b1-102">レポート サーバーの複数インスタンス配置における URL 予約 (SSRS 構成マネージャー)</span><span class="sxs-lookup"><span data-stu-id="5d4b1-102">URL Reservations for Multi-Instance Report Server Deployments  (SSRS Configuration Manager)</span></span>
  <span data-ttu-id="5d4b1-103">同じコンピューターに [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の複数のインスタンスをインストールする場合は、インスタンスごとに URL 予約を定義する方法を検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-103">If you install multiple instances of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on the same computer, you must consider how you will define the URL reservations for each instance.</span></span> <span data-ttu-id="5d4b1-104">各インスタンス内のレポート サーバー Web サービスとレポート マネージャーには、それぞれ 1 つ以上の URL 予約が必要です。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-104">Within each instance, the Report Server Web service and Report Manager must have at least one URL reservation each.</span></span> <span data-ttu-id="5d4b1-105">予約はすべて、HTTP.SYS 内で一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-105">The entire set of reservations must be unique in HTTP.SYS.</span></span>  
  
 <span data-ttu-id="5d4b1-106">重複する URL があれば、サービスの起動時に行われる URL の登録の際に検出されます。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-106">Duplicate URLs are detected during URL registration, which occurs when the service starts.</span></span> <span data-ttu-id="5d4b1-107">一意でない URL 予約を作成した場合、サービスを起動するまで名前の競合が検出されない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-107">If you create URL reservations that are not unique, the name conflict might not be detected until you start the service.</span></span> <span data-ttu-id="5d4b1-108">このため、名前付け規則に従ってすべての値が一意になるようにしてください。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-108">For this reason, make sure that you follow naming conventions or rules to ensure all values are unique.</span></span>  
  
## <a name="default-naming-conventions"></a><span data-ttu-id="5d4b1-109">既定の名前付け規則</span><span class="sxs-lookup"><span data-stu-id="5d4b1-109">Default Naming Conventions</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="5d4b1-110">は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の名前付きインスタンス内にインストールできます。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-110">can be installed within a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] named instance.</span></span> <span data-ttu-id="5d4b1-111">名前付きインスタンス内にレポート サーバーをインストールまたは構成すると、 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] に用意されている既定の URL 予約の仮想ディレクトリにインスタンス名が自動的に含められます。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-111">When you install or configure a report server within a named instance, the instance name is automatically included in the virtual directory in the default URL reservation that [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] provides.</span></span> <span data-ttu-id="5d4b1-112">次の表に、既定のインスタンスと名前付きインスタンスの URL 予約を示します。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-112">The following table shows the URL reservations for a default instance and a named instance.</span></span>  
  
|<span data-ttu-id="5d4b1-113">SQL Server インスタンス</span><span class="sxs-lookup"><span data-stu-id="5d4b1-113">SQL Server Instance</span></span>|<span data-ttu-id="5d4b1-114">既定の URL 予約</span><span class="sxs-lookup"><span data-stu-id="5d4b1-114">Default URL Reservation</span></span>|  
|-------------------------|-----------------------------|  
|<span data-ttu-id="5d4b1-115">既定 (MSSQLServer)</span><span class="sxs-lookup"><span data-stu-id="5d4b1-115">Default (MSSQLServer)</span></span>|http://+:80/reportserver|  
|<span data-ttu-id="5d4b1-116">名前付き (MynamedInstance)</span><span class="sxs-lookup"><span data-stu-id="5d4b1-116">Named (MynamedInstance)</span></span>|http://+:80/reportserver_MyNamedInstance|  
  
 <span data-ttu-id="5d4b1-117">名前付きインスタンスの場合は、仮想ディレクトリにインスタンス名が含まれます。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-117">For the named instance, the virtual directory includes the instance name.</span></span> <span data-ttu-id="5d4b1-118">既定のインスタンスと名前付きインスタンスは同じポートでリッスンしますが、一意の仮想ディレクトリ名によって、どちらのレポート サーバーが要求を受け取るかが決定されます。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-118">Both the default instance and the named instance listen on the same port, but the unique virtual directory names determine which report server gets the request.</span></span>  
  
 <span data-ttu-id="5d4b1-119">レポート サーバー インスタンスは、仮想ディレクトリ名を使用して区別することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-119">Best practice recommendations are to use the virtual directory name to distinguish among the report server instance.</span></span> <span data-ttu-id="5d4b1-120">仮想ディレクトリ名によって URL と対象インスタンスの対応関係が明確になり、アプリケーション名がシステム全体で一意になります。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-120">It provides a clear correspondence between a URL and the target instance, and ensures that the application names are unique across the whole system.</span></span>  
  
## <a name="custom-naming-conventions"></a><span data-ttu-id="5d4b1-121">カスタム名前付け規則</span><span class="sxs-lookup"><span data-stu-id="5d4b1-121">Custom Naming Conventions</span></span>  
 <span data-ttu-id="5d4b1-122">インスタンス名を使用することをお勧めしますが、URL 構文と独自の名前付け規則を使用して URL 予約の一意の名前の制約を満たすこともできます。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-122">Although using the instance name is recommended, you can use the URL syntax and your own naming conventions to meet the unique name constraints for URL reservations.</span></span> <span data-ttu-id="5d4b1-123">次の例はそれぞれ、インスタンスごとに一意の URL を作成するための方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-123">The following examples illustrate different approaches for creating unique URLs for each instance.</span></span>  
  
|<span data-ttu-id="5d4b1-124">既定のレポート サーバー インスタンス (MSSQLSERVER)</span><span class="sxs-lookup"><span data-stu-id="5d4b1-124">Report Server default instance (MSSQLSERVER)</span></span>|<span data-ttu-id="5d4b1-125">ReportServer_MyNamedInstance</span><span class="sxs-lookup"><span data-stu-id="5d4b1-125">ReportServer_MyNamedInstance</span></span>|<span data-ttu-id="5d4b1-126">一意性</span><span class="sxs-lookup"><span data-stu-id="5d4b1-126">Uniqueness</span></span>|  
|----------------------------------------------------|-----------------------------------|----------------|  
|http://+:80/reportserver|http://+:8888/reportserver|<span data-ttu-id="5d4b1-127">各インスタンスが、別々のポートでリッスンします。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-127">Each instance listens on a different port.</span></span>|  
|`http://www.contoso.com/reportserver`|`http://SRVR-46/reportserver`|<span data-ttu-id="5d4b1-128">各インスタンスが、別々のサーバー名 (完全修飾ドメイン名およびコンピューター名) に応答します。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-128">Each instance responds to different server names (fully qualified domain name, and machine name).</span></span>|  
  
## <a name="uniqueness-requirements"></a><span data-ttu-id="5d4b1-129">一意性の要件</span><span class="sxs-lookup"><span data-stu-id="5d4b1-129">Uniqueness Requirements</span></span>  
 <span data-ttu-id="5d4b1-130">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] の基になるテクノロジには、一意の名前に関する要件があります。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-130">The underlying technologies used by [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] impose requirements around unique names.</span></span> <span data-ttu-id="5d4b1-131">HTTP.SYS のリポジトリ内の URL はすべて一意にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-131">HTTP.SYS requires that all URLs within its repository be unique.</span></span> <span data-ttu-id="5d4b1-132">URL は、ポート、ホスト名、または仮想ディレクトリ名を変えることで一意にできます。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-132">You can vary the port, host name, or virtual directory name to create a unique URL.</span></span> [!INCLUDE[vstecasp](../../includes/vstecasp-md.md)] <span data-ttu-id="5d4b1-133">では、同一プロセス内の各アプリケーション ID が一意である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-133">requires that application identities be unique within the same process.</span></span> <span data-ttu-id="5d4b1-134">この要件は、仮想ディレクトリ名に影響します。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-134">This requirement affects the virtual directory names.</span></span> <span data-ttu-id="5d4b1-135">この要件では、同一レポート サーバー インスタンス内では重複する仮想ディレクトリ名を使用できないことが規定されています。</span><span class="sxs-lookup"><span data-stu-id="5d4b1-135">It specifies that you cannot duplicate a virtual directory name within the same report server instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4b1-136">参照</span><span class="sxs-lookup"><span data-stu-id="5d4b1-136">See Also</span></span>  
 <span data-ttu-id="5d4b1-137">[レポート サーバー URL の構成 &#40;SSRS 構成マネージャー&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span><span class="sxs-lookup"><span data-stu-id="5d4b1-137">[Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md) </span></span>  
 [<span data-ttu-id="5d4b1-138">URL の構成 &#40;SSRS 構成マネージャー&#41;</span><span class="sxs-lookup"><span data-stu-id="5d4b1-138">Configure a URL  &#40;SSRS Configuration Manager&#41;</span></span>](configure-a-url-ssrs-configuration-manager.md)  
  
  
